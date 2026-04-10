# Parte 11: Arquivos de Prompt Reutilizáveis

Os arquivos de prompt são uma maneira poderosa de criar prompts padronizados e reutilizáveis que podem ser compartilhados com toda a sua equipe. Eles ajudam a garantir consistência na forma como você interage com o GitHub Copilot e podem incorporar as melhores práticas para tarefas comuns como geração de código, testes e documentação.

Nesta parte, você criará um arquivo de prompt reutilizável para gerar testes unitários e o usará para adicionar testes ao projeto TinyShop.Tests existente.

## Entendendo os Arquivos de Prompt

Os arquivos de prompt são arquivos markdown armazenados na pasta `.github/prompts` do seu repositório. Eles:
- Podem ser invocados pelo nome no Copilot Chat
- São compartilhados com toda a sua equipe através do controle de versão
- Podem incluir espaços reservados para conteúdo dinâmico
- Ajudam a padronizar tarefas comuns de desenvolvimento

## Explorando o Projeto de Testes

A solução já inclui um projeto **TinyShop.Tests** com o MSTest configurado. Vamos dar uma olhada no que está disponível.

1. [] No **Solution Explorer**, expanda o projeto **TinyShop.Tests**.
1. [] Abra **ProductTests.cs** para ver o teste de referência existente.
1. [] Observe que o teste segue o padrão Arrange-Act-Assert e verifica os valores padrão de uma nova instância de Product.

## Criando um Arquivo de Prompt para Testes Unitários

Agora vamos criar um arquivo de prompt que ajuda a gerar testes unitários adicionais usando o MSTest.

1. [] No **Solution Explorer** veremos o nó **GitHub** da extensão para adicioná-lo facilmente:
   - Clique com o botão direito no ícone/extensão do nó **GitHub** no Visual Studio.
   - Escolha **Add Copilot File...**.
   - Selecione **Prompt file...** no diálogo.
   - Altere o nome do arquivo para `unit-test.prompt.md` e clique em **OK**.
   - O novo arquivo abrirá no editor; cole o conteúdo mostrado abaixo no arquivo e salve.

1. [] Se você puder criar o arquivo manualmente no explorador de arquivos, adicione um novo arquivo chamado `unit-test.prompt.md` em `.github/prompts` e cole o conteúdo abaixo.

1. [] Atualize o arquivo de prompt com o seguinte conteúdo:

   ```markdown
   ---
   mode: agent
   description: Generate comprehensive unit tests using MSTest
   ---

   # Unit Test Generator

   Generate unit tests for the selected code using the MSTest framework.

   ## Requirements

   - Use MSTest attributes ([TestClass], [TestMethod], [DataRow])
   - Follow the Arrange-Act-Assert pattern
   - Include both positive and negative test cases
   - Test edge cases and boundary conditions
   - Use descriptive test method names that explain what is being tested
   - Mock dependencies where appropriate

   ## Test Structure

   Each test should:
   1. Have a clear name following the pattern: `MethodName_Scenario_ExpectedBehavior`
   2. Include a brief comment explaining the test purpose
   3. Use proper assertions with meaningful failure messages

   ## Context

   Generate tests for: ${input:Describe what you want to test}
   ```

1. [] Salve o arquivo.

## Usando o Prompt Reutilizável

Agora vamos usar nosso novo arquivo de prompt para gerar testes unitários adicionais para a classe Product.

1. [] No Copilot Chat, digite `/` para ver os arquivos de prompt disponíveis.
1. [] Selecione `unit-test` da lista de prompts disponíveis.
1. [] Quando solicitado para entrada, digite: `the Product class in DataEntities, including tests for setting and getting each property, and tests using DataRow for multiple values`

   ![Usando um arquivo de prompt](./images/11-prompt-file.png)

1. [] Revise os testes gerados. Eles devem incluir:
   - Testes para cada propriedade (Name, Description, Price, ImageUrl)
   - Testes usando DataRow para testes parametrizados
   - Nomenclatura adequada dos métodos de teste seguindo o padrão
   - Comentários explicando os propósitos dos testes

## Exemplo de Testes Gerados

Os testes gerados devem ser semelhantes a:

```csharp
[TestMethod]
public void Name_SetValue_ReturnsExpectedValue()
{
    // Arrange
    var product = new Product();
    var expectedName = "Test Product";

    // Act
    product.Name = expectedName;

    // Assert
    Assert.AreEqual(expectedName, product.Name);
}

[TestMethod]
[DataRow(19.99)]
[DataRow(0)]
[DataRow(999.99)]
public void Price_SetValue_ReturnsExpectedValue(double price)
{
    // Arrange
    var product = new Product();
    var expectedPrice = (decimal)price;

    // Act
    product.Price = expectedPrice;

    // Assert
    Assert.AreEqual(expectedPrice, product.Price);
}

[TestMethod]
[DataRow("product1.png")]
[DataRow("product2.png")]
[DataRow("")]
public void ImageUrl_SetValue_ReturnsExpectedValue(string imageUrl)
{
    // Arrange
    var product = new Product();

    // Act
    product.ImageUrl = imageUrl;

    // Assert
    Assert.AreEqual(imageUrl, product.ImageUrl);
}
```

## Executando os Testes

1. [] Abra o **Test Explorer** em **Test -> Test Explorer**.
1. [] Compile a solução para descobrir os testes.
1. [] Clique em **Run All** para executar todos os testes, incluindo os novos testes gerados.
1. [] Verifique se todos os testes passam.

**Conclusão Principal**: Os arquivos de prompt reutilizáveis ajudam a padronizar como sua equipe usa o GitHub Copilot. Ao criar prompts para tarefas comuns como testes unitários, você garante consistência e incorpora as melhores práticas das quais todos na equipe podem se beneficiar.

---

[Voltar: Parte 10 - Modo de Planejamento no Agente](./part10-planning-mode.md) ← | [Próximo: Parte 12 - Delegar para a Nuvem](./part12-delegate-to-cloud.md) →
