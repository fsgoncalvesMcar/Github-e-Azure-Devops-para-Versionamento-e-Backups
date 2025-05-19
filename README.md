# Github-e-Azure-Devops-para-Versionamento-e-Backups

A seguir, segue um passo a passo detalhado para criar um Azure Data Factory integrado ao Azure DevOps e configurar o repositório Git para controle de versão e colaboração:

1. Criar a Organização, Projeto e o Repositório no Azure DevOps
Acesse o Azure DevOps:
Entre no portal do Azure DevOps em https://dev.azure.com.
Caso ainda não tenha, crie uma nova organização.
Crie um Projeto:
Clique em “New Project” para iniciar a criação de um novo projeto.
Dê um nome descritivo (por exemplo, “ADF-Projeto-Demo”) e defina a visibilidade (público ou privado) conforme sua necessidade.
Configure um Repositório Git Vazio:
Dentro do projeto, vá na seção “Repos”.
Crie um novo repositório vazio para receber os artefatos do Data Factory.
Essa ação garante um espaço dedicado para versionar pipelines, datasets, linked services e demais recursos do ADF.

2. Criar o Azure Data Factory no Portal do Azure
Inicie o Processo de Criação:
No Portal do Azure, clique em “Criar um recurso” e pesquise por “Data Factory”.
Clique para iniciar a criação de um novo Data Factory.
Defina as Configurações Básicas:
Nomeie o recurso (por exemplo, “adf-projeto-demo”).
Escolha a assinatura, grupo de recursos e região desejada.
Opção “Configure Git Later”:
Durante o processo de criação, quando solicitado a configurar o Git, selecione a opção “Configure Git later”.
Essa escolha permitirá que você integre o ADF ao Git do Azure DevOps posteriormente.

3. Conectar o Azure Data Factory ao Repositório Git do Azure DevOps
Acesse a Seção de Gerenciamento do ADF:
No portal do Azure, depois de criado o Data Factory, abra o seu recurso.
Na barra lateral esquerda, clique no ícone de engrenagem “Manage” para acessar as configurações.
Configuração do Git:
Selecione a opção “Git configuration”.
Escolha “Azure DevOps Git” como o provedor de repositório.
Informações para a Integração:
Conta e Organização: Conecte-se com a conta do Azure DevOps e escolha a organização criada anteriormente.
Projeto e Repositório: Selecione o projeto e o repositório Git vazio que você criou.
Branch de Colaboração: Defina um branch de colaboração, normalmente “main”, onde os desenvolvedores realizarão os commits.
Root Folder: Especifique a pasta raiz onde os arquivos do ADF serão organizados. Por exemplo, use “/adf”.
Branch de Publicação: Configure o branch de publicação, geralmente nomeado “adf_publish”. Esse branch representará o ambiente em produção do ADF.
Aplicar Configurações:
Após preencher os dados, confirme e aplique as configurações.
O Azure Data Factory irá conectar-se ao repositório e, a partir desse momento, cada alteração feita através do ADF Studio será versionada no Git.

4. Trabalhando com a Integração e o Controle de Versão
Edição e Versionamento dos Artefatos:
Ao criar ou editar pipelines, datasets e linked services pelo ADF Studio, as alterações serão salvas diretamente no branch de colaboração configurado.
Isso garante rastreabilidade e facilita o trabalho em equipe, permitindo reverter alterações e auditar as modificações.
Publicação das Alterações:
Após concluir suas alterações e testes, clique no botão “Publish” no ADF Studio.
Essa ação envia os artefatos para o branch “adf_publish”, que representa o ambiente ativo (produção).
Verificação da Estrutura no Repositório:
No repositório Git do Azure DevOps, você deverá visualizar uma estrutura de pastas organizada com diretórios como:
/adf – pasta raiz configurada.
/pipelines – contendo os arquivos JSON dos pipelines.
/datasets – arquivos JSON dos dados e esquemas.
/linkedServices – definições de conexões com fontes de dados e serviços.
Essa organização prepara o ambiente para implementar processos de CI/CD, possibilitando automações e deploys sem atritos.

5. Dicas e Recomendações Adicionais
Automação com CI/CD: Conforme sua equipe evoluir, configure pipelines no Azure DevOps para automatizar a integração e entrega contínua. Isso garantirá que as alterações sejam testadas e implantadas de maneira controlada e segura.
Boas Práticas de Controle de Versão: Utilize commits frequentes, mensagens claras e a revisão de código para manter a integridade dos artefatos e facilitar a colaboração entre os membros da equipe.
