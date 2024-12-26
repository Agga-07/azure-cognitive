# azure-cognitive

# Configuração de Pesquisa com Azure AI Search

Este repositório contém um passo a passo detalhado para configurar uma solução de pesquisa usando o **Azure AI Search**, integrando dados enriquecidos com **Serviços de IA do Azure** para gerar insights valiosos a partir de avaliações de clientes.

A solução foi criada para a **Fourth Coffee**, uma rede de cafés, com o objetivo de analisar e obter insights a partir das avaliações dos clientes. Ao final deste processo, você terá aprendido como indexar dados, aplicar habilidades cognitivas de IA e consultar esses dados de maneira eficaz.

## Requisitos

Antes de começar, certifique-se de ter acesso ao portal do Azure e de ter uma assinatura ativa. Você precisará de três recursos principais:

1. **Azure AI Search**: Para realizar a indexação e consulta dos dados.
2. **Serviços de IA do Azure**: Para enriquecer seus dados com análise cognitiva.
3. **Armazenamento de Blobs do Azure**: Para armazenar os documentos (avaliações) que serão indexados.

## Passo a Passo

### 1. Criar Recursos do Azure

#### 1.1 Criar um Recurso de Azure AI Search

1. No portal do Azure, clique em **+ Criar um recurso** e pesquise por **Azure AI Search**.
2. Selecione **Criar** e preencha as configurações:
   - Assinatura: Selecione sua assinatura do Azure.
   - Grupo de recursos: Selecione ou crie um novo grupo de recursos.
   - Nome do serviço: Escolha um nome exclusivo.
   - Local: Escolha a região desejada (ex: **Leste dos EUA 2**).
   - Tipo de preço: **Básico**.
3. Após a implantação, selecione **Ir para o recurso**.

#### 1.2 Criar um Recurso de Serviços de IA do Azure

1. Retorne à página inicial do portal do Azure e crie um novo recurso de **Serviços de IA do Azure**.
2. Certifique-se de que este recurso esteja na mesma região que o **Azure AI Search** e no mesmo grupo de recursos.

#### 1.3 Criar uma Conta de Armazenamento

1. Crie uma conta de armazenamento no Azure, preferencialmente na mesma região e grupo de recursos.
2. Após a criação, no painel da conta de armazenamento, ative a permissão de **Acesso anônimo ao Blob**.

### 2. Carregar Documentos no Armazenamento do Azure

1. No painel de Armazenamento de Blobs do Azure, crie um **contêiner** chamado `coffee-reviews`.
2. Baixe e extraia as **avaliações de clientes** (arquivo compactado) de [aqui](https://aka.ms/mslearn-coffee-reviews).
3. Carregue os arquivos extraídos para o contêiner recém-criado.

### 3. Criar um Índice de Pesquisa

1. Navegue até o recurso **Azure AI Search** e selecione **Importar dados**.
2. Selecione **Armazenamento de Blobs do Azure** como fonte de dados.
3. Configure o assistente de importação para criar automaticamente um índice e indexador.
   - Utilize **habilidades cognitivas** do Azure para enriquecer os dados (ex: extração de **frases-chave**, **sentimento**, **tags de imagem**, etc.).
4. Salve os dados enriquecidos em um **repositório de conhecimento** para análise posterior.

### 4. Consultar o Índice

1. Use o **Gerenciador de Pesquisa** para escrever e testar consultas sobre o índice criado.
2. Exemplos de consultas:
   - Pesquisar por localização (`locations: 'Chicago'`).
   - Filtrar por sentimento (`sentiment: 'negative'`).
   - Pesquisar todas as avaliações com a consulta `"search": "*"`.
3. Teste os filtros e analise os resultados no formato **JSON**.

### 5. Explorar o Repositório de Conhecimento

1. Acesse o **repositório de conhecimento** no Azure Storage para ver as projeções e tabelas de dados enriquecidos.
2. Explore os campos enriquecidos como **frases-chave**, **entidades** extraídas e **imagens geradas**.

## Ferramentas e Possibilidades

A integração com **Azure AI Search** e **Serviços de IA do Azure** abre várias possibilidades para enriquecer e explorar dados. Algumas ferramentas e cenários que podem se beneficiar dessa solução incluem:

- **Análise de Sentimentos**: Avaliar a opinião dos clientes sobre os produtos ou serviços oferecidos.
- **Extração de Entidades**: Identificar informações como locais, nomes de produtos ou eventos mencionados nas avaliações.
- **Extração de Frases-chave**: Identificar os tópicos mais importantes ou frequentes nas avaliações.
- **Análise de Imagens**: Detectar imagens e gerar tags associadas, que podem fornecer mais contexto sobre as avaliações.

Essas funcionalidades são extremamente úteis para áreas como **marketing**, **suporte ao cliente** e **inteligência de negócios**, proporcionando insights mais profundos e valiosos sobre as experiências dos clientes.

## Aprendizados Adquiridos

Durante o processo, aprendemos os seguintes pontos importantes:

- **Integração de Dados**: A integração entre o Azure AI Search e os Serviços de IA do Azure permite enriquecer os dados, tornando as consultas mais ricas e significativas.
- **Habilidades Cognitivas**: O uso de habilidades cognitivas (como OCR e extração de sentimento) ajuda a transformar dados brutos em insights acionáveis.
- **Gerenciamento de Dados**: Armazenar dados enriquecidos em um repositório de conhecimento facilita a análise e a consulta de dados em diferentes estágios.

## Conclusão

Com as ferramentas do Azure AI Search, você pode criar poderosas soluções de mineração de conhecimento para analisar grandes volumes de dados não estruturados e extrair insights valiosos. Este processo é ideal para empresas que desejam melhorar a experiência do cliente, otimizar o marketing e aprimorar o atendimento com base em dados concretos.
