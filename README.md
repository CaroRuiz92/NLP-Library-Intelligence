### Sistema de Recomendación de Libros Basado en NLP 📚

Este proyecto implementa un sistema inteligente de búsqueda y recomendación de libros utilizando técnicas avanzadas de Procesamiento de Lenguaje Natural (NLP). El sistema combina el reconocimiento de entidades, análisis sintáctico y búsqueda semántica para ofrecer recomendaciones precisas basadas en autores o temáticas.

🚀 Características Principales

Búsqueda Semántica Asimétrica: Implementación de un sistema de pregunta-respuesta para encontrar información específica dentro de sinopsis extensas.

Detección de Entidades (NER): Uso de modelos para identificar nombres de autores en las consultas de los usuarios.

Validación de Autores con Jaccard: Sistema de corrección de errores tipográficos para nombres de autores basado en similitud de Jaccard y n-gramas de caracteres.

Recomendación por Similitud de Coseno: Motor de recomendación que utiliza embeddings (vectores de 384 dimensiones) para comparar la semántica de las sinopsis.

Clasificación de Género: Si no se detecta un autor, el sistema infiere el género más probable y filtra las recomendaciones temáticamente.

🛠️ Tecnologías Utilizadas
- Python: Lenguaje principal.
- Pandas & NumPy: Procesamiento y manipulación de grandes volúmenes de datos (62k+ registros).
- Scikit-Learn: Cálculo de cosine_similarity y preprocesamiento.
- Sentence-Transformers: Generación de embeddings de alta calidad para las sinopsis.
- spaCy / GLiNER: Análisis lingüístico y reconocimiento de entidades nombradas.

📊 Estructura del Dataset

El sistema trabaja sobre un DataFrame integrado que vincula metadatos con representaciones vectoriales:

- autor, titulo, generos: Información descriptiva.
- embeddings: 384 columnas numéricas que representan el significado semántico de cada obra.

🧠 Lógica del Recomendador

El sistema opera bajo un flujo de decisión inteligente:

- Input del Usuario: Se analiza la consulta mediante POS Tagging y NER.
- Identificación de Autor: Si se detecta un autor, se valida contra el dataset mediante el coeficiente de Jaccard. Si hay coincidencia, se recomiendan obras similares de ese mismo autor.
- Análisis Temático: Si no hay un autor claro, el sistema vectoriza la frase del usuario y busca las sinopsis más parecidas dentro del género correspondiente mediante Similitud de Coseno.
