## Devido as mudanças no ASP.NET 6 atente-se aos detalhes sobre as aulas a seguir caso esteja usando esta versão

### PS - Consulte sempre esta aula de referência no caso de dúvidas além da aula final com o código completo.

### Aula - Trabalhando na classe Startup.cs

#### Apesar da classe Startup.cs não existir mais, toda configuração deve ser feita da mesma maneira, porém agora na classe Program.cs (conforme visto nas atualizações das aulas anteriores)

#### A base da classe program.cs é sempre a seguinte:

```csharp
// Tudo começa a partir do Builder
var builder = WebApplication.CreateBuilder(args);

// *** Adicionar aqui os serviços no Container pipeline ***

// *** Ex: Adicionando o MVC
builder.Services.AddControllersWithViews();

// Nunca remover, deve ser sempre a última linha antes da configuração do request do pipeline
var app = builder.Build();

// *** Configure aqui o resquest dos serviços no pipeline *** 

// *** Ex: Adicionando a Rota padrão
app.MapControllerRoute("default", "{controller=Home}/{action=Index}/{id?}");

// Nunca remover, deve ser sempre a última linha.
app.Run();
```

---

### Aula - Protegendo dados com User Secrets

#### Todos processos realizados nesta aula permanecem válidos, atente-se apenas ao fato de que agora a implementação ocorre na classe program.cs da seguinte forma:

```csharp
// Tudo começa a partir do Builder
var builder = WebApplication.CreateBuilder(args);

builder.Configuration
    .SetBasePath(builder.Environment.ContentRootPath)
    .AddJsonFile("appsettings.json", true, true)
    .AddJsonFile($"appsettings.{builder.Environment.EnvironmentName}.json", true, true)
    .AddEnvironmentVariables();

// Adicionando suporte ao secrets apenas em ambiente de produção, retire este IF se deseja aplicar os secrets para qualquer ambiente.
if (builder.Environment.IsProduction())
{
    builder.Configuration.AddUserSecrets<Program>();
}

// *** Adicionar aqui os serviços no Container pipeline ***
```

---

### Aula - Realizando o Log de tudo!

#### A implemementação do KissLog mudou um pouco devido a evolução do componente, baixe o projeto atualizado para conferir as mudanças:

- Versão do pacote KissLog
- Configuração do IKLogger
- Registro do Middleware
    
Roteiro atualizado [Docs do KissLogger](https://kisslog.net/Docs/SDK.install-instructions.netcore-webApp.html)



