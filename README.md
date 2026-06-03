# App réplica del Banco Pichincha - Pantalla de inicio

Esta es una réplica de la pantalla de inicio de la app del Banco Pichincha, desarrollada en Android con XML y `ConstraintLayout`.  
El objetivo fue practicar la creación de interfaces fieles a un diseño real, usando animaciones con Lottie, organización de elementos en pantalla y personalización de íconos mediante `tint`.

---

## ¿Qué tiene la app?

- **Animación de bienvenida**  
  Implementada con `LottieAnimationView`. El archivo JSON se encuentra en `res/raw/banco_animation.json`.  
  Se configura para que se reproduzca automáticamente y en loop (`app:lottie_autoPlay="true"` y `app:lottie_loop="true"`).

- **Logo y título**  
  Un `ImageView` con el logo del banco y un `TextView` con el nombre “BANCO PICHINCHA” en mayúsculas, color `#192e63` y fuente personalizada `prelo_book`. Ambos están centrados respecto a la animación.

- **Mensaje de seguridad**  
  Un `TextView` que dice “Cuida tus contraseñas, no las compartas con nadie.”, ubicado justo debajo de la animación.

- **Dos filas de botones con íconos y texto**  
  - **Primera fila**: “Usuario y contraseña”, “Huella / Face ID”, “Pin de 6 dígitos”. Íconos en color `#192E63`.  
  - **Segunda fila**: “Ubicanos”, “Clave digital”, “Llámanos”. Íconos en color `#3e79a7` (azul más claro) para diferenciar visualmente los servicios.

- **Diseño centrado y adaptable**  
  El layout principal es un `ConstraintLayout` que ancla los elementos entre sí y a los bordes de la pantalla.  
  Cada fila de botones es un `LinearLayout` horizontal con `layout_weight="1"` en cada columna, lo que distribuye el ancho equitativamente.  
  Los tamaños de los botones están en `dp` (64x64) para mantener consistencia en diferentes densidades de pantalla.

---

## Capturas de pantalla

<img width="720" height="1600" alt="image" src="https://github.com/user-attachments/assets/d633f740-47b3-476c-9250-7f0cab961164" />

---

## ¿Cómo se ve por dentro? (código)

El archivo `activity_main.xml` contiene toda la interfaz. A continuación se explica la estructura principal:

- **`ConstraintLayout`** como contenedor raíz. Permite posicionar la animación, el logo, el título y el mensaje con restricciones relativas (`layout_constraintTop_toBottomOf`, etc.).
- **`LottieAnimationView`** ocupa 346dp x 273dp, centrada con un `vertical_bias="0.209"` para dejarla un poco más arriba.
- **Las filas de botones** son `LinearLayout` horizontales con `layout_weight="1"` para repartir el espacio. Cada botón es un `ImageButton` (64x64dp, sin fondo, `scaleType="fitCenter"`) con un `TextView` debajo.  
  Los íconos son vectores y se les aplica color mediante `app:tint`, evitando duplicar recursos.

Ejemplo de un botón de la primera fila:

```xml
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
