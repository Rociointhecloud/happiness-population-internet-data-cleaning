<!-- =========================
     HERO
========================= -->

<h1 align="center">Limpieza e Integración de Datos</h1>
<h2 align="center">Happiness, Population & Internet — 2019</h2>

<p align="center">
  <em>
  La felicidad no es un estado fijo, sino la distancia entre lo que  
  una persona necesita y lo que el mundo le ofrece.  
  Este proyecto mira esa distancia desde los datos.
  </em>
</p>

<p align="center">
  <img
    src="https://github.com/user-attachments/assets/08023d92-f360-4f28-af5a-ee832ea71dad"
    alt="Paisaje costero al atardecer con acantilados y cielo rosado-morado reflejándose en el mar."
    width="45%">
</p>

<p align="center">
  <a href="#1-descripcion-del-proyecto">Descripción</a> ·
  <a href="#2-objetivos-del-proyecto">Objetivos</a> ·
  <a href="#3-herramientas-utilizadas">Herramientas</a> ·
  <a href="#4-dataset-utilizado">Dataset</a> ·
  <a href="#5-clasificacion-de-la-felicidad-en-niveles">Clasificación</a> ·
  <a href="#6-outliers-por-nivel-de-felicidad">Outliers</a> ·
  <a href="#7-visualizacion-accesible">Visualización</a> ·
  <a href="#8-revision-de-nulos-y-consistencia-interna">Nulos</a> ·
  <a href="#9-conclusiones">Conclusiones</a> ·
  <a href="#10-estructura-del-repositorio">Estructura</a> ·
  <a href="#ejecucion">Ejecución</a> ·
  <a href="#11-accesibilidad-del-readme">Accesibilidad</a> ·
  <a href="#12-referencias-y-reflexion-sobre-accesibilidad-digital">Referencias</a>
</p>

<hr>

## 1. Descripción del proyecto

Este proyecto reúne y limpia tres fuentes internacionales relacionadas con **felicidad**, **población** y **uso de internet**, con el propósito de obtener un dataset coherente que permita analizar cómo conviven bienestar, salud pública y acceso digital a escala global.

El trabajo se desarrolló en un entorno de notebook basado en **Google Colab**, lo que facilitó mantener un flujo ordenado: código, exploración y explicación caminando juntas. Cada transformación está documentada para que el proceso sea claro y reproducible.

Las fuentes empleadas son:

- **World Happiness Report 2019** (Kaggle)  
- **World Bank — Population, total**  
- **World Bank — Individuals using the Internet (%)**

Dado que la felicidad solo está disponible para 2019, filtré las otras dos tablas a ese mismo año para trabajar en un marco temporal común y evitar comparaciones incoherentes.

<hr>

## 2. Objetivos del proyecto

- Construir un dataset unificado que conecte felicidad, población y acceso digital en un mismo marco temporal.
- Entender qué desigualdades aparecen cuando se cruzan bienestar y tecnología, evitando explicaciones simplistas.
- Analizar cómo cambian los valores atípicos cuando agrupamos a los países por niveles de felicidad.
- Diseñar visualizaciones accesibles que reduzcan carga cognitiva y faciliten una lectura inclusiva de los datos.
- Documentar el proceso de forma clara, explicando no solo lo que hice, sino por qué lo hice así.

<hr>

## 3. Herramientas utilizadas

- Google Colab  
- Python  
- pandas (limpieza y manipulación)  
- numpy  
- missingno (visualización de nulos)  
- matplotlib y seaborn (gráficos accesibles)  
- plotly (mapa interactivo)

A lo largo del análisis usé **paletas color-blind friendly**, evitando saturación visual y cuidando el contraste para garantizar gráficos accesibles para distintos tipos de visión.

<hr>

## 4. Dataset utilizado

Los archivos originales venían con nombres poco descriptivos, por lo que los renombré para que su contenido fuese claro y trazable desde el primer vistazo.

**Datos originales — `01_raw_data/`:**

- `world_happiness_2019_kaggle_raw.csv`  
- `population_worldbank_raw.csv`  
- `internet_users_worldbank_raw.csv`

**Resultado final — `02_clean_data/`:**

- `full_2019_clean.csv`

Esta tabla integra felicidad, población e internet en un único conjunto de datos limpio y alineado.

<hr>

## 5. Clasificación de la felicidad en niveles

Retomé una idea trabajada en mi Proyecto 1: analizar valores atípicos dentro de categorías. Dividir es una forma de ver mejor, y en este caso me permitió profundizar en cómo cambia la realidad cuando agrupamos países con niveles de bienestar similares.

Creé cuatro niveles de felicidad:

- **baja**  
- **media**  
- **alta**  
- **muy alta**

Esta clasificación no pretende simplificar un fenómeno complejo, sino facilitar comparaciones más justas y observar si el acceso digital muestra patrones distintos según el nivel de bienestar.

<hr>

## 6. Outliers por nivel de felicidad

Analicé los valores atípicos del porcentaje de usuarios de internet dentro de cada nivel usando límites basados en IQR.

Los resultados mostraron contrastes marcados:

- Los países con **felicidad alta y muy alta** presentan una penetración digital más estable y homogénea.  
- En los niveles **bajo y medio** aparecen los outliers más extremos, tanto por exceso como por defecto.

Decidí **mantener estos valores**, porque en datos sociales los outliers suelen ser señales importantes, no simples anomalías. Cada caso extremo ofrece contexto y matices que ayudan a entender desigualdades internas.

<hr>

## 7. Visualización accesible

Toda la parte gráfica del proyecto se diseñó con criterios explícitos de accesibilidad:

