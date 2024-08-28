# Projeto Tele Sena

## Objetivo do Projeto

O projeto **Tele Sena** foi iniciado durante um hackathon com o propósito de responder à seguinte questão: **"Como organizar, categorizar e priorizar as informações recebidas para facilitar a tomada de decisão sobre quais conteúdos produzir?"**. Diante dessa problemática, desenvolvemos uma estrutura baseada na **Medallion Architecture Layers**, uma arquitetura de dados que organiza de forma lógica e eficiente os dados dentro de um **lakehouse**. Essa abordagem visa aprimorar, de maneira incremental e progressiva, a estrutura e a qualidade dos dados à medida que eles fluem pelas três camadas da arquitetura: **Bronze**, **Prata**, e **Ouro**.

## Introdução

Para iniciar o desenvolvimento do projeto **Tele Sena**, configuramos inicialmente um ambiente de servidor simples utilizando a infraestrutura do **Google Drive**. Esse servidor nos permitiu organizar e estruturar as camadas de arquitetura necessárias para o projeto. A partir daí, implementamos um pipeline de dados que segue os princípios da **Medallion Architecture**, garantindo que os dados sejam processados e armazenados de forma eficiente e escalável.

## Extração e Processamento de Dados do Instagram

Para a coleta de dados, utilizamos a biblioteca **Instaloader**, uma ferramenta robusta e popular para extração de dados do Instagram usando Python. O **Instaloader** permite que os usuários baixem postagens, histórias, perfis, e muito mais, diretamente da plataforma do Instagram. 

No contexto do projeto, o script do **Instaloader** carrega o perfil de um usuário do Instagram, localiza uma postagem específica pelo shortcode fornecido e, caso a postagem seja encontrada, extrai informações detalhadas sobre cada comentário dessa postagem. Para evitar sobrecarga de requisições na plataforma, implementamos um atraso programado entre as requisições e um período adicional de espera após a leitura dos comentários.

## Camada Bronze: Captura e Armazenamento Inicial dos Dados

A **Camada Bronze** é responsável por armazenar todos os dados provenientes de sistemas de origem externa. Nessa camada, os dados são armazenados no formato original ("como estão") do sistema de origem, juntamente com metadados adicionais, como data de carregamento, ID do processo, e outros detalhes relevantes. Esta camada permite uma captura rápida de dados alterados, arquivamento histórico (armazenamento a frio), e garante a linhagem dos dados, auditabilidade, e a capacidade de reprocessamento conforme necessário, sem a necessidade de recarregar dados diretamente do sistema de origem.

As tabelas na **Camada Bronze** mantêm a estrutura bruta dos dados para proporcionar um ponto de partida flexível e abrangente para as transformações subsequentes que ocorrem nas camadas mais refinadas.

## Camada Prata: Limpeza e Integração de Dados

A **Camada Prata** do **lakehouse** realiza a limpeza, integração, e a adaptação dos dados brutos presentes na **Camada Bronze** para fornecer uma visão corporativa consolidada de todas as principais entidades de negócios, conceitos, e transações. Isso inclui tabelas mestre de clientes, informações de lojas, transações desduplicadas, e dados de referência cruzada.

Nesta camada, os dados de diferentes fontes são unificados para criar uma base de dados consistente, permitindo análises de autoatendimento, como relatórios ad hoc, análises avançadas, e machine learning (ML). A **Camada Prata** é a fonte de dados primária para analistas de negócios, engenheiros de dados, e cientistas de dados, facilitando a resolução de desafios de negócios e suportando projetos de dados em diferentes departamentos, preparando os dados para a camada final.

## Camada Ouro: Dados Prontos para Consumo e Análise Avançada

Na **Camada Ouro**, os dados do **lakehouse** são organizados em bancos de dados otimizados para consumo e voltados para projetos específicos. Esta camada é desenhada para maximizar a eficiência em consultas, com dados organizados de maneira desnormalizada e otimizados para leitura, o que é ideal para relatórios e análises avançadas.

A **Camada Ouro** é a camada final para transformações de dados e aplicação de regras de qualidade, fornecendo dados prontos para uso em projetos como análise de clientes, análise de qualidade de produto, controle de estoque, segmentação de clientes, recomendação de produtos, e análise de vendas. As tabelas e métricas nesta camada são preparadas para suportar a tomada de decisão estratégica e insights de alto valor para o negócio.

## Qualidade dos Dados e Governança

A qualidade dos dados é garantida em todas as camadas do **lakehouse**:

- **Camada Bronze**: Captura de dados de forma bruta, com validação mínima para assegurar a integridade dos dados conforme capturados do sistema de origem.
- **Camada Prata**: Limpeza de dados e integração para assegurar a consistência e precisão. Realiza-se a remoção de duplicatas e a normalização de valores.
- **Camada Ouro**: Aplicação de regras de qualidade de dados e transformações finais para garantir que os dados estejam prontos para análise e relatórios avançados. Asseguramos a conformidade com os padrões de qualidade através de verificações rigorosas de completude, consistência e precisão dos dados.

## Desafios e Soluções

Durante o desenvolvimento do projeto **Tele Sena**, enfrentamos diversos desafios, como a integração de dados de múltiplas fontes, a garantia da qualidade dos dados em todas as camadas e a otimização do desempenho de consultas na **Camada Ouro**. Esses desafios foram superados através da utilização de técnicas avançadas de engenharia de dados, como paralelização de processos, uso de frameworks eficientes (como Apache Spark), e implementação de políticas rigorosas de governança de dados.

## Conclusão

A abordagem utilizando a **Medallion Architecture** permitiu uma gestão eficiente e escalável dos dados no projeto **Tele Sena**, desde a captura inicial de dados na **Camada Bronze**, passando pela integração e limpeza na **Camada Prata**, até a disponibilização de dados otimizados para análise na **Camada Ouro**. Esta arquitetura proporcionou uma base sólida para a tomada de decisões baseada em dados, facilitando o desenvolvimento de soluções analíticas avançadas e o suporte a estratégias de negócios informadas.

## Outras Considerações

Para futuras expansões e melhorias no projeto, sugerimos a inclusão de um glossário técnico para facilitar a compreensão dos termos utilizados e a criação de tutoriais passo a passo para novos colaboradores. Além disso, a utilização de ferramentas de versionamento de documentos pode ajudar a manter a documentação atualizada e consistente ao longo do tempo.

