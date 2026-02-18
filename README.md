# The_Huddle_Challenge_4_CodePro_4
“Hacelo por el bien de la literatura… y por los memes.” Challenge 4.
Este proyecto es una herramienta automatizada de extracción y gestión de datos de libros. Realiza un proceso completo de Web Scraping, enriquecimiento de datos a través de una API externa y persistencia en una base de datos relacional.

💡 Idea Base
La aplicación está diseñada para recolectar información de un catálogo de libros (títulos, precios, stock, categorías) desde la web, buscar automáticamente los autores de cada obra utilizando la API de Google Books y organizar toda esta información de forma estructurada para permitir consultas complejas de análisis de datos.

🚀 Cómo Funciona
El proyecto se divide en cuatro fases principales:

Inicialización de BD: Se crea una base de datos SQLite (libros.db) con un esquema relacional que incluye tablas para categorías, autores, libros y una tabla intermedia para la relación de libros y sus autores.

Web Scraping Masivo: Utiliza técnicas de scraping para recorrer todas las categorías del sitio books.toscrape.com. Implementa concurrencia para acelerar la descarga de datos de hasta 1,000 libros.

Enriquecimiento con API: Para cada libro encontrado, el sistema consulta la API de Google Books para intentar localizar al autor real de la obra.

Persistencia y Consulta: Los datos se limpian y se insertan en la base de datos local. Finalmente, el sistema permite realizar consultas SQL personalizadas (ej. filtrar libros por rating o precio).

🛠️ Tecnologías Utilizadas
Lenguaje: Python 3.x

Base de Datos: SQLite3

Librerías de Scraping: BeautifulSoup4, Requests y lxml

Procesamiento Paralelo: ThreadPoolExecutor (Concurrent Futures)

APIs Externas: Google Books API

Otras: re (Expresiones regulares para limpieza de stock y precios), python-dotenv.

📋 Estructura de la Base de Datos
El sistema genera un modelo relacional que permite evitar la duplicidad de información:

categorias: Almacena los géneros literarios.

autores: Registro de escritores obtenidos de la API.

libros: Información detallada de cada ejemplar (precio, stock, rating, link).

libro_autor: Tabla de unión para manejar relaciones de muchos a muchos.

⚙️ Cómo se usa
1. Requisitos Previos
Asegúrate de tener instaladas las dependencias necesarias:

Bash
pip install requests beautifulsoup4 lxml python-dotenv
2. Configuración
Si utilizas una API Key para Google Books, crea un archivo .env en la raíz del proyecto:

Fragmento de código
GOOGLE_BOOKS_API_KEY=tu_api_key_aqui
3. Ejecución
Simplemente ejecuta el notebook o script principal:

Abre challenge_4.ipynb.

Ejecuta todas las celdas.

El sistema creará automáticamente el archivo libros.db y comenzará el proceso de descarga y guardado.

4. Consultar resultados
Una vez finalizado, puedes realizar consultas SQL directamente sobre la base de datos para obtener insights, como por ejemplo:

SQL
SELECT titulo, precio, rating 
FROM libros 
WHERE rating > 3 AND precio < 15.0 
ORDER BY rating DESC;
Desarrollado como parte de un desafío técnico de programación y gestión de bases de datos.
