---

# DIAGRAMAÇÃO

<img width="646" height="412" alt="image" src="[https://github.com/user-attachments/assets/f3bcf9ef-113f-441d-8aaa-306150ddf93f](https://github.com/user-attachments/assets/f3bcf9ef-113f-441d-8aaa-306150ddf93f)" />
Diagrama Recepcionista
<img width="418" height="404" alt="image" src="[https://github.com/user-attachments/assets/08145321-8d66-4992-a0e8-e569741eb731](https://github.com/user-attachments/assets/08145321-8d66-4992-a0e8-e569741eb731)" />
Diagrama Aluno
<img width="680" height="457" alt="image" src="[https://github.com/user-attachments/assets/7f13a64e-af81-4ae8-9a18-a461542fe074](https://github.com/user-attachments/assets/7f13a64e-af81-4ae8-9a18-a461542fe074)" />
Diagrama API
<img width="524" height="449" alt="image" src="[https://github.com/user-attachments/assets/92f7c4db-9e8c-4c3b-98a3-ad4bf8cbc36c](https://github.com/user-attachments/assets/92f7c4db-9e8c-4c3b-98a3-ad4bf8cbc36c)" />
Diagrama Gerente
<img width="489" height="394" alt="image" src="[https://github.com/user-attachments/assets/82ed64e7-92ba-4ca0-a588-aa0d5f53204d](https://github.com/user-attachments/assets/82ed64e7-92ba-4ca0-a588-aa0d5f53204d)" />
Diagrama Instrutor

---

# CASOS DE USO

## UC01 — Realizar Matrícula e Vínculo RFID

### Ator Principal

Recepcionista

### Objetivo

Permitir o cadastro de um novo aluno no sistema, vinculando um plano e uma tag RFID para acesso.

### Pré-condições

* Recepcionista deve estar autenticado no sistema.

### Pós-condições

* Aluno registrado no banco de dados com plano vinculado e ID da tag RFID habilitado na catraca.

### Fluxo Principal

1. O aluno solicita a matrícula.
2. O recepcionista insere os dados pessoais e seleciona o plano.
3. O recepcionista aproxima a tag RFID para leitura no sistema.
4. O sistema processa os dados e envia o ID via API para o Sistema de Catraca.
5. O sistema confirma a gravação da matrícula.

### Fluxos Alternativos

* **A1 — Falha de integração com a Catraca:** O sistema exibe erro de timeout na API, salva o cadastro do aluno localmente e agenda o reenvio do RFID para quando a conexão for reestabelecida.

### RF Relacionados

* RF01
* RF05

### RNF Relacionados

* RNF02
* RNF03
* RNF06

### RN Relacionadas

* RN06

---

## UC02 — Registrar Pagamento Presencial

### Ator Principal

Recepcionista

### Objetivo

Registrar o recebimento de mensalidades pagas presencialmente e atualizar a situação do aluno.

### Pré-condições

* Aluno deve estar previamente cadastrado no sistema.

### Pós-condições

* Pagamento registrado no financeiro e regularidade do aluno atualizada.

### Fluxo Principal

1. O aluno solicita o pagamento da mensalidade.
2. O recepcionista busca o cadastro e verifica o valor total.
3. O recepcionista seleciona o método (Dinheiro, Cartão ou PIX) e processa o recebimento.
4. O sistema grava o pagamento.
5. O sistema atualiza automaticamente a situação do aluno para regular.

### Fluxos Alternativos

* **A1 — Tentativa de pagamento parcial:** O recepcionista tenta lançar um valor inferior à mensalidade, e o sistema bloqueia a ação informando que o valor deve ser integral.

### RF Relacionados

* RF03
* RF04

### RNF Relacionados

* RNF03

### RN Relacionadas

* RN04
* RN06
* RN07

---

## UC03 — Gerar Cobrança Online

### Ator Principal

Recepcionista

### Objetivo

Gerar um link de pagamento ou boleto para que o aluno pague a mensalidade remotamente.

### Pré-condições

* Aluno deve possuir um plano ativo.

### Pós-condições

* Link de pagamento/boleto gerado e notificação enviada ao aluno.

### Fluxo Principal

1. O recepcionista acessa o módulo financeiro do aluno.
2. O recepcionista aciona a geração de pagamento online.
3. O sistema gera a cobrança contendo o valor integral do plano.
4. O sistema dispara automaticamente uma notificação para o contato do aluno.

### Fluxos Alternativos

* **A1 — Falha no envio da notificação:** O sistema de mensageria apresenta instabilidade; o sistema gera o link de cobrança na tela para o recepcionista copiar e enviar manualmente ao aluno.

