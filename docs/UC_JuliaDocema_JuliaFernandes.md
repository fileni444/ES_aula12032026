# Casos de Uso — Sistema FitPass Gym Management

## UC01 — Cadastrar Aluno
### Ator Principal
Recepcionista

### Objetivo
Permitir o cadastro de novos alunos no sistema.

### Pré-condições
- Recepcionista deve estar autenticado no sistema.

### Pós-condições
- Aluno registrado no sistema com plano associado.

### Fluxo Principal
1. O recepcionista acessa a opção de cadastro de aluno.
2. O sistema solicita dados pessoais, contato e endereço.
3. O recepcionista seleciona o plano desejado.
4. O sistema valida os dados informados.
5. O sistema registra o aluno no banco de dados.

### Fluxos Alternativos
- **A1 — Dados obrigatórios ausentes:**  
  O sistema solicita o preenchimento dos campos faltantes.

### RF Relacionados
- RF01 — Cadastro de Alunos

### RNF Relacionados
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil


---

## UC02 — Gerenciar Planos
### Ator Principal
Gerente

### Objetivo
Permitir a criação e manutenção dos planos oferecidos pela academia.

### Pré-condições
- Gerente autenticado no sistema.

### Pós-condições
- Plano criado, atualizado ou desativado.

### Fluxo Principal
1. O gerente acessa o módulo de planos.
2. O sistema exibe a lista de planos cadastrados.
3. O gerente seleciona criar ou editar um plano.
4. O gerente informa nome, valor e duração.
5. O sistema salva as alterações.

### Fluxos Alternativos
- **A1 — Dados inválidos:**  
  O sistema solicita correção das informações.

### RF Relacionados
- RF02 — Gerenciamento de Planos

### RNF Relacionados
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil


---

## UC03 — Registrar Pagamento
### Ator Principal
Recepcionista

### Objetivo
Registrar o pagamento de mensalidade do aluno.

### Pré-condições
- Aluno cadastrado no sistema.
- Recepcionista autenticado.

### Pós-condições
- Pagamento registrado e situação do aluno atualizada.

### Fluxo Principal
1. O recepcionista localiza o aluno no sistema.
2. O sistema exibe a situação financeira.
3. O recepcionista seleciona a opção de registrar pagamento.
4. O recepcionista informa o método de pagamento.
5. O sistema registra o pagamento.
6. O sistema atualiza a regularidade do aluno.

### Fluxos Alternativos
- **A1 — Pagamento parcial informado:**  
  O sistema rejeita o pagamento.

### RF Relacionados
- RF03 — Controle de Pagamentos

### RNF Relacionados
- RNF02 — Segurança

### RN Relacionadas
- RN04 — Pagamento parcial  
- RN07 — Atualização automática da regularidade


---

## UC04 — Verificar Regularidade do Aluno
### Ator Principal
Sistema

### Objetivo
Determinar se o aluno está com mensalidade em dia.

### Pré-condições
- Aluno cadastrado.

### Pós-condições
- Status de regularidade atualizado.

### Fluxo Principal
1. O sistema consulta o histórico de pagamentos.
2. O sistema verifica a data de vencimento da mensalidade.
3. O sistema define o status como regular ou inadimplente.

### Fluxos Alternativos
- **A1 — Pagamento vencido:**  
  O sistema marca o aluno como inadimplente.

### RF Relacionados
- RF04 — Regularidade do Aluno

### RNF Relacionados
- RNF03 — Performance

### RN Relacionadas
- RN01 — Bloqueio por inadimplência


---

## UC05 — Validar Acesso na Catraca
### Ator Principal
Sistema de Catraca

### Objetivo
Permitir ou negar a entrada do aluno na academia.

### Pré-condições
- Aluno possuir RFID cadastrado.

### Pós-condições
- Entrada liberada ou bloqueada.

### Fluxo Principal
1. O aluno aproxima o cartão RFID da catraca.
2. A catraca envia o identificador para o sistema.
3. O sistema verifica a regularidade do aluno.
4. O sistema retorna autorização ou bloqueio.

