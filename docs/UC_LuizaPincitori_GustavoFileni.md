## UC01 — Realizar Login (UC EXEMPLO - FAZER DESSA FORMA PARA TODOS OS CASOS DE USO, NESSE MESMO DOCUMENTO)

### Ator Principal
Usuário

### Objetivo
Permitir que o usuário acesse o sistema.

### Pré-condições
- Usuário deve possuir cadastro ativo.

### Pós-condições
- Sessão iniciada com sucesso.

### Fluxo Principal
1. O usuário informa e-mail e senha.
2. O sistema valida as credenciais.
3. O sistema autentica o usuário e redireciona para a tela inicial.

### Fluxos Alternativos
- **A1 — Senha incorreta:**  
  O sistema exibe mensagem de erro.

- **A2 — Conta bloqueada:**  
  O sistema impede o login e instrui o usuário a recuperar o acesso.

### RF Relacionados
- (inserir RF aqui)

### RNF Relacionados
- (inserir RNF aqui)

### RN Relacionadas
- (inserir RN aqui)

---

Este documento detalha os 20 casos de uso do sistema FitPass, servindo como guia para o desenvolvimento e testes da plataforma.

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
