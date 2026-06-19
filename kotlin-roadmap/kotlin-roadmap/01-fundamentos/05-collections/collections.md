# 05 · Colecciones: List, Map, Set

← [Volver al inicio](../../README.md) · [← Anterior](../04-classes-and-objects/classes-and-objects.md)

---

## Objetivo

Aprender a almacenar y manipular grupos de datos utilizando las colecciones más utilizadas de Kotlin: List, Set y Map. Estas estructuras son fundamentales para trabajar con información en aplicaciones reales.

---

## ¿Qué vas a aprender?

- Qué son las colecciones
- Diferencia entre List, Set y Map
- Listas mutables e inmutables
- Acceso y recorrido de elementos
- Operaciones comunes sobre colecciones
- Uso de lambdas con colecciones
- Cuándo utilizar cada tipo de colección

---

## Teoría y ejemplos

### ¿Qué es una colección?

Una colección es una estructura que permite almacenar múltiples elementos en una sola variable. Kotlin proporciona varios tipos de colecciones según las necesidades de cada problema. Las más utilizadas son List, Set y Map.

```kotlin
fun main() {
    val nombres = listOf(
        "Ana",
        "Carlos",
        "Pedro"
    )

    println(nombres)
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gICAgdmFsIG5vbWJyZXMgPSBsaXN0T2YoXG4gICAgICAgIFwiQW5hXCIsXG4gICAgICAgIFwiQ2FybG9zXCIsXG4gICAgICAgIFwiUGVkcm9cIlxuICAgIClcblxuICAgIHByaW50bG4obm9tYnJlcylcbn0iLCJjb21waWxlckFyZ3VtZW50cyI6e319)

---

### List

Una List almacena elementos manteniendo el orden de inserción. Permite elementos repetidos y acceso por índice. Es la colección más utilizada cuando importa el orden de los datos.

```kotlin
fun main() {
    val frutas = listOf(
        "Manzana",
        "Banano",
        "Manzana"
    )

    println(frutas[0])
    println(frutas[2])
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gICAgdmFsIGZydXRhcyA9IGxpc3RPZihcbiAgICAgICAgXCJNYW56YW5hXCIsXG4gICAgICAgIFwiQmFuYW5vXCIsXG4gICAgICAgIFwiTWFuemFuYVwiXG4gICAgKVxuXG4gICAgcHJpbnRsbihmcnV0YXNbMF0pXG4gICAgcHJpbnRsbihmcnV0YXNbMl0pXG59IiwiY29tcGlsZXJBcmd1bWVudHMiOnt9fQ==)

---

### MutableList

Las listas creadas con listOf son de solo lectura. Si necesitas agregar o eliminar elementos debes utilizar mutableListOf.

```kotlin
fun main() {
    val numeros = mutableListOf(
        10,
        20,
        30
    )

    numeros.add(40)

    println(numeros)
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gICAgdmFsIG51bWVyb3MgPSBtdXRhYmxlTGlzdE9mKFxuICAgICAgICAxMCxcbiAgICAgICAgMjAsXG4gICAgICAgIDMwXG4gICAgKVxuXG4gICAgbnVtZXJvcy5hZGQoNDApXG5cbiAgICBwcmludGxuKG51bWVyb3MpXG59IiwiY29tcGlsZXJBcmd1bWVudHMiOnt9fQ==)

---

### Recorrer una lista

Una colección suele recorrerse utilizando un ciclo for.

```kotlin
fun main() {
    val ciudades = listOf(
        "Guatemala",
        "Antigua",
        "Xela"
    )

    //op1
    for (ciudad in ciudades) {
        println(ciudad)
    }

    //op2
    ciudades.forEach { println(it) }
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gICAgdmFsIGNpdWRhZGVzID0gbGlzdE9mKFxuICAgICAgICBcIkd1YXRlbWFsYVwiLFxuICAgICAgICBcIkFudGlndWFcIixcbiAgICAgICAgXCJYZWxhXCJcbiAgICApXG5cbiAgICAvL29wMVxuICAgIGZvciAoY2l1ZGFkIGluIGNpdWRhZGVzKSB7XG4gICAgICAgIHByaW50bG4oY2l1ZGFkKVxuICAgIH1cbiAgICBcbiAgICAvL29wMlxuICAgIGNpdWRhZGVzLmZvckVhY2ggeyBwcmludGxuKGl0KSB9XG59IiwiY29tcGlsZXJBcmd1bWVudHMiOnt9fQ==)

---

### Set

Un Set almacena elementos únicos. Si se agregan elementos repetidos, únicamente se conserva uno de ellos.

