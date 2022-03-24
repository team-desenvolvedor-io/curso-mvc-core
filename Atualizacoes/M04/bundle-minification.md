## Instale a ferramenta a seguir para ter acesso ao recurso de Bundling e Minification (próxima aula)

### APENAS VS 2017 e VS 2019
https://marketplace.visualstudio.com/items?itemName=MadsKristensen.BundlerMinifier

### APENAS VS 2022
https://marketplace.visualstudio.com/items?itemName=Failwyn.BundlerMinifier64

--- 

#### Execute esta ação no bundleconfig e logo após o seu Task Runner irá entender a configuração!

![image.png](https://desenvolvedorio.blob.core.windows.net/forum/47bdc937-ff69-4cab-acf4-dc20e0802e18.png)

---

### Todas versões do Visual Studio e Visual Studio Code:

#### Basta instalar o pacote a seguir no projeto web e seguir as mesmas recomendações do curso:

```
dotnet add package BuildBundlerMinifier
```

#### Apesar desta solução atender a qualquer cenário e ser compatível com qualquer versão do .NET e Visual Studio ela se comporta de forma invisível, não teremos visualização via Task Runner Explorer porém o output será exibido no log de compilação. 

#### Minha recomendação é observar se o arquivo de bundling está sendo gerado para validar o funcionamento correto do componente.

##### Outras referências:
- [Tutorial BuildBundlerMinifier](https://tattoocoder.com/simplifying-bundling-and-minification-asp-net-core/)

