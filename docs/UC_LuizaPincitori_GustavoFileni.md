---

## UC01 — Realizar Login (UC EXEMPLO - FAZER DESSA FORMA PARA TODOS OS CASOS DE USO, NESSE MESMO DOCUMENTO)

### Ator Principal

Usuário (Aluno, Instrutor, Recepcionista ou Gerente)

### Objetivo

Permitir que o usuário acesse as funcionalidades do sistema de acordo com seu perfil.

### Pré-condições

* Usuário deve possuir cadastro ativo no sistema.
* Conexão com o servidor ativa.

### Pós-condições

* Sessão iniciada com sucesso e redirecionamento para o dashboard correspondente.

### Fluxo Principal

1. O usuário informa e-mail e senha na tela de acesso.
2. O sistema valida as credenciais contra a base de dados criptografada.
3. O sistema identifica o perfil do usuário (RN06).
4. O sistema autentica o usuário e redireciona para a tela inicial específica do perfil.

### Fluxos Alternativos

* **A1 — Senha incorreta:** O sistema exibe mensagem de erro: "Credenciais inválidas".
* **A2 — Conta bloqueada:** O sistema impede o login e instrui o usuário a recuperar o acesso ou procurar o gerente.

### RF Relacionados

* **RF01 — Cadastro de Alunos:** Base de dados de usuários para autenticação.

### RNF Relacionados

* **RNF02 — Segurança:** Armazenamento de dados sensíveis (senhas) de forma criptografada.
* **RNF03 — Performance:** Tempo máximo de resposta de até 3 segundos para validar o acesso.

### RN Relacionadas

* **RN06 — Acesso restrito por perfil:** Cada perfil (Recepcionista, Instrutor, Gerente) possui permissões específicas após o login.

---

## UC02 — Cadastrar Aluno

### Ator Principal
Recepcionista

### Objetivo
Registrar um novo aluno no sistema para permitir o acesso às dependências da academia e contratação de serviços.

### Pré-condições
- O Recepcionista deve estar autenticado no sistema.

### Pós-condições
- O registro do aluno é salvo no banco de dados.
- O aluno está apto a realizar pagamentos.

### Fluxo Principal
1. O Recepcionista acessa o menu "Cadastro de Alunos".
2. O sistema exibe o formulário de cadastro.
3. O Recepcionista insere os dados pessoais, contato, endereço e seleciona o plano.
4. O sistema valida se o CPF é único e se os campos obrigatórios foram preenchidos.
5. O sistema salva os dados e exibe mensagem de sucesso.

### Fluxos Alternativos
- **A1 — CPF já cadastrado:** O sistema exibe mensagem de erro e solicita correção.
- **A2 — Dados incompletos:** O sistema destaca os campos vazios e impede o salvamento.

### RF Relacionados
- RF01 — Cadastro de Alunos

### RNF Relacionados
- RNF02 — Segurança
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

---

## UC03 — Gerenciar Planos de Acesso

### Ator Principal
Gerente

### Objetivo
Criar ou editar modalidades de planos (mensal, anual, etc.).

### Pré-condições
- Usuário logado com perfil de Gerente.

### Pós-condições
- Novo plano disponível para venda na recepção.

### Fluxo Principal
1. O Gerente acessa "Configurações de Planos".
2. O Gerente define nome, valor, duração e modalidades inclusas.
3. O sistema registra o plano no catálogo ativo.

### Fluxos Alternativos
- **A1 — Desativar plano:** O Gerente marca um plano como inativo; novos alunos não podem aderir a ele, mas contratos antigos permanecem válidos.

### RF Relacionados
- RF02 — Gerenciamento de Planos

### RNF Relacionados
- RNF05 — Escalabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

---

## UC04 — Registrar Pagamento na Recepção

### Ator Principal
Recepcionista

### Objetivo
Realizar a baixa manual de mensalidades via dinheiro, cartão ou PIX.

### Pré-condições
- Aluno deve estar cadastrado.

### Pós-condições
- Status de regularidade do aluno atualizado para "Em dia".
- Recibo gerado.

