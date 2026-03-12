# Documento de Casos de Uso – Sistema FitPass Gym Management

---

## UC01 — Realizar Login

### Ator Principal
Usuário (Aluno, Recepcionista, Instrutor, Gerente)

### Objetivo
Permitir que o usuário acesse o sistema com suas credenciais.

### Pré-condições
- Usuário deve possuir cadastro ativo no sistema.

### Pós-condições
- Sessão iniciada com sucesso e usuário redirecionado à tela inicial conforme seu perfil.

### Fluxo Principal
1. O usuário acessa a tela de login.
2. O usuário informa e-mail e senha.
3. O sistema valida as credenciais.
4. O sistema autentica o usuário e redireciona para a tela inicial correspondente ao seu perfil.

### Fluxos Alternativos
- **A1 — Senha incorreta:**
  O sistema exibe mensagem de erro e solicita nova tentativa.

- **A2 — Conta bloqueada:**
  O sistema impede o login e exibe orientação para recuperação de acesso.

- **A3 — Campos em branco:**
  O sistema exibe mensagem solicitando preenchimento dos campos obrigatórios.

### RF Relacionados
- (Não se aplica diretamente a um RF específico — funcionalidade base do sistema)

### RNF Relacionados
- RNF01 — Disponibilidade
- RNF02 — Segurança
- RNF03 — Performance

### RN Relacionadas
- RN06 — Acesso restrito por perfil

---

## UC02 — Cadastrar Aluno

### Ator Principal
Recepcionista

### Objetivo
Registrar um novo aluno no sistema com todos os dados necessários.

### Pré-condições
- Recepcionista deve estar autenticado no sistema.
- O e-mail do aluno não pode estar previamente cadastrado.

### Pós-condições
- Aluno cadastrado com situação "ativo" e plano associado.

### Fluxo Principal
1. A recepcionista acessa o módulo de cadastro de alunos.
2. A recepcionista preenche os dados pessoais (nome, CPF, data de nascimento).
3. A recepcionista preenche os dados de contato (e-mail, telefone).
4. A recepcionista preenche o endereço do aluno.
5. A recepcionista seleciona o plano contratado.
6. O sistema valida os dados e registra o aluno.
7. O sistema exibe confirmação do cadastro.

### Fluxos Alternativos
- **A1 — CPF ou e-mail já cadastrado:**
  O sistema exibe mensagem de duplicidade e impede o cadastro.

- **A2 — Dados obrigatórios não preenchidos:**
  O sistema destaca os campos em branco e solicita preenchimento.

### RF Relacionados
- RF01 — Cadastro de Alunos

### RNF Relacionados
- RNF02 — Segurança
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

---

## UC03 — Editar Dados do Aluno

### Ator Principal
Recepcionista

### Objetivo
Atualizar informações cadastrais de um aluno já existente.

### Pré-condições
- Recepcionista autenticado.
- Aluno previamente cadastrado no sistema.

### Pós-condições
- Dados do aluno atualizados com sucesso.

### Fluxo Principal
1. A recepcionista acessa o módulo de alunos e pesquisa pelo aluno.
2. O sistema exibe os dados atuais do aluno.
3. A recepcionista edita os campos desejados.
4. O sistema valida e salva as alterações.
5. O sistema exibe confirmação da atualização.

### Fluxos Alternativos
- **A1 — Aluno não encontrado:**
  O sistema exibe mensagem informando que nenhum resultado foi encontrado.

- **A2 — Dados inválidos:**
  O sistema exibe mensagem de erro específica ao campo inválido.

### RF Relacionados
- RF01 — Cadastro de Alunos

### RNF Relacionados
- RNF02 — Segurança
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

---

## UC04 — Gerenciar Planos

### Ator Principal
Gerente

### Objetivo
Criar, editar, ativar e desativar planos disponíveis na academia.

### Pré-condições
- Gerente autenticado no sistema.

### Pós-condições
- Plano criado, editado ou com status atualizado conforme ação realizada.

### Fluxo Principal
1. O gerente acessa o módulo de planos.
2. O gerente seleciona a ação desejada (criar, editar, ativar, desativar).
3. O sistema exibe o formulário correspondente.
4. O gerente preenche ou altera os dados (nome, tipo, valor, duração).
5. O sistema valida e salva as alterações.
6. O sistema exibe confirmação.

### Fluxos Alternativos
- **A1 — Plano com nome duplicado:**
  O sistema exibe mensagem de erro e impede a criação.

