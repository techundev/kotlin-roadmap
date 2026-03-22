# 01 · Variables y Null Safety

← [Volver al inicio](../../README.md)

---

## 🎯 Objetivo

Entender cómo Kotlin maneja las variables y por qué su sistema de **null safety** es una de sus características más poderosas — y lo que más lo diferencia de Java.

---

## 📖 ¿Qué vas a aprender?

- Declarar variables con `val` y `var`
- Entender los tipos de datos básicos
- Comprender qué es `null` y por qué es peligroso
- Usar tipos nullables (`String?`) con seguridad
- Aplicar los operadores `?.`, `?:` y `!!`

---

## 💡 Teoría y ejemplos

### `val` vs `var`

En Kotlin tienes dos formas de declarar variables:

```kotlin
val nombre = "Ana"   // inmutable (no se puede reasignar)
var edad = 25        // mutable (se puede cambiar)

edad = 26            // ✅ OK
nombre = "Luis"      // ❌ Error de compilación
```

> 🔑 **Regla de oro:** usa siempre `val` por defecto. Solo usa `var` cuando realmente necesites cambiar el valor.

▶️ [Ejecutar en Kotlin Playground](https://pl.kotl.in/WcteahpyY)

---

### Tipos de datos básicos

Kotlin infiere el tipo automáticamente, pero también puedes declararlo explícitamente:

```kotlin
val entero: Int = 42
val decimal: Double = 3.14
val texto: String = "Hola Kotlin"
val booleano: Boolean = true
val caracter: Char = 'K'

// Kotlin infiere el tipo sin necesidad de declararlo
val inferido = "Esto es un String"  // tipo: String
```

▶️ [Ejecutar en Kotlin Playground](https://pl.kotl.in/WcteahpyY)

---

### El problema del `null`

En Java, cualquier variable puede ser `null` sin advertencia, lo que provoca el temido `NullPointerException`. Kotlin lo resuelve a nivel de compilador.

```kotlin
// En Kotlin, por defecto las variables NO pueden ser null
var nombre: String = "Ana"
nombre = null   // ❌ Error de compilación — el compilador no lo permite
```

Para permitir `null`, debes declarar el tipo con `?`:

```kotlin
var nombre: String? = "Ana"
nombre = null   // ✅ OK porque el tipo es nullable (String?)
```

▶️ [Ejecutar en Kotlin Playground](https://pl.kotl.in/WcteahpyY)

---

### Operadores para trabajar con nullables

#### `?.` — Safe call (llamada segura)

Ejecuta la operación solo si el valor no es null. Si es null, devuelve null.

```kotlin
val nombre: String? = null
val longitud = nombre?.length   // No explota — devuelve null
println(longitud)               // null
```

#### `?:` — Elvis operator

Proporciona un valor por defecto cuando el resultado es null:

```kotlin
val nombre: String? = null
val longitud = nombre?.length ?: 0   // Si es null, usa 0
println(longitud)                     // 0

val apodo: String? = null
val display = apodo ?: "Sin apodo"
println(display)                      // "Sin apodo"
```

#### `!!` — Non-null assertion (úsalo con cuidado)

Fuerza el acceso ignorando el null. Si el valor es null, **lanza una excepción**:

```kotlin
val nombre: String? = "Ana"
val longitud = nombre!!.length   // ✅ funciona porque nombre no es null

val vacio: String? = null
val falla = vacio!!.length       // 💥 NullPointerException en tiempo de ejecución
```

> ⚠️ Evita `!!` siempre que puedas. Si lo usas mucho, estás peleando contra el sistema de tipos en lugar de aprovecharlo.

▶️ [Ejecutar en Kotlin Playground](https://pl.kotl.in/WcteahpyY)

---

### Ejemplo completo

```kotlin
fun describir(nombre: String?): String {
    val longitud = nombre?.length ?: 0
    return if (longitud > 0) {
        "El nombre '$nombre' tiene $longitud caracteres."
    } else {
        "No se proporcionó ningún nombre."
    }
}

fun main() {
    println(describir("Kotlin"))   // El nombre 'Kotlin' tiene 6 caracteres.
    println(describir(null))       // No se proporcionó ningún nombre.
    println(describir(""))         // No se proporcionó ningún nombre.
}
```

▶️ [Ejecutar en Kotlin Playground](https://pl.kotl.in/WcteahpyY)

---

## 🏋️ Reto

Crea una función llamada `formatearUsuario` que reciba tres parámetros:

- `nombre: String?`
- `apellido: String?`
- `edad: Int?`

La función debe retornar un `String` con el siguiente comportamiento:

| Caso | Resultado esperado |
|------|-------------------|
| Los tres datos completos | `"Ana García, 25 años"` |
| Sin apellido | `"Ana Desconocido, 25 años"` |
| Sin edad | `"Ana García, edad no disponible"` |
| Sin nombre ni apellido | `"Usuario anónimo, edad no disponible"` |

### Condiciones

- No puedes usar `!!` en ningún momento.
- Debes usar `?.` y `?:` donde corresponda.
- El nombre completo debe estar en formato `"Nombre Apellido"`.

### Plantilla de inicio

```kotlin
fun formatearUsuario(nombre: String?, apellido: String?, edad: Int?): String {
    // Tu código aquí
}

fun main() {
    println(formatearUsuario("Ana", "García", 25))
    println(formatearUsuario("Ana", null, 25))
    println(formatearUsuario("Ana", "García", null))
    println(formatearUsuario(null, null, null))
}
```

▶️ [Abrir plantilla en Kotlin Playground](https://pl.kotl.in/WcteahpyY)

---

> 💬 Intenta resolver el reto antes de ver la solución. No importa si tu solución es diferente a la propuesta — lo importante es que funcione y no use `!!`.

➡️ [Ver solución](./SOLUCION.md)
