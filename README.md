# 🤖 Agente Inteligente "Carrarurquía" (RAG + Web Search)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)]
https://colab.research.google.com/drive/1K1BSm3vDoq9SAO0JTijGigdCc1XRQ5ml?usp=sharing

## 📝 Descripción del Proyecto
Este proyecto implementa un **Agente de IA con arquitectura de enrutamiento dinámico** utilizando LangGraph. El agente actúa como un asistente experto para la empresa "Carrarurquía", capaz de tomar decisiones algorítmicas en tiempo real sobre qué fuente de datos consultar para responder a las preguntas del usuario.

Si la consulta es sobre información interna (ej. paquetes de viaje, políticas), el agente utiliza un sistema **RAG (Retrieval-Augmented Generation)** consultando una base de datos vectorial local basada en documentos PDF. Si la pregunta requiere información de cultura general o datos actualizados, el agente rutea la consulta hacia una búsqueda en la **Web**.

Finalmente, el agente consolida la información, la formatea estructuradamente y genera un reporte descargable de forma automática.

## 🚀 Características Principales
* **Ruteo Inteligente (LangGraph):** Toma de decisiones autónoma para clasificar consultas entre `RAG` y `Web`.
* **RAG Local:** Ingesta y partición de documentos PDF utilizando `PyPDFLoader` y fragmentación semántica.
* **Búsqueda Web:** Integración con SerpAPI para resolver consultas fuera de la base de conocimiento interna.
* **Exportación Automática:** Generación dinámica de reportes en formatos `.md` (Markdown) y `.pdf` listos para descargar.
* **Protección contra Alucinaciones:** Prompt engineering avanzado para forzar el *grounding* estricto en los documentos locales.

## 🛠️ Stack Tecnológico
* **Lenguaje:** Python 3
* **LLM Core:** Google Gemini 2.5 Flash
* **Orquestación & Flujos:** LangChain & LangGraph
* **Base de Datos Vectorial:** FAISS (Facebook AI Similarity Search)
* **Embeddings:** Google Generative AI Embeddings (`gemini-embedding-001`)
* **Búsqueda Web:** SerpAPI
* **Procesamiento de Documentos:** `pypdf`, `fpdf2`, `markdown`

## ⚙️ Arquitectura del Flujo (LangGraph)
El estado del agente fluye a través de los siguientes nodos:
1. **Nodo Agente:** Evalúa la pregunta y decide la fuente (`RAG` o `Web`).
2. **Nodos de Recuperación:** Extraen el contexto relevante de FAISS o de SerpAPI.
3. **Nodo Markdown:** Unifica el contexto recuperado y genera una respuesta final estructurada sin alucinar información.

*(Opcional: Reemplaza este texto con una imagen de tu grafo generado por LangGraph)*

## 💻 Cómo ejecutar este proyecto

Este proyecto está diseñado para ejecutarse nativamente en Google Colab.

1. Haz clic en el botón **"Open in Colab"** en la parte superior de este documento.
2. En el entorno de Colab, ve al menú lateral izquierdo y selecciona el ícono de la llave (`Secrets` / `userdata`).
3. Agrega tus credenciales de forma segura (el código nunca expondrá tus claves públicas):
   * `GEMINI_API_KEY`: Tu clave de Google AI Studio.
   * `SERPAPI_API_KEY`: Tu clave de SerpAPI.
4. Sube al entorno de Colab los archivos PDF de prueba que desees que el agente analice.
5. Ejecuta todas las celdas secuencialmente. En la última celda, se abrirá un *prompt* interactivo para que ingreses tu pregunta.

## 👨‍💻 Autor
**Jesús Antonio Díaz**
*Proyecto desarrollado para la Inmersión IA Dev*
