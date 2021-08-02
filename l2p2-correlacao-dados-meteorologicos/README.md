# EDA em dados meteorológicos do INMET

João Pessoa, Campina Grande e Patos são 3 referências para entender o clima na Paraíba. A primeira cidade está no litoral, a segunda próximo ao topo da Serra da Borborema, e a terceira no Sertão. Nesse exercício, você experimentará com o processo de análise exploratória dos dados usando dados dessas 3 cidades. O resultado será um relatório em RMarkdowne publicado (instruções para publicar mais abaixo).

## As perguntas

Na resposta das perguntas abaixo queremos dar ênfase à análise de distribuições e usos de sumários, então **não use nenhuma visualização de linha do tempo**. Também lembre que a resposta a qualquer tarefa de análise _é uma combinação de visualização de dados, sumários estatísticos e texto que interpreta ambos_. Ao acabar cada resposta, confira se você tem esses 3 elementos. Você descreveu as distribuições envolvidas? Comentou em formato e pontos extremos? Está comentando as diferenças que observa? Elas são grandes? Pequenas? 

1. Descreva a relação entre temperatura média, umidade e chuvas por semana nas 3 cidades, analisando essas características duas a duas. Além de descrever as relações, comparando-as entre cidades e para uma mesma cidade, comente o que se deve esperar em geral em uma semana mais fria nas 3 cidades. 
2. Escolha duas das cidades e compare a temperatura e as chuvas das duas nos últimos doze meses. Quantifique e comente a diferença entre a temperatura nas duas cidades. Lembre que você tem medições pareadas das variáveis para as duas cidades, e lembre de olhar a distribuição além de qualquer sumário que você escolher. 
3. Escolha uma das cidades e compare a temperatura e as chuvas das semanas de 2021 com a temperatura e chuva das semanas dos últimos 10 anos. Esse ano tem sido um ano muito quente? Com muita chuva? Compare as distribuições.

## Os dados

Dados vêm do BDMEP: https://tempo.inmet.gov.br/ . Selecionei lá a estação convencional em João Pessoa, Campina Grande e Patos - PB, e baixei os csvs com dados desde 2010. 

Os dados brutos estão em `data/raw`. O código em `transform` faz ETL e o coloca em `data/`.

No processo de ETL, calculamos as variáveis de interesse por semana. Isso porque há bastante medições vazias nas estações, e queremos deixar o dado mais fácil de ser trabalhado. Mas ainda há várias semanas onde alguma ou todas as medidas são NA.

Colunas nos dados prontos: 

```
$ cidade      <chr> "Campina Grande", "Campina Grande", "…
$ semana      <date> 2009-12-27, 2010-01-03, 2010-01-10, …
$ temp_max    <dbl> 29.9, 31.4, 32.1, 31.0, 31.2, 32.1, 3…
$ temp_media  <dbl> 25.90000, 25.53333, 25.60952, 24.2095…
$ temp_min    <dbl> 21.9, 21.2, 21.3, 20.5, 21.2, 21.4, 2…
$ vento_medio <dbl> 3.960000, 4.080952, 3.952381, 2.86000…
$ vento_max   <dbl> 5.0, 5.3, 6.6, 5.0, 5.5, 6.5, 6.3, 5.…
$ umidade     <dbl> 76.00000, 76.23810, 75.95238, 85.3333…
$ chuva       <dbl> 0.0, 4.7, 0.2, 69.3, 3.8, 1.2, 10.9, …
```
