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

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gICAgdmFsIGVudGVybzogSW50ID0gNDJcbiAgICB2YWwgZGVjaW1hbDogRG91YmxlID0gMy4xNFxuICAgIHZhbCB0ZXh0bzogU3RyaW5nID0gXCJIb2xhIEtvdGxpblwiXG4gICAgdmFsIGJvb2xlYW5vOiBCb29sZWFuID0gdHJ1ZVxuICAgIHZhbCBpbmZlcmlkbyA9IFwiVGlwbyBpbmZlcmlkbyBhdXRvbcOhdGljYW1lbnRlXCJcbn0ifQ==)

---

### El problema del `null`

En Java cualquier variable puede ser `null` sin advertencia, provocando el temido `NullPointerException`. Kotlin lo resuelve en tiempo de compilación.

```kotlin
var nombre: String = "Ana"
nombre = null   // ❌ Error de compilación

var apodo: String? = "Ana"
apodo = null    // ✅ OK — el tipo String? permite null
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gICAgdmFyIG5vbWJyZTogU3RyaW5nID0gXCJBbmFcIlxuICAgIG5vbWJyZSA9IG51bGwgICAvLyDinYwgRXJyb3IgZGUgY29tcGlsYWNpw7NuXG5cbiAgICB2YXIgYXBvZG86IFN0cmluZz8gPSBcIkFuYVwiXG4gICAgYXBvZG8gPSBudWxsICAgIC8vIOKchSBPSyDigJQgZWwgdGlwbyBTdHJpbmc/IHBlcm1pdGUgbnVsbFxufSJ9)

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

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gXHRwcmludGxuKGRlc2NyaWJpcihcIktvdGxpblwiKSlcbiAgICBwcmludGxuKGRlc2NyaWJpcihudWxsKSlcbiAgICBwcmludGxuKGRlc2NyaWJpcihcIlwiKSlcbn1cblxuZnVuIGRlc2NyaWJpcihub21icmU6IFN0cmluZz8pOiBTdHJpbmcge1xuICAgIHZhbCBsb25naXR1ZCA9IG5vbWJyZT8ubGVuZ3RoID86IDBcbiAgICByZXR1cm4gaWYgKGxvbmdpdHVkID4gMCkge1xuICAgICAgICBcIkVsIG5vbWJyZSAnJG5vbWJyZScgdGllbmUgJGxvbmdpdHVkIGNhcmFjdGVyZXMuXCJcbiAgICB9IGVsc2Uge1xuICAgICAgICBcIk5vIHNlIHByb3BvcmNpb27DsyBuaW5nw7puIG5vbWJyZS5cIlxuICAgIH1cbn1cbiJ9)

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

▶️ [Abrir plantilla en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gICAgLyoqXG4gICAgICogQWRkIHlvdXIgY29kZSBoZXJlIVxuICAgICAqIC9cbn0ifQ==)

> 💬 Intenta resolverlo antes de ver la solución.

➡️ [Ver solución](./variables-and-null-safety-solutions.md)
