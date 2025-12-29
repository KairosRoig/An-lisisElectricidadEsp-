# 📊 Proyecto: Análisis del Mercado Eléctrico de España

**Descripción breve**

Este repositorio contiene un análisis exploratorio y visualización del mercado eléctrico (datos históricos) de España. El análisis se realiza principalmente en el notebook `notebooks/Proyecto_JaimeRoig_MercadoElectrico.ipynb`, que carga los datos, realiza limpieza y consistencia, explora series temporales y detecta outliers.

---

## 📁 Estructura del repositorio

- `README.md` — Este documento.
- `datos/spain_energy_market.csv` — Dataset principal (no incluido en el repositorio por privacidad/volumen).
- `notebooks/Proyecto_JaimeRoig_MercadoElectrico.ipynb` — Notebook principal con todo el flujo de trabajo.
- `informes/` — Carpeta destinada a informes finales y visualizaciones exportadas.

---

## 🎯 Objetivos del notebook

- Cargar y validar la existencia del fichero CSV con datos del mercado eléctrico.
- Verificar y limpiar inconsistencias en columnas clave (`id`, `name`, `datetime`, `value`).
- Enriquecer datos con campos auxiliares (`date`, `time`, `year`, `geoname`, `geoid`).
- Análisis exploratorio: distribuciones, series temporales y detección de outliers (IQR).
- Visualizaciones de series temporales, histogramas y boxplots para apoyar conclusiones.

---

## 🗂️ Sobre el dataset

- Ruta esperada: `datos/spain_energy_market.csv`.
- Columnas usadas por el notebook (si no existen, el notebook crea un placeholder):
  - `id`, `name`, `datetime`, `value`, `geoname`, `geoid`
- El notebook intenta localizar el CSV en varias rutas relativas (ver primera celda) y crea un DataFrame placeholder si no lo encuentra. Asegúrate de colocar el archivo en `./datos/` o actualizar la ruta en la primera celda.

---

## 🔧 Requisitos y cómo ejecutar

1. Entorno recomendado
   - Python 3.8+ (3.9/3.10 recomendados)
   - Instalar dependencias mínimas:

```bash
pip install pandas numpy matplotlib jupyterlab
```

2. Abrir y ejecutar
   - Desde VS Code: abrir el notebook y ejecutar las celdas en orden.
   - Desde JupyterLab/Notebook: `jupyter lab` o `jupyter notebook`, abrir `notebooks/Proyecto_JaimeRoig_MercadoElectrico.ipynb` y ejecutar.

3. Notas de ejecución
   - La primera celda intenta localizar el CSV en múltiples rutas y mostrará un aviso si no lo encuentra.
   - Ejecuta las celdas secuencialmente para mantener el flujo (limpieza → transformaciones → visualizaciones).

---

## 🔎 Qué hace cada sección del notebook

1. **Carga y diagnóstico inicial**: comprueba existencia del CSV, imprime `head()` y `info()` del DataFrame.
2. **Consistencia `id` / `name`**: funciones para detectar ids con múltiples `name` y para rellenar `name` usando `(id, geoname)`.
3. **Transformaciones de tiempo**: conversión a `datetime`, extracción de `date`, `time` y `year`.
4. **Identificación de país**: heurística sencilla para etiquetar `geoname`/`geoid` desde `name`.
5. **Análisis exploratorio**: conteo por `name`/`geoname`, gráficos de barras.
6. **Series temporales**: gráficos de `value` para `Precio mercado SPOT Diario ESP` y subset por año (ej. 2017).
7. **Detección de outliers**: IQR para `value`, y boxplot para visualizarlos.

---

## ✅ Resultados y puntos clave (resumen)

- Se realizan transformaciones y rellenados inteligentes para `name` mediante la combinación `(id, geoname)`.
- El notebook permite visualizar la evolución del precio spot diario para España y periodos concretos (ej. 2017).
- Se identifican outliers con la regla IQR y se visualizan con boxplots para facilitar decisiones de limpieza o análisis robusto.

---

## 💡 Buenas prácticas y recomendaciones

- Verifica la codificación (UTF-8) y formato de `datetime` en el CSV antes de análisis a gran escala.
- Si trabajas con grandes volúmenes, considera cargar por trozos (`chunksize`) y/o usar herramientas de procesamiento por lotes.
- Añade archivo `requirements.txt` o `environment.yml` para facilitar reproducción.

---

## ✍️ Contribuciones y contacto

- **Autor (sugerido):** Jaime Roig Martín — edita este campo si procede.
- Para mejoras: crea un issue o un fork y envía un pull request con pruebas o ejemplos reproducibles.

---

## 📄 Licencia

- Añade un fichero `LICENSE` con la licencia de tu preferencia (por ejemplo, MIT) si quieres permitir reutilización.

---

Si quieres, puedo:
- Añadir un `requirements.txt` automáticamente con las dependencias detectadas, ✅
- Generar un fichero `LICENSE` (por ejemplo MIT), ✅
- Extender el README con ejemplos de salida (gráficos exportados) o con capturas, ✅

Dime cuál de estas opciones prefieres y lo implemento. ¡Listo para el siguiente paso! ✨
