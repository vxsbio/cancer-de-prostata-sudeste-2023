# Tratamento dos Dados
## Dados brutos
Os dados foram coletados do [Transferência de Arquivos DATASUS](https://datasus.saude.gov.br/transferencia-de-arquivos/) e feito o ETL via Power Query posteriormente seguindo a padronização de dados em saúde. Abaixo se encontra as etapas pré-analítica e analítica realizadas.

## Coleta
- Coleta de dados do [Transferência de Arquivos DATASUS](https://datasus.saude.gov.br/transferencia-de-arquivos/)
- Coleta de dados do CID-10 via [DATASUS](http://www2.datasus.gov.br/cid10/V2008/descrcsv.htm/)
- Consulta de informações e descrições no [PCDaS](https://pcdas.icict.fiocruz.br/conjunto-de-dados/sistema-de-informacoes-de-mortalidade-sim/dicionario-de-variaveis/)
- Consulta de informações no [IBGE](https://www.ibge.gov.br/explica/codigos-dos-municipios.php/)

## SQL
- Seleção de registros únicos na base de dados de Declaração de Óbitos.
- Filtragem dos dados pela coluna CAUSABAS pela CID-10 C61.

## Limpeza (Power Query)
- Remoção de dados duplicados
- Preenchimento de dados ausentes e não esclarecidos
- Padronização de DADOS
- Divisão de colunas

## Transformações (Power BI)
- Criação da tabela "Calendário" usando o código DAX:  
= List.Dates(#date(1900,1,1), Number.From(DateTime.LocalNow())- Number.From(#date(1900,1,1)) ,#duration(1,0,0,0))  
- Relacionamento entre a tabela "Calendário", entre colunas Data(Calendário) e DATA NASCIMENTO(CancerSE2023)
- Divisão da coluna "LINHAA" em 2, contendo os dados duplicados ou triplicados em valores únicos em cada coluna "LINHAA2" e "LINHAA3"
- Relacionamento entre a tabela com códigos e descrições CID-10 às colunas "LINHAA", "LINHAA2" e "LINHAA3"
- Duplicação da tabela CID-10-SUBCATEGORIAS para o nome "LINHAA Normalizada" para remover sufixos que pudessem atrapalhar o relacionamento à tabela CID-10-SUBCATEGORIAS e CancerSE2023, como * ou espaços
- Criação de colunas país de origem, data de óbito, idade em anos, cor, estado civil, descrição de CID-10, mês do óbito, data de nascimento, UF origem, UF óbito, data nascimento

## DAX
- Criação de medidas média, soma total, contagem e coluna de relacionamento de tabelas  
Medida de média de óbitos: Media Obito = AVERAGE(CancerSE2023[IDADE_ANOS])  
Medida de quantidade de óbitos: Quantidade Obito = (COUNT(CancerSE2023[DATA OBITO]))  
Relacionamento de tabelas: DESCR CID-10 = RELATED('CID-10-SUBCATEGORIAS'[DESCRICAO])

## Dashboard (Power BI)
- Elaboração no dashboard com filtros por doença finais, óbito por UF, país de origem do paciente, idade média de óbito, óbito por idade, óbito por mês

## Integrações
- [DATASUS](https://datasus.saude.gov.br/transferencia-de-arquivos/) + [microdatasus](https://github.com/rfsaldanha/microdatasus/)
- [DATASUS](https://datasus.saude.gov.br/transferencia-de-arquivos/) + [CID-10](http://www2.datasus.gov.br/cid10/V2008/descrcsv.htm/)
- [DATASUS](https://datasus.saude.gov.br/transferencia-de-arquivos/) + [IBGE](https://www.ibge.gov.br/explica/codigos-dos-municipios.php/)
- [DATASUS](https://datasus.saude.gov.br/transferencia-de-arquivos/) + [PCDaS](https://pcdas.icict.fiocruz.br/conjunto-de-dados/sistema-de-informacoes-de-mortalidade-sim/dicionario-de-variaveis/)
- [DATASUS](https://datasus.saude.gov.br/transferencia-de-arquivos/) + [Calendário](#transformações-power-bi)
