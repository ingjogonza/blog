---
layout: post
title: Convertir Fecha en formato Juliano a Gregoriano (TSQL)
---

Una vez me vi en la necesidad de convertir un string que almacenaba una fecha en [formato juliano](https://es.wikipedia.org/wiki/Fecha_juliana) a un [formato gregoriano](https://es.wikipedia.org/wiki/Calendario_gregoriano#Norma_ISO) con la forma "AAMMDD" es decir año mes dia en cierto sistema que usa una base de datos SQL SERVER 2012.

La función recibe un string de 7 caracteres (Ej. 2020202) y devuelve un string de 8 caracteres (Ej. 20200721), así que sin más nada que explicar he aquí la función

```sql
-- =============================================
-- Author:		<Author,,Name>
-- Create date: <Create Date, ,>
-- Description:	<Description, ,>
-- =============================================
CREATE FUNCTION [dbo].[CONVERTIR_FECHA_JULIANA_A_GREGORIANA] 
(
	-- Add the parameters for the function here
	@fechajuliana VARCHAR(7)
)
RETURNS VARCHAR(10)
AS
BEGIN
	-- Declare the return variable here
	DECLARE @fechagregoriana varchar(10)

	-- Add the T-SQL statements to compute the return value here
	SELECT @fechagregoriana = convert(nvarchar,(DateAdd (day, CAST(@fechajuliana as int)-1000*(CAST(@fechajuliana as int)/1000), convert(datetime, 'Jan 1 ' + str(CAST(@fechajuliana as int)/1000)))),112)

	-- Return the result of the function
	RETURN @fechagregoriana

END
```

Funciona para TSQL pero con unas pequeñas modificaciones se puede usar para cualquier otro motor SQL.
