# Parte 02: Aprimorando a Interface com Inline Chat

Agora, você melhorará a experiência de carregamento usando o inline chat do Copilot.

> NOTA: Este exercício fornece prompts específicos para digitar, mas como parte da experiência de aprendizado, encorajamos você a descobrir como interagir com o Copilot. Sinta-se à vontade para usar linguagem natural, descrevendo o que você está procurando ou precisa realizar.

1. [] No **Solution Explorer**, no projeto **Store**, abra **Components/Pages/Products.razor**.
1. [] Encontre o texto "Loading..." no código.
1. [] Selecione este texto e clique com o botão direito.
1. [] Escolha "Chat" ou pressione `Alt+/`.
1. [] No inline chat, digite: `Update this razor to have a simple spinner style, using built in bootstrap styles.`

    ![Captura de tela do VS com inline chat](./images/2-inline-code.png)

1. [] Selecione **Tab** para aceitar as alterações, e o resultado deve ser semelhante a:  

    ```html
    <div class="spinner-border text-primary" role="status">
        <span class="visually-hidden">Loading...</span>
    </div>
    ```

1. [] Execute o aplicativo para ver o novo spinner de carregamento em ação.

1. [] Pare a depuração e feche o aplicativo

**Conclusão Principal**: O inline chat permite que você faça melhorias pontuais no seu código sem sair do contexto do editor.

---

[Voltar: Parte 01 - Completação de Código com Ghost Text](./part01-code-completion.md) | [Próximo: Parte 03 - Referenciando Arquivos de Código no Chat](./part03-referencing-files.md)
