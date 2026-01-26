# Software-enfermedades-de-hojas-de-paltas 
entrar y selecionar la carpeta SOFTWARE 🥑
Preparación en Google Colab
Entra a Google Colab.

Crea un Nuevo cuaderno.

Asegúrate de activar la aceleración por GPU para que el entrenamiento no tarde horas:

Ve a Entorno de ejecución > Cambiar tipo de entorno de ejecución.

Selecciona T4 GPU (o la que esté disponible).

2. Ejecución del Código
Copia y pega el contenido del archivo palta.py en una celda de Colab y ejecútala. El script hará lo siguiente automáticamente:

Instalar librerías: Instalará dependencias como TensorFlow, Streamlit y Pyngrok.

Descargar Datos: Clonará el dataset desde GitHub y organizará las carpetas de imágenes.

Crear archivos auxiliares: Generará los archivos .py necesarios (model_utils.py, preprocessing.py, etc.) usando el comando %%writefile.

Entrenar los Modelos: Entrenará tres arquitecturas diferentes (CNN Personalizada, EfficientNetB0 y DenseNet121). Nota: Esto puede tardar varios minutos dependiendo del número de imágenes.

3. Acceso a la Interfaz Gráfica (Streamlit)
Al final del script, verás una sección que utiliza pyngrok.

Busca en la salida de la última celda una línea que diga:

Tu app está en: http://XXXX-XX-XX.ngrok-free.app

Haz clic en ese enlace.

Se abrirá una pestaña nueva con la interfaz de Streamlit donde podrás:

Subir una foto de una hoja de palta.

Seleccionar el modelo que prefieras.

Ver el diagnóstico (Sana o Enferma) y el Mapa de Saliencia (que resalta qué parte de la hoja analizó el modelo).

Descargar un reporte en PDF.

4. Consideraciones Importantes
Token de Ngrok
En el código aparece un token de autenticación:

Python

conf.get_default().auth_token = "2xFZJFASH..."
Si ese token llega a fallar o expirar, deberás crear una cuenta gratuita en ngrok.com, obtener tu propio Authtoken y reemplazarlo en esa línea.

Estructura de Archivos
Una vez que ejecutes el código, tu panel lateral de archivos en Colab debería verse así:

models/ (donde se guardan los modelos .keras entrenados).

app.py (el código de la interfaz).

model_utils.py, preprocessing.py, report_utils.py, metrics_utils.py.

Avocado Augmneted_Dataset/ (las imágenes).

Re-entrenamiento
Si solo quieres probar la interfaz sin esperar a que los modelos se entrenen cada vez, podrías comentar la sección de if __name__ == "__main__": en la parte de entrenamiento una vez que los archivos .keras ya existan en la carpeta /models.
