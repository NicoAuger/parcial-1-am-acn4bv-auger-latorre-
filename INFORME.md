# Informe Final — Aplicaciones Móviles
## Proyecto: Mis Gastos Diarios
### Comisión: ACN4BV
### Integrantes: Nicolás Auger — Javier Latorre
### Profesor: Sergio Daniel Medina
### Repositorio: [https://github.com/NicoAuger/parcial-2-am-acn4bv-auger-latorre](https://github.com/NicoAuger/parcial-2-am-acn4bv-auger-latorre-)
### Año: 2025

---

## 1. Introducción y Evolución del Proyecto

"Mis Gastos Diarios" es una aplicación móvil desarrollada en Android con Kotlin. Su propósito es permitir al usuario gestionar de forma sencilla sus gastos diarios, definiendo un presupuesto, registrando consumos y visualizando un resumen informativo.

Para esta entrega final, el proyecto ha evolucionado significativamente desde su versión del Parcial 2, migrando de un sistema de persistencia local (`SharedPreferences`) a una arquitectura robusta y conectada a la nube utilizando **Firebase Firestore**. Además, se han incorporado nuevas funcionalidades de consumo de servicios web, como la descarga de contenido de texto con **OkHttp** y la carga de imágenes remotas con **Glide**.

---

## 2. Pantallas y Funcionalidades Principales

### 2.1. Flujo de Autenticación (`LoginActivity`, `RegisterActivity`)

La aplicación mantiene su sistema de autenticación gestionado por **Firebase Authentication**, el cual es el punto de entrada al ecosistema de datos del usuario.

*   **Funcionalidad:** Permite al usuario iniciar sesión o registrarse con correo electrónico y contraseña.
*   **Rol del UID:** Una vez autenticado, el `UID` del usuario se convierte en la clave principal para todas las operaciones en la base de datos, garantizando que cada usuario acceda únicamente a su propia información.

### 2.2. `MainActivity` (Pantalla Principal)

La pantalla central ha sido refactorizada para integrar las nuevas tecnologías de backend y consumo de APIs.

1.  **Base de Datos en la Nube (Firebase Firestore):**
    *   **Sustitución de `SharedPreferences`**: Toda la persistencia de datos (presupuesto y gastos) ahora es manejada por Firestore. Esto permite que la información del usuario esté sincronizada y disponible en cualquier momento, incluso si reinstala la app.
    *   **Estructura:** Se definieron dos colecciones: `usuarios` (para guardar el presupuesto) y `gastos` (para cada registro individual, vinculado mediante el campo `userId`).
    *   **Operaciones CRUD:** La app realiza operaciones de lectura (`get`), creación (`add`) y eliminación (`delete`) de documentos en tiempo real, actualizando la UI de forma asíncrona mediante listeners (`.addOnSuccessListener`). Para optimizar la consulta de gastos por usuario y fecha, se creó un **índice compuesto** en Firestore.

2.  **Carga de Imagen Remota (Glide):**
    *   Al iniciar la pantalla, se descarga y muestra una imagen de banner desde una URL remota usando la librería **Glide**.
    *   **URL:** (https://images.unsplash.com/photo-1634733988138-bf2c3a2a13fa?q=80&w=1170&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D)

3.  **Descarga de Contenido desde URL (OkHttp):**
    *   Se ha añadido una nueva funcionalidad que muestra "tips de ahorro" dinámicos.
    *   La función `loadTipFromUrl()` utiliza **OkHttp** para realizar una petición `GET` a un archivo de texto alojado en internet (en el repositorio Git) y muestra el contenido en un `Toast`.

4.  **Lista de Gastos (`RecyclerView`):**
    *   Se mantiene el uso de `RecyclerView` por su eficiencia para mostrar listas de datos, que ahora se alimentan de la información proveniente de Firestore.

---

## 3. Tecnologías y Dependencias Clave Implementadas

1.  **Firebase Authentication:** Para registro, inicio de sesión y gestión de usuarios.
2.  **Firebase Firestore:** Como base de datos NoSQL en la nube para persistencia de datos (presupuesto y gastos).
3.  **Glide:** Para la carga eficiente de imágenes desde una URL remota.
4.  **OkHttp:** Para realizar peticiones de red y consumir APIs de texto simples.
5.  **Kotlin y Android Jetpack:** Lenguaje moderno y componentes como `RecyclerView` para construir una UI eficiente y mantenible.

---

## 4. Organización de Recursos y Diseño

El proyecto sigue las mejores prácticas de organización de recursos en Android para garantizar un código limpio:
*   **`strings.xml`**: Centraliza todos los textos de la interfaz.
*   **`colors.xml`**: Define la paleta de colores.
*   **`dimens.xml`**: Contiene valores de márgenes y tamaños para consistencia visual.
*   **`drawable`**: Incluye los íconos vectoriales.
*   **Layouts**: Se emplean `ConstraintLayout` y `LinearLayout` de forma apropiada.

---

## 5. ScreenShots UX
### CARPETA DE IMÁGENES
\print-pantallas-UX

---

## 6. Conclusión Final

El desarrollo de "Mis Gastos Diarios" ha sido un recorrido de aprendizaje práctico y sumamente valioso. La transición desde una aplicación con lógica local a una solución conectada a la nube representó el mayor desafío y, a la vez, el logro más significativo de este proyecto. Integrar el ecosistema de Firebase, especialmente Firestore, nos obligó a repensar la gestión de datos, a trabajar con operaciones asíncronas y a comprender la importancia de una arquitectura de datos bien definida desde el inicio.

La implementación de librerías como Glide y OkHttp nos permitió ir más allá de los recursos estáticos de la app, abriendo la puerta al consumo de contenido dinámico desde internet, una habilidad que consideramos fundamental en el desarrollo mobile actual. Cada nueva funcionalidad, desde la autenticación de usuarios hasta la carga de una simple imagen remota, nos ha proporcionado una comprensión más profunda de cómo las diferentes piezas del desarrollo Android moderno se conectan entre sí.

Este proyecto nos deja una base de código sólida y la confianza para abordar proyectos más complejos en el futuro. Ha sido una experiencia que nos ha llevado de la teoría a la práctica de una manera muy tangible.

----
