```csharp
using AspNetCoreIdentity.Config;
using AspNetCoreIdentity.Extensions;

var builder = WebApplication.CreateBuilder(args);

// Adicionando suporte a Diversos arquivos de configuração por ambiente.
builder.Configuration
    .SetBasePath(builder.Environment.ContentRootPath)
    .AddJsonFile("appsettings.json", true, true)
    .AddJsonFile($"appsettings.{builder.Environment.EnvironmentName}.json", true, true)
    .AddEnvironmentVariables();

// Adicionando suporte a User Secrets
if (builder.Environment.IsProduction())
{
    builder.Configuration.AddUserSecrets<Program>();
}

// *** Configurando serviços no container ***

// Extension Method de configuração do Identity
builder.Services.AddIdentityConfig(builder.Configuration);

// Extension Method de Authorization (Policies)
builder.Services.AddAuthorizationConfig();

// Extension Method de resolução de DI
builder.Services.ResolveDependencies();

// Extension Method de configuração KissLog
builder.Services.RegisterKissLogListeners();

// Adicionando o MVC com suporte ao filtro de auditoria
builder.Services.AddControllersWithViews(options =>
{
    options.Filters.Add(typeof(AuditoriaFilter));
});

// Adicionando suporte a componentes Razor (ex: Telas do Identity)
builder.Services.AddRazorPages();

var app = builder.Build();

// *** Configurando o resquest dos serviços no pipeline ***

if (app.Environment.IsDevelopment())
{
    app.UseDeveloperExceptionPage();
    app.UseMigrationsEndPoint();
}
else
{
    app.UseExceptionHandler("/erro/500");
    app.UseStatusCodePagesWithRedirects("/erro/{0}");
    app.UseHsts();
}

// Força redirect para HTTPS
app.UseHttpsRedirection();

// Adicionando suporte a arquivos (ex: CSS, JS)
app.UseStaticFiles();

// Adicionando suporte a rota
app.UseRouting();

// Autenticacao e autorização (Identity)
app.UseAuthentication();
app.UseAuthorization();

// Rota padrão
app.MapControllerRoute("default", "{controller=Home}/{action=Index}/{id?}");

// Mapeando componentes Razor Pages (ex: Identity)
app.MapRazorPages();

// Adicionando suporte ao KissLog
app.RegisterKissLogListeners(builder.Configuration);

app.Run();
``` 
