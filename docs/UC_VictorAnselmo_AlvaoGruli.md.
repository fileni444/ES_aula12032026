# UC01 - Autenticar no Sistema (Login)

**Atores:** Aluno, Recepcionista, Instrutor, Gerente.
**Pré-condições:** O usuário deve possuir um cadastro ativo no sistema FitPass e credenciais (e-mail e senha) válidas.
**Pós-condições:** O usuário é autenticado com sucesso e redirecionado para o painel principal.

**Fluxo Principal:**
1. O usuário acessa a tela de login do sistema FitPass.
2. O usuário insere seu e-mail e senha.
3. O usuário clica em "Entrar".
4. O sistema valida as credenciais fornecidas na base de dados.
5. O sistema identifica o perfil do usuário.
6. O sistema redireciona o usuário para o dashboard adequado.

**Fluxos Alternativos:**
**FA01 - Credenciais Inválidas (Passo 4):**
  1. O sistema identifica que o e-mail ou a senha estão incorretos.
  2. O sistema exibe: "E-mail ou senha inválidos" e limpa a senha.
**FA02 - Recuperação de Senha (Passo 2):**
  1. O usuário clica em "Esqueci minha senha".
  2. O sistema solicita o e-mail cadastrado, e o usuário informa.
  3. O sistema envia um link de redefinição para o e-mail.

**Requisitos Funcionais Relacionados:** [Ex: RF-01]
**Requisitos Não Funcionais Relacionados:** [Ex: RNF-02]
**Regras de Negócio Relacionadas:** [Ex: RN-01]

---

# UC02 - Realizar Matrícula de Novo Aluno

**Atores:** Recepcionista.
**Pré-condições:** Recepcionista autenticada; futuro aluno fornece os dados.
**Pós-condições:** O novo aluno possui registro, plano associado e tag RFID atribuída.

**Fluxo Principal:**
1. A recepcionista acessa "Nova Matrícula".
2. O sistema apresenta o formulário.
3. A recepcionista preenche os dados pessoais do aluno.
4. O sistema valida os dados e verifica se já existe registro.
5. A recepcionista seleciona o plano de treino.
6. A recepcionista associa a tag RFID.
7. A recepcionista clica em "Salvar Matrícula".
8. O sistema grava as informações e gera o contrato.

**Fluxos Alternativos:**
**FA01 - Documento já registrado (Passo 4):**
  1. O sistema emite alerta de cadastro existente e encerra o fluxo.
**FA02 - Aluno Menor de Idade (Passo 3):**
  1. O sistema exige dados do Responsável Legal.

**Requisitos Funcionais Relacionados:** [Ex: RF-02, RF-03]
**Requisitos Não Funcionais Relacionados:** [Ex: RNF-03]
**Regras de Negócio Relacionadas:** [Ex: RN-02]

---

# UC03 - Atualizar Dados Cadastrais

**Atores:** Aluno, Recepcionista.
**Pré-condições:** Usuário autenticado e aluno registrado.
**Pós-condições:** Informações atualizadas na base de dados.

**Fluxo Principal:**
1. O usuário acessa a edição de perfil.
2. O sistema apresenta os dados atuais editáveis.
3. O usuário altera as informações necessárias.
4. O usuário clica em "Salvar Alterações".
5. O sistema valida e atualiza a base de dados.

**Fluxos Alternativos:**
**FA01 - Dados Inválidos (Passo 5):**
  1. O sistema detecta formato inválido (ex: e-mail) e impede a gravação.

**Requisitos Funcionais Relacionados:** [Ex: RF-04]
**Requisitos Não Funcionais Relacionados:** [Ex: RNF-04]
**Regras de Negócio Relacionadas:** [Ex: RN-03]

---

# UC04 - Consultar e Selecionar Planos Disponíveis

**Atores:** Aluno, Recepcionista.
**Pré-condições:** Acesso ao portal de vendas ou sistema da recepção.
**Pós-condições:** Plano selecionado para contratação.

**Fluxo Principal:**
1. O usuário acessa "Planos e Preços".
2. O sistema exibe a lista de planos ativos.
3. O usuário clica em "Ver Detalhes".
4. O sistema apresenta os detalhes completos.
5. O usuário clica em "Selecionar este Plano".
6. O sistema guarda a seleção em memória.

**Fluxos Alternativos:**
**FA01 - Nenhum plano ativo (Passo 2):**
  1. O sistema avisa que não há planos disponíveis.

**Requisitos Funcionais Relacionados:** [Ex: RF-05]
**Requisitos Não Funcionais Relacionados:** [Ex: RNF-05]
**Regras de Negócio Relacionadas:** [Ex: RN-04]

---

# UC05 - Contratar/Alterar Plano de Treino

