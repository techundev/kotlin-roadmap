# ✅ Solución — Variables y Null Safety

← [Volver al tema](./README.md) · [Volver al inicio](../../README.md)

---

> ⚠️ **¿Ya intentaste el reto?**
> Esta página contiene la solución completa. Si aún no lo intentaste, regresa al [README](./README.md) y prueba primero.

---

## Solución

```kotlin
fun formatearUsuario(nombre: String?, apellido: String?, edad: Int?): String {
    val nombreFinal = nombre ?: "Usuario anónimo"
    val apellidoFinal = apellido ?: "Desconocido"
    val edadFinal = edad?.let { "$it años" } ?: "edad no disponible"

    // Si no hay nombre, ignoramos el apellido también
    val nombreCompleto = if (nombre != null) {
        "$nombreFinal $apellidoFinal"
    } else {
        "Usuario anónimo"
    }

    return "$nombreCompleto, $edadFinal"
}

fun main() {
    println(formatearUsuario("Ana", "García", 25))   // Ana García, 25 años
    println(formatearUsuario("Ana", null, 25))        // Ana Desconocido, 25 años
    println(formatearUsuario("Ana", "García", null))  // Ana García, edad no disponible
    println(formatearUsuario(null, null, null))        // Usuario anónimo, edad no disponible
}
```

▶️ [Ejecutar en Kotlin Playground](https://pl.kotl.in/WcteahpyY)

---

## 🔍 Explicación paso a paso

### 1. Manejar el nombre y apellido con `?:`

```kotlin
val nombreFinal = nombre ?: "Usuario anónimo"
val apellidoFinal = apellido ?: "Desconocido"
```

El operador Elvis `?:` devuelve el valor de la izquierda si no es null, y el de la derecha como fallback. Es la forma más limpia de proveer valores por defecto.

### 2. Formatear la edad con `?.let`

```kotlin
val edadFinal = edad?.let { "$it años" } ?: "edad no disponible"
```

`?.let { }` ejecuta el bloque solo si `edad` no es null. Dentro del bloque, `it` es el valor no-null de `edad`. Si `edad` es null, `let` no se ejecuta y el `?:` provee el fallback.

Este patrón es muy común en Kotlin: **transforma un valor nullable en otro tipo** de forma segura.

### 3. Condición especial para el nombre

```kotlin
val nombreCompleto = if (nombre != null) {
    "$nombreFinal $apellidoFinal"
} else {
    "Usuario anónimo"
}
```

Cuando `nombre` es null, el reto pide "Usuario anónimo" sin apellido, así que evaluamos explícitamente el nombre antes de construir el nombre completo.

---

## 🔄 Variante alternativa (más compacta)

Kotlin permite escribir esto de forma aún más concisa usando una sola expresión:

```kotlin
fun formatearUsuario(nombre: String?, apellido: String?, edad: Int?): String {
    val nombreCompleto = nombre?.let { "$it ${apellido ?: "Desconocido"}" } ?: "Usuario anónimo"
    val edadStr = edad?.let { "$it años" } ?: "edad no disponible"
    return "$nombreCompleto, $edadStr"
}
```

Aquí `nombre?.let { ... }` solo se ejecuta si `nombre` no es null. Dentro del bloque, `it` es el nombre, y `apellido ?: "Desconocido"` maneja el caso nullable del apellido.

▶️ [Ejecutar variante en Kotlin Playground](https://pl.kotl.in/WcteahpyY)

---

## ✏️ ¿Qué aprendimos?

| Concepto | Cuándo usarlo |
|----------|---------------|
| `?:` (Elvis) | Proveer un valor por defecto cuando algo es null |
| `?.` (Safe call) | Acceder a propiedades/métodos de un nullable sin riesgo |
| `?.let { }` | Transformar un nullable en otro valor de forma segura |
| `if (x != null)` | Cuando necesitas lógica más compleja según si algo es null |

---

➡️ [Siguiente tema: Control de flujo](../02-control-de-flujo/README.md) *(próximamente)*
