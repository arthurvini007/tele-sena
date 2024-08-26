# Projeto Tele Sena
### Objetivo: 
O projeto Tele Sena começou a ser desenvolvido em um hackton com o proposito de "Como organizar, categorizar e priorizar as informações recebidas para facilitar a
tomada de decisão sobre quais conteúdos produzir?" , com esse problematica desenvolvemos uma estrutura Medallion Architecture Layers , onde organizamos logicamente os dados do lakehouse, 
que visa melhorar de forma incremental e progressiva a estrutura e a qualidade dos dados à medida que fluem pelas três camadas da arquitetura (tabelas Bronze ⇒ Prata ⇒ Ouro).
### introdução: 
Para iniciar o projeto primeiramente estruturamos um mini servirdo dentro da plataforma que a google disponibilisa no Google Divre , assim começamos a organizar e a estruturaçao as camda de de arquiteturas do nosso projeto.

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

A camada Bronze armazena todos os dados de sistemas de origem externa. As estruturas da tabela desta camada correspondem às estruturas da tabela “como estão” no sistema de origem, juntamente com metadados de colunas adicionais, como data de carregamento, ID do processo etc. Essa camada fornece captura rápida de dados alterados, arquivamento histórico de fonte (armazenamento a frio), linhagem de dados, auditabilidade e reprocessamento conforme necessário, sem recarregar os dados do sistema de origem.

#### TERCEIRA CAMADA DA ARQUITETURA (Silver):
A camada Prata do lakehouse combina, faz merge, adapta e limpa (moderadamente) os dados na camada Bronze para fornecer uma “visão corporativa” de todas as principais entidades de negócios, conceitos e transações (por exemplo, tabelas mestre de clientes, lojas, transações desduplicadas e referência cruzada).

A camada Prata traz dados de fontes diferentes para uma visão corporativa, permitindo análises de autoatendimento, como relatórios ad hoc, análises avançadas e ML. Os dados da camada Prata são a fonte de projetos e análises para analistas, engenheiros de dados e data scientists para ajudar a resolver desafios de negócios em empresas e projetos de dados departamentais na camada Ouro.

#### QUARTA CAMADA DA ARQUITETURA (Gold):
Os dados na camada Ouro do lakehouse são normalmente organizados em bancos de dados consumíveis “somente para projetos”. A camada Ouro é boa para relatórios e usa um modelo de dados com menos junção, mais desnormalizado e otimizado para leitura. É a camada final para transformações de dados, regras de qualidade de dados e apresentação em projetos como análise de clientes, análise de qualidade do produto, análise de estoque, segmentação de clientes, recomendação de produtos, análise de marcação/vendas.