**Atores:** Aluno, Recepcionista.
**Pré-condições:** Aluno cadastrado, plano selecionado e sem bloqueios financeiros.
**Pós-condições:** Novo plano associado ao perfil.

**Fluxo Principal:**
1. O usuário escolhe "Assinar" ou "Alterar Plano".
2. O sistema apresenta o plano selecionado.
3. O usuário confirma a contratação/alteração.
4. O usuário aceita os Termos e Condições.
5. O sistema atualiza o ciclo de faturamento e confirma.

**Fluxos Alternativos:**
**FA01 - Inadimplência (Passo 2):**
  1. O sistema bloqueia a alteração e exige regularização.
**FA02 - Downgrade com fidelização (Passo 4):**
  1. O sistema calcula a taxa de penalização e pede confirmação.

**Requisitos Funcionais Relacionados:** [Ex: RF-06]
**Requisitos Não Funcionais Relacionados:** [Ex: RNF-06]
**Regras de Negócio Relacionadas:** [Ex: RN-05]
# UC06 - Cancelar Plano de Treino

**Atores:** Recepcionista, Gerente.
**Pré-condições:** Aluno com plano ativo.
**Pós-condições:** Plano desativado e acesso programado para bloqueio.

**Fluxo Principal:**
1. O usuário seleciona "Cancelar Plano" no perfil do aluno.
2. O sistema solicita e o usuário insere o motivo.
3. O sistema calcula possíveis taxas rescisórias e exibe o resumo.
4. O usuário confirma o cancelamento.
5. O sistema atualiza o status para "Cancelado".

**Fluxos Alternativos:**
**FA01 - Cancelamento não autorizado (Passo 4):**
  1. O sistema exige senha do Gerente para isentar multas.

**Requisitos Funcionais Relacionados:** [Ex: RF-07]
**Requisitos Não Funcionais Relacionados:** [Ex: RNF-07]
**Regras de Negócio Relacionadas:** [Ex: RN-06]

---

# UC07 - Registrar Pagamento de Mensalidade

**Atores:** Recepcionista.
**Pré-condições:** Aluno com cobrança pendente e caixa aberto.
**Pós-condições:** Cobrança baixada e recibo gerado.

**Fluxo Principal:**
1. A recepcionista seleciona a cobrança pendente do aluno.
2. O sistema solicita a forma de pagamento (Dinheiro, Pix, Cartão).
3. A recepcionista seleciona e confirma o recebimento.
4. O sistema atualiza a cobrança para "Pago".
5. O sistema gera o recibo digital.

**Fluxos Alternativos:**
**FA01 - Pagamento Parcial (Passo 3):**
  1. O sistema registra parte do valor e mantém status "Parcialmente Pago".

**Requisitos Funcionais Relacionados:** [Ex: RF-08]
**Requisitos Não Funcionais Relacionados:** [Ex: RNF-08]
**Regras de Negócio Relacionadas:** [Ex: RN-07]

---

# UC08 - Processar Pagamento Automático (Cartão de Crédito)

**Atores:** Sistema.
**Pré-condições:** Plano recorrente ativo com cartão cadastrado.
**Pós-condições:** Mensalidade debitada e plano renovado.

**Fluxo Principal:**
1. O sistema identifica a cobrança na data de vencimento.
2. O sistema envia a requisição para o Gateway de Pagamento.
3. O Gateway processa e retorna sucesso.
4. O sistema atualiza a fatura para "Pago" e renova o plano.
5. O sistema envia e-mail de confirmação.

**Fluxos Alternativos:**
**FA01 - Transação Recusada (Passo 3):**
  1. O sistema mantém fatura "Pendente", envia e-mail e agenda nova tentativa.

**Requisitos Funcionais Relacionados:** [Ex: RF-09]
**Requisitos Não Funcionais Relacionados:** [Ex: RNF-09]
**Regras de Negócio Relacionadas:** [Ex: RN-08]

---

# UC09 - Consultar Histórico de Pagamentos

**Atores:** Aluno, Recepcionista.
**Pré-condições:** Usuário autenticado.
**Pós-condições:** Histórico financeiro exibido.

**Fluxo Principal:**
1. O usuário acessa a área de histórico financeiro.
2. O sistema busca e exibe a lista de faturas geradas.
3. O usuário clica em uma fatura para ver os detalhes.
4. O sistema exibe detalhes e opções de recibo/pagamento.

**Fluxos Alternativos:**
**FA01 - Nenhum histórico (Passo 2):**
  1. O sistema exibe aviso de que não há faturas.

**Requisitos Funcionais Relacionados:** [Ex: RF-10]
**Requisitos Não Funcionais Relacionados:** [Ex: RNF-10]
**Regras de Negócio Relacionadas:** [Ex: RN-09]

---

# UC10 - Validar Acesso de Aluno via RFID