- **A2 — Plano com alunos ativos vinculados sendo desativado:**
  O sistema exibe aviso e solicita confirmação do gerente.

### RF Relacionados
- RF02 — Gerenciamento de Planos

### RNF Relacionados
- RNF04 — Usabilidade
- RNF05 — Escalabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

---

## UC05 — Registrar Pagamento Presencial

### Ator Principal
Recepcionista

### Objetivo
Registrar o pagamento da mensalidade realizado presencialmente na recepção.

### Pré-condições
- Recepcionista autenticado.
- Aluno cadastrado e com mensalidade em aberto.

### Pós-condições
- Pagamento registrado e situação financeira do aluno atualizada para "regular".

### Fluxo Principal
1. A recepcionista localiza o aluno no sistema.
2. O sistema exibe a mensalidade em aberto.
3. A recepcionista seleciona a forma de pagamento (dinheiro, cartão ou PIX).
4. O sistema registra o pagamento e o valor integral.
5. O sistema atualiza automaticamente a situação do aluno para "regular".
6. O sistema exibe comprovante do pagamento.

### Fluxos Alternativos
- **A1 — Tentativa de pagamento parcial:**
  O sistema rejeita a operação e exibe mensagem informando que o pagamento deve ser integral.

- **A2 — Falha na comunicação com operadora de cartão:**
  O sistema exibe mensagem de erro e solicita nova tentativa ou forma alternativa.

### RF Relacionados
- RF03 — Controle de Pagamentos
- RF04 — Regularidade do Aluno

### RNF Relacionados
- RNF02 — Segurança
- RNF03 — Performance

### RN Relacionadas
- RN04 — Pagamento parcial
- RN07 — Atualização automática da regularidade

---

## UC06 — Gerar Boleto / Link de Pagamento Online

### Ator Principal
Sistema (automático) / Recepcionista

### Objetivo
Gerar boleto ou link de pagamento para que o aluno quite sua mensalidade remotamente.

### Pré-condições
- Aluno com mensalidade em aberto.

### Pós-condições
- Boleto ou link gerado e disponibilizado ao aluno.

### Fluxo Principal
1. O sistema identifica alunos com vencimento próximo ou em aberto.
2. O sistema gera o boleto ou link de pagamento online.
3. O sistema envia o boleto/link ao e-mail cadastrado do aluno.
4. O sistema registra o envio.

### Fluxos Alternativos
- **A1 — E-mail inválido ou não cadastrado:**
  O sistema registra falha no envio e notifica a recepcionista.

- **A2 — Geração manual pela recepcionista:**
  A recepcionista localiza o aluno e solicita a geração manual do boleto/link.

### RF Relacionados
- RF03 — Controle de Pagamentos
- RF10 — Notificações

### RNF Relacionados
- RNF02 — Segurança

### RN Relacionadas
- RN04 — Pagamento parcial
- RN07 — Atualização automática da regularidade

---

## UC07 — Verificar Regularidade do Aluno

### Ator Principal
Sistema (automático)

### Objetivo
Verificar automaticamente se o aluno está com a mensalidade em dia.

### Pré-condições
- Aluno cadastrado no sistema.

### Pós-condições
- Situação financeira do aluno atualizada (regular ou inadimplente).

### Fluxo Principal
1. O sistema verifica diariamente os vencimentos das mensalidades.
2. O sistema identifica alunos com pagamento vencido.
3. O sistema atualiza o status do aluno conforme a situação.
4. O sistema registra o histórico de verificação.

### Fluxos Alternativos
- **A1 — Pagamento registrado no mesmo dia do vencimento:**
  O sistema mantém o aluno como "regular" sem aplicar penalidade.

### RF Relacionados
- RF04 — Regularidade do Aluno

### RNF Relacionados
- RNF03 — Performance

### RN Relacionadas
- RN01 — Bloqueio por inadimplência
- RN07 — Atualização automática da regularidade

---

## UC08 — Validar Acesso pela Catraca (RFID)

### Ator Principal
Aluno / Sistema de Catraca

### Objetivo
Validar a entrada do aluno na academia por meio da integração com a catraca via RFID.

### Pré-condições
- Aluno com cartão RFID ativo.
- Sistema de catraca integrado via API REST.

### Pós-condições
- Acesso liberado ou negado e registro de tentativa gravado no histórico.

### Fluxo Principal
1. O aluno aproxima o cartão RFID da catraca.
2. A catraca envia o código RFID para o sistema via API REST.
3. O sistema valida o RFID e verifica a situação do aluno.
4. O sistema retorna autorização de acesso.
5. A catraca libera a entrada e o sistema registra o acesso.

