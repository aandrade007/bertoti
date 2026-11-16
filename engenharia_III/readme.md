# Minhas contribuições

## Projeto de Design Patterns — Engenharia III

Implementei um mecanismo de eventos para acompanhar as atividades do atendimento sem acoplar diretamente os componentes do sistema. O mecanismo registra e notifica os componentes interessados sobre a criação de tickets, mudanças de estado, recebimento de mensagens e encerramento de conversas, usando as classes `SupportEventListener`, `SupportEventPublisher` e `EventLogger`.

<br>

## API do AI4PO


### Contibuições

- Criei o endpoint `POST /api/reformatar/`, que recebe um requisito em rascunho e o transforma em um PBI, uma Feature ou um Épico, usando um modelo local executado pelo Ollama.
- Também desenvolvi o prompt de análise de lacunas e contribuí para o histórico do chatbot.


- Implementei a autenticação JWT e a tela de login.
- Desenvolvi as operações de desativação, reativação e exclusão de logins, restritas a administradores. A exclusão é lógica: o registro permanece no banco, preservando projetos e documentos do PO e evitando exclusões em cascata.
- Garanti que logins desativados ou excluídos não possam autenticar e que sessões já abertas sejam invalidadas imediatamente, incluindo seus refresh tokens.
- Criei a tela administrativa com listagem, filtros e confirmação das ações.
- Implementei o cadastro e a edição de POs, com validação de campos e de e-mails duplicados, inclusive em relação a logins excluídos. O identificador (`id`) não é reaproveitado.
- Desenvolvi a tela de perfil, com os dados do usuário e a opção de logoff, que encerra a sessão no servidor.


- Criei uma rota para buscar profissionais por competência, ordenando os resultados por afinidade. A afinidade considera o percentual das competências buscadas que cada profissional possui; os desempates são feitos pelo foco (menos competências fora da busca) e, em seguida, pelo nome.
- A resposta da rota informa os critérios utilizados e justifica a posição de cada profissional.
- Desenvolvi a interface de busca, listagem e cadastro de profissionais, acessível a qualquer PO. Ela apresenta os critérios de afinidade, as competências que cada profissional possui e as que ainda faltam.
