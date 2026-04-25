# Histórias de Usuário

## HU01 - Autenticação no sistema
`Atores:` Aluno, Professor, Empresa Parceira

`Relacionamento com os diagramas:` `Autenticar-se`, `UsuarioSistema`, `AuthController`, `AutenticacaoService`

`História:` Como usuário do sistema, quero me autenticar com login e senha para acessar apenas as funcionalidades permitidas ao meu perfil.

`Critérios de aceitação:`
- O sistema deve exigir login e senha válidos para liberar o acesso.
- O sistema deve identificar o perfil autenticado e apresentar as funcionalidades correspondentes.
- O sistema deve impedir o acesso quando as credenciais forem inválidas.

## HU02 - Cadastro de aluno
`Ator:` Aluno

`Relacionamento com os diagramas:` `Cadastrar aluno`, `Aluno`, `InstituicaoEnsino`, `AlunoController`, `CadastroAlunoService`

`História:` Como aluno, quero me cadastrar informando meus dados pessoais e acadêmicos para participar do sistema de moeda estudantil.

`Critérios de aceitação:`
- O cadastro do aluno deve armazenar nome, email, CPF, RG, endereço, instituição de ensino e curso.
- A instituição de ensino deve ser selecionada entre as instituições previamente cadastradas no sistema.
- Após o cadastro, o aluno deve possuir credenciais de acesso e uma carteira de moedas vinculada à sua conta.

## HU03 - Consulta de extrato do aluno
`Ator:` Aluno

`Relacionamento com os diagramas:` `Consultar extrato`, `CarteiraMoedas`, `TransacaoMoedas`, `ExtratoController`, `ExtratoService`

`História:` Como aluno, quero consultar meu extrato para visualizar meu saldo atual e o histórico de recebimentos e resgates realizados.

`Critérios de aceitação:`
- O aluno deve visualizar o saldo atual da sua carteira.
- O extrato do aluno deve listar recebimentos de moedas e resgates de vantagens.
- A consulta de extrato deve estar disponível somente após autenticação.

## HU04 - Consulta de extrato do professor
`Ator:` Professor

`Relacionamento com os diagramas:` `Consultar extrato`, `Professor`, `CarteiraMoedas`, `ExtratoController`, `ExtratoService`

`História:` Como professor, quero consultar meu extrato para acompanhar meu saldo de moedas e as distribuições já realizadas aos alunos.

`Critérios de aceitação:`
- O professor deve visualizar o saldo atual disponível para distribuição.
- O extrato do professor deve listar os envios de moedas realizados.
- A consulta de extrato deve estar disponível somente após autenticação.

## HU05 - Recebimento semestral de moedas pelo professor
`Ator:` Professor

`Relacionamento com os diagramas:` `Professor`, `CreditoSemestralProfessor`, `CarteiraMoedas`, `CargaSemestralProfessorService`

`História:` Como professor, quero receber automaticamente 1000 moedas a cada semestre para reconhecer o mérito dos meus alunos ao longo do período letivo.

`Critérios de aceitação:`
- O sistema deve adicionar 1000 moedas ao saldo do professor a cada semestre.
- O valor não utilizado em semestres anteriores deve permanecer acumulado no saldo corrente.
- O novo saldo deve ficar disponível para consulta e distribuição após a carga semestral.

## HU06 - Envio de moedas para aluno
`Ator:` Professor

`Relacionamento com os diagramas:` `Enviar moedas ao aluno`, `Professor`, `Aluno`, `DistribuicaoMoedas`, `ProfessorController`, `DistribuicaoMoedasService`

`História:` Como professor, quero enviar moedas para um aluno com uma mensagem de reconhecimento para premiar seu desempenho, comportamento ou participação.

`Critérios de aceitação:`
- O professor deve selecionar o aluno destinatário, a quantidade de moedas e informar uma mensagem obrigatória de reconhecimento.
- O sistema deve validar se o professor possui saldo suficiente antes de concluir a operação.
- Ao concluir o envio, o saldo do professor deve ser debitado e o saldo do aluno deve ser creditado.
- A distribuição deve ser registrada no extrato de ambos os envolvidos.

## HU07 - Notificação de recebimento de moedas
`Ator:` Aluno

`Relacionamento com os diagramas:` `Notificar recebimento de moedas`, `DistribuicaoMoedas`, `NotificacaoEmailService`

`História:` Como aluno, quero receber uma notificação por email quando ganhar moedas para saber que fui reconhecido por um professor.

`Critérios de aceitação:`
- Após uma distribuição de moedas concluída com sucesso, o sistema deve enviar um email ao aluno.
- A notificação deve estar associada ao recebimento efetivado na carteira do aluno.
- O envio do email deve ocorrer sem dispensar o registro da transação no sistema.

