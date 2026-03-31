Favor aplicar as seguintes melhorias técnicas nos arquivos index.html, style.css e script.js:"

Padrão de Formulário de Captação

Os formulários de contato não podem parecer modelos defasados.

- **Campos Indispensáveis:**
  - Nome, E-mail, Telefone (WhatsApp formatado com DDD) e um **Seletor de Assunto (`<select>`)**.
  - O campo de Seleção (`Como podemos ajudar?` ou `Assunto`) é obrigatório para segmentar o atendimento.
  - **Redirecionamento para o WhatsApp (Crucial):** Em vez de enviar o formulário "para o nada" ou gerar recarregamento nativo traumático, ao concluir o preenchimento, todas as informações captadas nos inputs devem ser concatenadas e o usuário deve ser redirecionado para a abertura do WhatsApp (Web ou App via `wa.me`) com uma mensagem perfeitamente formatada em lista.
  - A estrutura OBRIGATÓRIA da mensagem redirecionada via API do WhatsApp deve ser exatamente esta:
    ```text
    Olá, me chamo [NOME_DO_LEAD], vim através do site e gostaria de uma informação.

    - E-mail: [EMAIL_PREENCHIDO]
    - Telefone: [TELEFONE_PREENCHIDO]
    - Assunto/Serviço: [ASSUNTO_SELECIONADO]
    - Mensagem/Situação: [MENSAGEM_SE_HOUVER]
    ```