### Fluxos Alternativos
- **A1 — Aluno inadimplente:**  
  O acesso é bloqueado.

### RF Relacionados
- RF05 — Controle de Acesso

### RNF Relacionados
- RNF03 — Performance  
- RNF06 — Integração

### RN Relacionadas
- RN01 — Bloqueio por inadimplência


---

## UC06 — Agendar Aula
### Ator Principal
Aluno

### Objetivo
Permitir que o aluno reserve vaga em uma aula.

### Pré-condições
- Aluno autenticado.
- Aula disponível.

### Pós-condições
- Reserva registrada.

### Fluxo Principal
1. O aluno acessa a lista de aulas disponíveis.
2. O sistema exibe horários e vagas.
3. O aluno seleciona uma aula.
4. O sistema registra a reserva.

### Fluxos Alternativos
- **A1 — Aula lotada:**  
  O sistema bloqueia o agendamento.

### RF Relacionados
- RF06 — Agendamento de Aulas

### RNF Relacionados
- RNF04 — Usabilidade

### RN Relacionadas
- RN02 — Limite de vagas


---

## UC07 — Cancelar Agendamento de Aula
### Ator Principal
Aluno

### Objetivo
Permitir que o aluno cancele uma reserva.

### Pré-condições
- Agendamento existente.

### Pós-condições
- Reserva cancelada.

### Fluxo Principal
1. O aluno acessa seus agendamentos.
2. O aluno seleciona a aula.
3. O aluno solicita cancelamento.
4. O sistema remove a reserva.

### Fluxos Alternativos
- **A1 — Prazo expirado:**  
  O sistema impede o cancelamento.

### RF Relacionados
- RF06 — Agendamento de Aulas

### RNF Relacionados
- RNF04 — Usabilidade

### RN Relacionadas
- RN03 — Cancelamento de agendamento


---

## UC08 — Registrar Presença em Aula
### Ator Principal
Instrutor

### Objetivo
Registrar presença dos alunos nas aulas.

### Pré-condições
- Aula iniciada.

### Pós-condições
- Presença registrada.

### Fluxo Principal
1. O instrutor acessa a aula no sistema.
2. O sistema exibe lista de alunos inscritos.
3. O instrutor marca presença.
4. O sistema salva o registro.

### Fluxos Alternativos
- **A1 — Aluno não compareceu:**  
  O instrutor marca ausência.

### RF Relacionados
- RF07 — Lista de Presença

### RNF Relacionados
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil


---

## UC09 — Registrar Avaliação Física
### Ator Principal
Instrutor

### Objetivo
Registrar dados da avaliação física do aluno.

### Pré-condições
- Aluno ativo.

### Pós-condições
- Avaliação armazenada no sistema.

### Fluxo Principal
1. O instrutor seleciona o aluno.
2. O instrutor insere dados como peso, IMC e percentual de gordura.
3. O instrutor anexa arquivos, se necessário.
4. O sistema salva a avaliação.

### Fluxos Alternativos
- **A1 — Aluno irregular:**  
  O sistema impede o registro da avaliação.

### RF Relacionados
- RF08 — Avaliação Física

### RNF Relacionados
- RNF02 — Segurança

### RN Relacionadas
- RN05 — Avaliação física


---

## UC10 — Emitir Relatórios Gerenciais
### Ator Principal
Gerente

### Objetivo
Gerar relatórios sobre o funcionamento da academia.

### Pré-condições
- Gerente autenticado.

### Pós-condições
- Relatório exibido ou exportado.

### Fluxo Principal
1. O gerente acessa o módulo de relatórios.
2. O sistema exibe opções disponíveis.
3. O gerente seleciona um tipo de relatório.
4. O sistema gera o relatório.

### Fluxos Alternativos
- **A1 — Nenhum dado disponível:**  
  O sistema informa ausência de dados.

### RF Relacionados
- RF09 — Relatórios Gerenciais