**Atores:** Sistema de Catraca (API externa).
**Pré-condições:** Aluno aproxima tag RFID do leitor.
**Pós-condições:** Acesso registrado e catraca destravada.

**Fluxo Principal:**
1. O Sistema de Catraca envia o código RFID para o FitPass.
2. O sistema busca o aluno e verifica se o plano está ativo.
3. O sistema registra o "Check-in".
4. O sistema envia o comando "Acesso Liberado".
5. A catraca física é destravada.

**Fluxos Alternativos:**
**FA01 - Tag não reconhecida (Passo 2):**
  1. O sistema envia "Acesso Negado" e a catraca não abre.

**Requisitos Funcionais Relacionados:** [Ex: RF-11]
**Requisitos Não Funcionais Relacionados:** [Ex: RNF-11]
**Regras de Negócio Relacionadas:** [Ex: RN-10]
# UC11 - Bloquear Acesso por Inadimplência

**Atores:** Sistema, Sistema de Catraca.
**Pré-condições:** Aluno aproxima tag, mas possui atraso além da tolerância.
**Pós-condições:** Acesso negado.

**Fluxo Principal:**
1. O Sistema de Catraca envia o RFID para o FitPass.
2. O sistema verifica as faturas e identifica inadimplência.
3. O sistema registra a tentativa bloqueada.
4. O sistema envia o comando "Acesso Bloqueado".
5. A catraca emite aviso e permanece travada.

**Fluxos Alternativos:**
**FA01 - Atraso na tolerância (Passo 2):**
  1. O sistema libera o acesso com um aviso de vencimento no visor.

**Requisitos Funcionais Relacionados:** [Ex: RF-12]
**Requisitos Não Funcionais Relacionados:** [Ex: RNF-12]
**Regras de Negócio Relacionadas:** [Ex: RN-11]

---

# UC12 - Liberar Acesso Manualmente na Catraca

**Atores:** Recepcionista.
**Pré-condições:** Aluno na recepção com problemas de acesso; recepcionista logada.
**Pós-condições:** Acesso liberado no sistema e catraca destravada.

**Fluxo Principal:**
1. A recepcionista pesquisa o perfil do aluno.
2. A recepcionista verifica o plano ativo e clica em "Liberar Catraca".
3. O sistema solicita motivo (ex: "Esqueceu a Tag").
4. A recepcionista insere e confirma.
5. O sistema registra o log e destrava a roleta.

**Fluxos Alternativos:**
**FA01 - Aluno inadimplente (Passo 2):**
  1. A recepcionista cobra o pagamento no balcão antes de liberar.

**Requisitos Funcionais Relacionados:** [Ex: RF-13]
**Requisitos Não Funcionais Relacionados:** [Ex: RNF-13]
**Regras de Negócio Relacionadas:** [Ex: RN-12]

---

# UC13 - Cadastrar Nova Aula na Grade

**Atores:** Gerente.
**Pré-condições:** Gerente autenticado com permissão.
**Pós-condições:** Nova aula adicionada à grade.

**Fluxo Principal:**
1. O gerente clica em "Adicionar Nova Aula" na grade.
2. O gerente preenche detalhes (Nome, Instrutor, Sala, Horário).
3. O sistema valida conflitos de sala ou instrutor.
4. O sistema salva a aula e exibe confirmação.

**Fluxos Alternativos:**
**FA01 - Conflito de Horário (Passo 3):**
  1. O sistema bloqueia cadastro e pede ajuste de sala/instrutor.

**Requisitos Funcionais Relacionados:** [Ex: RF-14]
**Requisitos Não Funcionais Relacionados:** [Ex: RNF-14]
**Regras de Negócio Relacionadas:** [Ex: RN-13]

---

# UC14 - Agendar Participação em Aula

**Atores:** Aluno, Recepcionista.
**Pré-condições:** Plano ativo e vagas disponíveis.
**Pós-condições:** Vaga reservada.

**Fluxo Principal:**
1. O usuário acessa a "Grade de Aulas" e seleciona a aula.
2. O usuário clica em "Agendar".
3. O sistema verifica vagas e confirma a reserva.
4. O sistema diminui as vagas em 1.

**Fluxos Alternativos:**
**FA01 - Aula Lotada (Passo 3):**
  1. O sistema oferece entrar na "Lista de Espera".

**Requisitos Funcionais Relacionados:** [Ex: RF-15]
**Requisitos Não Funcionais Relacionados:** [Ex: RNF-15]
**Regras de Negócio Relacionadas:** [Ex: RN-14]

---

# UC15 - Cancelar Agendamento de Aula

**Atores:** Aluno, Recepcionista.
**Pré-condições:** Reserva ativa para aula futura.
**Pós-condições:** Reserva cancelada e vaga devolvida.

**Fluxo Principal:**
1. O usuário clica em "Cancelar Reserva" nos seus agendamentos.
2. O usuário confirma a ação.
3. O sistema remove o aluno da lista e incrementa as vagas.
4. O sistema exibe mensagem de sucesso.

