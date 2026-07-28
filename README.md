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
| 1 · De la bandeja de entrada al RAG: vectorización de emails con BigQuery | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/noelserdna/colab-gcp-ia/blob/main/curso_rag_emails_bigquery_v2.ipynb) |
| 2 · Del PDF al RAG: documentos con estructura (Document AI + BigQuery) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/noelserdna/colab-gcp-ia/blob/main/curso_rag_pdf_polizas_bigquery.ipynb) |
| 3 · RAG sobre PDF con un OCR open-source en tu GPU (Unlimited-OCR) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/noelserdna/colab-gcp-ia/blob/main/curso_rag_pdf_ocr_opensource.ipynb) |
| 4 · RAG con soberanía total: Postgres+pgvector + Gemma, todo self-hosted | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/noelserdna/colab-gcp-ia/blob/main/curso_rag_selfhosted_pgvector.ipynb) |
| 5 · Fine-tuning de Gemma 4 para el RAG (QLoRA con Unsloth) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/noelserdna/colab-gcp-ia/blob/main/curso_finetuning_gemma_seguros.ipynb) |

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

### RAG · Del PDF al RAG: documentos con estructura

Continuación del anterior (~90 min). Mismo pipeline, fuente radicalmente distinta: los **condicionados de seguro en PDF** de *Peñalara Seguros, S.A.*. Un PDF no es un formato de datos, es un formato de presentación — hay que **reconstruir** el texto y su estructura antes de poder vectorizar nada.

- **Qué cambia respecto a los emails**: el texto no viene dado, hay layout (páginas, columnas, tablas) y hay que poder **citar la página y la cláusula**.
- **El caso que lo vertebra**: *"¿me cubre el agua de lluvia?"* — el mismo riesgo aparece en **coberturas** (pág. 4) y en **exclusiones** (pág. 5). Un chunk sin su título jerárquico hace que el RAG **le mienta al cliente** con total seguridad.
- **Cloud Storage + object tables**: por qué los binarios no viven en BigQuery.
- **Document AI Layout Parser** vía `ML.PROCESS_DOCUMENT`, con `include_ancestor_headings` — la opción que salva el sistema.
- **El contraste**, ejecutado en vivo: chunking naive (`pypdf` + cortar por caracteres) vs. Layout Parser.
- **RAG con citas verificables** (póliza, página, cláusula) y **versionado de documentos** (`DELETE`+`INSERT`: una póliza nueva *sustituye* a la vieja, un email nunca lo hacía).

### RAG · PDF con un OCR open-source en tu GPU

Mismo caso y mismo pipeline que el anterior, pero **sustituyendo la extracción**: en vez de la API de Document AI, un modelo abierto ([`baidu/Unlimited-OCR`](https://huggingface.co/baidu/Unlimited-OCR), MIT, sucesor de DeepSeek-OCR) corriendo en la **GPU del propio Colab**. Requiere GPU (T4 vale, L4/A100 mejor).

- **El porqué — soberanía del dato**: en seguros/salud/legal, mandar documentos con datos personales a una API de terceros es un problema de cumplimiento. Con un OCR local, **el PDF nunca sale de la máquina**.
- **PDF → imágenes → markdown**: se rasteriza cada página (PyMuPDF) y el modelo la *lee* (`infer_multi`), devolviendo markdown con estructura; se rastrea la página por el separador `<PAGE>`.
- **El chunking es tuyo**: se trocea el markdown respetando sus encabezados y anteponiendo la sección a cada chunk — a mano, lo que Document AI daba hecho.
- **El contraste**: OCR self-hosted vs. API gestionada (coste, velocidad, control, soberanía).
- De la sección de embeddings en adelante, **el pipeline es idéntico** a los otros dos cursos — la extracción es intercambiable.

**Requisito:** GPU en Colab + proyecto GCP con BigQuery y Vertex AI. Sin coste por página (la extracción es local y gratis).

**Requisito:** proyecto GCP con **facturación activa** — ⚠️ Document AI no tiene capa gratuita ($10/1.000 págs; este cuaderno procesa 24 págs ≈ **$0,24**).

### RAG · Soberanía total: Postgres + pgvector + Gemma

El cierre de la serie: fuera BigQuery, fuera Vertex, fuera Gemini. El RAG completo sobre **infraestructura propia** — el único tercero es GCloud como IaaS.

- **Vector store propio**: **PostgreSQL + `pgvector`** en una VM de Compute Engine (creada con `gcloud` desde el Colab, vía *startup-script*), conectada de forma segura por **túnel IAP** (sin abrir puertos a internet).
- **Embeddings open-source**: `BAAI/bge-m3` (MIT, 1024 dims) en la GPU — el `ML.GENERATE_EMBEDDING` de Vertex se sustituye por `SentenceTransformer`.
- **Búsqueda en SQL**: el `VECTOR_SEARCH` pasa a ser `ORDER BY embedding <=> consulta` con índice **HNSW** de pgvector.
- **Generación con Gemma 4** (E4B, Apache 2.0) en 4-bit en la GPU, en vez de Gemini.
- **Comparativa honesta** self-hosted vs. gestionado (privacidad, coste, mantenimiento, calidad) y **borrado de la VM** al final para no dejar coste.

**Requisito:** GPU en Colab + proyecto GCP con facturación (una VM `e2-medium`). El paso previo —extraer el texto— se cubre en el curso 3.

### RAG · Fine-tuning de Gemma 4 para el RAG

Continuación del anterior: afinamos el modelo generador para el **estilo Peñalara** y enchufamos el adapter al RAG self-hosted. Solo GPU (T4).

- **El porqué, con honestidad**: el fine-tuning **no añade conocimiento** (eso lo da el RAG); da **estilo y consistencia** — citar siempre la cláusula, nunca confundir cobertura con exclusión, tono de asesor.
- **QLoRA con Unsloth** sobre `gemma-4-E4B-it` (4-bit, entra en T4): LoRA, `train_on_responses_only`, dataset sintético `(contexto + pregunta) → respuesta ideal` generado desde el catálogo de pólizas.
- **Antes vs. después**: se compara la misma pregunta trampa con el modelo base y el afinado.
- **Se guarda solo el adapter** (unos MB) y se muestra cómo **cargarlo con `peft` puro** (sin Unsloth) para enchufarlo al Cuaderno 4 sin tocar el resto del pipeline.

**Requisito:** GPU en Colab. Cierra la serie self-hosted (cursos 4 + 5).

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