## HU08 - Cadastro de empresa parceira
`Ator:` Empresa Parceira

`Relacionamento com os diagramas:` `Cadastrar empresa parceira`, `EmpresaParceira`, `EmpresaParceiraController`, `CadastroParceiroService`

`História:` Como empresa parceira, quero me cadastrar no sistema para oferecer vantagens em troca de moedas estudantis.

`Critérios de aceitação:`
- O cadastro da empresa deve armazenar, no mínimo, sua identificação e email de contato.
- Após o cadastro, a empresa deve possuir credenciais de acesso para administrar suas vantagens.
- A empresa autenticada deve poder acessar o fluxo de cadastro de vantagens.

## HU09 - Cadastro de vantagem
`Ator:` Empresa Parceira

`Relacionamento com os diagramas:` `Cadastrar vantagem`, `Vantagem`, `VantagemController`, `CatalogoVantagensService`

`História:` Como empresa parceira, quero cadastrar vantagens com descrição, foto e custo em moedas para disponibilizar benefícios aos alunos.

`Critérios de aceitação:`
- A empresa deve informar título, descrição, foto e custo em moedas da vantagem.
- A vantagem cadastrada deve ficar associada à empresa parceira responsável.
- O cadastro de vantagem deve estar disponível somente para empresa autenticada.

## HU10 - Consulta de vantagens
`Ator:` Aluno

`Relacionamento com os diagramas:` `Consultar vantagens`, `Vantagem`, `VantagemController`, `CatalogoVantagensService`

`História:` Como aluno, quero consultar as vantagens disponíveis para escolher em quais benefícios posso trocar minhas moedas.

`Critérios de aceitação:`
- O sistema deve listar as vantagens ativas cadastradas pelas empresas parceiras.
- Cada vantagem exibida deve apresentar informações suficientes para decisão, incluindo descrição, imagem e custo em moedas.
- A consulta de vantagens deve estar disponível somente após autenticação.

## HU11 - Resgate de vantagem
`Ator:` Aluno

`Relacionamento com os diagramas:` `Resgatar vantagem`, `Aluno`, `Vantagem`, `ResgateVantagem`, `ResgateController`, `ResgateVantagemService`

`História:` Como aluno, quero resgatar uma vantagem usando minhas moedas para trocar meu saldo por produtos ou descontos oferecidos por parceiros.

`Critérios de aceitação:`
- O aluno deve conseguir selecionar uma vantagem disponível para resgate.
- O sistema deve validar se o aluno possui saldo suficiente antes de concluir a troca.
- Ao concluir o resgate, o sistema deve debitar o valor correspondente da carteira do aluno.
- O resgate deve ser registrado no extrato do aluno com um código de conferência gerado pelo sistema.

## HU12 - Envio de cupom de resgate ao aluno
`Ator:` Aluno

`Relacionamento com os diagramas:` `Enviar cupom de resgate`, `ResgateVantagem`, `NotificacaoEmailService`

`História:` Como aluno, quero receber por email um cupom com código de resgate para utilizar a vantagem presencialmente junto ao parceiro.

`Critérios de aceitação:`
- Após um resgate concluído com sucesso, o sistema deve enviar um email ao aluno.
- O email deve conter o código de conferência gerado para o resgate.
- O cupom enviado deve corresponder à vantagem efetivamente resgatada.

## HU13 - Recebimento de aviso de resgate pela empresa parceira
`Ator:` Empresa Parceira

`Relacionamento com os diagramas:` `Enviar cupom de resgate`, `EmpresaParceira`, `ResgateVantagem`, `NotificacaoEmailService`

`História:` Como empresa parceira, quero receber por email os dados do resgate e seu código de conferência para validar a troca presencial realizada pelo aluno.

`Critérios de aceitação:`
- Após um resgate concluído com sucesso, o sistema deve enviar um email também para a empresa parceira responsável pela vantagem.
- O email da empresa deve conter o código de conferência do resgate.
- A notificação deve permitir a conferência da troca presencial associada à vantagem resgatada.

## Observações de alinhamento
- As histórias HU01, HU02, HU03, HU04, HU06, HU08, HU09, HU10 e HU11 refletem diretamente os casos de uso presentes no diagrama de casos de uso.
- As histórias HU05, HU12 e HU13 complementam regras explícitas do PDF e já estão representadas no diagrama de classes e no diagrama de componentes.
- As entidades centrais mapeadas nas histórias são `Aluno`, `Professor`, `EmpresaParceira`, `CarteiraMoedas`, `DistribuicaoMoedas`, `ResgateVantagem` e `Vantagem`.