### Fluxo Principal
1. O Recepcionista busca o aluno pelo nome ou CPF.
2. Seleciona a mensalidade em aberto.
3. Escolhe a forma de pagamento (Dinheiro, Cartão ou PIX).
4. O sistema confirma o recebimento e atualiza o status.

### Fluxos Alternativos
- **A1 — Pagamento Parcial:** O sistema bloqueia a operação conforme regra de negócio.

### RF Relacionados
- RF03 — Controle de Pagamentos
- RF04 — Regularidade do Aluno

### RNF Relacionados
- RNF03 — Performance

### RN Relacionadas
- RN04 — Pagamento parcial (Proibido)
- RN07 — Atualização automática da regularidade

---

## UC05 — Validar Acesso na Catraca

### Ator Principal
Aluno / Sistema de Catraca

### Objetivo
Controlar a entrada física do aluno na unidade.

### Pré-condições
- Integração via API ativa.

### Pós-condições
- Acesso liberado ou bloqueado.
- Registro de log de entrada.

### Fluxo Principal
1. O Aluno aproxima a tag RFID da catraca.
2. A catraca envia o ID para o sistema via API JSON.
3. O sistema verifica a regularidade financeira.
4. O sistema retorna comando de "Liberar" para a catraca.

### Fluxos Alternativos
- **A1 — Inadimplência:** O sistema identifica atraso > 5 dias e retorna "Bloqueado".

### RF Relacionados
- RF05 — Controle de Acesso
- RF04 — Regularidade do Aluno

### RNF Relacionados
- RNF03 — Performance (Resposta < 3s)
- RNF06 — Integração (API REST)

### RN Relacionadas
- RN01 — Bloqueio por inadimplência

---


## UC06 — Agendar Aula em Grupo

### Ator Principal

Aluno

### Objetivo

Permitir que o aluno reserve uma vaga em uma aula específica.

### Pré-condições

* Aluno deve estar com a mensalidade em dia (Regular).
* Deve haver vagas disponíveis na aula desejada.

### Pós-condições

* Reserva confirmada e vaga subtraída do total disponível.

### Fluxo Principal

1. O Aluno acessa o módulo de "Agendamento" via mobile.
2. O sistema exibe a lista de aulas, horários e vagas.
3. O Aluno seleciona a aula desejada e confirma a reserva.
4. O sistema valida a regularidade do aluno e a disponibilidade de vaga.
5. O sistema confirma o agendamento.

### Fluxos Alternativos

* **A1 — Aula Lotada:** O sistema impede o agendamento e informa que não há vagas.
* **A2 — Aluno Inadimplente:** O sistema impede a reserva e direciona para o financeiro.

### RF Relacionados

* **RF06 — Agendamento de Aulas:** Visualizar horários e reservar vagas.
* **RF04 — Regularidade do Aluno:** Verificar se o aluno está em dia.

### RNF Relacionados

* **RNF04 — Usabilidade:** Interface intuitiva e responsiva para mobile.

### RN Relacionadas

* **RN02 — Limite de vagas:** Bloqueio de agendamento ao atingir o limite.

---

## UC07 — Cancelar Agendamento de Aula

### Ator Principal

Aluno

### Objetivo

Permitir que o aluno desista de uma reserva previamente feita.

### Pré-condições

* Possuir uma reserva ativa.

### Pós-condições

* Reserva cancelada e vaga liberada.

### Fluxo Principal

1. O Aluno visualiza seus agendamentos ativos.
2. O Aluno solicita o cancelamento da aula selecionada.
3. O sistema verifica se o horário atual respeita o limite de antecedência.
4. O sistema processa o cancelamento.

### Fluxos Alternativos

* **A1 — Fora do prazo:** O sistema informa que o cancelamento não é mais possível por estar a menos de 1 hora do início.

### RF Relacionados

* **RF06 — Agendamento de Aulas:** Gerenciamento de reservas.

### RNF Relacionados

* **RNF03 — Performance:** Tempo de resposta de até 3 segundos.

### RN Relacionadas

* **RN03 — Cancelamento de agendamento:** Permitido até 1 hora antes do início.

---

