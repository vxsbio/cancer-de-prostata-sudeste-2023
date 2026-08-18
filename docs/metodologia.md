# Metodologia

## 1. Coleta dos dados
Os dados foram coletados do DATASUS, informações DO (Declarações de Óbito) e tabelas da Classificação Internacional de Doenças e Problemas Relacionados à Saúde.

## 2. Conversão dos dados
Depois de baixados, os arquivos .dbc foram convertidos em .dbf e depois armazenados em uma database no SQLite de forma sequencial no arquivo .db.

## 3. Filtragem
Foi feita uma consulta no SQL para filtrar os óbitos pela CID-10 C61 e C61.9 (Neoplasia maligna da próstata)

## 4. ETL e Transformação dos dados
Após a filtragem, os dados foram limpos, tratados e transformados no Power Query, seguindo os padrões de ETL, juntamente com informações do microdatasus.

## 5. Pré-análise
No Power BI foram feitas colunas para o cálculo de média e soma total de óbitos, e criação de uma coluna específica com relacionamento à tabela de CID-10.

## 6. Elaboração do Dashboard
A utilização das novas colunas baseadas nas informações originais no Power Query se fez presente aqui. Foi elaborado para fins de análise a idade média de óbitos, principais doenças finais desencadeadas, óbitos por mês, cor do paciente, óbito por idade e mais algumas informações.