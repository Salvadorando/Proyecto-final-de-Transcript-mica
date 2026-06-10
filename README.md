# Transcriptomica_Proyecto_Final
# Proyecto scRNA-seq Transcriptómica: Caracterización Celular y Expresión Diferencial en Colon Murino Bajo Condiciones Inflamatorias

## Integrantes

* Valeria Sasia
* Verónica Ramos
* Salvador López

## Programa cursado

**Maestría en Ciencias (Neurobiología)**

## Materia

**Bioinformática aplicada al análisis de transcriptómica diferencial**

## Semestre

**Segundo semestre**

## Fecha de entrega

**10 de junio de 2026**

---

# Resumen (Abstract)

La secuenciación de ARN de célula única (scRNA-seq) constituye una herramienta fundamental para estudiar la heterogeneidad celular y los cambios transcripcionales asociados a procesos fisiológicos y patológicos. En este proyecto se analizaron muestras de colon murino provenientes de condiciones normales, inflamación aguda e inflamación crónica mediante un flujo de trabajo de bioinformática aplicado al análisis transcriptómico diferencial.

El análisis incluyó control de calidad, normalización, integración de muestras mediante Harmony, reducción de dimensionalidad, agrupamiento celular, identificación de genes marcadores y anotación manual de tipos celulares. Posteriormente, se realizó un análisis de expresión diferencial mediante una estrategia pseudobulk utilizando edgeR para preservar la estructura de replicación biológica de las muestras.

Los resultados permitieron identificar doce poblaciones celulares principales, incluyendo células endoteliales, fibroblastos, macrófagos, linfocitos T y B, células musculares lisas, colonocitos maduros y células madre. Asimismo, se detectaron cambios en la composición celular y en los perfiles de expresión génica asociados a los estados inflamatorios agudos y crónicos, proporcionando una visión integral de las alteraciones transcriptómicas presentes durante la progresión de la inflamación intestinal.

---

# Reporte renderizado
El reporte completo puede consultarse en:
* **Código Fuente:** [Proyecto_scRNA_entregable_final.Rmd](./Proyecto%20final%20transcriptomica/Proyecto_scRNA_entregable_final.Rmd)
* **Visualización del Reporte:** 🚀 [Haz clic aquí para ver el reporte interactivo completo en HTML](https://htmlpreview.github.io/?https://github.com/Salvadorando/Proyecto-final-de-Transcript-mica/blob/main/Proyecto%20final%20transcriptomica/Proyecto_scRNA_entregable_final.html)

---

## Datos del proyecto

Los objetos Seurat utilizados en este análisis son demasiado grandes para almacenarse directamente en GitHub.  
Puedes acceder a todos los archivos `.rds` en la siguiente carpeta de Google Drive.

https://drive.google.com/drive/folders/1oDNIz-TUGk8oxrn56PHhsfO_PRVfujhg?usp=sharing

---

### Archivos incluidos:
- colon_annotated.rds  
- colon_annotated_v2F.rds  
- colon_integrated.rds  
- colon_scRNA_seurat_raw.rds  
- combined_seurat.rds
- También se encuentran los archivos CSV, Rmd y html

*Nota: Todos los códigos de los programas utilizados y sus respectivos outlogs se encuentran embebidos o enlazados dentro del reporte HTML adjunto.*

# Explicación detallada de los pasos y scripts

## Parte 1. Control de calidad y normalización

**Script:** `Parte1_QC_Normalizacion.R`

Objetivos:

* Importación de matrices de expresión.
* Creación de objetos Seurat.
* Cálculo de métricas de calidad.
* Filtrado de células de baja calidad.
* Evaluación de genes mitocondriales y métricas de expresión.
* Normalización mediante SCTransform.
* Identificación de genes altamente variables.

Funciones principales:

* CreateSeuratObject()
* PercentageFeatureSet()
* SCTransform()
* FindVariableFeatures()

---

## Parte 2. Integración de muestras y clustering

**Script:** `Parte2_Integracion.R`

Objetivos:

* Integración de muestras provenientes de diferentes condiciones experimentales.
* Corrección de efectos de lote mediante Harmony.
* Reducción de dimensionalidad utilizando PCA.
* Construcción de representación UMAP.
* Identificación de clústeres celulares.

Funciones principales:

* RunPCA()
* RunHarmony()
* FindNeighbors()
* FindClusters()
* RunUMAP()

---

## Parte 3. Identificación de genes marcadores y anotación celular

**Script:** `Parte3_Anotacion.R`

Objetivos:

* Identificación de genes marcadores por clúster.
* Generación de heatmaps, dotplots y violin plots.
* Anotación manual de tipos celulares basada en genes marcadores reportados en la literatura.
* Validación biológica de las poblaciones celulares identificadas.

Funciones principales:

* FindAllMarkers()
* DoHeatmap()
* DotPlot()
* VlnPlot()
* FeaturePlot()

---

## Parte 4. Expresión diferencial por condiciones

**Script:** `Parte4_Expresion_Diferencial.R`

Objetivos:

* Comparación entre condiciones Normal, Aguda y Crónica.
* Evaluación de cambios en la composición celular.
* Implementación de análisis pseudobulk mediante edgeR.
* Identificación de genes diferencialmente expresados por tipo celular.
* Evaluación del efecto potencial del ciclo celular.

Funciones principales:

* AggregateExpression()
* DGEList()
* calcNormFactors()
* estimateDisp()
* glmQLFit()
* glmQLFTest()

---

# Referencias

Amezquita RA, Lun ATL, Becht E, et al. Orchestrating single-cell analysis with Bioconductor. Nature Methods. 2020;17:137–145.

Aran D, Looney AP, Liu L, et al. Reference-based analysis of lung single-cell sequencing reveals a transitional profibrotic macrophage. Nature Immunology. 2019;20:163–172.

Hao Y, Hao S, Andersen-Nissen E, et al. Integrated analysis of multimodal single-cell data. Cell. 2021;184(13):3573–3587.

