# Parte 04: Usando Instruções Personalizadas

Sempre há informações essenciais que qualquer pessoa gerando código para sua base de código precisa saber — as tecnologias em uso, os padrões de codificação a seguir, a estrutura do projeto, etc. Como o contexto é tão importante, como discutimos, provavelmente queremos garantir que o Copilot sempre tenha essas informações. Felizmente, podemos fornecer essa visão geral por meio do uso de instruções do Copilot.

Antes de começarmos atualizações maiores no site com a ajuda do Copilot, queremos garantir que o Copilot tenha uma boa compreensão de como estamos construindo nossa aplicação. Por isso, vamos adicionar um arquivo de instruções do Copilot ao repositório.

As instruções do Copilot são um arquivo markdown colocado na sua pasta **.github**. Ele se torna parte do seu projeto e, por sua vez, está disponível para todos os contribuidores da sua base de código. Você pode usar este arquivo para indicar vários padrões de codificação que deseja seguir, as tecnologias que seu projeto usa, ou qualquer outra coisa importante para o Copilot Chat entender ao gerar sugestões.

> [!IMPORTANT]
> O arquivo *copilot-instructions.md* é incluído em **cada** chamada ao GitHub Copilot Chat e fará parte do contexto enviado ao Copilot. Como sempre há um conjunto limitado de tokens que um LLM pode operar, um arquivo de instruções grande pode obscurecer informações relevantes. Por isso, você deve limitar seu arquivo de instruções a informações de âmbito global do projeto, fornecendo uma visão geral do que você está construindo e como está construindo. Se precisar fornecer informações mais específicas para tarefas particulares, você pode criar [arquivos de prompt](https://docs.github.com/copilot/customizing-copilot/adding-repository-custom-instructions-for-github-copilot?tool=vscode#about-prompt-files).

Aqui estão algumas diretrizes a considerar ao criar um arquivo de instruções do Copilot:

- O arquivo de instruções do Copilot se torna parte do projeto, ou seja, se aplicará a todos os desenvolvedores; qualquer coisa indicada no arquivo deve ser globalmente aplicável.
- O arquivo é markdown, então você pode aproveitar isso agrupando conteúdo para melhorar a legibilidade.
- Forneça uma visão geral do **que** você está construindo e **como** está construindo, incluindo:
    - linguagens, frameworks e bibliotecas em uso.
    - ativos necessários a serem gerados (como testes unitários) e onde devem ser colocados.
    - quaisquer regras específicas de linguagem
- Se você notar que o GitHub Copilot fornece consistentemente uma sugestão inesperada (por exemplo, usando componentes de classe para React), adicione essas notas ao arquivo de instruções.

## Criar um arquivo de instruções do Copilot

1. [] No **Solution Explorer**, expanda o **GitHub Node** e abra **copilot-instructions.md**

1. [] Adicione informações específicas do projeto sobre sua aplicação:

    ```markdown
    ### Backend
    - Products project is the backend API.
    - Built with .NET Minimal APIs.
    - Uses Entity Framework Core with an in-memory database.
    - Should follow OpenAPI best practices.

    ### Frontend
    - Store project is a .NET 10 Blazor Server application.
    - Uses default Bootstrap styling.
    - UI should have a modern look and feel.
    - CSS should be in .razor.css files.
    ```
1. Inicie um novo chat clicando no ícone `+` no canto superior direito da janela de chat.

   ![Novo chat](./images/5-new-edits.png)

1. [] Volte ao Copilot Chat e re-execute o prompt da Parte 03; você pode fazer isso pressionando a tecla de seta para cima. ou
1. [] Pergunte: `How would I implement getting and visualizing the products in a table using the code in #ProductService and the css required.`
1. [] Revise a sugestão de código, mas não a implemente ainda.
1. [] Observe como as respostas agora incorporam suas instruções personalizadas.

**Conclusão Principal**: As instruções personalizadas tornam as sugestões do Copilot mais alinhadas com os padrões do seu projeto e as preferências de arquitetura.

---

[Voltar: Parte 03 - Referenciando Arquivos de Código no Chat](./part03-referencing-files.md) | [Próximo: Parte 05 - Implementando Funcionalidades com o Agente Copilot](./part05-implementing-features.md)