**Fluxos Alternativos:**
**FA01 - Cancelamento fora do prazo (Passo 2):**
  1. O sistema avisa sobre penalidade de "Falta" (no-show) antes da confirmação.

**Requisitos Funcionais Relacionados:** [Ex: RF-16]
**Requisitos Não Funcionais Relacionados:** [Ex: RNF-16]
**Regras de Negócio Relacionadas:** [Ex: RN-15]
# UC16 - Registrar Presença do Aluno na Aula

**Atores:** Instrutor, Recepcionista.
**Pré-condições:** Aula iniciando e aluno na lista.
**Pós-condições:** Presença confirmada.

**Fluxo Principal:**
1. O instrutor abre a lista de presença da aula.
2. O instrutor marca "Presente" ao lado do aluno.
3. O sistema atualiza o status.
4. O sistema salva a lista finalizada.

**Fluxos Alternativos:**
**FA01 - Aluno sem agendamento (Passo 2):**
  1. O instrutor verifica se há vagas sobrando e o adiciona manualmente.

**Requisitos Funcionais Relacionados:** [Ex: RF-17]
**Requisitos Não Funcionais Relacionados:** [Ex: RNF-17]
**Regras de Negócio Relacionadas:** [Ex: RN-16]

---

# UC17 - Agendar Avaliação Física

**Atores:** Aluno, Recepcionista.
**Pré-condições:** Aluno matriculado e horários livres.
**Pós-condições:** Horário reservado na agenda do instrutor.

**Fluxo Principal:**
1. O usuário seleciona "Nova Avaliação".
2. O usuário seleciona instrutor e horário livre.
3. O sistema verifica a disponibilidade e bloqueia a agenda.
4. O sistema confirma e envia lembretes.

**Fluxos Alternativos:**
**FA01 - Avaliação Cobrada (Passo 3):**
  1. O sistema gera cobrança avulsa caso o plano não cubra.

**Requisitos Funcionais Relacionados:** [Ex: RF-18]
**Requisitos Não Funcionais Relacionados:** [Ex: RNF-18]
**Regras de Negócio Relacionadas:** [Ex: RN-17]

---

# UC18 - Registrar Resultados da Avaliação Física

**Atores:** Instrutor.
**Pré-condições:** Avaliação realizada e instrutor logado.
**Pós-condições:** Métricas salvas no histórico.

**Fluxo Principal:**
1. O instrutor abre o formulário da avaliação do aluno.
2. O instrutor insere as métricas coletadas (Peso, %, etc.).
3. O instrutor clica em "Salvar".
4. O sistema processa os dados e salva no perfil do aluno.

**Fluxos Alternativos:**
**FA01 - Campos vazios (Passo 3):**
  1. O sistema impede o salvamento até o preenchimento de campos essenciais.

**Requisitos Funcionais Relacionados:** [Ex: RF-19]
**Requisitos Não Funcionais Relacionados:** [Ex: RNF-19]
**Regras de Negócio Relacionadas:** [Ex: RN-18]

---

# UC19 - Consultar Histórico e Evolução Física

**Atores:** Aluno, Instrutor.
**Pré-condições:** Aluno possui avaliações.
**Pós-condições:** Gráficos de evolução exibidos.

**Fluxo Principal:**
1. O usuário acessa a área de histórico de evolução.
2. O sistema recupera as métricas salvas.
3. O sistema gera os gráficos comparativos.
4. O usuário visualiza as informações.

**Fluxos Alternativos:**
**FA01 - Nenhuma avaliação (Passo 2):**
  1. O sistema sugere o agendamento de uma nova avaliação.

**Requisitos Funcionais Relacionados:** [Ex: RF-20]
**Requisitos Não Funcionais Relacionados:** [Ex: RNF-20]
**Regras de Negócio Relacionadas:** [Ex: RN-19]

---

# UC20 - Gerar Relatórios Gerenciais

**Atores:** Gerente.
**Pré-condições:** Gerente autenticado.
**Pós-condições:** Relatório exibido/exportado.

**Fluxo Principal:**
1. O gerente acessa o módulo "Relatórios" e escolhe a categoria.
2. O gerente define os filtros (datas, status) e clica em "Gerar".
3. O sistema processa e exibe tabelas e gráficos.
4. O gerente clica em "Exportar" e faz o download.

**Fluxos Alternativos:**
**FA01 - Nenhum dado (Passo 3):**
  1. O sistema não encontra registros e emite aviso para mudar os filtros.

**Requisitos Funcionais Relacionados:** [Ex: RF-21]
**Requisitos Não Funcionais Relacionados:** [Ex: RNF-21]
**Regras de Negócio Relacionadas:** [Ex: RN-20]

