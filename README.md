# TMDB Medallion Pipeline en Databricks (Bronze → Silver → Gold)

Pipeline en Databricks que consume datos desde la API de The Movie Database (TMDB), los almacena como JSON crudo en **Bronze**, los transforma a tablas Delta en **Silver**, y finalmente genera analítica agregada en **Gold**.

## Arquitectura (Medallion)

- **Bronze (Raw / JSON):**
  - Descarga desde TMDB y guarda archivos JSON crudos en Unity Catalog Volumes.
- **Silver (Curated / Delta):**
  - Limpieza, tipado y normalización.
  - Modelado relacional básico: movies + genres + tabla puente movie_genres.
- **Gold (Analytics / Delta):**
  - Métricas agregadas por género (weighted rating, votos totales, etc.).
  - Top movies por mejor género y top movies por cada género.

