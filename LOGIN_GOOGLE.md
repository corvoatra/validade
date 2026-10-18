# Login Google — preparação

Este trabalho está isolado na branch `feature/login-google`. O site publicado permanece inalterado.

## Objetivo
- Manter https://corvoatra.github.io/validade/
- Autenticar cada usuário com Google Identity Services (OAuth 2.0)
- Salvar os produtos e validades numa planilha no Drive da própria conta, sem compartilhar registros entre usuários
- Nunca inserir tokens de acesso, client secrets ou credenciais privadas no repositório

## Configuração necessária pelo proprietário
1. Acessar https://console.cloud.google.com/ e criar ou selecionar um projeto.
2. Configurar a tela de consentimento OAuth para o aplicativo, incluindo usuários de teste durante o desenvolvimento.
3. Criar um **OAuth Client ID** do tipo **Aplicativo da Web**.
4. Adicionar a origem JavaScript autorizada: `https://corvoatra.github.io` (origem, sem caminho).
5. Informar **apenas o Client ID público** para integrar a interface. **Não compartilhar client secret, token de acesso nem chave de API privada.**
6. Configurar os escopos mínimos necessários para Google Drive e Google Sheets, e realizar o fluxo de consentimento.

## Observações técnicas
- O site atual usa localStorage e não está sincronizado com a nuvem.
- A planilha de testes existente não deve ser usada como banco de dados comum a todos.
- Para planilhas individuais, o aplicativo deve operar com tokens OAuth do próprio usuário. O código deve evitar gravar tokens no localStorage e tratar expiração/revogação.
- O Google Apps Script atual, com ID de planilha fixo e execução como proprietário, **não** fornece isolamento por usuário.
- A implementação da autenticação, sincronização e migração dos dados locais virá após obter o Client ID e validar a configuração de permissões.
