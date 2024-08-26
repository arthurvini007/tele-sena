# Projeto Tele Sena

### Objetivo

O projeto Tele Sena surgiu durante um hackathon com o objetivo de resolver a questão: "Como organizar, categorizar e priorizar as informações recebidas para facilitar a tomada de decisão sobre quais conteúdos produzir?" Para abordar essa problemática, desenvolvemos uma estrutura baseada na Medallion Architecture Layers. Esta arquitetura organiza logicamente os dados do lakehouse e visa aprimorar de forma incremental e progressiva a estrutura e a qualidade dos dados à medida que eles passam pelas três camadas da arquitetura: Bronze, Prata e Ouro.

### Introdução

O projeto começou com a criação de um mini servidor na plataforma disponibilizada pelo Google Drive. Essa etapa inicial permitiu a organização e a estruturação das camadas da arquitetura para o nosso projeto, facilitando a gestão dos dados e a implementação das camadas de arquitetura necessárias.

### Raspagem de Dados do Instagram

Utilizamos a biblioteca Instaloader, uma ferramenta popular para extração de dados do Instagram usando Python. A Instaloader permite o download de postagens, histórias, perfis e muito mais diretamente do Instagram.

O código desenvolvido carrega o perfil de um usuário do Instagram, localiza uma postagem específica pelo shortcode fornecido e, se a postagem for encontrada, imprime informações sobre cada comentário dessa postagem. Para evitar sobrecarga, o script insere um atraso entre as requisições. Após a leitura dos comentários, o script aguarda um período adicional antes de finalizar. Se a postagem não for encontrada, uma mensagem de erro é exibida.


![Capturar](https://github.com/user-attachments/assets/16a14f6f-bc55-4375-9617-d69e7ed0e62e)

#### PRIMEIRA CAMADA DA ARQUITETURA (Lakehouse ou Raw):
Onde nessa camda colocamos toda a nossa base de dados , assim armazendo todos os dados no formado fornecido pela a origem ou coletado pela as nossas ferramentas de coleta de dados.

![Raw](https://github.com/user-attachments/assets/81a9e580-fc45-454a-ad15-4133c215ff1a)

#### SEGUNDA CAMADA DA ARQUITETURA (Broze):
Nessa segunda camada onde vamos começar a estruturação dos dados em apenas um tipo de arquivo escolhido pelo o grupo , resolvemos trabalhar com apenas um arquivo central em .CSV , assim nessa camada sentimos a necessidade de automatizar esse processo , para isso desenvolvemos um scrip onde fica responsavel em fazer de forma automaica a reestruturaçao desse formatos para apenas um so arquivo. 
- AUTOMATIZAÇÃO:
  
![Bronze 1](https://github.com/user-attachments/assets/ad35a4a0-9b21-446e-af6c-49fdae5722b8)
![Bronze 2](https://github.com/user-attachments/assets/569c0235-6a5d-4e43-b1c8-b008c2e1863c)
![Bronze 3](https://github.com/user-attachments/assets/41d1e772-9257-456b-926c-8be8bf2b9c39)

Modelo de estruturação dos dados 

![Bronze 4](https://github.com/user-attachments/assets/d8223f5e-3344-433a-8f0b-24471d1effd5)

### Camada Bronze

A camada Bronze armazena todos os dados provenientes de sistemas externos. As tabelas nesta camada refletem as estruturas de dados "como estão" nos sistemas de origem, acrescidas de metadados adicionais, como data de carregamento e ID do processo. Esta camada oferece captura rápida de dados alterados, arquivamento histórico das fontes (armazenamento a frio), rastreamento da linhagem dos dados, auditabilidade e possibilidade de reprocessamento, sem necessidade de recarregar os dados do sistema de origem.

### Camada Prata (Silver)

A camada Prata do lakehouse é responsável por combinar, integrar, adaptar e limpar moderadamente os dados da camada Bronze, oferecendo uma visão corporativa das principais entidades de negócios, conceitos e transações. Exemplos incluem tabelas mestres de clientes, lojas, transações desduplicadas e referências cruzadas.

Essa camada permite a criação de uma visão corporativa abrangente, possibilitando análises de autoatendimento, como relatórios ad hoc, análises avançadas e machine learning. Os dados da camada Prata servem como base para projetos e análises realizados por analistas, engenheiros de dados e cientistas de dados, ajudando a resolver desafios de negócios e projetos departamentais na camada Ouro.

### Camada Ouro (Gold)

Os dados na camada Ouro do lakehouse são organizados em bancos de dados otimizados para consumo "somente para projetos". Esta camada é ideal para relatórios e utiliza um modelo de dados com menos junções, mais desnormalizado e otimizado para leitura. A camada Ouro é a etapa final para transformações de dados, aplicação de regras de qualidade e apresentação de insights em projetos, como análise de clientes, análise da qualidade do produto, gestão de estoque, segmentação de clientes, recomendação de produtos e análise de vendas.