## UC08 — Registrar Presença em Aula

### Ator Principal

Instrutor

### Objetivo

Confirmar a presença dos alunos agendados.

### Pré-condições

* Instrutor autenticado.

### Pós-condições

* Lista de presença atualizada.

### Fluxo Principal

1. O Instrutor acessa a lista de agendados para sua aula.
2. O Instrutor marca a presença para cada aluno presente.
3. O Instrutor salva a lista.

### Fluxos Alternativos

* **A1 — Adição manual:** O Instrutor adiciona um aluno que não agendou, mas o sistema valida se há vaga disponível antes de permitir.

### RF Relacionados

* **RF07 — Lista de Presença:** Registro de presença pelos instrutores.

### RNF Relacionados

* **RNF04 — Usabilidade:** Interface intuitiva.

### RN Relacionadas

* **RN06 — Acesso restrito por perfil:** Permissão específica para o Instrutor.

---

## UC09 — Realizar Avaliação Física

### Ator Principal

Instrutor

### Objetivo

Registrar métricas corporais e progresso do aluno.

### Pré-condições

* Aluno deve estar ativo e regular.

### Pós-condições

* Avaliação salva e notificação enviada ao aluno.

### Fluxo Principal

1. O Instrutor seleciona o aluno.
2. O sistema valida se o aluno está regular (RN05).
3. O Instrutor insere dados (peso, IMC, etc.) e anexa arquivos se necessário.
4. O Instrutor finaliza a avaliação.

### Fluxos Alternativos

* **A1 — Aluno Irregular:** O sistema bloqueia a criação da avaliação.

### RF Relacionados

* **RF08 — Avaliação Física:** Registro de peso, IMC e percentual de gordura.
* **RF10 — Notificações:** Enviar alerta de liberação de nova avaliação.

### RNF Relacionados

* **RNF02 — Segurança:** Dados sensíveis armazenados de forma criptografada.

### RN Relacionadas

* **RN05 — Avaliação física:** Realizada apenas se o aluno estiver ativo e regular.

---

## UC10 — Emitir Relatório de Inadimplência

### Ator Principal

Gerente

### Objetivo

Identificar alunos com pagamentos atrasados.

### Pré-condições

* Perfil de Gerente.

### Pós-condições

* Relatório gerado.

### Fluxo Principal

1. O Gerente acessa "Relatórios Gerenciais".
2. Seleciona "Inadimplência".
3. O sistema lista todos os alunos com mensalidades vencidas.

### Fluxos Alternativos

* **A1 — Nenhum atraso:** O sistema informa que não há pendências financeiras.

### RF Relacionados

* **RF09 — Relatórios Gerenciais:** Emissão de relatório de inadimplência.

### RNF Relacionados

* **RNF05 — Escalabilidade:** Suporte a múltiplas unidades da rede.

### RN Relacionadas

* **RN06 — Acesso restrito por perfil:** Gerente tem permissão para relatórios.

---

## UC11 — Notificar Vencimento de Mensalidade

### Ator Principal

Sistema

### Objetivo

Avisar o aluno sobre o vencimento da fatura.

### Pré-condições

* Mensalidade próxima ao vencimento ou vencida.

### Pós-condições

* Notificação enviada.

### Fluxo Principal

1. O sistema verifica diariamente as datas de vencimento.
2. Identifica alunos com faturas pendentes.
3. Envia notificação automática para o aluno.

### Fluxos Alternativos

* **A1 — Falha no envio:** O sistema tenta reenviar na próxima execução agendada.

### RF Relacionados

* **RF10 — Notificações:** Envio sobre vencimento de mensalidade.

### RNF Relacionados

* **RNF01 — Disponibilidade:** Sistema disponível 99% do tempo.

### RN Relacionadas

* **RN07 — Atualização automática da regularidade:** Sincronia entre pagamento e status.

---

## UC12 — Consultar Histórico de Acessos

### Ator Principal

Gerente

### Objetivo

Monitorar o fluxo de alunos na academia.

### Pré-condições

* Perfil de Gerente.

### Pós-condições

* Lista de acessos exibida.

