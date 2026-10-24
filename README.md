# Plan Invierno Inteligente
**Tecnicatura Superior en Ciencia de Datos e Inteligencia Artificial — ISPC**
Integrantes: Espinosa, Rodrigo Alejandro · Guevara, Gonzalo Hernán · Ormeño Quinteros, Florencia Micaela · Pedrone Pfeiffer, Joaquín · Rojas, Simón · Sanches, Mauricio Ezequiel

## Problemática

La falta de precisión en la distribución de recursos críticos (leña, garrafas y tanques de agua) representa un desafío para la ONG que ejecuta el "Operativo Invierno" en barrios populares de Argentina. La organización no cuenta con una herramienta que integre los datos de carencia energética con el volumen real de familias por barrio, lo que impide una planificación logística eficiente.

Esto afecta directamente a la Coordinación Logística, que debe decidir la asignación de presupuesto y camiones sin información precisa, y perjudica principalmente a las familias de los barrios populares del RENABAP: al momento de cargar los camiones y diseñar rutas, la ONG no puede determinar con exactitud qué insumo necesita cada barrio ni si la cantidad enviada cubrirá a las familias censadas. El resultado es pérdida de recursos y tiempo operativo y, sobre todo, desprotección social ante las olas de frío.

## Fuente de Datos

- **RENABAP** — Registro Nacional de Barrios Populares, Portal Nacional de Datos Públicos ([datos.gob.ar](https://datos.gob.ar)), Ministerio de Economía (Subsecretaría de Integración Socio Urbana). Formato CSV, Licencia Abierta de Datos de Argentina.

- **Censo Nacional de Población, Hogares y Viviendas 2022** — Instituto Nacional de Estadística y Censos (INDEC), República Argentina. Indicadores obtenidos a nivel de radio censal a través de **REDATAM** (REcuperación de DATos para Áreas pequeñas por Microcomputador, [redatam.indec.gob.ar](https://redatam.indec.gob.ar)), la plataforma oficial de INDEC para la consulta de microdatos censales por áreas pequeñas, y asignados a cada barrio por cruce espacial (centroide del barrio dentro del radio censal)

## Variables de Interés

| Variable | Tipo de variable |
| :--- | :--- |
| **Nombre barrio** | Cualitativa Nominal |
| **Provincia** | Cualitativa Nominal |
| **Departamento** | Cualitativa Nominal |
| **Localidad** | Cualitativa Nominal |
| **Cantidad de viviendas** | Cuantitativa Discreta |
| **Cantidad de familias** | Cuantitativa Discreta |
| **Década de creación** | Cualitativa Ordinal |
| **Energía eléctrica** | Cualitativa Nominal |
| **Efluentes cloacales** | Cualitativa Nominal |
| **Agua corriente** | Cualitativa Nominal |
| **Cocina** | Cualitativa Nominal |
| **Calefacción** | Cualitativa Nominal |
| **Título de propiedad** | Cualitativa Dicotómica |
| **Clasificación barrio** | Cualitativa Nominal |
| **Superficie m²** | Cuantitativa Continua |
| **pct_nbi_tot, pct_hacinamiento_critico, pct_privacion_convergente, pct_alguna_privacion** | Cuantitativas Continuas (Censo 2022, incorporadas en Evidencia 2) |
| **indice_logistico** | Cuantitativa Continua (variable objetivo construida: combina volumen de familias y severidad del déficit energético) |

## Producto final

El entregable es **`dashboard_portable.html`**: un dashboard autocontenido en HTML, que se abre con doble clic en cualquier navegador, sin instalar nada. Incluye:

- Filtros por provincia, localidad y tipo de calefacción
- Cálculo y visualización de insumos (leña y garrafas) por barrio.
- Mapa interactivo (Leaflet.js + Esri World Street Map) que prioriza los barrios según el `indice_logistico`.
- Tabla de priorización ordenable, con selección de fila y zoom automático al barrio elegido.

Los datos y el modelo ya entrenado viajan embebidos en el propio archivo.
