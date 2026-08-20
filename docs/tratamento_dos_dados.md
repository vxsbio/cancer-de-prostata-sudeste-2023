# Tratamento dos Dados
## Dados brutos
Os dados foram coletados do [Transferência de Arquivos DATASUS](https://datasus.saude.gov.br/transferencia-de-arquivos/) e feito o ETL via Power Query posteriormente seguindo a padronização de dados em saúde. Abaixo se encontra as etapas pré-analítica e analítica realizadas.

## Coleta
- Coleta de dados do [Transferência de Arquivos DATASUS](https://datasus.saude.gov.br/transferencia-de-arquivos/)
- Coleta de dados do CID-10 via [DATASUS](http://www2.datasus.gov.br/cid10/V2008/descrcsv.htm/)
- Consulta de informações e descrições no [PCDaS](https://pcdas.icict.fiocruz.br/conjunto-de-dados/sistema-de-informacoes-de-mortalidade-sim/dicionario-de-variaveis/)
- Consulta de informações no [IBGE](https://www.ibge.gov.br/explica/codigos-dos-municipios.php/)

## Limpeza
- Remoção de dados duplicados
- Preenchimento de dados ausentes e não esclarecidos
- Padronização de DADOS
- Divisão de colunas

## Transformações Power BI
- Criação de colunas país de origem, data de óbito, idade em anos, cor, estado civil, descrição de CID-10, mês do óbito, data de nascimento, UF origem, UF óbito, data nascimento
- Elaboração no dashboard com filtros por doença final desencadeada, óbitos por UF

### DAX
- Criação de medidas média, soma total, contagem e coluna de relacionamento de tabelas
Medida de média de óbitos: Media Obito = AVERAGE(CancerSE2023[IDADE_ANOS])
Medida de quantidade de óbitos: Quantidade Obito = (COUNT(CancerSE2023[DATA OBITO]))
Relacionamento de tabelas: DESCR CID-10 = RELATED('CID-10-SUBCATEGORIAS'[DESCRICAO])

## Integrações
- [DATASUS](https://datasus.saude.gov.br/transferencia-de-arquivos/) + [microdatasus](https://github.com/rfsaldanha/microdatasus/)
- [DATASUS](https://datasus.saude.gov.br/transferencia-de-arquivos/) + [CID-10](http://www2.datasus.gov.br/cid10/V2008/descrcsv.htm/)
- [DATASUS](https://datasus.saude.gov.br/transferencia-de-arquivos/) + [IBGE](https://www.ibge.gov.br/explica/codigos-dos-municipios.php/)
- [DATASUS](https://datasus.saude.gov.br/transferencia-de-arquivos/) + [PCDaS](https://pcdas.icict.fiocruz.br/conjunto-de-dados/sistema-de-informacoes-de-mortalidade-sim/dicionario-de-variaveis/)
