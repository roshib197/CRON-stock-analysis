install.packages("quantmod")
library(quantmod)

# Descargar datos de CRON desde Yahoo Finance
getSymbols("CRON", src = "yahoo")

# Crear un gráfico de velas japonesas que muestra el precio de las acciones de CRON
chartSeries(CRON, type = "candlesticks", theme = "white")

# Agregar una línea de tendencia en rojo
addTA(EMA(Cl(CRON), n = 20), on = 1, col = "red")


# Calcular el índice de fuerza relativa (RSI)
CRON$RSI <- RSI(Cl(CRON), n = 14)

# Crear un gráfico que muestra el RSI y el precio de cierre de las acciones de CRON
chartSeries(CRON, type = "line", theme = "white")
addRSI(n = 14, on = 1)