### Fluxos Alternativos
- **A1 — Aluno inadimplente:**
  O sistema retorna negação de acesso; a catraca permanece fechada.

- **A2 — RFID não cadastrado:**
  O sistema retorna erro de identificação.

- **A3 — Falha na comunicação com a API:**
  A catraca registra a falha e mantém bloqueio por segurança.

### RF Relacionados
- RF04 — Regularidade do Aluno
- RF05 — Controle de Acesso

### RNF Relacionados
- RNF03 — Performance
- RNF06 — Integração

### RN Relacionadas
- RN01 — Bloqueio por inadimplência

---

## UC09 — Agendar Aula

### Ator Principal
Aluno

### Objetivo
Permitir que o aluno visualize os horários disponíveis e reserve uma vaga em uma aula.

### Pré-condições
- Aluno autenticado e com situação regular.
- Aula com vagas disponíveis.

### Pós-condições
- Reserva confirmada e vaga reduzida no sistema.

### Fluxo Principal
1. O aluno acessa o módulo de agendamento.
2. O sistema exibe as aulas disponíveis com horários e vagas.
3. O aluno seleciona a aula desejada.
4. O sistema verifica a disponibilidade de vagas.
5. O sistema confirma a reserva e notifica o aluno.

### Fluxos Alternativos
- **A1 — Aula sem vagas disponíveis:**
  O sistema exibe mensagem informando que a aula está lotada e bloqueia o agendamento.

- **A2 — Aluno inadimplente:**
  O sistema exibe mensagem bloqueando o agendamento até regularização.

### RF Relacionados
- RF06 — Agendamento de Aulas
- RF10 — Notificações

### RNF Relacionados
- RNF03 — Performance
- RNF04 — Usabilidade

### RN Relacionadas
- RN02 — Limite de vagas

---

## UC10 — Cancelar Agendamento de Aula

### Ator Principal
Aluno

### Objetivo
Permitir que o aluno cancele uma reserva de aula previamente realizada.

### Pré-condições
- Aluno autenticado.
- Reserva ativa com pelo menos 1 hora de antecedência em relação ao início da aula.

### Pós-condições
- Reserva cancelada e vaga devolvida ao sistema.

### Fluxo Principal
1. O aluno acessa o módulo "Meus Agendamentos".
2. O sistema exibe as reservas ativas do aluno.
3. O aluno seleciona o agendamento que deseja cancelar.
4. O sistema verifica se o cancelamento está dentro do prazo permitido.
5. O sistema cancela a reserva e libera a vaga.
6. O sistema confirma o cancelamento ao aluno.

### Fluxos Alternativos
- **A1 — Cancelamento fora do prazo (menos de 1 hora antes):**
  O sistema exibe mensagem informando que o prazo de cancelamento expirou e bloqueia a ação.

### RF Relacionados
- RF06 — Agendamento de Aulas

### RNF Relacionados
- RNF04 — Usabilidade

### RN Relacionadas
- RN03 — Cancelamento de agendamento

---

## UC11 — Registrar Presença em Aula

### Ator Principal
Instrutor

### Objetivo
Registrar a presença dos alunos em uma aula ministrada.

### Pré-condições
- Instrutor autenticado.
- Aula com alunos agendados.

### Pós-condições
- Presenças registradas no histórico dos alunos.

### Fluxo Principal
1. O instrutor acessa o módulo de aulas do dia.
2. O sistema exibe a lista de alunos agendados na aula.
3. O instrutor marca a presença de cada aluno presente.
4. O sistema registra e salva as presenças.
5. O sistema exibe confirmação do registro.

### Fluxos Alternativos
- **A1 — Aluno presente mas não agendado:**
  O instrutor pode registrar presença avulsa, que ficará sinalizada no sistema.

### RF Relacionados
- RF07 — Lista de Presença

### RNF Relacionados
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

---

## UC12 — Registrar Avaliação Física

### Ator Principal
Instrutor

### Objetivo
Registrar os dados de avaliação física de um aluno ativo e regular.

### Pré-condições
- Instrutor autenticado.
- Aluno com status ativo e regular (mensalidade em dia).

### Pós-condições
- Avaliação física registrada e vinculada ao histórico do aluno.

