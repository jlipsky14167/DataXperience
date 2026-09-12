# Análisis de Energía Solar — Plan 6GW+ Colombia

Proyecto de ciencia de datos que analiza los **29.354 proyectos** de generación solar del Plan 6GW+ de Colombia para demostrar cómo la inversión en energía solar fotovoltaica genera **soberanía energética** frente a la dependencia histórica de las hidroeléctricas y su vulnerabilidad ante el **Fenómeno del Niño**.

## Contexto

Colombia genera cerca del 70% de su electricidad a partir de fuentes hidroeléctricas. Durante el Fenómeno del Niño, las sequías reducen la generación hídrica hasta un 30-40%, exponiendo al país a déficits energéticos. Este análisis evalúa el Plan 6GW+ como estrategia de diversificación, su impacto económico en los hogares y su rol en la movilidad eléctrica.

### Urgencia actual: el Niño de este año rompe récords

La coyuntura de 2026 refuerza la urgencia del análisis. Según el Ideam, el Fenómeno del Niño previsto para 2026-2027 continúa fortaleciéndose de manera excepcional, con un 75 % de probabilidad de convertirse en uno de los más fuertes desde 1950 (El País, 2026). A escala global, el Centro de Predicción Climática de EE. UU. estima esa misma probabilidad de que el episodio supere todos los registros históricos (Bloomberg, 2026). Ante la menor generación hidráulica que esto implica, el Gobierno prepara una nueva subasta de energía y enfrenta un déficit cercano a los 4,57 billones de pesos para financiar los subsidios eléctricos de 2027, con riesgo de alza en las tarifas (Galeano Balaguera, 2026).

Este escenario evidencia que la diversificación hacia energía solar no es una opción a futuro, sino una necesidad inmediata para la seguridad energética del país.

*Nota: el contenido de las fuentes fue parafraseado para cumplir con las restricciones de licenciamiento. Ver la sección Referencias.*

## Entregable

El análisis completo está en el notebook **`index.ipynb`**, estructurado en tres etapas progresivas y documentado íntegramente en español.

### Etapa 1 — Fundamentos y Preparación de Datos
- Exploración inicial (EDA): dimensiones, tipos de datos, nulos, duplicados y estadísticas descriptivas
- Diagnóstico de problemas: redundancia de índice, inconsistencias categóricas, vacíos en fechas
- Pipeline de limpieza reproducible que produce `df_clean` con tabla resumen antes/después

### Etapa 2 — Análisis Estadístico
- Medidas de tendencia central (media, mediana, moda) global y por tipo de proyecto
- Medidas de dispersión (rango, varianza, desviación estándar) y detección de outliers por IQR
- Análisis comparativo por departamento, estado y tipo de proyecto con hipótesis fundamentadas

### Etapa 3 — Modelado Matemático y Storytelling
- 5 visualizaciones: barras Top-10 departamentos, histograma log, línea temporal acumulada, distribución por estado y heatmap de correlación
- Modelo de regresión lineal sobre capacidad acumulada mensual (split cronológico 80/20) con proyección a 24 meses
- Narrativa de soberanía energética, estimación de ahorro económico AGPE y aplicación profesional

## Dataset

`informacion_proyectos_plan_6gw_plus.xlsx` — Registro oficial del Plan 6GW+ de la UPME (Unidad de Planeación Minero-Energética de Colombia).

Columnas principales: `capacidad_mw`, `tipo_tecnologia`, `estado_proyecto`, `tipo_proyecto`, `municipio`, `departamento`, `fecha_entrada_operacion`.

## Stack Tecnológico

- **Python 3.12**
- **pandas** — manipulación de datos
- **numpy** — cálculos numéricos
- **matplotlib** / **seaborn** — visualizaciones
- **scikit-learn** — modelo de regresión lineal

## Cómo Ejecutar

1. Crear y activar un entorno virtual (opcional pero recomendado):
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

2. Instalar dependencias:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn openpyxl jupyter
   ```

3. Abrir el notebook y ejecutar todas las celdas en orden:
   ```bash
   jupyter notebook index.ipynb
   ```
   O desde el editor: **Restart Kernel and Run All Cells**.

El notebook está diseñado para ejecutarse de principio a fin sin errores.

## Estructura del Proyecto

```
ProyectoFinalDataXperience/
├── index.ipynb                              # Notebook principal (entregable)
├── informacion_proyectos_plan_6gw_plus.xlsx # Dataset fuente
├── ejemplos/                                # Notebooks de referencia del curso
├── README.md
```

## Hallazgos Principales

1. **Distribución bimodal extrema**: el parque solar está polarizado entre mega-proyectos de Generación Centralizada (100-370 MW) y micro-proyectos AGPE (fracciones de kW). La mediana es el estadístico representativo, no la media.
2. **Concentración geográfica**: la Costa Caribe lidera la capacidad instalada por su alta irradiación solar.
3. **Crecimiento acelerado**: la capacidad acumulada creció de forma exponencial en 2024-2026, superando la tendencia lineal histórica.
4. **Complementariedad hidro-solar**: la solar puede cubrir los valles de generación hídrica durante sequías, no reemplazar totalmente las hidroeléctricas.
5. **Auge de la movilidad eléctrica**: el registro de vehículos eléctricos creció un 176 % en agosto de 2026 frente al mismo mes de 2025 (4.542 unidades), lo que refuerza la sinergia entre generación solar distribuida y transporte eléctrico (Fenalco & ANDI, 2026).

## Referencias

Bloomberg. (2026, septiembre). *El Niño amenaza con un récord histórico y más clima extremo*. Yahoo Finanzas. https://es-us.finanzas.yahoo.com/noticias/ni%C3%B1o-amenaza-r%C3%A9cord-hist%C3%B3rico-clima-164316055.html

El País. (2026, 11 de septiembre). *Fenómeno de El Niño toma fuerza y preocupa a Colombia; hay 75 % de probabilidad de que sea el más fuerte en la historia*. El País. https://elpais.com.co/colombia/fenomeno-de-el-nino-toma-fuerza-y-preocupa-a-colombia-hay-75-de-probabilidad-de-que-sea-el-mas-fuerte-en-la-historia-1057.html

Federación Nacional de Comerciantes & Asociación Nacional de Empresarios de Colombia. (2026, septiembre). *Informe del sector automotor a agosto 2026*. Fenalco. https://www.fenalco.com.co/blog/gremial-4/informe-del-sector-automotor-a-agosto-2026-9088

Galeano Balaguera, P. (2026, 10 de septiembre). *Tarifas de energía subirían: Gobierno prepara subasta ante El Niño y enfrenta déficit de $4,57 billones*. Portafolio. https://www.portafolio.co/energia/tarifas-de-energia-subirian-gobierno-prepara-subasta-ante-el-nino-y-enfrenta-deficit-de-4-57-billones-502192

Unidad de Planeación Minero-Energética. (s.f.). *Plan 6GW+* [Conjunto de datos]. Sistema de Información Minero-Energético Colombiano (SIMEC). https://www.upme.gov.co/simec/plan-6gw/
