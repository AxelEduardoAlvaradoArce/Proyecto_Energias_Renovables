# Transición hacia Energías Renovables

Proyecto final del Módulo 8 (Comunicación de resultados) del Diplomado **Introducción Analítica a la Ciencia de Datos**, UNAM.

Este repositorio contiene los datos y el código del análisis. Estudiamos cómo ha cambiado la generación de electricidad a partir de fuentes renovables (excluyendo la hidroeléctrica) en **78 países entre 1990 y 2025**, con dos preguntas de investigación:

1. ¿Qué países han realizado las transiciones más rápidas hacia las energías renovables?
2. ¿Qué factores están relacionados con una mayor adopción de energías renovables?

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
| `tes_per_capita_raw.csv` | Energy Institute, *Statistical Review of World Energy* (hoja "TES per capita") |
| `renovables_excl_hidro_raw.csv` | Energy Institute, *Statistical Review of World Energy* (hoja "Ren power (excl hydro) - TWh") |
| `generacion_electrica_raw.csv` | Energy Institute, *Statistical Review of World Energy* (hoja "Electricity Generation - TWh") |
| `pib_per_capita_ppp_raw.csv` | Banco Mundial, Indicadores del Desarrollo Mundial (indicador NY.GDP.PCAP.PP.CD) |

El *Statistical Review of World Energy* es la fuente que utiliza [Our World in Data](https://ourworldindata.org/renewable-energy) para construir sus series de energía renovable. Su archivo de Excel (101 hojas) se descargó del sitio del [Energy Institute](https://www.energyinst.org/statistical-review) y cada una de las tres hojas utilizadas se guardó como CSV. El PIB se descargó en CSV desde el [portal del Banco Mundial](https://datos.bancomundial.org/indicador/NY.GDP.PCAP.PP.CD).

Los archivos `_raw` se conservan tal como se descargaron, con encabezados, notas al pie y agregados regionales; toda la limpieza se realiza en el notebook.

## Resumen del análisis

1. **Limpieza e integración.** Se eliminaron metadatos, notas al pie y agregados que no son países (24 del Statistical Review y 46 del Banco Mundial), se asignó a cada país su código ISO3 y se unieron las fuentes por país y año. Resultado: 78 países y 2,788 observaciones país-año (1990–2025).
2. **Variable objetivo.** La penetración renovable: generación renovable sin hidroeléctrica entre generación eléctrica total.
3. **Velocidad de transición.** Pendiente de una regresión lineal de la penetración renovable contra el año, para cada país.
4. **Modelado.** Regresiones Lasso y Ridge con PIB per cápita, suministro de energía per cápita, año y continente como variables explicativas; el nivel de penalización se eligió con validación cruzada.
5. **Proyección.** Escenario de la penetración renovable por continente hacia 2035.

## Principales resultados

- Dinamarca (2.78 puntos porcentuales por año), Lituania (2.04) y Alemania (1.52) encabezan la transición; 14 de los 15 países más rápidos son europeos.
- La correlación entre el PIB per cápita y la velocidad de transición es positiva pero débil (0.192).
- Lasso y Ridge explican cerca del 42 % de la variabilidad de la penetración renovable. El PIB per cápita y el año se asocian positivamente con ella, y el suministro de energía per cápita negativamente.
- Los resultados describen asociaciones, no relaciones causales.

## ¿Cómo reproducir el análisis?

### En Google Colab

1. Abre el notebook en Colab: [Proyecto_Transicion_Hacia_Energias_Renovables.ipynb](https://colab.research.google.com/github/AxelEduardoAlvaradoArce/Proyecto_Energias_Renovables/blob/main/Proyecto_Transicion_Hacia_Energias_Renovables.ipynb)
2. Ejecuta todas las celdas desde **Entorno de ejecución → Ejecutar todo**.

No es necesario instalar nada: la primera celda instala `pycountry-convert` y el resto de las librerías ya vienen incluidas en Colab.

### En un entorno local

1. Clona el repositorio:

    ```bash
    git clone https://github.com/AxelEduardoAlvaradoArce/Proyecto_Energias_Renovables.git
    cd Proyecto_Energias_Renovables
    ```

2. Instala las librerías necesarias (Python 3.10 o superior):

    ```bash
    pip install pandas numpy scipy matplotlib seaborn plotly scikit-learn pycountry-convert jupyter
    ```

3. Abre `Proyecto_Transicion_Hacia_Energias_Renovables.ipynb` con Jupyter y ejecuta todas las celdas en orden.

El notebook descarga los datos directamente desde este repositorio, por lo que se requiere conexión a internet. La partición de los datos usa una semilla fija (`random_state=42`), así que los resultados son reproducibles.

## Equipo

- Aguilera Yáñez Mariana
- Alvarado Arce Axel Eduardo
- Canseco Galván Tanivet Leonor
- García Soto Kevin
- Hernández Mareles Francisco Javier
- Rendón Cardoso Karla
- Suarez Urbano David Hiram

**Profesores:** Claudia Juarez y Eduardo Selim.
