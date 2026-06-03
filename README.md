App replica del Banco Pichincha - Pantalla de inicio
Esta es una réplica de la pantalla de inicio de la app del Banco Pichincha, desarrollada en Android con XML y ConstraintLayout. El objetivo fue practicar la creación de interfaces fieles a un diseño real, usando animaciones con Lottie, organización de elementos en pantalla y personalización de íconos mediante tint.

¿Qué tiene la app?
Animación de bienvenida: Implementada con LottieAnimationView. El archivo JSON se encuentra en res/raw/banco_animation.json. Se configura para que se reproduzca automáticamente y en loop (app:lottie_autoPlay="true" y app:lottie_loop="true").

Logo y título: Un ImageView con el logo del banco y un TextView con el nombre “BANCO PICHINCHA” en mayúsculas, color #192e63 y fuente personalizada prelo_book. Ambos están centrados respecto a la animación.

Mensaje de seguridad: Un TextView que dice “Cuida tus contraseñas, no las compartas con nadie.”, ubicado justo debajo de la animación.

Dos filas de botones con íconos y texto:

Primera fila: “Usuario y contraseña”, “Huella / Face ID”, “Pin de 6 dígitos”. Íconos en color #192E63.

Segunda fila: “Ubicanos”, “Clave digital”, “Llámanos”. Íconos en color #3e79a7 (azul más claro) para diferenciar visualmente los servicios.

Diseño centrado y adaptable: El layout principal es un ConstraintLayout que ancla los elementos entre sí y a los bordes de la pantalla. Cada fila de botones es un LinearLayout horizontal con layout_weight="1" en cada columna, lo que distribuye el ancho equitativamente. Los tamaños de los botones están en dp (64x64) para mantener consistencia en diferentes densidades de pantalla.

Capturas de pantalla
(acá van tus imágenes, por ejemplo:)

https://screenshots/home_screen.png

¿Cómo se ve por dentro? (código)
El archivo activity_main.xml contiene toda la interfaz. A continuación se explica la estructura principal:

ConstraintLayout como contenedor raíz. Permite posicionar la animación, el logo, el título y el mensaje con restricciones relativas (layout_constraintTop_toBottomOf, etc.).

LottieAnimationView ocupa un ancho de 346dp y alto 273dp, centrado tanto horizontal como verticalmente con un sesgo (vertical_bias="0.209") para dejarlo ligeramente más arriba.

Las filas de botones están fuera del ConstraintLayout solo en apariencia; en realidad están ancladas entre sí y al mensaje de texto y al fondo.
Cada botón se compone de un ImageButton (sin fondo, con scaleType="fitCenter" y padding="0" para que el ícono se muestre completo) y un TextView debajo.
Los íconos son vectores (drawables XML) y se les aplica color mediante app:tint, lo que evita tener múltiples versiones del mismo ícono.

Fragmento de ejemplo para un botón de la primera fila:

xml
<LinearLayout
    android:layout_width="0dp"
    android:layout_weight="1"
    android:gravity="center_horizontal"
    android:orientation="vertical">

    <ImageButton
        android:layout_width="64dp"
        android:layout_height="64dp"
        android:background="@android:color/transparent"
        android:scaleType="fitCenter"
        app:srcCompat="@drawable/persona"
        app:tint="#192E63" />

    <TextView
        android:text="Usuario y contraseña"
        android:textColor="#192E63"
        ... />
</LinearLayout>
Para la segunda fila solo cambia el app:tint y el color del texto a #3e79a7.

Recursos necesarios (además del código)
Fuente: prelo_book.ttf en res/font/.

Animación Lottie: Archivo JSON en res/raw/banco_animation.json.

Drawables: Vectores o imágenes PNG para persona, huella, pin, ubicacion, llave y telefono en res/drawable/.

Dependencia en build.gradle (nivel app):

gradle
implementation 'com.airbnb.android:lottie:6.0.0'
¿Cómo se prueba?
Se importa el proyecto en Android Studio.

Se colocan los recursos en las carpetas correspondientes.

Se compila y se ejecuta en un dispositivo o emulador (API 21+).

Con esto se obtiene una pantalla inicial casi idéntica a la referencia, funcional en cuanto a diseño y animación. Los botones aún no tienen acciones (solo interfaz), pero se pueden agregar OnClickListener en la Activity.
