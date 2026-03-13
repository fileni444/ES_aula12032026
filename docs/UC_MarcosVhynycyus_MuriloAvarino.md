# FitPass Gym Management – Documento de Casos de Uso

## Sistema
FitPass Gym Management

## Descrição
Sistema de gestão para academias da rede FitPass, permitindo controle de alunos, planos, pagamentos, acesso por catraca RFID, agendamento de aulas, avaliações físicas e geração de relatórios gerenciais.

---

# UC01 — Cadastrar Aluno

**Atores:** Recepcionista  

**Descrição:** Permite cadastrar novos alunos no sistema.

**Pré-condições**

- Recepcionista autenticado.

**Pós-condições**

- Aluno cadastrado no sistema.

**Fluxo Principal**

1. Recepcionista acessa o módulo de alunos.
2. Recepcionista seleciona "Cadastrar aluno".
3. Sistema solicita dados do aluno.
4. Recepcionista informa dados pessoais.
5. Sistema valida dados.
6. Sistema registra aluno.

**Fluxos Alternativos**

A1 — Dados inválidos  
1. Sistema informa erro.  
2. Recepcionista corrige dados.

**RF:** RF01  
**RN:** RN06  
**RNF:** RNF04

---

# UC02 — Gerenciar Planos

**Atores:** Gerente

**Fluxo Principal**

1. Gerente acessa módulo de planos.
2. Seleciona criar ou editar plano.
3. Informa dados do plano.
4. Sistema salva alterações.

**RF:** RF02  
**RN:** RN06

---

# UC03 — Registrar Pagamento

**Atores:** Recepcionista

**Fluxo Principal**

1. Recepcionista busca aluno.
2. Seleciona registrar pagamento.
3. Informa forma de pagamento.
4. Sistema registra pagamento.
5. Sistema executa atualização de regularidade.

**RF:** RF03  
**RN:** RN04

---

# UC04 — Verificar Regularidade do Aluno

**Atores:** Sistema

**Fluxo Principal**

1. Sistema verifica data de vencimento.
2. Sistema verifica pagamentos registrados.
3. Sistema define situação do aluno.

**RF:** RF04  
**RN:** RN01

---

# UC05 — Validar Acesso na Catraca

**Atores**

- Aluno
- Sistema de Catraca

**Fluxo Principal**

1. Aluno aproxima RFID da catraca.
2. Sistema da catraca consulta API.
3. Sistema verifica regularidade.
4. Sistema retorna autorização.

**Fluxos Alternativos**

A1 — Aluno inadimplente  
1. Sistema bloqueia acesso.

**RF:** RF05  
**RN:** RN01  
**RNF:** RNF03, RNF06

---

# UC06 — Consultar Horários de Aula

**Atores:** Aluno

**Fluxo**

1. Aluno acessa agenda.
2. Sistema exibe aulas disponíveis.

**RF:** RF06

---

# UC07 — Agendar Aula

**Atores:** Aluno

**Fluxo**

1. Aluno seleciona aula.
2. Sistema verifica vagas.
3. Sistema registra reserva.

**Fluxos Alternativos**

A1 — Aula lotada.

**RF:** RF06  
**RN:** RN02

---

# UC08 — Cancelar Agendamento

**Atores:** Aluno

**Fluxo**

1. Aluno acessa reservas.
2. Seleciona cancelar reserva.
3. Sistema confirma cancelamento.

**Fluxos Alternativos**

A1 — Prazo excedido.

**RF:** RF06  
**RN:** RN03

---

# UC09 — Registrar Presença em Aula

**Atores:** Instrutor

**Fluxo**

1. Instrutor acessa aula.
2. Instrutor registra presença.

**RF:** RF07

---

# UC10 — Registrar Avaliação Física

**Atores:** Instrutor

**Fluxo**

1. Instrutor seleciona aluno.
2. Sistema verifica regularidade.
3. Instrutor registra dados físicos.
4. Sistema salva avaliação.

**Fluxos Alternativos**

A1 — Aluno irregular.

**RF:** RF08  
**RN:** RN05

---

# UC11 — Anexar Arquivo de Avaliação

**Atores:** Instrutor

**Fluxo**

1. Instrutor adiciona arquivo.
2. Sistema armazena arquivo.

**RF:** RF08  
**RNF:** RNF02

---

# UC12 — Emitir Relatório de Inadimplência

**Atores:** Gerente

**Fluxo**

1. Gerente solicita relatório.
2. Sistema gera relatório.

**RF:** RF09

---

# UC13 — Emitir Relatório de Alunos Ativos

**Atores:** Gerente

**Fluxo**

1. Gerente solicita relatório.
2. Sistema apresenta dados.

**RF:** RF09

---

# UC14 — Emitir Relatório de Acessos

**Atores:** Gerente

**Fluxo**

1. Gerente solicita histórico.
2. Sistema apresenta acessos.

**RF:** RF09

---

# UC15 — Emitir Relatório de Ocupação de Aulas

**Atores:** Gerente

**Fluxo**

1. Gerente seleciona período.
2. Sistema gera relatório.

**RF:** RF09

---

# UC16 — Enviar Notificação de Vencimento

**Atores:** Sistema

**Fluxo**

1. Sistema identifica mensalidades próximas do vencimento.
2. Sistema envia notificação.

**RF:** RF10

---

# UC17 — Enviar Confirmação de Agendamento

**Atores:** Sistema

**Fluxo**

1. Sistema registra reserva.
2. Sistema envia confirmação ao aluno.

**RF:** RF10

---

# UC18 — Notificar Nova Avaliação Física

**Atores:** Sistema

**Fluxo**

1. Sistema detecta nova avaliação.
2. Sistema envia notificação.

**RF:** RF10

---

# UC19 — Atualizar Regularidade

**Atores:** Sistema

**Fluxo**

1. Sistema registra pagamento.
2. Sistema atualiza status do aluno.

**RN:** RN07

---

# UC20 — Autenticar Usuário

**Atores**

- Recepcionista
- Instrutor
- Gerente

**Fluxo**

1. Usuário informa login e senha.
2. Sistema valida credenciais.
3. Sistema identifica perfil.
4. Sistema libera acesso.

**RN:** RN06  
**RNF:** RNF02