### Fluxo Principal
1. O instrutor acessa o módulo de avaliações físicas.
2. O instrutor pesquisa e seleciona o aluno.
3. O sistema verifica se o aluno está ativo e regular.
4. O instrutor preenche os dados (peso, altura, IMC, percentual de gordura, etc.).
5. O instrutor anexa arquivos, se necessário.
6. O sistema salva a avaliação e exibe confirmação.

### Fluxos Alternativos
- **A1 — Aluno inadimplente ou inativo:**
  O sistema impede o registro e exibe mensagem orientando a regularização.

### RF Relacionados
- RF08 — Avaliação Física
- RF10 — Notificações

### RNF Relacionados
- RNF02 — Segurança
- RNF04 — Usabilidade

### RN Relacionadas
- RN05 — Avaliação física
- RN06 — Acesso restrito por perfil

---

## UC13 — Emitir Relatório de Inadimplência

### Ator Principal
Gerente

### Objetivo
Gerar um relatório com todos os alunos com mensalidades em atraso.

### Pré-condições
- Gerente autenticado.

### Pós-condições
- Relatório gerado e disponibilizado para visualização ou exportação.

### Fluxo Principal
1. O gerente acessa o módulo de relatórios.
2. O gerente seleciona o relatório de inadimplência.
3. O gerente define filtros opcionais (período, plano, unidade).
4. O sistema consolida os dados e gera o relatório.
5. O sistema exibe o relatório e permite exportação.

### Fluxos Alternativos
- **A1 — Nenhum aluno inadimplente no período:**
  O sistema exibe mensagem informando ausência de resultados.

### RF Relacionados
- RF09 — Relatórios Gerenciais

### RNF Relacionados
- RNF03 — Performance
- RNF05 — Escalabilidade

### RN Relacionadas
- RN01 — Bloqueio por inadimplência
- RN06 — Acesso restrito por perfil

---

## UC14 — Emitir Relatório de Alunos Ativos

### Ator Principal
Gerente

### Objetivo
Gerar um relatório com todos os alunos com matrícula ativa no sistema.

### Pré-condições
- Gerente autenticado.

### Pós-condições
- Relatório de alunos ativos gerado com sucesso.

### Fluxo Principal
1. O gerente acessa o módulo de relatórios.
2. O gerente seleciona o relatório de alunos ativos.
3. O gerente define filtros opcionais (plano, período de cadastro, unidade).
4. O sistema gera e exibe o relatório.
5. O sistema permite exportação do relatório.

### Fluxos Alternativos
- **A1 — Nenhum resultado com os filtros aplicados:**
  O sistema exibe mensagem informando ausência de resultados.

### RF Relacionados
- RF09 — Relatórios Gerenciais

### RNF Relacionados
- RNF03 — Performance
- RNF05 — Escalabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

---

## UC15 — Emitir Relatório de Histórico de Acessos

### Ator Principal
Gerente

### Objetivo
Gerar um relatório com o histórico de entradas na academia por aluno ou período.

### Pré-condições
- Gerente autenticado.

### Pós-condições
- Relatório de acessos gerado e disponível para exportação.

### Fluxo Principal
1. O gerente acessa o módulo de relatórios.
2. O gerente seleciona o relatório de histórico de acessos.
3. O gerente define os filtros desejados (aluno, período, unidade).
4. O sistema busca os registros de acesso e gera o relatório.
5. O sistema exibe e permite exportação.

### Fluxos Alternativos
- **A1 — Nenhum acesso no período filtrado:**
  O sistema informa ausência de registros.

### RF Relacionados
- RF05 — Controle de Acesso
- RF09 — Relatórios Gerenciais

### RNF Relacionados
- RNF03 — Performance
- RNF05 — Escalabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil

---

## UC16 — Emitir Relatório de Ocupação de Aulas

### Ator Principal
Gerente

### Objetivo
Gerar relatório com a taxa de ocupação das aulas por período.

### Pré-condições
- Gerente autenticado.

### Pós-condições
- Relatório de ocupação gerado com sucesso.

### Fluxo Principal
1. O gerente acessa o módulo de relatórios.
2. O gerente seleciona o relatório de ocupação de aulas.
3. O gerente define filtros (aula, instrutor, período).
4. O sistema calcula e gera o relatório com dados de lotação.
5. O sistema exibe e permite exportação.

### Fluxos Alternativos
- **A1 — Nenhuma aula no período selecionado:**
  O sistema informa ausência de dados.

### RF Relacionados
- RF07 — Lista de Presença
- RF09 — Relatórios Gerenciais

### RNF Relacionados
- RNF03 — Performance
- RNF05 — Escalabilidade

