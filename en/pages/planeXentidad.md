# Planes por entidade


## Finalidade do procedemento

* Procedemento para procesar as listas de entidades que participan nos plans de explotación conxuntos e os tipos de plans que presenta cada entidade tanto soas como con outras entidades.

## Taboa plantidad"aaaa"

1. Para poder relacionar mellor cada plan con unha entidade creamos para cada ano a táboa _plantidad_ coa cifra do ano a que corresponde. O comando SQL para a súa creación é o seguinte:  
```sql
-- 2006
CREATE TABLE "plantidad2006" ("ideplentidad" INTEGER PRIMARY KEY  AUTOINCREMENT  NOT NULL , "anualidad" INTEGER, "idPlanAnual" INTEGER NOT NULL , "tipoCode" CHAR(4), "entidad" VARCHAR(150), "id_cofradia" INTEGER)
```
1. Para desagregar o campo _"entidad"_ no caso dos plans conxuntos e normalizar os nomes das entidades para un tratamento mais eficiente empregamos a seguinte consulta:  
```sql
SELECT "anualidad", "idPlanAnual", "tipoCode", "entidad" FROM pexma2006 ORDER BY "tipoCode", "idPlanAnual"
```

1. O resultado da consulta en formato **csv** o tratamos para que cada entidade dun plan e os códigos que o identifican están nunha liña cúa cabeceira será: `"anualidad","idPlanAnual","tipoCode","entidad"`

1. No arquivo csv non están tódolos campos de táboa o campo "id_cofradia" hai que asinalos mediante comandos "**UPDATE**" que están preparados no ficheiro "**comandoentidadeupdate.sql**" pódese executar todos os comandos xuntos o por separado para axustar a condición de execución a variabilidade na denominaciones empregadas nos distintos plans de explotación.  
```sql
UPDATE "plantidad2006" SET "id_cofradia" = '67' WHERE RTRIM("entidad") LIKE '% Anllóns%' AND "id_cofradia" ISNULL;
```

## Procesos executados

* plantidad2016
* plantidad2015
* plantidad2014
* plantidad2013
* plantidad2012
* plantidad2011
* plantidad2010
* plantidad2009
* plantidad2008
* plantidad2007
* plantidad2006
* plantidad2005
* plantidad2004


