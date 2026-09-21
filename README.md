Netflix PostgreSQL: Modelado relacional y normalización
Proyecto de laboratorio que normaliza el dataset de catálogo de Netflix (netflix_titles.csv, 8.807 títulos) hasta Tercera Forma Normal, lo carga en PostgreSQL y lo consulta con JOIN.

Autor:juan bastos-julian ovalle-cristian rojas 

Stack
PostgreSQL 14+
psql
Dataset: Netflix Movies and TV Shows 

netflix-postgresql/
── data/netflix_titles.csv
── diagram/modelo_entidad_relacion.png
── sql/
   ── 01_creacion_base_datos.sql
   ── 02_carga_datos.sql
   ── 03_consultas_join.sql
── dump/netflix_db.dump
── README.md

Justificación 3NF
1NF: los campos con varios valores separados por comas (cast, director, country, listed_in) se separan en filas, y duration se divide en valor numérico y unidad.
2NF: los atributos dependen de la clave completa. Las relaciones N:M viven en tablas asociativas (titulo_genero, titulo_pais, titulo_persona).
3NF: se eliminan dependencias transitivas con catálogos propios: tipo_produccion, clasificacion, genero, pais y persona.
titulo_persona guarda el rol (Actor o Director) con PK (id_titulo, id_persona, rol), así una persona puede tener varios roles en un mismo título.
Los valores vacíos se guardan como NULL y las fechas como DATE.
