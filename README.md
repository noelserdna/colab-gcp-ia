# Cuadernos Colab · GCP + IA (embudo AI-first)

Colección de cuadernos de **Google Colab** para aprender, desde cero y con mucho detalle, a construir el **embudo AI-first** sobre Google Cloud: desde la **ingesta de datos** hasta el **RAG** y el **fine-tuning** de modelos. Cada cuaderno es material de aprendizaje autoexplicado, pensado para impartirse como clase o seguirse en solitario.

## Índice de cuadernos

### Serie · Capa 1 — Ingesta de datos en GCP

| # | Cuaderno | Abrir en Colab |
|---|----------|----------------|
| 0.0 | Panorama de la Capa 1 (clase de 90 min: las 7 tecnologías de ingesta) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/noelserdna/colab-gcp-ia/blob/main/00_0_panorama_capa1_ingesta.ipynb) |
| 0 | Fundamentos y setup | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/noelserdna/colab-gcp-ia/blob/main/00_fundamentos_setup.ipynb) |
| 1 | Ingesta batch: API pública → BigQuery | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/noelserdna/colab-gcp-ia/blob/main/01_batch_api_a_bigquery.ipynb) |

### RAG y vectorización con BigQuery

| Cuaderno | Abrir en Colab |
|----------|----------------|
| De la bandeja de entrada al RAG: vectorización de emails con BigQuery | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/noelserdna/colab-gcp-ia/blob/main/curso_rag_emails_bigquery_v2.ipynb) |

### Fine-tuning de LLMs

Subproyecto en [`fine/`](fine/) — detalles en [`fine/README.md`](fine/README.md).

| Cuaderno | Abrir en Colab |
|----------|----------------|
| Probar el modelo entrenado (chat + `backend_sim`) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/noelserdna/colab-gcp-ia/blob/main/fine/notebooks/probar_modelo_reservas.ipynb) |
| Entrenar (QLoRA con Unsloth) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/noelserdna/colab-gcp-ia/blob/main/fine/notebooks/finetune_gemma4_reservas.ipynb) |

---

## Qué cubre cada cuaderno

### 0.0 · Panorama de la Capa 1

Clase magistral de 90 min que da el **mapa de toda la Capa 1** antes de bajar al detalle práctico. Caso conductor **InnovaCo**, stack didáctico Notion + Google Workspace + Telegram + Neon Postgres.

- Los **4 modos de ingesta**: batch, streaming, CDC y event-driven.
- Las **7 tecnologías** y cuándo usar (y no usar) cada una: **Application Integration**, **Workflows**, **Pub/Sub**, **Eventarc**, **Datastream**, **Storage Transfer Service** y **Cortex Framework**.
- Patrón de trabajo AI-first: *arquitectura → prompt → LLM genera YAML/código → revisión → `gcloud`*.
- Por bloque: concepto, anatomía, prompt de ejemplo, YAML/código generado, comandos `gcloud`, trampas y ejercicio mental.
- Trampas transversales, biblioteca de prompts reutilizables y guía de setup del stack en 30 min.
- Incluye celdas Python ejecutables (mapa mental, recomendador de tecnología, plantilla de prompts) que corren sin ningún setup.

### 0 · Fundamentos y setup

- Qué es la nube, GCP y Colab (con analogías).
- Python mínimo imprescindible (variables, diccionarios, listas, funciones).
- Qué es una API REST y qué es JSON, en vivo.
- Autenticación y por qué no se escriben contraseñas en el código.
- Conectar Colab con tu proyecto de Google Cloud.
- Consultar un dataset público de BigQuery.
- Los 4 modos de ingesta que organizan la serie.

**Tiempo estimado:** 60-90 min.

### 1 · Ingesta batch: API pública → BigQuery

Tu **primera ingesta de datos real**: traer información de una fuente externa y dejarla en BigQuery, lista para que una IA razone sobre ella.

- Qué es la **ingesta batch** (por lotes) y cuándo es el modo adecuado.
- Llamar a una **API pública** (clima, sin clave) y entender su respuesta JSON.
- Qué es la **paginación** y cómo recorrer datos página a página.
- **Transformar** datos crudos a un **esquema canónico** limpio con pandas.
- Escribir en BigQuery con **MERGE** para una ingesta **idempotente** (ejecutarla dos veces no duplica).
- Hacer ingesta **incremental** (traer solo lo nuevo).
- Desplegar en producción con un **prompt para Claude Code + gcloud**.

**Requisito:** Notebook 0 completado (entorno en verde). **Tiempo estimado:** ~60 min.

### RAG · Vectorización de emails con BigQuery

Curso práctico (~90 min) que construye, paso a paso, un sistema **RAG (Retrieval-Augmented Generation)** sobre el correo de una tienda de perfumes ficticia (*Esencia Ibérica, S.L.*): preguntar en lenguaje natural sobre decenas de emails de consultas, pedidos, quejas y devoluciones.

- La decisión de diseño de partida: **documentos sueltos vs. base de datos**.
- **Extract & Load** de emails sintéticos a BigQuery; **Transform**: limpieza y *chunking*.
- Conexión a **Vertex AI** y embeddings en SQL con **`ML.GENERATE_EMBEDDING`** (incluido el parámetro `task_type` que casi todos ignoran).
- **Búsqueda semántica** con `VECTOR_SEARCH` y búsqueda **híbrida** (semántica + filtros SQL).
- De la búsqueda al **RAG** (buscador + dos pasos); anexo **RAG vs. CAG**.
- **Vectorización incremental** en producción (patrón *anti-join*), evaluación del retrieval, ejercicios y limpieza de recursos.

**Tiempo estimado:** ~90 min. Requiere un proyecto GCP con BigQuery y Vertex AI habilitados.

### Fine-tuning · Asistente de reservas (Gemma 4 E2B)

Subproyecto en [`fine/`](fine/): especializar **Gemma 4 E2B** con **QLoRA** para un asistente de reservas de instalaciones deportivas (*Polideportivo Municipal Las Encinas*) que conversa y **llama a herramientas** (consultar disponibilidad, crear / consultar / modificar / cancelar reservas…) sobre un **backend simulado**. Incluye el dataset sintético (~1.200 conversaciones), el backend, los dos cuadernos y el **adapter ya entrenado**.

- **Entrenar** — QLoRA con Unsloth sobre Gemma 4 E2B.
- **Probar** — cargar el adapter entrenado y charlar con el modelo, con `backend_sim` ejecutando de verdad las llamadas a herramientas (bucle completo *modelo ↔ datos*). Requiere GPU (T4).

---

## Uso

Abre cualquier cuaderno con su badge **Open in Colab**, o clona el repositorio:

```bash
git clone https://github.com/noelserdna/colab-gcp-ia.git
```
