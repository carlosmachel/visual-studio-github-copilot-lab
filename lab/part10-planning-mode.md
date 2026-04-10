# Parte 10: Modo de Planejamento no Agente

Ao trabalhar em funcionalidades complexas, é útil planejar antes de começar a implementação. O Modo de Planejamento do GitHub Copilot no Agente permite que você crie um plano estruturado para implementar novas funcionalidades. Isso ajuda a garantir que você entenda o escopo completo das alterações necessárias antes que qualquer código seja gerado.

Nesta parte, você usará o Modo de Planejamento para planejar e implementar uma funcionalidade que permite aos usuários navegar diretamente para a página de detalhes de um produto específico.

## Entendendo o Modo de Planejamento

O Modo de Planejamento é um recurso no Agente que ajuda você a:
- Dividir funcionalidades complexas em etapas gerenciáveis
- Entender todos os arquivos e alterações necessárias antes da implementação
- Revisar e refinar o plano antes que o Copilot comece a gerar código

## Criando um Plano para Navegação de Produtos

Vamos usar o Modo de Planejamento para implementar uma funcionalidade que permite aos usuários clicar em um produto na página de listagem e navegar para uma página de detalhes dedicada ao produto.

1. [] Abra a janela do Copilot Chat, se ainda não estiver aberta.
1. [] Crie uma nova sessão de chat.
1. [] Mude para o modo **Agent**.
1. [] Certifique-se de que o **Planning** está ativado nas ferramentas.

   ![Modo de Planejamento ativado](./images/10-planning-mode.png)

1. [] Insira o seguinte prompt:

   ```
   Create a plan for the following: I want to add product navigation to the TinyShop application. When a user clicks on a product in the product listing page, they should be taken to a new product detail page that shows:
   - The product image (larger size)
   - Product name as the page title
   - Full description
   - Price
   - A "Back to Products" button

   The URL should be /product/{id} where id is the product ID.
   ```

1. [] Revise o plano que o Copilot gera. Ele deve incluir:
   - Criação de um novo componente `ProductDetail.razor`
   - Atualização da configuração de roteamento
   - Modificação da listagem de produtos para incluir links de navegação
   - Adição de qualquer estilo CSS necessário
   - Etc.

   ![Plano Gerado](./images/10-generated-plan.png)

1. [] Se o plano parecer bom, clique em **Execute Plan** para iniciar a implementação.
1. [] Se quiser modificar o plano, você pode adicionar instruções adicionais ou pedir ao Copilot que revise etapas específicas.

## Revisando e Refinando o Plano

Antes de executar, é uma boa prática revisar o plano cuidadosamente:

1. [] Verifique se todos os arquivos necessários estão incluídos no plano.
1. [] Verifique se a abordagem está alinhada com a estrutura do seu projeto e os padrões de codificação.
1. [] Adicione quaisquer requisitos ausentes digitando instruções adicionais.

Por exemplo, você pode adicionar:

```
Update the plan to also ensure the product detail page handles cases where the product ID doesn't exist by showing a "Product not found" message.
```

## Executando o Plano

1. [] Uma vez satisfeito com o plano, diga ao copilot para **Execute Plan**.
1. [] O Copilot implementará cada etapa do plano, criando e modificando arquivos conforme necessário.
1. [] Revise as alterações no editor conforme são feitas.
1. [] Execute o aplicativo para testar a nova funcionalidade de navegação de produtos.

## Testando a Funcionalidade

1. [] Inicie o aplicativo com F5 ou Debug -> Start Debugging.
1. [] Navegue até a página de Produtos.
1. [] Clique em um produto na listagem.
1. [] Verifique se você é levado à página de detalhes do produto com as informações corretas.
1. [] Clique no botão "Back to Products" para retornar à listagem.

**Conclusão Principal**: O Modo de Planejamento ajuda você a pensar em funcionalidades complexas antes da implementação. Ao criar um plano estruturado, você pode garantir que todas as alterações necessárias sejam consideradas e revisar a abordagem antes que qualquer código seja gerado. Isso leva a um código melhor organizado e menos iterações.

---

[Voltar: Parte 09 - Servidores MCP](./part09-mcp.md) | [Próximo: Parte 11 - Arquivos de Prompt Reutilizáveis](./part11-reusable-prompts.md)
