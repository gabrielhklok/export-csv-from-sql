# tlpp-export-from-sql

Exportar em CSV ou JSON qualquer consulta SQL. Desenvolvida na linguagem TL++ (Linguagem proprietária da TOTVS)

<br />

1. [Defini��o](#Defini��o)
1. [Exemplo de execu��o](#Exemplo-de-execu��o)
1. [Observa��es](#Observa��es)

<br />

## Defini��o
Fun��o construida para realizar extra��o de dados atrav�s de uma query no ERP Protheus da TOTVS, principalmente em ambientes TOTVS Cloud visto que a unica forma de realizar a extra��o � via TCloud e fica limitado a CSV. Ent�o desenvolvi a fun��o para realizar a extra��o nos formatos CSV e JSON.
A rotina realiza uma valida��o simples para evitar que alguns comandos sejam executados, visto que a rotina � apenas para consultas (SELECT), os comandos que s�o validados atualmente s�o:

- UPDATE
- DELETE
- TRUNCATE
- CREATE
- DROP
- INSERT


<br />

## Exemplo de execu��o
Fluxo de execu��o, ao acionar a rotina a tela abaixo � exibida.
<br />
![](assets/tela-inicial-exportsql.png)

<br />

Ao clicar no bot�o 'Arquivo SQL' a seguinte tela � aberta, para selecionar o arquivo SQL desejado.
<br />
![](assets/escolha-arquivo-sql-exportsql.png)

<br />

Ap�s selecionar o arquivo SQL devemos escolher o diret�rio para salvar o arquivo que ser� extraido.
<br />
![](assets/tela-escolha-diretorio-exportsql.png)

<br />

Ap�s selecionar o arquivo SQL, definir o diret�rio para salvar a extra��o e o formato, podemos observar que ao lado direito dos bot�es o status ficou na cor verde, indicando que s�o v�lidos, caso fiquem vermelhos, devem ser revisados antes de clicar em 'Executar'.
<br />
![](assets/tela-inicial-completa-exportsql.png)

<br />

Tudo certo vamos executar a extra��o acionando o bot�o 'Executar', feito isso observamos a tela abaixo. (Obs.: A quantidade de dados sendo extraidos vai variar de acordo com o retorno, na imagem abaixo � apenas um exemplo.)
<br />
![](assets/tela-extraindo-exportsql.png)

<br />

Ao final da rotina, ap�s a extra��o ser concluida a seguinte mensagem � exibida.
<br />
![](assets/tela-final-sucesso-exportsql.png)

<br />

## Observa��es
Dependendo do seu n�vel de conhecimento em Tl++ / Framework Protheus, voc� pode me perguntar porque n�o usei a classe 'JsonObject' para manipular a exporta��o no formato JSON. Optei por realizar a constru��o manual do arquivo JSON por 2 motivos simples:

- Toda query executada no protheus retorna os campos no formato String;
- N�o sei o tamanho do retorno.

Vamos detalhor os motivos, quando executamos uma query que n�o seja por Embedded, ela sempre retorna os campos no formato String, sendo assim n�o preciso fazer tratamento dos dados. Sobre o tamanho do retorno a quest�o � a seguinte, como cada linha significa uma posi��o no array do arquivo JSON, caso tenhamos muitas linhas ficaria com desempenho defasado manter tudo em mem�ria. Por esses 2 motivos construi a rotina gerando o arquivo JSON manualmente.