### RF Relacionados

* RF03
* RF10

### RNF Relacionados

* RNF01
* RNF03

### RN Relacionadas

* RN04
* RN06

---

## UC04 — Consultar Regularidade e Bloqueio

### Ator Principal

Recepcionista

### Objetivo

Verificar o status financeiro de um aluno e identificar possíveis bloqueios de acesso.

### Pré-condições

* Recepcionista deve estar logado no sistema.

### Pós-condições

* Status financeiro e de acesso do aluno exibido na tela.

### Fluxo Principal

1. O recepcionista pesquisa o cadastro de um aluno.
2. O sistema verifica as datas de vencimento e pagamentos registrados.
3. O sistema calcula os dias de atraso.
4. O sistema exibe o status; se o atraso for superior a 5 dias, destaca o status como "Bloqueado".

### Fluxos Alternativos

* **A1 — Instabilidade no banco de dados:** O sistema não consegue recuperar o histórico financeiro no tempo limite de 3 segundos, exibe um alerta de indisponibilidade e solicita nova consulta.

### RF Relacionados

* RF04

### RNF Relacionados

* RNF01
* RNF03
* RNF04

### RN Relacionadas

* RN01
* RN06

---

## UC05 — Criar Novo Plano de Matrícula

### Ator Principal

Gerente

### Objetivo

Cadastrar novos pacotes de serviços e planos para serem comercializados pela academia.

### Pré-condições

* Gerente deve estar autenticado no sistema com perfil de gestão.

### Pós-condições

* Um novo tipo de plano é salvo na base de dados e disponibilizado para comercialização.

### Fluxo Principal

1. O gerente acessa o módulo de Configuração de Planos.
2. O gerente seleciona a opção para criar um novo plano.
3. O gerente insere a descrição e o valor da mensalidade.
4. O sistema valida se os dados inseridos estão corretos.
5. O sistema salva o plano e confirma a operação.

### Fluxos Alternativos

* **A1 — Dados obrigatórios ausentes:** O sistema alerta sobre os campos vazios e impede a gravação até que o gerente preencha os dados faltantes.

### RF Relacionados

* RF02

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN06

---

## UC06 — Editar ou Desativar Plano Existente

### Ator Principal

Gerente

### Objetivo

Atualizar informações de planos existentes ou retirá-los de comercialização.

### Pré-condições

* Gerente deve estar logado e o plano alvo deve estar previamente cadastrado.

### Pós-condições

* O status ou as características do plano são atualizadas no sistema.

### Fluxo Principal

1. O gerente acessa a listagem de planos cadastrados.
2. O gerente seleciona um plano específico para edição ou alteração de status.
3. O gerente modifica os dados ou muda o status do plano para "Inativo".
4. O sistema processa a atualização.
5. O sistema salva as alterações e emite mensagem de sucesso.

### Fluxos Alternativos

* **A1 — Tentativa de desativar plano com alunos ativos:** O sistema identifica que há alunos vinculados ao plano e emite um alerta informando que o plano ficará invisível para novas matrículas, mas será mantido para os alunos atuais até o fim da vigência.

### RF Relacionados

* RF02

### RNF Relacionados

* RNF03
* RNF04

### RN Relacionadas

* RN06

---

## UC07 — Emitir Relatório de Alunos Ativos e Inadimplentes

### Ator Principal

Gerente

### Objetivo

Gerar um balanço dos alunos regulares em contraste com os alunos em atraso financeiro.

### Pré-condições

* Gerente deve estar autenticado no sistema.

### Pós-condições

* O sistema consolida e exibe os dados financeiros e de atividade dos alunos.

### Fluxo Principal

1. O gerente acessa a área de Relatórios Gerenciais.
2. O gerente seleciona a emissão de relatório filtrando por "Alunos Ativos" ou "Inadimplência".
3. O sistema processa a consulta na base de dados verificando as regularidades.
4. O sistema apresenta o relatório completo na tela.

### Fluxos Alternativos

* **A1 — Nenhum registro encontrado:** O sistema informa que não há alunos correspondentes ao filtro aplicado no momento e orienta o gerente a escolher outro filtro.

### RF Relacionados

* RF04
* RF09

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN06

---

## UC08 — Emitir Relatório de Ocupação e Acessos

### Ator Principal

Gerente

### Objetivo

Monitorar a lotação das aulas e o volume de acessos na catraca para tomadas de decisão.

### Pré-condições

* Gerente deve estar autenticado no sistema.

### Pós-condições

* O sistema gera e exibe as estatísticas de uso da academia e frequência de turmas.

