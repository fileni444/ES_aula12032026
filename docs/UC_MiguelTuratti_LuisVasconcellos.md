---

## UC01 — Realizar Login

### Ator Principal

Usuário (Aluno, Instrutor ou Administrador)

### Objetivo

Permitir que o usuário acesse o sistema.

### Pré-condições

* Usuário deve possuir cadastro ativo.

### Pós-condições

* Sessão iniciada com sucesso.

### Fluxo Principal

1. O usuário informa e-mail e senha.
2. O sistema valida as credenciais.
3. O sistema autentica o usuário e redireciona para a tela inicial.

### Fluxos Alternativos

* **A1 — Senha incorreta:** O sistema exibe mensagem de erro.
* **A2 — Conta bloqueada:** O sistema impede o login e instrui o usuário a recuperar o acesso.

### RF Relacionados

* RF01: Autenticação de usuários.

### RNF Relacionados

* RNF01: Criptografia de senhas.

### RN Relacionadas

* RN01: Bloqueio após 3 tentativas falhas.

---

## UC02 — Cadastrar Aluno

### Ator Principal

Recepcionista / Administrador

### Objetivo

Registrar novos alunos no sistema para controle de acesso e cobrança.

### Pré-condições

* Usuário autenticado com perfil administrativo.

### Pós-condições

* Aluno cadastrado com matrícula ativa.

### Fluxo Principal

1. O usuário preenche dados pessoais (nome, CPF, contato).
2. O sistema valida a unicidade do CPF.
3. O sistema gera um número de matrícula único.
4. O sistema salva o registro.

### Fluxos Alternativos

* **A1 — CPF já cadastrado:** O sistema impede o registro e sugere recuperar cadastro.

### RF Relacionados

* RF02: Gestão de perfis de alunos.

### RNF Relacionados

* RNF02: Armazenamento seguro de dados pessoais (LGPD).

### RN Relacionadas

* RN02: Idade mínima de 14 anos para cadastro independente.

---

## UC03 — Registrar Entrada (Check-in)

### Ator Principal

Aluno

### Objetivo

Validar a entrada do aluno na academia via QR Code ou Biometria.

### Pré-condições

* Aluno possuir plano ativo e sem pendências financeiras.

### Pós-condições

* Registro de presença salvo; acesso liberado.

### Fluxo Principal

1. O aluno apresenta sua identificação (QR Code via app).
2. O sistema verifica o status do plano e pagamento.
3. O sistema registra data/hora e libera o acesso.

### Fluxos Alternativos

* **A1 — Plano vencido:** O sistema bloqueia a entrada e exibe alerta financeiro.

### RF Relacionados

* RF03: Controle de acesso.

### RNF Relacionados

* RNF03: Tempo de resposta inferior a 2 segundos.

### RN Relacionadas

* RN03: Impedir entrada com atraso de pagamento superior a 5 dias.

---

## UC04 — Montar Ficha de Treino

### Ator Principal

Instrutor

### Objetivo

Prescrever exercícios e séries para o aluno.

### Pré-condições

* Aluno selecionado no sistema; Instrutor logado.

### Pós-condições

* Ficha de treino vinculada ao aluno.

### Fluxo Principal

1. O instrutor seleciona os exercícios do catálogo.
2. O instrutor define séries, repetições e carga.
3. O sistema salva e disponibiliza o treino no app do aluno.

### Fluxos Alternativos

* **A1 — Aluno sem avaliação física:** O sistema emite um aviso recomendando avaliação prévia.

### RF Relacionados

* RF04: Prescrição de treinos.

### RNF Relacionados

* RNF04: Interface responsiva para tablets.

---

## UC05 — Visualizar Treino do Dia

### Ator Principal

Aluno

### Objetivo

Permitir que o aluno consulte sua rotina de exercícios pelo celular.

### Pré-condições

* Aplicativo instalado; Treino prescrito pelo instrutor.

### Pós-condições

* Exercícios exibidos na tela.

### Fluxo Principal

1. O aluno acessa a aba "Meus Treinos".
2. O sistema exibe a ficha atualizada conforme o cronograma (ex: Treino A).

### Fluxos Alternativos

* **A1 — Sem treino cadastrado:** O sistema orienta o aluno a procurar um instrutor.

### RF Relacionados

* RF05: Consulta de ficha técnica.

---

## UC06 — Realizar Avaliação Física

### Ator Principal

Instrutor / Avaliador

### Objetivo

Registrar medidas antropométricas e percentual de gordura.

### Pré-condições

* Perfil do aluno ativo.

### Pós-condições

* Relatório de evolução gerado.

### Fluxo Principal

1. O usuário insere peso, altura e dobras cutâneas.
2. O sistema calcula automaticamente o IMC e composição corporal.
3. O sistema salva os dados e gera o comparativo.

### RF Relacionados

* RF06: Módulo de avaliação física.

