# NormaBot 📚

Asistente virtual de Bibliotecología integrado en Telegram y potenciado por Inteligencia Artificial (Google Gemini), diseñado para asistir a estudiantes y profesionales en catalogación descriptiva y temática (RCAA2, ISBD, MARC21, Dewey 23, BNMM y Koha).

## 🚀 Características Principales
- **Entrada Multimodal:** Permite enviar consultas por texto o subir fotos de portadas de libros y pantallas de Koha.
- **Flujo Modular:** Cada comando (`/rcaa2`, `/marc`, `/auditoria`, `/dewey`, `/materia`, `/koha`) responde a una única tarea específica para evitar respuestas abrumadoras.
- **Guía Adaptada a Koha:** Indica de manera clara en qué pestaña y con qué indicadores se debe cargar cada campo MARC21.
- **Auditoría con Semáforo:** Detecta errores comunes de tipeo o formato marcándolos con 🔴, 🟡 y 🟢.

## ⚙️ Arquitectura Técnica (Make.com)
El proyecto utiliza una automatización low-code basada en Make.com distribuida en dos ramas gestionadas por un Router:
1. **Rama de Texto:** Captura mensajes y comandos de Telegram y los procesa directamente con el modelo de lenguaje de Google Gemini.
2. **Rama de Fotos:** 
   - Descarga el archivo desde los servidores de Telegram (`Telegram Bot - Download a File`).
   - Lo sube temporalmente a la API de Google (`Google Gemini AI - Upload a File`) para generar un `File URI` válido.
   - Analiza la imagen junto con el prompt del sistema y el pie de foto del usuario.
   - Devuelve la respuesta estructurada al chat de Telegram.

## 🛠️ Comandos de Telegram
- `/start` - Menú principal y guía de uso.
- `/rcaa2` - Ficha ISBD y reglas RCAA2.
- `/marc` - Guía de carga en Koha (MARC21 por pestañas).
- `/auditoria` - Corrección paso a paso de ejercicios o capturas de Koha.
- `/dewey` - Clasificación Dewey Edición 23.
- `/materia` - Consulta de términos autorizados campo 650 (BNMM).
- `/koha` - Diagnóstico de errores técnicos en Koha.