### Fluxo Principal

1. O gerente navega até o módulo de Relatórios Gerenciais.
2. O gerente solicita a emissão do "Histórico de Acessos" ou "Ocupação das Aulas" filtrando por um período.
3. O sistema cruza os dados de entradas na catraca e agendamentos com a capacidade máxima das aulas.
4. O sistema compila as métricas e exibe o relatório solicitado.

### Fluxos Alternativos

* **A1 — Período sem registros:** O sistema não encontra agendamentos ou acessos no período selecionado e exibe o relatório vazio com a mensagem "Nenhum dado de ocupação encontrado para o intervalo".

### RF Relacionados

* RF09

### RNF Relacionados

* RNF03
* RNF04

### RN Relacionadas

* RN02
* RN06

---

## UC09 — Registrar Presença na Aula

### Ator Principal

Instrutor

### Objetivo

Realizar a chamada dos alunos que reservaram vaga em uma aula específica.

### Pré-condições

* Instrutor deve estar autenticado no sistema.

### Pós-condições

* A presença ou falta do aluno é registrada no histórico da aula.

### Fluxo Principal

1. O instrutor acessa a lista de aulas do dia.
2. O instrutor seleciona a aula que está ministrando.
3. O sistema exibe a lista de alunos com vagas reservadas.
4. O instrutor marca a presença dos alunos presentes.
5. O sistema salva as informações de presença.

### Fluxos Alternativos

* **A1 — Turma sem alunos inscritos:** O sistema verifica que não houve reservas para a aula selecionada, exibe a mensagem "Nenhum agendamento realizado para esta aula" e bloqueia a chamada.

### RF Relacionados

* RF07

### RNF Relacionados

* RNF03
* RNF04

### RN Relacionadas

* RN02
* RN06

---

## UC10 — Registrar Avaliação Física

### Ator Principal

Instrutor

### Objetivo

Cadastrar as métricas corporais e de saúde do aluno de forma segura.

### Pré-condições

* Instrutor deve estar autenticado no sistema.

### Pós-condições

* Os dados corporais do aluno são registrados e salvos de forma criptografada.

### Fluxo Principal

1. O instrutor busca o cadastro do aluno.
2. O sistema verifica automaticamente se o aluno está ativo e regular.
3. O instrutor insere as métricas avaliadas (peso, IMC, percentual de gordura).
4. O sistema criptografa e salva os dados sensíveis de saúde.
5. O sistema confirma a gravação da avaliação.

### Fluxos Alternativos

* **A1 — Aluno inativo ou inadimplente:** O sistema exibe um bloqueio na tela e impede a realização da avaliação física, instruindo o instrutor a encaminhar o aluno à recepção.

### RF Relacionados

* RF08

### RNF Relacionados

* RNF02
* RNF03

### RN Relacionadas

* RN05
* RN06

---

## UC11 — Anexar Arquivo à Avaliação Física

### Ator Principal

Instrutor

### Objetivo

Vincular exames, fotos ou documentos complementares ao histórico de avaliação do aluno.

### Pré-condições

* Uma avaliação física deve estar em andamento ou ter sido recém-criada.

### Pós-condições

* O arquivo é vinculado ao histórico do aluno e armazenado com segurança.

### Fluxo Principal

1. Na tela de Avaliação Física, o instrutor seleciona a opção "Anexar Arquivo".
2. O instrutor faz o upload do documento no sistema.
3. O sistema valida o formato e anexa o arquivo de forma segura e criptografada.
4. O sistema exibe mensagem de sucesso na importação.

### Fluxos Alternativos

* **A1 — Falha no envio do arquivo:** O sistema informa que o arquivo é muito grande ou possui formato inválido, solicitando que o instrutor escolha um novo arquivo compatível.

### RF Relacionados

* RF08

### RNF Relacionados

* RNF02
* RNF04

### RN Relacionadas

* RN06

---

## UC12 — Liberar Nova Avaliação Física e Notificar

### Ator Principal

Instrutor

### Objetivo

Sinalizar no sistema que o aluno está apto para uma reavaliação e avisá-lo automaticamente.

### Pré-condições

* Aluno deve estar apto e dentro do prazo estipulado para reavaliação.

### Pós-condições

* O sistema agenda a liberação e notifica o aluno.

### Fluxo Principal

1. O instrutor acessa o perfil do aluno.
2. O instrutor aciona a opção "Liberar Nova Avaliação Física".
3. O sistema registra a liberação no banco de dados.
4. O sistema dispara uma notificação automática para o dispositivo do aluno informando a liberação.