### Fluxo Principal

1. O Gerente acessa "Relatório de Acessos".
2. Filtra por período e/ou unidade.
3. O sistema exibe os logs de entrada registrados pela catraca.

### Fluxos Alternativos

* **A1 — Filtro vazio:** O sistema informa que não houve registros no período.

### RF Relacionados

* **RF09 — Relatórios Gerenciais:** Histórico de acessos.
* **RF05 — Controle de Acesso:** Integração com dados da catraca.

### RNF Relacionados

* **RNF03 — Performance:** Resposta rápida na consulta.

### RN Relacionadas

* **RN06 — Acesso restrito por perfil:** Acesso permitido ao Gerente.

---

## UC13 — Gerar Boleto/QR Code PIX Online

### Ator Principal

Aluno

### Objetivo

Permitir pagamento remoto da mensalidade.

### Pré-condições

* Aluno possui fatura em aberto.

### Pós-condições

* Documento de pagamento gerado.

### Fluxo Principal

1. O Aluno acessa o portal/app.
2. Seleciona a mensalidade pendente.
3. Solicita a geração do boleto ou PIX.
4. O sistema gera o código via integração.

### Fluxos Alternativos

* **A1 — Erro de Integração:** O sistema informa indisponibilidade e sugere tentar mais tarde.

### RF Relacionados

* **RF03 — Controle de Pagamentos:** Gerar boletos/cartões online.

### RNF Relacionados

* **RNF02 — Segurança:** Criptografia de dados de pagamento.
* **RNF06 — Integração:** Comunicação via API REST.

### RN Relacionadas

* **RN04 — Pagamento parcial:** Não é permitido; valor deve ser integral.

---

## UC14 — Editar Cadastro de Aluno

### Ator Principal

Recepcionista

### Objetivo

Atualizar informações de um aluno.

### Pré-condições

* Aluno previamente cadastrado.

### Pós-condições

* Cadastro atualizado.

### Fluxo Principal

1. O Recepcionista localiza o aluno.
2. Altera os dados necessários (telefone, endereço, etc).
3. O sistema valida e salva as alterações.

### Fluxos Alternativos

* **A1 — Cancelamento da edição:** Os dados permanecem como estavam antes da alteração.

### RF Relacionados

* **RF01 — Cadastro de Alunos:** Permitir editar dados pessoais e contato.

### RNF Relacionados

* **RNF04 — Usabilidade:** Interface intuitiva.

### RN Relacionadas

* **RN06 — Acesso restrito por perfil:** Recepcionista realiza matrículas e cadastros.

---

## UC15 — Emitir Relatório de Ocupação de Aulas

### Ator Principal

Gerente

### Objetivo

Analisar a lotação das aulas para tomada de decisão.

### Pré-condições

* Perfil de Gerente.

### Pós-condições

* Dados de ocupação exibidos.

### Fluxo Principal

1. O Gerente seleciona o relatório de ocupação.
2. Define o período de análise.
3. O sistema apresenta a relação entre vagas totais e vagas preenchidas.

### Fluxos Alternativos

* **A1 — Exportação:** O Gerente exporta o relatório em PDF.

### RF Relacionados

* **RF09 — Relatórios Gerenciais:** Ocupação das aulas.

### RNF Relacionados

* **RNF05 — Escalabilidade:** Processamento de dados de múltiplas unidades.

### RN Relacionadas

* **RN02 — Limite de vagas:** Relatório baseado na capacidade máxima das aulas.

---

## UC16 — Ativar/Desativar Plano

### Ator Principal

Gerente

### Objetivo

Controlar a disponibilidade de planos de venda.

### Pré-condições

* Perfil de Gerente.

### Pós-condições

* Status do plano atualizado.

### Fluxo Principal

1. O Gerente acessa a lista de planos.
2. Seleciona um plano e altera seu status para "Inativo" ou "Ativo".
3. O sistema confirma a operação.

### Fluxos Alternativos

* **A1 — Plano com alunos vinculados:** O sistema desativa para novas vendas, mas mantém para alunos atuais.

### RF Relacionados

