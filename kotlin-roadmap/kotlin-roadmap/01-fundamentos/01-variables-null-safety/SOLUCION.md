# ✅ Solución — Variables y Null Safety

← [Volver al tema](./README.md) · [Volver al inicio](../../README.md)

---

> ⚠️ **¿Ya intentaste el reto?** Si aún no, regresa al [README](./README.md) y prueba primero.

---

## Solución

```kotlin
fun formatearUsuario(nombre: String?, apellido: String?, edad: Int?): String {
    val nombreCompleto = nombre?.let { "$it ${apellido ?: "Desconocido"}" } ?: "Usuario anónimo"
    val edadStr = edad?.let { "$it años" } ?: "edad no disponible"
    return "$nombreCompleto, $edadStr"
}

fun main() {
    println(formatearUsuario("Ana", "García", 25))   // Ana García, 25 años
    println(formatearUsuario("Ana", null, 25))        // Ana Desconocido, 25 años
    println(formatearUsuario("Ana", "García", null))  // Ana García, edad no disponible
    println(formatearUsuario(null, null, null))        // Usuario anónimo, edad no disponible
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/editor/v1?code=fun%20formatearUsuario%28nombre%3A%20String%3F%2C%20apellido%3A%20String%3F%2C%20edad%3A%20Int%3F%29%3A%20String%20%7B%0A%20%20%20%20val%20nombreCompleto%20%3D%20nombre%3F.let%20%7B%20%22%24it%20%24%7Bapellido%20%3F%3A%20%22Desconocido%22%7D%22%20%7D%20%3F%3A%20%22Usuario%20an%C3%B3nimo%22%0A%20%20%20%20val%20edadStr%20%3D%20edad%3F.let%20%7B%20%22%24it%20a%C3%B1os%22%20%7D%20%3F%3A%20%22edad%20no%20disponible%22%0A%20%20%20%20return%20%22%24nombreCompleto%2C%20%24edadStr%22%0A%7D%0A%0Afun%20main%28%29%20%7B%0A%20%20%20%20println%28formatearUsuario%28%22Ana%22%2C%20%22Garc%C3%ADa%22%2C%2025%29%29%0A%20%20%20%20println%28formatearUsuario%28%22Ana%22%2C%20null%2C%2025%29%29%0A%20%20%20%20println%28formatearUsuario%28%22Ana%22%2C%20%22Garc%C3%ADa%22%2C%20null%29%29%0A%20%20%20%20println%28formatearUsuario%28null%2C%20null%2C%20null%29%29%0A%7D)

---

## 🔍 Explicación paso a paso

### 1. `?.let { }` para transformar el nombre

```kotlin
val nombreCompleto = nombre?.let { "$it ${apellido ?: "Desconocido"}" } ?: "Usuario anónimo"
```

- `nombre?.let { }` solo ejecuta el bloque si `nombre` no es null. `it` es el valor seguro dentro del bloque.
- Dentro del bloque, `apellido ?: "Desconocido"` provee el fallback si el apellido es null.
- Si `nombre` es null, todo el `?.let` devuelve null y el `?:` final da `"Usuario anónimo"`.

### 2. `?.let { }` para formatear la edad

```kotlin
val edadStr = edad?.let { "$it años" } ?: "edad no disponible"
```

- Si `edad` tiene valor, lo convierte en `"25 años"`.
- Si `edad` es null, devuelve `"edad no disponible"`.

---

## ✏️ Resumen de operadores usados

| Operador | Para qué sirve |
|----------|----------------|
| `?:` (Elvis) | Valor por defecto cuando algo es null |
| `?.` (Safe call) | Acceder a propiedades de un nullable sin riesgo |
| `?.let { }` | Transformar un nullable en otro valor de forma segura |

---

➡️ [Siguiente tema: Control de flujo](../02-control-de-flujo/README.md) *(próximamente)*