```kotlin
fun main() {
    val colores = setOf(
        "Rojo",
        "Azul",
        "Rojo",
        "Verde"
    )

    println(colores)
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gICAgdmFsIGNvbG9yZXMgPSBzZXRPZihcbiAgICAgICAgXCJSb2pvXCIsXG4gICAgICAgIFwiQXp1bFwiLFxuICAgICAgICBcIlJvam9cIixcbiAgICAgICAgXCJWZXJkZVwiXG4gICAgKVxuXG4gICAgcHJpbnRsbihjb2xvcmVzKVxufSIsImNvbXBpbGVyQXJndW1lbnRzIjp7fX0=)

---

### Map

Un Map almacena pares clave-valor. Cada clave es única y se utiliza para recuperar el valor asociado.

```kotlin
fun main() {
    val edades = mapOf(
        "Ana" to 25,
        "Carlos" to 30,
        "Pedro" to 28
    )

    println(edades["Carlos"])
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gICAgdmFsIGVkYWRlcyA9IG1hcE9mKFxuICAgICAgICBcIkFuYVwiIHRvIDI1LFxuICAgICAgICBcIkNhcmxvc1wiIHRvIDMwLFxuICAgICAgICBcIlBlZHJvXCIgdG8gMjhcbiAgICApXG5cbiAgICBwcmludGxuKGVkYWRlc1tcIkNhcmxvc1wiXSlcbn0iLCJjb21waWxlckFyZ3VtZW50cyI6e319)

---

### Operaciones con lambdas

Las colecciones funcionan muy bien junto con lambdas.

```kotlin
fun main() {
    val numeros = listOf(1, 2, 3, 4, 5)

    val pares = numeros.filter {
        it % 2 == 0
    }

    println(pares)
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gICAgdmFsIG51bWVyb3MgPSBsaXN0T2YoMSwgMiwgMywgNCwgNSlcblxuICAgIHZhbCBwYXJlcyA9IG51bWVyb3MuZmlsdGVyIHtcbiAgICAgICAgaXQgJSAyID09IDBcbiAgICB9XG5cbiAgICBwcmludGxuKHBhcmVzKVxufSIsImNvbXBpbGVyQXJndW1lbnRzIjp7fX0=)

---

## Reto

Una tienda registra las ventas de la semana utilizando una lista.

Debes crear una función llamada `generarReporteVentas()` que reciba una lista de montos y devuelva un Map con la siguiente información:

- totalVentas
- promedioVentas
- ventaMayor
- cantidadVentas

### Casos esperados

| Entrada | Resultado esperado |
|----------|----------|
| [100, 200, 300] | total=600, promedio=200, mayor=300, cantidad=3 |
| [50, 50, 50, 50] | total=200, promedio=50, mayor=50, cantidad=4 |
| [1000] | total=1000, promedio=1000, mayor=1000, cantidad=1 |
| [] | total=0, promedio=0, mayor=0, cantidad=0 |

**Reglas:**

- Debes utilizar List
- Debes devolver un Map
- Debes utilizar al menos una función de colección (`sum`, `maxOrNull`, `average`, etc.)
- No utilices variables globales
- Maneja correctamente listas vacías

```kotlin
fun generarReporteVentas(
    ventas: List<Double>
): Map<String, Double> {
    TODO("Implementar")
}

fun main() {
    println(generarReporteVentas(listOf(100.0, 200.0, 300.0)))
    println(generarReporteVentas(listOf(50.0, 50.0, 50.0, 50.0)))
    println(generarReporteVentas(listOf(1000.0)))
    println(generarReporteVentas(emptyList()))
}
```

▶️ [Abrir plantilla en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIGdlbmVyYXJSZXBvcnRlVmVudGFzKFxuICAgIHZlbnRhczogTGlzdDxEb3VibGU+XG4pOiBNYXA8U3RyaW5nLCBEb3VibGU+IHtcbiAgICBUT0RPKFwiSW1wbGVtZW50YXJcIilcbn1cblxuZnVuIG1haW4oKSB7XG4gICAgcHJpbnRsbihnZW5lcmFyUmVwb3J0ZVZlbnRhcyhsaXN0T2YoMTAwLjAsIDIwMC4wLCAzMDAuMCkpKVxuICAgIHByaW50bG4oZ2VuZXJhclJlcG9ydGVWZW50YXMobGlzdE9mKDUwLjAsIDUwLjAsIDUwLjAsIDUwLjApKSlcbiAgICBwcmludGxuKGdlbmVyYXJSZXBvcnRlVmVudGFzKGxpc3RPZigxMDAwLjApKSlcbiAgICBwcmludGxuKGdlbmVyYXJSZXBvcnRlVmVudGFzKGVtcHR5TGlzdCgpKSlcbn0iLCJjb21waWxlckFyZ3VtZW50cyI6e319)

> Intenta resolverlo antes de ver la solución.

➡️ [Ver solución](./collections-solutions.md)