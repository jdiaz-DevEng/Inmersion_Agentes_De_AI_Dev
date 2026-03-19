# 🤖 Agente Inteligente "Carrarurquía" (RAG + Web Search)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1K1BSm3vDoq9SAO0JTijGigdCc1XRQ5ml?usp=sharing)

## 📝 Descripción del Proyecto
Este proyecto fue desarrollado como parte de la **Inmersión IA Dev**, utilizando los archivos y documentos base proporcionados durante el curso para la empresa ficticia "Carrarurquía". 

El sistema implementa un **Agente de IA con arquitectura de enrutamiento dinámico** utilizando LangGraph, capaz de tomar decisiones algorítmicas en tiempo real sobre qué fuente de datos consultar:
* **RAG (Retrieval-Augmented Generation):** Para consultas sobre información interna de la empresa (paquetes de viaje, políticas) utilizando una base de datos vectorial local.
* **Búsqueda Web:** Para preguntas de cultura general o datos dinámicos, enrutando la consulta hacia internet mediante SerpAPI.

## 🏆 Desafío Final y Experiencia de Usuario (UX)
Como parte del desafío de la última clase de la inmersión, este proyecto va un paso más allá de la simple generación de texto en consola, implementando dos grandes mejoras:

1. **Doble Exportación Automática:** Las respuestas del agente se formatean, procesan y descargan automáticamente de forma física en dos formatos: **Markdown (.md)** y **PDF (.pdf)**, dejándolos listos para su distribución y lectura.
2. **Interactividad y UX:** Pensando en la Experiencia del Usuario final, se eliminó la ejecución estática de consultas. Se implementó una interfaz de línea de comandos interactiva donde el usuario ingresa su pregunta de forma natural. El sistema captura la entrada y genera dinámicamente nombres de archivo limpios y seguros (sanitización de *strings*) basados en la consulta original.

## 🚀 Características Principales
* **Ruteo Inteligente (LangGraph):** Clasificación autónoma de consultas entre la base local y la web.
* **Procesamiento de Documentos:** Ingesta de PDFs con `PyPDFLoader` y partición semántica.
* **Protección contra Alucinaciones:** Prompt engineering estricto para forzar el anclaje (*grounding*) en los documentos y evitar invención de precios o datos corporativos.

## 🛠️ Stack Tecnológico
* **Lenguaje:** Python 3
* **LLM Core:** Google Gemini 2.5 Flash
* **Orquestación & Flujos:** LangChain & LangGraph
* **Base de Datos Vectorial:** FAISS (Facebook AI Similarity Search)
* **Embeddings:** Google Generative AI Embeddings (`gemini-embedding-001`)
* **Procesamiento y Exportación:** `pypdf`, `fpdf2`, `markdown`

## 💻 Cómo ejecutar este proyecto
1. Haz clic en el botón **"Open in Colab"** en la parte superior de este documento.
2. En el entorno de Colab, ve al menú lateral izquierdo y selecciona el ícono de la llave (`Secrets` / `userdata`).
3. Agrega tus credenciales de forma segura (el código nunca expondrá tus claves públicas):
   * `GEMINI_API_KEY`: Tu clave de Google AI Studio.
   * `SERPAPI_API_KEY`: Tu clave de SerpAPI.
4. Sube al entorno de Colab los archivos PDF de la inmersión de "Carrarurquía".
5. Ejecuta todas las celdas secuencialmente. En la última celda, se abrirá el *prompt* interactivo para que inicies la conversación.

## 👨‍💻 Autor
**Jesus Antonio Díaz**

*Proyecto desarrollado para la Inmersión IA Dev*
