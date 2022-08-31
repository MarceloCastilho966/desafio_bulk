# Desafio BULK

## A partir dos repositórios:

--> https://github.com/paaarx/semantix/raw/master/NASA_access_log_Jul95.gz

--> https://github.com/paaarx/semantix/raw/master/NASA_access_log_Aug95.gz

## Responder as perguntas

1. Número de hosts únicos ?
2. O total de erros 404 ?
3. Os 5 URLs que mais causaram erro 404 ?
4. Quantidade de erros 404 por dia ?
5. O total de bytes retornados ?

--------------------------------------------------------------

# Como foi feito:

## Comandos no Terminal:

### Baixando arquivos:

wget https://github.com/paaarx/semantix/raw/master/NASA_access_log_Jul95.gz
wget https://github.com/paaarx/semantix/raw/master/NASA_access_log_Aug95.gz

### Enviando arquivos para HDFS no Docker:

docker cp NASA_access_log_Aug95.gz namenode:/home
docker cp NASA_access_log_Jul95.gz namenode:/home

### Criando Pasta para receber arquivos:

hdfs dfs -mkdir /user/marcelo/data/desafio_bulk

### Enviando arquivos para pasta:

hdfs dfs -copyFromLocal /home/NASA_access_log_Jul95.gz /user/marcelo/data/desafio_bulk
hdfs dfs -copyFromLocal /home/NASA_access_log_Aug95.gz /user/marcelo/data/desafio_bulk

--------------------------------------------------------------


## Após os dados terem sido tratados com a ajuda do Regexp_extract, as respostas para as perguntas puderam ser respondidas:


## 1. Número de hosts únicos ?
137979

## 2. O total de erros 404 ?
20901

## 3.Os 5 URLs que mais causaram erro 404 ?
|/pub/winvn/readme.txt                       |2004 |
|/pub/winvn/release.txt                      |1732 |
|/shuttle/missions/STS-69/mission-STS-69.html|682  |
|/shuttle/missions/sts-68/ksc-upclose.gif    |426  |
|/history/apollo/a-001/a-001-patch-small.gif |384  |  

## 4. Quantidade de erros 404 por dia ?
|06/Jul/1995|  640|
|19/Jul/1995|  639|
|30/Aug/1995|  571|
|07/Jul/1995|  570|
|07/Aug/1995|  537|

## 5. O total de bytes retornados ?
65524314915