### Fluxos Alternativos

* **A1 — Aluno sem contato válido:** O sistema identifica a ausência de e-mail ou aplicativo vinculado ao cadastro, grava a liberação no banco de dados, mas avisa o instrutor para informar o aluno presencialmente.

### RF Relacionados

* RF10

### RNF Relacionados

* RNF03

### RN Relacionadas

* RN05
* RN06

---

## UC13 — Visualizar Horários de Aulas

### Ator Principal

Aluno

### Objetivo

Permitir que o aluno consulte a grade de aulas disponíveis na academia.

### Pré-condições

* Aluno deve possuir acesso ao aplicativo ou portal web da academia.

### Pós-condições

* O sistema apresenta a grade de horários atualizada.

### Fluxo Principal

1. O aluno acessa a seção de agendamentos no sistema.
2. O sistema recupera a grade de aulas do banco de dados.
3. O sistema exibe os horários, os nomes das aulas e os instrutores responsáveis.

### Fluxos Alternativos

* **A1 — Grade de horários indisponível:** O sistema verifica que o gerente ainda não publicou as aulas da semana e exibe a mensagem "Grade de horários em atualização. Retorne mais tarde".

### RF Relacionados

* RF06

### RNF Relacionados

* RNF01
* RNF03
* RNF04

### RN Relacionadas

* RN02
* RN06

---

## UC14 — Reservar Vaga em Aula

### Ator Principal

Aluno

### Objetivo

Garantir a participação do aluno em uma aula específica respeitando a capacidade da sala.

### Pré-condições

* Aluno deve estar logado e a aula desejada deve estar disponível no dia.

### Pós-condições

* A vaga é garantida para o aluno e a ocupação da aula é atualizada.

### Fluxo Principal

1. O aluno seleciona uma aula específica na grade de horários.
2. O aluno clica em "Reservar Vaga".
3. O sistema verifica a quantidade de alunos já inscritos na aula.
4. O sistema confirma a reserva e deduz uma vaga da capacidade máxima.
5. O sistema envia uma notificação automática de confirmação para o aluno.

### Fluxos Alternativos

* **A1 — Limite de vagas atingido:** O sistema identifica que a aula atingiu o número máximo de alunos, bloqueia a reserva e exibe a mensagem de turma lotada.

### RF Relacionados

* RF06
* RF10

### RNF Relacionados

* RNF03
* RNF04

### RN Relacionadas

* RN02

---

## UC15 — Cancelar Agendamento de Aula

### Ator Principal

Aluno

### Objetivo

Permitir que o aluno desista de uma reserva, liberando a vaga para outros, dentro do prazo permitido.

### Pré-condições

* Aluno deve ter uma reserva ativa em uma aula futura.

### Pós-condições

* A reserva é cancelada e a vaga retorna para a disponibilidade do sistema.

### Fluxo Principal

1. O aluno acessa a área de suas reservas ativas.
2. O aluno seleciona a aula agendada e clica em "Cancelar Reserva".
3. O sistema verifica o horário atual em relação ao horário de início da aula.
4. O sistema valida que o pedido foi feito com pelo menos 1 hora de antecedência.
5. O sistema remove o aluno da lista e libera a vaga.

### Fluxos Alternativos

* **A1 — Cancelamento fora do prazo:** O sistema verifica que falta menos de 1 hora para o início da aula, bloqueia a ação e informa que o prazo para cancelamento expirou.

### RF Relacionados

* RF06

### RNF Relacionados

* RNF03
* RNF04

### RN Relacionadas

* RN03

---

## UC16 — Visualizar Notificações do Sistema

### Ator Principal

Aluno

### Objetivo

Manter o aluno informado sobre pendências, confirmações e avisos gerais.

### Pré-condições

* Aluno deve estar logado na interface do sistema (desktop ou mobile).

### Pós-condições

* O aluno toma conhecimento dos avisos pendentes gerados pelo sistema.

### Fluxo Principal

1. O aluno acessa a central de notificações do sistema.
2. O sistema exibe a lista de mensagens recebidas, como vencimento de mensalidade e confirmações.
3. O aluno marca as notificações como lidas.

### Fluxos Alternativos

* **A1 — Caixa de notificações vazia:** O sistema verifica que não há nenhum alerta disparado para o aluno e exibe um estado vazio com a mensagem "Você não possui novas notificações".

### RF Relacionados

* RF10

### RNF Relacionados

* RNF04

### RN Relacionadas

* RN01
* RN06

---

## UC17 — Solicitar Validação de Acesso (RFID)

### Ator Principal

