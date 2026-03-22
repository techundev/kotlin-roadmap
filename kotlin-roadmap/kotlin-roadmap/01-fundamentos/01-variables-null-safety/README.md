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

```kotlin
val nombre = "Ana"   // inmutable (no se puede reasignar)
var edad = 25        // mutable (se puede cambiar)

edad = 26            // ✅ OK
nombre = "Luis"      // ❌ Error de compilación
```

> 🔑 **Regla de oro:** usa siempre `val` por defecto. Solo usa `var` cuando realmente necesites cambiar el valor.

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIwIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gIHZhbCBub21icmUgPSBcIkFuYVwiICAgLy8gaW5tdXRhYmxlIChubyBzZSBwdWVkZSByZWFzaWduYXIpXG4gIHZhciBlZGFkID0gMjUgICAgICAgIC8vIG11dGFibGUgKHNlIHB1ZWRlIGNhbWJpYXIpXG5cbiAgZWRhZCA9IDI2ICAgICAgICAgICAgLy8g4pyFIE9LXG4gIG5vbWJyZSA9IFwiTHVpc1wiICAgICAgLy8g4p2MIEVycm9yIGRlIGNvbXBpbGFjacOzblxufSJ9)

---

### Tipos de datos básicos

```kotlin
val entero: Int = 42
val decimal: Double = 3.14
val texto: String = "Hola Kotlin"
val booleano: Boolean = true
val inferido = "Tipo inferido automáticamente"
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/editor/v1?code=fun%20main%28%29%20%7B%0A%20%20%20%20val%20entero%3A%20Int%20%3D%2042%0A%20%20%20%20val%20decimal%3A%20Double%20%3D%203.14%0A%20%20%20%20val%20texto%3A%20String%20%3D%20%22Hola%20Kotlin%22%0A%20%20%20%20val%20booleano%3A%20Boolean%20%3D%20true%0A%20%20%20%20val%20inferido%20%3D%20%22Tipo%20inferido%22%0A%20%20%20%20println%28%22%24entero%2C%20%24decimal%2C%20%24texto%2C%20%24booleano%2C%20%24inferido%22%29%0A%7D)

---

### El problema del `null`

En Java cualquier variable puede ser `null` sin advertencia, provocando el temido `NullPointerException`. Kotlin lo resuelve en tiempo de compilación.

```kotlin
var nombre: String = "Ana"
nombre = null   // ❌ Error de compilación

var apodo: String? = "Ana"
apodo = null    // ✅ OK — el tipo String? permite null
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/editor/v1?code=fun%20main%28%29%20%7B%0A%20%20%20%20var%20nombre%3A%20String%3F%20%3D%20%22Ana%22%0A%20%20%20%20println%28nombre%3F.length%29%0A%20%20%20%20nombre%20%3D%20null%0A%20%20%20%20println%28nombre%3F.length%29%0A%20%20%20%20println%28nombre%3F.length%20%3F%3A%200%29%0A%7D)

---

### Operadores para nullables

#### `?.` — Safe call
Ejecuta la operación solo si el valor no es null, si no devuelve null:
```kotlin
val nombre: String? = null
println(nombre?.length)   // null — no explota
```

#### `?:` — Elvis operator
Valor por defecto cuando el resultado es null:
```kotlin
val longitud = nombre?.length ?: 0    // 0 si nombre es null
val display  = nombre ?: "Sin nombre" // fallback de texto
```

#### `!!` — Non-null assertion
Fuerza el acceso; lanza excepción si es null. **Úsalo lo menos posible:**
```kotlin
val nombre: String? = "Ana"
println(nombre!!.length)  // ✅ funciona

val vacio: String? = null
println(vacio!!.length)   // 💥 NullPointerException
```

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
    println(describir("Kotlin"))
    println(describir(null))
    println(describir(""))
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/editor/v1?code=fun%20describir%28nombre%3A%20String%3F%29%3A%20String%20%7B%0A%20%20%20%20val%20longitud%20%3D%20nombre%3F.length%20%3F%3A%200%0A%20%20%20%20return%20if%20%28longitud%20%3E%200%29%20%7B%0A%20%20%20%20%20%20%20%20%22El%20nombre%20%27%24nombre%27%20tiene%20%24longitud%20caracteres.%22%0A%20%20%20%20%7D%20else%20%7B%0A%20%20%20%20%20%20%20%20%22No%20se%20proporcion%C3%B3%20ning%C3%BAn%20nombre.%22%0A%20%20%20%20%7D%0A%7D%0A%0Afun%20main%28%29%20%7B%0A%20%20%20%20println%28describir%28%22Kotlin%22%29%29%0A%20%20%20%20println%28describir%28null%29%29%0A%20%20%20%20println%28describir%28%22%22%29%29%0A%7D)

---

## 🏋️ Reto

Crea una función `formatearUsuario` que reciba:

- `nombre: String?`
- `apellido: String?`
- `edad: Int?`

| Caso | Resultado esperado |
|------|-------------------|
| Los tres datos completos | `"Ana García, 25 años"` |
| Sin apellido | `"Ana Desconocido, 25 años"` |
| Sin edad | `"Ana García, edad no disponible"` |
| Sin nombre ni apellido | `"Usuario anónimo, edad no disponible"` |

**Reglas:** no puedes usar `!!` en ningún momento.

▶️ [Abrir plantilla en Kotlin Playground](https://play.kotlinlang.org/editor/v1?code=fun%20formatearUsuario%28nombre%3A%20String%3F%2C%20apellido%3A%20String%3F%2C%20edad%3A%20Int%3F%29%3A%20String%20%7B%0A%20%20%20%20//%20Tu%20c%C3%B3digo%20aqu%C3%AD%0A%20%20%20%20return%20%22%22%0A%7D%0A%0Afun%20main%28%29%20%7B%0A%20%20%20%20println%28formatearUsuario%28%22Ana%22%2C%20%22Garc%C3%ADa%22%2C%2025%29%29%0A%20%20%20%20println%28formatearUsuario%28%22Ana%22%2C%20null%2C%2025%29%29%0A%20%20%20%20println%28formatearUsuario%28%22Ana%22%2C%20%22Garc%C3%ADa%22%2C%20null%29%29%0A%20%20%20%20println%28formatearUsuario%28null%2C%20null%2C%20null%29%29%0A%7D)

> 💬 Intenta resolverlo antes de ver la solución.

➡️ [Ver solución](./SOLUCION.md)
