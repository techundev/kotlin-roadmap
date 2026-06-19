# 02 · Control de flujo

← [Volver al inicio](../../README.md) · [← Anterior](../01-variables-null-safety/variables-and-null-safety.md)

---

## 🎯 Objetivo

Aprender a controlar el comportamiento de un programa utilizando condiciones y ciclos. Este tema permite tomar decisiones y repetir acciones de manera eficiente según diferentes escenarios.

---

## 📖 ¿Qué vas a aprender?

- Utilizar expresiones `if` y `else`
- Trabajar con `when` para múltiples condiciones
- Repetir instrucciones con `for`
- Utilizar ciclos `while`
- Controlar la ejecución con condiciones y rangos

---

## 💡 Teoría y ejemplos

### Estructura `if` como expresión

En Kotlin, `if` no solo sirve para tomar decisiones, también puede devolver un valor.

```kotlin
fun main() {
    val edad = 20

    val mensaje = if (edad >= 18) {
        "Mayor de edad"
    } else {
        "Menor de edad"
    }

    println(mensaje)
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gICAgdmFsIGVkYWQgPSAyMFxuXG4gICAgdmFsIG1lbnNhamUgPSBpZiAoZWRhZCA+PSAxOCkge1xuICAgICAgICBcIk1heW9yIGRlIGVkYWRcIlxuICAgIH0gZWxzZSB7XG4gICAgICAgIFwiTWVub3IgZGUgZWRhZFwiXG4gICAgfVxuXG4gICAgcHJpbnRsbihtZW5zYWplKVxufSJ9)

### Estructura `when`
`when` reemplaza al clásico `switch` pero con capacidades mucho más potentes. Puede evaluar rangos, tipos y múltiples condiciones en una sola línea, y también funciona como expresión obligatoria si se requiere un retorno.

```kotlin
fun main() {
    val opcion = 2
    val mensaje = when (opcion) {
        1 -> "Opción 1 seleccionada"
        2 -> "Opción 2 seleccionada"
        else -> "Opción no válida"
    }
    println(mensaje)
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gICAgdmFsIG9wY2lvbiA9IDJcbiAgICB2YWwgbWVuc2FqZSA9IHdoZW4gKG9wY2lvbikge1xuICAgICAgICAxIC0+IFwiT3BjacOzbiAxIHNlbGVjY2lvbmFkYVwiXG4gICAgICAgIDIgLT4gXCJPcGNpw7NuIDIgc2VsZWNjaW9uYWRhXCJcbiAgICAgICAgZWxzZSAtPiBcIk9wY2nDs24gbm8gdsOhbGlkYVwiXG4gICAgfVxuICAgIHByaW50bG4obWVuc2FqZSlcbn0ifQ==)

### Bucles e Iteración
Kotlin simplifica la iteración mediante rangos y lambdas optimizadas. Usando funciones integradas de colecciones, podemos interactuar dinámicamente utilizando el parámetro implícito `it`.

```kotlin
fun main() {
    val nombres = listOf("Ana", "Bob", "Carlos")
    nombres.forEach { println(it) }
    
    for (i in 1..3) {
        println("Número: $i")
    }
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gICAgdmFsIG5vbWJyZXMgPSBsaXN0T2YoXCJBbmFcIiwgXCJCb2JcIiwgXCJDYXJsb3NcIilcbiAgICBub21icmVzLmZvckVhY2ggeyBwcmludGxuKGl0KSB9XG4gICAgXG4gICAgZm9yIChpIGluIDEuLjMpIHtcbiAgICAgICAgcHJpbnRsbihcIk7Dum1lcm86ICRpXCIpXG4gICAgfVxufSJ9)

### Ciclo while

`while` ejecuta un bloque mientras una condición sea verdadera.

```kotlin
fun main() {
    var contador = 1

    while (contador <= 5) {
        println(contador)
        contador++
    }
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gICAgdmFyIGNvbnRhZG9yID0gMVxuXG4gICAgd2hpbGUgKGNvbnRhZG9yIDw9IDUpIHtcbiAgICAgICAgcHJpbnRsbihjb250YWRvcilcbiAgICAgICAgY29udGFkb3IrK1xuICAgIH1cbn0ifQ==)

---

## 🏋️ Reto

Crea una función llamada `clasificarTemperatura()` que reciba una temperatura entera y devuelva:

| Temperatura | Resultado |
|------------|------------|
| Menor a 0 | Congelación |
| 0 a 15 | Frío |
| 16 a 25 | Templado |
| 26 o más | Calor |

### Casos esperados

| Entrada | Salida |
|----------|---------|
| -5 | Congelación |
| 10 | Frío |
| 20 | Templado |
| 35 | Calor |

**Reglas:**

- Debes utilizar `when`
- La función debe devolver un `String`
- No imprimas directamente dentro de la función
- Prueba al menos los cuatro casos en `main()`

```kotlin
fun clasificarTemperatura(temperatura: Int): String {
    TODO("Implementa tu solución")
}

fun main() {
    println(clasificarTemperatura(-5))
    println(clasificarTemperatura(10))
    println(clasificarTemperatura(20))
    println(clasificarTemperatura(35))
}
```

▶️ [Abrir plantilla en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gICAvKipcbiAgICAqIEFkZCB5b3VyIGNvZGUgaGVyZSEgXG4gICAgKi9cbn0ifQ==)

> 💬 Intenta resolverlo antes de ver la solución.

➡️ [Ver solución](./control-flow-solutions.md)