### RN Relacionadas

* RN04: Cálculos baseados no protocolo de Pollock (7 dobras).

---

## UC07 — Gerenciar Planos e Mensalidades

### Ator Principal

Administrador

### Objetivo

Criar e editar modalidades de planos (Mensal, Anual, VIP).

### Pré-condições

* Usuário logado como administrador.

### Fluxo Principal

1. O usuário define o nome do plano, preço e duração.
2. O sistema registra as regras de renovação.
3. O sistema disponibiliza o plano para novas vendas.

### RF Relacionados

* RF07: Configuração de produtos/serviços.

---

## UC08 — Processar Pagamento

### Ator Principal

Recepcionista

### Objetivo

Registrar o recebimento de mensalidades.

### Pré-condições

* Aluno com fatura em aberto.

### Pós-condições

* Status do aluno atualizado para "Pago".

### Fluxo Principal

1. O usuário seleciona o aluno e a fatura.
2. O sistema registra o método de pagamento (Pix, Cartão, Dinheiro).
3. O sistema emite o recibo digital.

### RF Relacionados

* RF08: Fluxo financeiro PDV.

---

## UC09 — Agendar Aula Coletiva

### Ator Principal

Aluno

### Objetivo

Reservar vaga em aulas com limite de participantes.

### Pré-condições

* Existência de vagas disponíveis.

### Fluxo Principal

1. O aluno escolhe a aula e o horário no aplicativo.
2. O sistema valida a disponibilidade de vaga.
3. O sistema confirma o agendamento.

### Fluxos Alternativos

* **A1 — Lista de espera:** O sistema oferece inclusão em lista se a aula estiver lotada.

### RF Relacionados

* RF09: Reserva de horários.

---

## UC10 — Consultar Histórico de Frequência

### Ator Principal

Aluno / Administrador

### Objetivo

Visualizar a assiduidade do aluno na academia.

### Fluxo Principal

1. O usuário seleciona o período desejado.
2. O sistema lista todos os dias e horários de entrada registrados.

---

## UC11 — Bloquear Aluno por Inadimplência

### Ator Principal

Sistema (Automático)

### Objetivo

Suspender o acesso de alunos com atrasos financeiros.

### Pré-condições

* Data de vencimento ultrapassada.

### Pós-condições

* Matrícula suspensa para entrada.

### Fluxo Principal

1. O sistema verifica diariamente as faturas vencidas.
2. O sistema altera o status da matrícula para "Bloqueado".
3. O sistema envia uma notificação automática ao aluno.

---

## UC12 — Cadastrar Exercício no Catálogo

### Ator Principal

Administrador / Instrutor

### Objetivo

Alimentar o banco de dados de exercícios com fotos ou vídeos.

### Fluxo Principal

1. O usuário insere nome, grupo muscular e link do vídeo.
2. O sistema salva o exercício para uso na montagem de fichas.

---

## UC13 — Emitir Relatório de Faturamento

### Ator Principal

Administrador

### Objetivo

Gerar visão financeira de recebimentos mensais.

### Fluxo Principal

1. O usuário filtra o período (mês/ano).
2. O sistema soma os pagamentos confirmados.
3. O sistema exibe o total por categoria de plano.

---

## UC14 — Notificar Vencimento de Plano

### Ator Principal

Sistema (Automático)

### Objetivo

Alertar o aluno antes da expiração do plano.

### Fluxo Principal

1. O sistema identifica planos que vencem em 5 dias.
2. O sistema envia notificação Push para o celular do aluno.

---

## UC15 — Gerenciar Horários de Professores

### Ator Principal

Administrador

### Objetivo

Escalar instrutores para turnos e aulas coletivas.

---

## UC16 — Cancelar Matrícula

### Ator Principal

Recepcionista

### Objetivo

Encerrar o vínculo contratual do aluno.

### RN Relacionadas

* RN05: Verificar se existem multas de rescisão para planos anuais.

---

## UC17 — Vender Produtos (Loja)

### Ator Principal

Vendedor / Recepcionista

### Objetivo

Vender suplementos, água ou acessórios.

---

## UC18 — Alterar Senha de Acesso

### Ator Principal

Usuário

### Objetivo

Permitir a atualização da senha pessoal.

---

## UC19 — Exportar PDF de Avaliação Física

### Ator Principal

Aluno / Instrutor

### Objetivo

Gerar documento para impressão.

### Fluxo Principal

1. O usuário seleciona a avaliação desejada.
2. O sistema gera um arquivo .PDF formatado.

---

## UC20 — Configurar Unidade

### Ator Principal

Administrador

### Objetivo

Definir dados da unidade (São João da Boa Vista), horários e logotipos.

---
### DUC_MiguelTuratti_LuisVasconcellos
<img width="501" height="1948" alt="image" src="https://github.com/user-attachments/assets/2f5077da-8e56-4fb9-8d16-719859b81fb6" />


