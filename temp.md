## Criando o projeto utilizando apenas o CLI e VS Code

#### Para obter o mesmo resultado da criação do projeto via Visual Studio siga os passos a seguir:

1) ##### Em seu terminal crie uma pasta para a criação do projetos (ex: "C:/Demos/MinhaAppFuncional") e navegue até esta pasta.
2) ##### Execute o comando a seguir:

```cmd
dotnet new sln -n MinhaAppFuncional
```

3) ##### Agora crie uma pasta chamada "src" e navegue até ela
4) ##### Execute o comando a seguir:

```cmd
dotnet new mvc -n AppMvcFuncional --auth Individual
```
5) ##### Navegue até a pasta AppMvcFuncional e execute o comando para associação da Solution com o projeto:

```cmd
dotnet sln ../../MinhaAppFuncional.sln add AppMvcFuncional.csproj
```

6) ##### Navegue até o nivel de diretório da Solution (*.sln) e execute o comando para chamar o VS Code:

```cmd
code . 
```

#### O VS Code abrirá da seguinte forma:
![image](https://github.com/team-desenvolvedor-io/eduardo-pires/assets/5068797/1a71c1c7-b275-47f8-874b-5dccb8eec3f4)

#### Caso esteja usando o C# Dev Kit no VS Code poderá usar o Solution Explorer dessa forma:
![image](https://github.com/team-desenvolvedor-io/eduardo-pires/assets/5068797/21421f1f-8723-4d87-98d8-252104b6328b)



