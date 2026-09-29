# Transición hacia Energías Renovables

Proyecto final del Módulo 8 "Comunicación de resultados" del Diplomado "Introducción Analítica a la Ciencia de Datos", UNAM.

Este repositorio contiene los datos y el código del análisis realizado.

## Contenido del repositorio

| Archivo | Descripción |
|---|---|
| `Proyecto_Transicion_Hacia_Energias_Renovables.ipynb` | Notebook con el análisis completo: obtención y limpieza de los datos, análisis exploratorio, cálculo de la penetración renovable y de la velocidad de transición, modelos Lasso y Ridge, diagnóstico y proyección a 2035. |
| `tes_per_capita_raw.csv` | Datos originales: suministro total de energía por habitante, en gigajoules (GJ). |
| `renovables_excl_hidro_raw.csv` | Datos originales: generación de electricidad con fuentes renovables, excluyendo la hidroeléctrica, en teravatios-hora (TWh). |
| `generacion_electrica_raw.csv` | Datos originales: generación total de electricidad, en teravatios-hora (TWh). |
| `pib_per_capita_ppp_raw.csv` | Datos originales: PIB per cápita en paridad de poder adquisitivo (PPA), en dólares internacionales corrientes. |
| `datos.csv` | Base consolidada país-año que resulta de la limpieza e integración de las cuatro fuentes. |

## Fuentes de datos

| Archivo | Fuente |
|---|---|
| `tes_per_capita_raw.csv` | Energy Institute, Statistical Review of World Energy (hoja "TES per capita") |
| `renovables_excl_hidro_raw.csv` | Energy Institute, Statistical Review of World Energy (hoja "Ren power (excl hydro) - TWh") |
| `generacion_electrica_raw.csv` | Energy Institute, Statistical Review of World Energy (hoja "Electricity Generation - TWh") |
| `pib_per_capita_ppp_raw.csv` | Banco Mundial, Indicadores del Desarrollo Mundial (indicador NY.GDP.PCAP.PP.CD) |

El Statistical Review of World Energy es la fuente que utiliza [Our World in Data](https://ourworldindata.org/renewable-energy) para construir sus series de energía renovable. Su archivo de Excel (101 hojas) se descargó del sitio del [Energy Institute](https://www.energyinst.org/statistical-review) y cada una de las tres hojas utilizadas se guardó como CSV. El PIB se descargó en CSV desde el [portal del Banco Mundial](https://datos.bancomundial.org/indicador/NY.GDP.PCAP.PP.CD).

Los archivos `_raw` se conservan tal como se descargaron, con encabezados, notas al pie y agregados regionales; toda la limpieza se realiza en el notebook.

## Equipo

- Aguilera Yáñez Mariana
- Alvarado Arce Axel Eduardo
- Canseco Galván Tanivet Leonor
- García Soto Kevin
- Hernández Mareles Francisco Javier
- Rendón Cardoso Karla
- Suarez Urbano David Hiram

**Profesores:** Claudia Juarez y Eduardo Selim.