Sistema de Catraca (API)

### Objetivo

Consultar a base de dados do sistema para verificar se a catraca deve ser liberada para o aluno.

### Pré-condições

* O aluno deve aproximar a tag RFID da catraca e haver conexão de rede.

### Pós-condições

* A catraca recebe a resposta (liberação ou bloqueio) via API REST.

### Fluxo Principal

1. O aluno aproxima o cartão/tag da leitora física.
2. O Sistema de Catraca envia uma requisição via API REST (JSON) para o sistema central.
3. O sistema FitPass recebe o ID e consulta o cadastro do aluno.
4. O sistema verifica a regularidade do aluno em menos de 3 segundos.
5. O sistema valida que o aluno não possui atraso superior a 5 dias.
6. O sistema retorna o comando de liberação para a Catraca.

### Fluxos Alternativos

* **A1 — Aluno Inadimplente:** O sistema identifica que a mensalidade está vencida há mais de 5 dias e retorna o comando de bloqueio de acesso para a Catraca.

### RF Relacionados

* RF05

### RNF Relacionados

* RNF01
* RNF03
* RNF06

### RN Relacionadas

* RN01
* RN06

---

## UC18 — Registrar Histórico de Acesso

### Ator Principal

Sistema de Catraca (API)

### Objetivo

Gravar a entrada do aluno na academia após a liberação física da catraca.

### Pré-condições

* O acesso do aluno deve ter sido validado e liberado pelo UC17.

### Pós-condições

* A entrada física é registrada no banco de dados para relatórios futuros.

### Fluxo Principal

1. Após o giro físico da catraca, o Sistema de Catraca envia uma confirmação de entrada via API JSON.
2. O sistema FitPass recebe a confirmação de passagem.
3. O sistema grava a data e hora exatas da entrada no perfil do aluno.
4. O sistema retorna um recibo de sucesso (HTTP 200) para a Catraca.

### Fluxos Alternativos

* **A1 — Instabilidade temporária na rede:** O sistema de catraca não consegue conexão imediata via API REST; a catraca armazena o evento localmente e repete a sincronização automaticamente quando a rede voltar.

### RF Relacionados

* RF05
* RF09

### RNF Relacionados

* RNF01
* RNF03
* RNF06

### RN Relacionadas

* RN06

---

## UC19 — Executar Verificação Automática de Regularidade

### Ator Principal

Sistema FitPass (Rotina Automática)

### Objetivo

Fazer a varredura periódica de vencimentos para bloquear automaticamente alunos inadimplentes.

### Pré-condições

* O sistema deve estar em execução e as datas de vencimento cadastradas.

### Pós-condições

* A situação dos alunos é atualizada para inadimplente/bloqueado se o prazo de 5 dias expirar.

### Fluxo Principal

1. O sistema dispara a rotina diária de verificação de pagamentos.
2. O sistema varre o banco de dados buscando mensalidades não pagas.
3. O sistema calcula os dias de atraso de cada registro.
4. Ao identificar atraso maior que 5 dias, o sistema altera o status do aluno para "Bloqueado".

### Fluxos Alternativos

* **A1 — Conflito de atualização de registro:** O sistema tenta atualizar o status de um aluno, mas o cadastro está sendo editado simultaneamente pela recepção; o sistema pula o registro temporariamente e reprocessa no ciclo seguinte.

### RF Relacionados

* RF04

### RNF Relacionados

* RNF01
* RNF03

### RN Relacionadas

* RN01
* RN07

---

## UC20 — Processar e Enviar Notificações de Vencimento

### Ator Principal

Sistema FitPass (Rotina Automática)

### Objetivo

Avisar de forma proativa os alunos sobre faturas a vencer ou em atraso.

### Pré-condições

* Aluno deve ter um plano ativo com mensalidade a vencer ou recém-vencida.

### Pós-condições

* Um alerta é disparado para o dispositivo ou contato do aluno.

### Fluxo Principal

1. O sistema consulta a base de dados em busca de mensalidades com vencimento próximo ou expirado.
2. O sistema gera a mensagem padrão de alerta financeiro.
3. O sistema envia a notificação automaticamente para o perfil/contato do aluno.
4. O sistema registra no histórico do aluno que a notificação foi enviada.

### Fluxos Alternativos

* **A1 — Gateway de envio inoperante:** O serviço de envio de notificações encontra-se fora do ar; o sistema enfileira as mensagens não enviadas e realiza novas tentativas automáticas posteriormente.

### RF Relacionados

* RF10

### RNF Relacionados

* RNF01

### RN Relacionadas

* RN01
* RN04

---