### RNF Relacionados
- RNF05 — Escalabilidade


---

## UC11 — Consultar Dados do Aluno
### Ator Principal
Recepcionista

### Objetivo
Permitir visualizar os dados cadastrais e situação do aluno.

### Pré-condições
- Recepcionista autenticado.
- Aluno cadastrado no sistema.

### Pós-condições
- Informações do aluno exibidas na tela.

### Fluxo Principal
1. O recepcionista acessa a busca de alunos.
2. O recepcionista informa nome, CPF ou matrícula.
3. O sistema localiza o aluno.
4. O sistema exibe dados pessoais, plano e situação financeira.

### Fluxos Alternativos
- **A1 — Aluno não encontrado:**  
  O sistema informa que nenhum registro foi localizado.

### RF Relacionados
- RF01 — Cadastro de Alunos

### RNF Relacionados
- RNF03 — Performance

### RN Relacionadas
- RN06 — Acesso restrito por perfil


---

## UC12 — Atualizar Dados do Aluno
### Ator Principal
Recepcionista

### Objetivo
Permitir a atualização de dados cadastrais do aluno.

### Pré-condições
- Recepcionista autenticado.
- Aluno cadastrado.

### Pós-condições
- Dados atualizados no sistema.

### Fluxo Principal
1. O recepcionista localiza o aluno.
2. O sistema exibe os dados atuais.
3. O recepcionista altera as informações necessárias.
4. O sistema valida os dados.
5. O sistema salva as alterações.

### Fluxos Alternativos
- **A1 — Dados inválidos:**  
  O sistema solicita correção antes de salvar.

### RF Relacionados
- RF01 — Cadastro de Alunos

### RNF Relacionados
- RNF04 — Usabilidade

### RN Relacionadas
- RN06 — Acesso restrito por perfil


---

## UC13 — Visualizar Grade de Aulas
### Ator Principal
Aluno

### Objetivo
Permitir que o aluno visualize todas as aulas disponíveis.

### Pré-condições
- Aluno autenticado.

### Pós-condições
- Lista de aulas exibida.

### Fluxo Principal
1. O aluno acessa o menu de aulas.
2. O sistema consulta a programação disponível.
3. O sistema exibe horários, instrutores e vagas restantes.

### Fluxos Alternativos
- **A1 — Nenhuma aula disponível:**  
  O sistema informa que não há aulas cadastradas.

### RF Relacionados
- RF06 — Agendamento de Aulas

### RNF Relacionados
- RNF04 — Usabilidade

### RN Relacionadas
- RN02 — Limite de vagas


---

## UC14 — Receber Notificação de Mensalidade
### Ator Principal
Aluno

### Objetivo
Informar o aluno sobre o vencimento da mensalidade.

### Pré-condições
- Aluno cadastrado no sistema.

### Pós-condições
- Notificação enviada ao aluno.

### Fluxo Principal
1. O sistema verifica datas de vencimento das mensalidades.
2. O sistema identifica mensalidades próximas do vencimento.
3. O sistema envia notificação ao aluno.

### Fluxos Alternativos
- **A1 — Falha no envio:**  
  O sistema registra erro e tenta reenviar posteriormente.

### RF Relacionados
- RF10 — Notificações

### RNF Relacionados
- RNF01 — Disponibilidade

### RN Relacionadas
- RN01 — Bloqueio por inadimplência


---

## UC15 — Confirmar Agendamento de Aula
### Ator Principal
Sistema

### Objetivo
Enviar confirmação ao aluno após reserva de aula.

### Pré-condições
- Agendamento realizado.

### Pós-condições
- Aluno recebe confirmação do agendamento.

### Fluxo Principal
1. O aluno realiza o agendamento de aula.
2. O sistema registra a reserva.
3. O sistema envia notificação de confirmação.

### Fluxos Alternativos
- **A1 — Falha na notificação:**  
  O sistema registra o erro.

### RF Relacionados
- RF10 — Notificações

### RNF Relacionados
- RNF01 — Disponibilidade

