# Parcial 2 — Aplicaciones Móviles  
## Proyecto: Mis Gastos Diarios  
### Comisión: ACN4BV  
### Integrantes: Nicolás Auger — Javier Latorre  
### Profesor: Sergio Daniel Medina  
### Año: 2025  

---

## 1. Introducción

Mis Gastos Diarios es una aplicación mobile desarrollada en Android con Kotlin. Su propósito es permitir al usuario gestionar de forma sencilla sus gastos diarios, definiendo un presupuesto, registrando consumos y visualizando un resumen informativo tanto a nivel diario como mensual.

La aplicación implementa múltiples pantallas, navegación entre actividades, Firebase Authentication, persistencia de datos, recursos organizados y un comportamiento dinámico que cumple con los requisitos establecidos para el Parcial 2 de la materia.

---

## 2. Pantallas de la Aplicación

### 2.1. LoginActivity

Función principal:
Permite al usuario iniciar sesión o crear una cuenta mediante Firebase Authentication.

Elementos:
- Campo de correo electrónico
- Campo de contraseña
- Botón para iniciar sesión
- Botón para crear una cuenta

Flujo general:
- Si las credenciales son válidas, se accede a MainActivity.
- Si el registro es exitoso, el usuario inicia sesión automáticamente.
- Si ocurre un error, se muestra un mensaje descriptivo.

---

### 2.2. MainActivity (Pantalla Principal)

Es la pantalla central del sistema. Sus funcionalidades principales incluyen:

1. Presupuesto diario
   El usuario define un presupuesto que habilita la carga de gastos.
   El valor se almacena mediante SharedPreferences.

2. Registro de gastos
   El usuario puede registrar un gasto ingresando monto, categoría y nota opcional.
   Al agregar un gasto:
   - Se actualiza la lista dinámica.
   - Se recalculan Presupuesto, Gastado y Restante.
   - Se actualiza el gráfico de categorías.

3. Lista dinámica de gastos (RecyclerView)
   Cada ítem muestra:
   - Ícono de categoría
   - Monto
   - Nota
   - Botón para eliminar
   Además, los ítems permiten abrir su detalle.

4. Gráfico por categoría
   Construido dinámicamente. Representa la distribución del gasto por categoría en base al presupuesto ingresado.

5. Menú flotante (FAB)
   Opciones disponibles:
   - Limpiar todos los gastos
   - Recalcular totales
   - Acceder al resumen mensual
   - Cerrar sesión

---

### 2.3. ExpenseDetailActivity

Presenta la información detallada de un gasto seleccionado.

Datos mostrados:
- Categoría
- Monto
- Nota (o "Sin nota" cuando está vacía)

Acciones disponibles:
- Editar el gasto mediante un cuadro de diálogo
- Eliminar el gasto
- Volver sin realizar cambios

Resultados:
Devuelve a MainActivity si el gasto fue editado, eliminado o si no hubo modificaciones.

---

### 2.4. MonthlySummaryActivity

Pantalla destinada al resumen mensual.

Funcionamiento:
- La aplicación guarda automáticamente el presupuesto, el total gastado y el saldo al cambiar el día.
- Los datos se almacenan en SharedPreferences.
- La pantalla muestra una lista con:
  - Fecha
  - Presupuesto del día
  - Total gastado
  - Saldo resultante 
- El día actual se identifica como "Activo".

---

## 3. Comportamiento Dinámico Implementado

1. Lista de gastos dinámica
   La lista se actualiza en tiempo real al agregar, editar o eliminar gastos.

2. Recalculado automático
   El presupuesto, el total gastado, el saldo restante y los colores de advertencia se actualizan inmediatamente al modificar la información.

3. Gráfico generado por código
   Las barras del gráfico se crean en tiempo de ejecución en función del porcentaje asignado a cada categoría.

4. Persistencia diaria automatizada
   La aplicación registra automáticamente los datos del día anterior al detectar un cambio de fecha.

5. Navegación entre pantallas
   Login → Main → Detalle → Resumen mensual → Logout

---

## 4. Firebase Authentication

Se utiliza Firebase Auth para:
- Registro de nuevas cuentas
- Inicio de sesión
- Manejo de sesiones persistentes
- Cierre de sesión

Esta integración cumple con uno de los requisitos opcionales del Parcial 2.

---

## 5. Organización de Recursos y Diseño

- strings.xml centraliza todos los textos.
- colors.xml define la paleta de colores, incluyendo colores asociados a categorías.
- dimens.xml contiene márgenes, tamaños y espaciados utilizados en la interfaz.
- drawable incluye los íconos correspondientes a cada categoría.
- Los layouts emplean ConstraintLayout y LinearLayout según lo requerido.

---

## 6. Conclusión

Mis Gastos Diarios cumple con los requerimientos del Parcial 2: manejo de múltiples pantallas, navegación entre actividades, uso obligatorio de layouts, comportamiento dinámico, recursos organizados, imágenes, persistencia interna y autenticación con Firebase.

Las mejoras proyectadas, tales como la carga de imágenes desde URL y contenido dinámico obtenido desde la web, permiten ampliar el alcance del proyecto y sumar valor dentro de los criterios opcionales del parcial.

---
