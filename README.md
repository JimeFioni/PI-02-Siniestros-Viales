
![Static Badge](https://img.shields.io/badge/PowerBI-gray?style=flat&logo=powerbi)
![Static Badge](https://img.shields.io/badge/Python-gray?style=flat&logo=python)
![Static Badge](https://img.shields.io/badge/-Pandas-gray?style=flat&logo=pandas)
![Static Badge](https://img.shields.io/badge/-Matplotlib-gray?style=flat&logo=matplotlib)
![Static Badge](https://img.shields.io/badge/-Seaborn-gray?style=flat&logo=seaborn)
![Static Badge](https://img.shields.io/badge/-Jupyter_Notebook-gray?style=flat&logo=jupyter)
![Static Badge](https://img.shields.io/badge/Visual_Studio_Code-gray?style=flat&logo=visual%20studio%20code&logoColor=white)

# **Proyecto Individual** - 02-Siniestros Viales en CABA con víctimas fatales -(2016-2021)
## **Introducción**

Este proyecto se realizó simulando ser un Data Analist de una consultora; y tiene como finalidad la elaboración de un análisis de datos solicitado por el `Observatorio de Movilidad y Seguridad Vial (OMSV)`, bajo la órbita de la Secretaría de Transporte del Gobierno de la Ciudad Autónoma de Buenos Aires (CABA).

El Objetivo del proyecto es lograr información que permita la toma de decisiones, de manera fundada, a quienes corresponda; a fin de lograr la prevención, el aumento de la seguridad vial y  disminución de siniestros viales con víctimas fatales en la Ciudad de Buenos Aires.

Las tasas de mortalidad relacionadas con siniestros viales suelen ser un indicador crítico de la seguridad vial en una región. Estas tasas se calculan, generalmente, como el número de muertes por cada cierto número de habitantes o por cada cierta cantidad de vehículos registrados. Reducir estas tasas es un objetivo clave para mejorar la seguridad vial y proteger la vida de las personas en la ciudad.

Para cumplir con ello, los datos iniciales que se utilizan son derivados de un dataset con información sobre homicidios de siniestros viales en la Ciudad de Buenos Aires, durante los años 2016-2021, que es de píblico acceso en la página oficial de CABA. 
Podemos acceder a ellos desde [Datos oficiales](https://data.buenosaires.gob.ar/dataset/victimas-siniestros-viales)

## **Contexto**

Los siniestros viales, también conocidos como accidentes de tráfico o accidentes de tránsito, son eventos que involucran vehículos en las vías públicas y que pueden tener diversas causas, como colisiones entre automóviles, motocicletas, bicicletas o peatones, atropellos, choques con objetos fijos o caídas de vehículos. Estos incidentes pueden tener consecuencias que van desde daños materiales hasta lesiones graves o fatales para los involucrados.

En Argentina, cada año mueren cerca de 4.000 personas en siniestros viales. Aunque muchas jurisdicciones han logrado disminuir la cantidad de accidentes de tránsito, esta sigue siendo la principal causa de muertes violentas en el país. Los informes del Sistema Nacional de Información Criminal (SNIC), del Ministerio de Seguridad de la Nación, revelan que entre 2018 y 2022 se registraron 19.630 muertes en siniestros viales en todo el país. Estas cifras equivalen a 11 personas por día que resultaron víctimas fatales por accidentes de tránsito.

Buenos Aires es la capital y ciudad más poblada de la República Argentina. La superficie de la Ciudad es algo superior a los 200 km2 y su perímetro, 60 km.  Los habitantes que residen en ella, están distribuidos en barrios que, desde el punto de vista político-administrativo, se agrupan en quince comunas. La densidad de la población es de más de 15.000 habitantes por kilómetro cuadrado. Las zonas centro y norte son los espacios territoriales más densamente poblados.[Página de la ciudad](https://buenosaires.gob.ar/laciudad/ciudad#:~:text=La%20densidad%20de%20la%20poblaci%C3%B3n,espacios%20territoriales%20m%C3%A1s%20densamente%20poblados.)
La población de la ciudad, según el Censo de 2022 es de 3 120 612 habitantes.[Indec](https://www.indec.gob.ar/ftp/cuadros/poblacion/cnphv2022_resultados_provisionales.pdf)
Solo en 2022, se contabilizaron 3.828 muertes fatales en este tipo de hechos. Los expertos en la materia indican que en Argentina es dos o tres veces más alta la probabilidad de que una persona muera en un siniestro vial que en un hecho de inseguridad delictiva.

 Por todo ello, el estudio del problema para la prevención y disminución de Siniestros viales es escencialmente importante para las autoridades.

## **Desarrollo**

### Datos

Para este proyecto se trabajó con la **Bases de Víctimas Fatales en Siniestros Viales** que se encuentra en formato de Excel y contiene dos pestañas de datos:

 * **HECHOS**: que contiene una fila de hecho con id único y las variables temporales, espaciales y participantes asociadas al mismo.

 * **VICTIMAS**: contiene una fila por cada víctima de los hechos y las variables edad, sexo y modo de desplazamiento asociadas a cada víctima. Se vincula a los HECHOS mediante el id del hecho.
En este [documento](NOTAS_HOMICIDIOS_SINIESTRO_VIAL.pdf) se detallan todas las definiciones manejadas en los datos y en el desarrollo de este proyecto. Por otra parte, en este [link](https://data.buenosaires.gob.ar/dataset/victimas-siniestros-viales) se encuentran los datos utilizados en el análisis.


-`Proceso de ETL (Extracción, limpieza y carga de datos)` se realiza la extraccíon y limpieza de los datos de los dos dataset `HECHOS` y `VICTIMAS`, a tráves de la utilización de Pandas y Jupyter Netbook.[ETL](ETL.ipnyb) Eliminando nulos, duplicados, con transformaciones necesarias como cambio en los tipos de datos, eliminación de columnas y unión de las tablas en un archivo `siniestros_limpio.csv` [archivo](data/siniestos_limpio.csv).

-`Proceso de EDA (Análisis Exploratorio de los datos)` una vez que los datos están limpios, es momento de revisar las relaciones que existen entre las variables numéricas y categóricas de los datasets, encontrar si hay presencia de outliers o anomalías (que no tienen que ser errores necesariamente), y se verificó si hay algún patrón o conocimiento que sirva en un análisis posterior. [EDA](EDA.ipnyb)

### Análisis de los datos

- Se analizan las variables numéricas del dataset su correlación por medio de una matriz, donde se encuentra una relación positiva entre las variables `Edad`y `Hora`
- La máyoria de los siniestros resultan con una víctima fatal, rara vez involucran 3 víctimas.
  
Análisis Temporal: 
En el transcurso de los años, los accidentes con víctimas fatales muestran: para el período 2016-2018 una tendencia alta y estacionaria, que luego se convierte en bajista (teniendo en cuenta el comienzo de la Pandemia por COVID19 durante 2020); puede verse un pico de siniestros durante Diciembre de 2021 y se retoma la tendencia bajista.
Los meses con más victimas fatales son **Diciembre** (86) y **Agosto**(71); mientras que los días de la semana **Sábado** (114) y **Domingo** (114) tienen la mayor cantidad de víctimas.

![Linkedin](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)
![Gmail](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)