- Paletas perceptualmente uniformes y aptas para daltonismo.  
- Contrastes adecuados para distintos perfiles visuales.  
- Gráficos sencillos y sin adornos innecesarios.  
- Etiquetas legibles, rotaciones suaves y tamaños moderados.  
- Boxplots para comparar la dispersión del acceso digital entre niveles.  
- Gráficos KDE para observar la forma de las distribuciones.  
- Mapas y matrices configuradas para reducir carga cognitiva.

La intención siempre fue la misma: que cualquier persona pueda leer los gráficos sin barreras.

<hr>

## 8. Revisión de nulos y consistencia interna

Antes de la integración realicé un análisis de nulos con `missingno`, comparando la completitud de cada tabla:

- **Happiness 2019:** prácticamente sin nulos.  
- **Población 2019:** un único valor faltante.  
- **Internet 2019:** huecos considerables.

Preferí no imputar datos sin fundamento claro. Cuando falta información, suele existir una razón, y rellenarla sin contexto puede distorsionar más de lo que ayuda.  
La tabla final conserva esas diferencias sin ocultarlas.

<hr>

## 9. Conclusiones

- Al unir felicidad, población y acceso digital en un mismo año, aparecen relaciones que no se veían en cada tabla por separado. La limpieza no solo ordenó datos: reveló fronteras sociales que estaban escondidas.
- La clasificación en niveles de felicidad mostró que la estabilidad digital suele acompañar a los países con mayor bienestar, mientras que la variabilidad extrema se concentra en los niveles bajos y medios.
- Los outliers dejaron de ser “errores” cuando se observaron por grupos.
- La brecha digital no parece explicarse solo por infraestructura: también tiene un componente social fuerte.
- La revisión de nulos confirmó que la falta de datos también cuenta una historia.
- Las visualizaciones accesibles permitieron ver patrones sin saturación cognitiva.
- Trabajar con datos sociales exige cautela y transparencia.
- Este conjunto final queda preparado para preguntas más ambiciosas.

Puedes descargar la versión final aquí:  
**[Descargar full_2019_clean.csv](https://drive.google.com/file/d/1qmRiq__w_Xs4yFC69a9vYy5h_mPSuxRo/view?usp=sharing)**

<hr>

## 10. Estructura del repositorio

```
happiness-population-internet-data-cleaning/
├──
01_raw_data/
├── world_happiness_2019_kaggle_raw.csv
├── population_worldbank_raw.csv
├── internet_users_worldbank_raw.csv
notebook/
├── happiness_internet_population_data_cleaning.ipynb
README.md
```
<hr>

<a id="ejecucion"></a>

## 10.A Cómo ejecutar el proyecto

Este proyecto fue desarrollado en un entorno de notebook. Puede ejecutarse tanto en **Google Colab** como en **Jupyter Notebook** local.

### Opción 1 — Google Colab (recomendado)

1. Descarga o clona este repositorio.
2. Abre el archivo:

P2_happiness_population_internet_2019_cleaning.ipynb

3. Súbelo a Google Colab.
4. Sube también los archivos de la carpeta `01_raw_data/` al entorno de Colab.
5. Ejecuta las celdas en orden, de arriba hacia abajo.

### Opción 2 — Entorno local (Jupyter)

1. Clona el repositorio:

git clone <URL_DEL_REPO>
Instala dependencias necesarias:

pip install pandas numpy missingno matplotlib seaborn plotly

Abre Jupyter:

jupyter notebook

Ejecuta el notebook principal siguiendo el orden de celdas.

Resultado esperado

El proceso genera el dataset limpio:

02_clean_data/full_2019_clean.csv

Este archivo es el que se utiliza en los análisis y visualizaciones finales.

Todas las transformaciones están documentadas dentro del notebook para facilitar la trazabilidad y la reproducibilidad.

<hr>


## 11. Accesibilidad del README

Este README sigue principios de accesibilidad:

- Encabezados jerárquicos coherentes  
- Párrafos breves que facilitan la lectura  
- Listas limpias, sin sobrecarga visual  
- Negritas moderadas para resaltar solo lo esencial  
- Sin emojis decorativos  
- Compatible con lectores de pantalla  
- Lenguaje claro y comprensible sin tecnicismos innecesarios  

<hr>

## 12. Referencias y reflexión sobre accesibilidad digital

En este proyecto he reforzado mi compromiso con la accesibilidad digital. Uno de los recursos más valiosos en mi aprendizaje ha sido el artículo de **Tran et al. (2024)**, *Discovering Accessible Data Visualizations for People with ADHD*, disponible en:  
https://dl.acm.org/doi/10.1145/3613904.3642112

Este estudio muestra qué tipos de gráficos, densidad visual y animaciones resultan más accesibles para personas con ADHD, y me ayudó a ajustar mis visualizaciones en Python de forma más inclusiva.

También he revisado el estándar internacional **WCAG 2.2**, que establece pautas claras para crear contenido perceptible, operable y comprensible. Estas recomendaciones aplican directamente a notebooks, gráficos y herramientas como Google Colab o Jupyter.

Además, desde el **28 de junio de 2025**, en España está en vigor la **Ley 11/2023**, que obliga a que los servicios y productos digitales sean accesibles siguiendo criterios derivados de WCAG. Es una normativa muy reciente, por lo que he considerado importante incorporarla desde ya en mi proceso de trabajo.  
Noticia:  
https://cincodias.elpais.com/legal/2025-06-25/los-servicios-digitales-accesibles-por-ley-desde-el-28-de-junio.html

Mi objetivo ha sido asegurar que las visualizaciones, análisis y notebooks generados aquí sean lo más accesibles posible, especialmente para personas con neurodivergencia, discapacidad visual o daltonismo.


