## Siga o roteiro abaixo para reproduzir no Visual Studio 2022 com ASP.NET 6 o mesmo procedimento realizado na aula "Criando um projeto MVC sem template"

### Na janela inicial do Visual Studio 2022, crie um novo projeto

![image](https://user-images.githubusercontent.com/5068797/159869071-382fad75-7043-44f2-81ee-f4fed7744f37.png)

### Pesquise pelo template "Blank Solution" e na sequência defina seu nome como "AppModelo"

![image](https://user-images.githubusercontent.com/5068797/159869300-5c392f6b-52c3-446e-b68c-87e075aaa7e5.png)

### Agora está na hora de adicionar o projeto MVC Vazio

![image](https://user-images.githubusercontent.com/5068797/159869410-dee4b740-b37c-49ed-b7c9-bc2e809f1739.png)

### Pesquise por Empty e selecione o modelo conforme a imagem

![image](https://user-images.githubusercontent.com/5068797/159869521-53b82704-a80d-43e4-8803-b5ffef8a94f0.png)

### Defina o nome do projeto como DevIO.UI.Site

![image](https://user-images.githubusercontent.com/5068797/159869585-33b0d506-eb20-484b-a957-d87f7d9a5830.png)

### Defina a versão do .NET a ser utilizada (neste caso a 6.0)

![image](https://user-images.githubusercontent.com/5068797/159869622-53cefb68-b632-4a13-84f3-6bf5880a6bbd.png)

### O resultado do projeto criado é esta estrutura de pastas:

![image](https://user-images.githubusercontent.com/5068797/159869702-3cecf1eb-4ed6-4d6d-9744-c08444cbc4d6.png)

### Analisando a classe Program.cs ela vem naturalmente o mais simples possível:

```csharp
// Builder que será o meio de acesso de todos os recursos
var builder = WebApplication.CreateBuilder(args);

// Construção da APP
var app = builder.Build();

// Definindo uma rota simples (raiz) onde retornará um texto
app.MapGet("/", () => "Hello World!");

// Rodando a APP
app.Run();
```

### Para dar seguimento a próxima aula onde o front-end será customizado é importante modificar a Program.cs para a seguinte configuração:

```csharp
// Tudo inicia a partir do builder
var builder = WebApplication.CreateBuilder(args);

// Adicionando o MVC ao container
builder.Services.AddControllersWithViews();

// Realizando o buid das configurações que resultará na App
var app = builder.Build();

// Ativando a pagina de erros caso seja ambiente de desenvolvimento
if (app.Environment.IsDevelopment())
{
    app.UseDeveloperExceptionPage();
}

// Adicionando Rota padrão
app.MapControllerRoute(
    name: "default",
    pattern: "{controller=Home}/{action=Index}/{id?}");

// Colocando a App para rodar
app.Run();
```


