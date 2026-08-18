# Tratamento dos Dados
## Dados brutos
Os dados foram coletados do DATASUS (Transferência de Arquivos), e feito o ETL via Power Query posteriormente.

## Coleta
- Coleta de dados do DATASUS
- Coleta de dados do CID-1O via DATASUS

## Limpeza
- Remoção de dados duplicados
- Preenchimento de dados ausentes e não esclarecidos
- Padronização de nomes
- Divisão de colunas

## Transformações
- Criação de colunas de UF origem, UF óbito, data nascimento...
- Filtros por doença final desencadeada, óbitos por UF...

## Integrações
- DATASUS + microdatasus
- DATASUS + CID-10