* **RF02 — Gerenciamento de Planos:** Ativar e desativar tipos de planos.

### RNF Relacionados

* **RNF01 — Disponibilidade:** Manter o serviço de gestão ativo.

### RN Relacionadas

* **RN06 — Acesso restrito por perfil:** Gerente configura os planos.

---

## UC17 — Consultar Regularidade do Aluno

### Ator Principal

Recepcionista

### Objetivo

Verificar se o aluno pode entrar ou agendar aulas.

### Pré-condições

* Aluno cadastrado.

### Pós-condições

* Status financeiro exibido.

### Fluxo Principal

1. O Recepcionista pesquisa o aluno.
2. O sistema exibe o status de regularidade e últimas faturas.

### Fluxos Alternativos

* **A1 — Aluno Inadimplente:** O sistema destaca o débito e o tempo de atraso.

### RF Relacionados

* **RF04 — Regularidade do Aluno:** Verificar se a mensalidade está em dia.

### RNF Relacionados

* **RNF03 — Performance:** Tempo de resposta de até 3 segundos.

### RN Relacionadas

* **RN01 — Bloqueio por inadimplência:** Alunos com atraso > 5 dias não podem entrar.

---

## UC18 — Notificar Liberação de Avaliação

### Ator Principal

Sistema

### Objetivo

Informar o aluno que seus resultados estão disponíveis.

### Pré-condições

* Avaliação física finalizada pelo Instrutor.

### Pós-condições

* Aluno notificado.

### Fluxo Principal

1. O sistema detecta o salvamento de uma nova avaliação.
2. Dispara automaticamente uma notificação para o aluno.

### Fluxos Alternativos

* **A1 — Falha no Push:** O sistema registra no log e o aluno verá ao abrir o app.

### RF Relacionados

* **RF10 — Notificações:** Liberação de nova avaliação física.
* **RF08 — Avaliação Física:** Fonte do dado da notificação.

### RNF Relacionados

* **RNF06 — Integração:** Uso de API para envio de notificações.

### RN Relacionadas

* **RN05 — Avaliação física:** Vinculada ao status do aluno.

---

## UC19 — Vincular Tag RFID

### Ator Principal

Recepcionista

### Objetivo

Associar um dispositivo de acesso ao aluno.

### Pré-condições

* Perfil de Recepcionista.

### Pós-condições

* RFID vinculado ao cadastro.

### Fluxo Principal

1. O Recepcionista acessa o perfil do aluno.
2. Clica em "Vincular RFID".
3. O aluno aproxima a tag no leitor.
4. O sistema registra o ID único.

### Fluxos Alternativos

* **A1 — Tag duplicada:** O sistema avisa que a tag já pertence a outro aluno.

### RF Relacionados

* **RF05 — Controle de Acesso:** Integrar à catraca via RFID.

### RNF Relacionados

* **RNF06 — Integração:** Comunicação via API REST JSON.

### RN Relacionadas

* **RN06 — Acesso restrito por perfil:** Recepcionista realiza o vínculo.

---

## UC20 — Realizar Login

### Ator Principal

Usuário (Aluno, Instrutor, Recepcionista ou Gerente)

### Objetivo

Permitir acesso seguro ao sistema.

### Pré-condições

* Usuário possuir cadastro ativo.

### Pós-condições

* Sessão iniciada com permissões de perfil.

### Fluxo Principal

1. O usuário informa e-mail e senha.
2. O sistema valida as credenciais.
3. O sistema redireciona para a tela inicial correspondente ao perfil.

### Fluxos Alternativos

* **A1 — Senha incorreta:** O sistema exibe mensagem de erro.
* **A2 — Conta bloqueada:** O sistema impede o login e instrui a recuperação.

### RF Relacionados

* **RF01 — Cadastro de Usuário:** Base para autenticação.

### RNF Relacionados

* **RNF02 — Segurança:** Criptografia de senhas.
* **RNF03 — Performance:** Autenticação rápida.

### RN Relacionadas

* **RN06 — Acesso restrito por perfil:** Permissões baseadas no tipo de usuário (Recepcionista, Instrutor, Gerente).

---
