✔  WriteFile Writing to Audiobook_Project\README.md                                               │
 │                                                                                                   │
 │     1 # Audiobook Studio Lite                                                                     │
 │     2                                                                                             │
 │     3 Bienvenido a Audiobook Studio Lite, una aplicación de escritorio para convertir tus         │
 │       documentos de texto (.docx, .pdf) en audiolibros enriquecidos con diferentes voces,         │
 │       efectos de sonido y música de fondo.                                                        │
 │     4                                                                                             │
 │     5 ## Requisitos Previos                                                                       │
 │     6                                                                                             │
 │     7 1.  **Python 3:** Asegúrate de tener Python 3 instalado. Puedes descargarlo desde [         │
 │       python.org](https://www.python.org/).                                                       │
 │     8 2.  **FFmpeg:** Esta herramienta es **esencial** para el procesamiento de audio             │
 │       (especialmente para archivos `.mp3`).                                                       │
 │     9     *   **Windows:** Descarga FFmpeg desde [su sitio oficial](                              │
 │       https://ffmpeg.org/download.html), descomprime el archivo y agrega la carpeta `bin` a la    │
 │       variable de entorno PATH de tu sistema.                                                     │
 │    10     *   **macOS:** Puedes instalarlo con Homebrew: `brew install ffmpeg`                    │
 │    11     *   **Linux:** Puedes instalarlo con tu gestor de paquetes: `sudo apt-get install       │
 │       ffmpeg`                                                                                     │
 │    12                                                                                             │
 │    13 ## Instalación                                                                              │
 │    14                                                                                             │
 │    15 1.  **Crea la estructura de carpetas:** Antes de ejecutar el programa, debes crear la       │
 │       siguiente estructura de carpetas. El programa las necesita para encontrar tus archivos y    │
 │       guardar los resultados.                                                                     │
 │    16                                                                                             │
 │    17     ```                                                                                     │
 │    18     Audiobook_Project/                                                                      │
 │    19     |-- main.py                                                                             │
 │    20     |-- requirements.txt                                                                    │
 │    21     |-- README.md                                                                           │
 │    22     |-- input_docs/      <-- Coloca aquí tus archivos .docx y .pdf                          │
 │    23     |-- output_audio/    <-- Aquí se guardarán los audiolibros generados                    │
 │    24     |-- sfx/             <-- Coloca aquí tus efectos de sonido (.mp3 o .wav)                │
 │    25     |-- music/           <-- Coloca aquí tus pistas de música de fondo (.mp3 o .wav)        │
 │    26     ```                                                                                     │
 │    27                                                                                             │
 │    28 2.  **Instala las dependencias de Python:** Abre una terminal o línea de comandos en la     │
 │       carpeta `Audiobook_Project` y ejecuta el siguiente comando para instalar todas las          │
 │       librerías necesarias.                                                                       │
 │    29                                                                                             │
 │    30     ```bash                                                                                 │
 │    31     pip install -r requirements.txt                                                         │
 │    32     ```                                                                                     │
 │    33                                                                                             │
 │    34 ## ¿Cómo Formatear tu Documento?                                                            │
 │    35                                                                                             │
 │    36 Para que el programa pueda crear un audiolibro enriquecido, necesitas añadir "marcadores"   │
 │       especiales en tu archivo `.docx` o `.pdf`.                                                  │
 │    37                                                                                             │
 │    38 ### Capítulos                                                                               │
 │    39 Para marcar el inicio de un nuevo capítulo, escribe en una línea separada:                  │
 │    40 `[CAPITULO]`                                                                                │
 │    41 o                                                                                           │
 │    42 `[CHAPTER]`                                                                                 │
 │    43                                                                                             │
 │    44 Cada capítulo se guardará como un archivo de audio independiente.                           │
 │    45                                                                                             │
 │    46 ### Diálogos de Personajes                                                                  │
 │    47 Para asignar una voz diferente (masculina simulada) a un personaje, usa este formato:       │
 │    48 `[NOMBRE_PERSONAJE: "El texto del diálogo aquí."]`                                          │
 │    49                                                                                             │
 │    50 *Ejemplo:*                                                                                  │
 │    51 `[CARLOS: "No me esperaba esto."]`                                                          │
 │    52                                                                                             │
 │    53 El texto fuera de este formato será leído por la voz del narrador (femenina).               │
 │    54                                                                                             │
 │    55 ### Efectos de Sonido (SFX)                                                                 │
 │    56 Para insertar un efecto de sonido en un punto específico, asegúrate de que el archivo de    │
 │       audio esté en la carpeta `/sfx` y usa el marcador:                                          │
 │    57 `[SFX: nombre_del_archivo.mp3]`                                                             │
 │    58                                                                                             │
 │    59 *Ejemplo:*                                                                                  │
 │    60 `El viento soplaba con fuerza [SFX: viento_fuerte.mp3] mientras caminaba por el páramo.`    │
 │    61                                                                                             │
 │    62 ### Música de Fondo                                                                         │
 │    63 Para iniciar una pista de música de fondo, asegúrate de que el archivo esté en la carpeta   │
 │       `/music` y usa el marcador:                                                                 │
 │    64 `[MUSICA: nombre_de_la_pista.mp3]`                                                          │
 │    65                                                                                             │
 │    66 La música comenzará a sonar a un volumen bajo y continuará hasta que termine el capítulo,   │
 │       se encuentre una nueva pista de música o se detenga explícitamente con el marcador:         │
 │    67 `[MUSICA_FIN]`                                                                              │
 │    68                                                                                             │
 │    69 *Ejemplo:*                                                                                  │
 │    70 `[MUSICA: musica_suspenso.mp3]`                                                             │
 │    71 `La casa estaba en silencio, demasiado en silencio.`                                        │
 │    72 `[MUSICA_FIN]`                                                                              │
 │    73                                                                                             │
 │    74 ## Ejecutar el Programa                                                                     │
 │    75                                                                                             │
 │    76 Una vez que hayas configurado todo, simplemente ejecuta el script `main.py` desde tu        │
 │       terminal:                                                                                   │
 │    77                                                                                             │
 │    78 ```bash                                                                                     │
 │    79 python main.py                                                                              │
 │    80 ```                                                                                         │
 │    81                                                                                             │
 │    82 Se abrirá la interfaz gráfica. ¡Sigue las instrucciones en pantalla y disfruta de tu        │
 │       audiolibro!