### RN Relacionadas
- RN02 — Limite de vagas
- RN06 — Acesso restrito por perfil

---

## UC17 — Enviar Notificação de Vencimento de Mensalidade

### Ator Principal
Sistema (automático)

### Objetivo
Notificar o aluno sobre o vencimento próximo ou em atraso da sua mensalidade.

### Pré-condições
- Aluno com e-mail cadastrado.
- Mensalidade com vencimento próximo ou em atraso.

### Pós-condições
- Notificação enviada e registrada no sistema.

### Fluxo Principal
1. O sistema verifica diariamente os vencimentos.
2. O sistema identifica alunos com vencimento em até 5 dias ou já vencido.
3. O sistema gera a notificação personalizada.
4. O sistema envia a notificação por e-mail ao aluno.
5. O sistema registra o envio.

### Fluxos Alternativos
- **A1 — Falha no envio de e-mail:**
  O sistema registra a falha e tenta reenvio após intervalo definido.

### RF Relacionados
- RF10 — Notificações

### RNF Relacionados
- RNF01 — Disponibilidade

### RN Relacionadas
- RN01 — Bloqueio por inadimplência

---

## UC18 — Enviar Notificação de Confirmação de Agendamento

### Ator Principal
Sistema (automático)

### Objetivo
Notificar o aluno sobre a confirmação de uma reserva de aula realizada.

### Pré-condições
- Reserva realizada com sucesso.
- Aluno com e-mail cadastrado.

### Pós-condições
- Notificação de confirmação enviada ao aluno.

### Fluxo Principal
1. O aluno realiza o agendamento de uma aula (UC09).
2. O sistema confirma a reserva.
3. O sistema gera e envia automaticamente a notificação de confirmação.
4. O sistema registra o envio.

### Fluxos Alternativos
- **A1 — Falha no envio:**
  O sistema registra a falha; o agendamento permanece ativo mesmo sem o envio.

### RF Relacionados
- RF06 — Agendamento de Aulas
- RF10 — Notificações

### RNF Relacionados
- RNF01 — Disponibilidade

### RN Relacionadas
- RN02 — Limite de vagas
- RN03 — Cancelamento de agendamento

---

## UC19 — Recuperar Senha

### Ator Principal
Usuário (Aluno, Recepcionista, Instrutor, Gerente)

### Objetivo
Permitir que o usuário redefina sua senha em caso de esquecimento.

### Pré-condições
- Usuário com cadastro ativo e e-mail válido registrado.

### Pós-condições
- Nova senha definida e acesso restaurado.

### Fluxo Principal
1. O usuário acessa a tela de login e clica em "Esqueci minha senha".
2. O usuário informa o e-mail cadastrado.
3. O sistema valida o e-mail e envia um link de redefinição.
4. O usuário acessa o link e define uma nova senha.
5. O sistema atualiza a senha e exibe confirmação.

### Fluxos Alternativos
- **A1 — E-mail não encontrado:**
  O sistema exibe mensagem genérica sem confirmar ou negar a existência do cadastro.

- **A2 — Link expirado:**
  O sistema informa que o link expirou e orienta o usuário a solicitar um novo.

### RF Relacionados
- (Funcionalidade base de segurança do sistema)

### RNF Relacionados
- RNF02 — Segurança

### RN Relacionadas
- RN06 — Acesso restrito por perfil

---

## UC20 — Enviar Notificação de Liberação de Avaliação Física

### Ator Principal
Sistema (automático)

### Objetivo
Notificar o aluno quando uma nova avaliação física estiver disponível para ser agendada.

### Pré-condições
- Aluno ativo e regular.
- Prazo para nova avaliação física atingido (conforme política da academia).

### Pós-condições
- Notificação enviada ao aluno.

### Fluxo Principal
1. O sistema verifica periodicamente se alunos atingiram o prazo para nova avaliação.
2. O sistema identifica os alunos elegíveis.
3. O sistema gera a notificação de liberação.
4. O sistema envia a notificação por e-mail ao aluno.
5. O sistema registra o envio.

### Fluxos Alternativos
- **A1 — Aluno inadimplente ou inativo:**
  O sistema não envia a notificação enquanto o aluno estiver irregular.

- **A2 — Falha no envio de e-mail:**
  O sistema registra a falha e agenda novo envio.

### RF Relacionados
- RF08 — Avaliação Física
- RF10 — Notificações

### RNF Relacionados
- RNF01 — Disponibilidade

### RN Relacionadas
- RN05 — Avaliação física