### RN Relacionadas
- RN02 — Limite de vagas


---

## UC16 — Registrar Novo Tipo de Aula
### Ator Principal
Gerente

### Objetivo
Cadastrar novos tipos de aulas no sistema.

### Pré-condições
- Gerente autenticado.

### Pós-condições
- Aula registrada na programação.

### Fluxo Principal
1. O gerente acessa o módulo de aulas.
2. O gerente seleciona criar nova aula.
3. O gerente informa nome, horário e capacidade.
4. O sistema salva o cadastro.

### Fluxos Alternativos
- **A1 — Capacidade inválida:**  
  O sistema solicita correção.

### RF Relacionados
- RF06 — Agendamento de Aulas

### RNF Relacionados
- RNF05 — Escalabilidade

### RN Relacionadas
- RN02 — Limite de vagas


---

## UC17 — Consultar Histórico de Acessos
### Ator Principal
Gerente

### Objetivo
Visualizar registros de entrada e saída dos alunos.

### Pré-condições
- Gerente autenticado.

### Pós-condições
- Histórico exibido.

### Fluxo Principal
1. O gerente acessa o módulo de relatórios.
2. O gerente seleciona histórico de acessos.
3. O sistema consulta registros da catraca.
4. O sistema exibe o histórico.

### Fluxos Alternativos
- **A1 — Nenhum registro encontrado:**  
  O sistema informa ausência de dados.

### RF Relacionados
- RF09 — Relatórios Gerenciais

### RNF Relacionados
- RNF06 — Integração

### RN Relacionadas
- RN06 — Acesso restrito por perfil


---

## UC18 — Gerar Relatório de Inadimplência
### Ator Principal
Gerente

### Objetivo
Identificar alunos com pagamentos atrasados.

### Pré-condições
- Gerente autenticado.

### Pós-condições
- Relatório exibido ou exportado.

### Fluxo Principal
1. O gerente acessa relatórios.
2. O gerente seleciona inadimplência.
3. O sistema consulta pagamentos vencidos.
4. O sistema gera relatório.

### Fluxos Alternativos
- **A1 — Nenhum aluno inadimplente:**  
  O sistema informa que não há registros.

### RF Relacionados
- RF09 — Relatórios Gerenciais

### RNF Relacionados
- RNF03 — Performance

### RN Relacionadas
- RN01 — Bloqueio por inadimplência


---

## UC19 — Anexar Arquivo em Avaliação Física
### Ator Principal
Instrutor

### Objetivo
Adicionar arquivos ou documentos à avaliação física.

### Pré-condições
- Avaliação física iniciada.

### Pós-condições
- Arquivo anexado ao registro.

### Fluxo Principal
1. O instrutor abre a avaliação do aluno.
2. O instrutor seleciona anexar arquivo.
3. O sistema realiza upload do documento.
4. O sistema associa o arquivo à avaliação.

### Fluxos Alternativos
- **A1 — Arquivo inválido:**  
  O sistema rejeita o upload.

### RF Relacionados
- RF08 — Avaliação Física

### RNF Relacionados
- RNF02 — Segurança

### RN Relacionadas
- RN05 — Avaliação física


---

## UC20 — Verificar Situação do Aluno na Entrada
### Ator Principal
Recepcionista

### Objetivo
Permitir consulta rápida da situação do aluno.

### Pré-condições
- Recepcionista autenticado.
- Aluno cadastrado.

### Pós-condições
- Situação exibida.

### Fluxo Principal
1. O recepcionista busca o aluno.
2. O sistema consulta situação financeira.
3. O sistema exibe status do aluno.

### Fluxos Alternativos
- **A1 — Aluno inadimplente:**  
  O sistema alerta o recepcionista.

### RF Relacionados
- RF04 — Regularidade do Aluno

### RNF Relacionados
- RNF03 — Performance

### RN Relacionadas
- RN01 — Bloqueio por inadimplência

### RN Relacionadas
- RN06 — Acesso restrito por perfil
