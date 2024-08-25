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
