# 03 · Funciones y lambdas básicas

← [Volver al inicio](../../README.md) · [← Anterior](../02-control-flow/variables-and-null-safety.md)

---

## Objetivo

Aprender a encapsular lógica reutilizable mediante funciones y a utilizar lambdas para escribir comportamientos de forma más concisa. Estos conceptos son fundamentales para escribir código limpio y reutilizable en Kotlin.

---

## ¿Qué vas a aprender?

- Declarar y utilizar funciones
- Parámetros y valores de retorno
- Expresiones de una sola línea
- Lambdas básicas
- Uso de lambdas como variables

---

## Teoría y ejemplos

### Funciones básicas


Las funciones permiten agrupar instrucciones bajo un nombre para reutilizarlas desde diferentes partes del programa.

```kotlin
fun saludar(nombre: String) {
    println("Hola, $nombre")
}

fun main() {
    saludar("Armando")
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIHNhbHVkYXIobm9tYnJlOiBTdHJpbmcpIHtcbiAgICBwcmludGxuKFwiSG9sYSwgJG5vbWJyZVwiKVxufVxuXG5mdW4gbWFpbigpIHtcbiAgICBzYWx1ZGFyKFwiQXJtYW5kb1wiKVxufSIsImNvbXBpbGVyQXJndW1lbnRzIjp7fX0=)

### Funciones con retorno

Una función puede devolver un valor utilizando un tipo de retorno.

```kotlin
fun sumar(a: Int, b: Int): Int {
    return a + b
}

fun main() {
    println(sumar(5, 3))
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIHN1bWFyKGE6IEludCwgYjogSW50KTogSW50IHtcbiAgICByZXR1cm4gYSArIGJcbn1cblxuZnVuIG1haW4oKSB7XG4gICAgcHJpbnRsbihzdW1hcig1LCAzKSlcbn0iLCJjb21waWxlckFyZ3VtZW50cyI6e319)

### Funciones de una sola expresión

Cuando una función devuelve una única expresión, Kotlin permite una sintaxis más compacta.

```kotlin
fun multiplicar(a: Int, b: Int) = a * b

fun main() {
    println(multiplicar(4, 6))
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG11bHRpcGxpY2FyKGE6IEludCwgYjogSW50KSA9IGEgKiBiXG5cbmZ1biBtYWluKCkge1xuICAgIHByaW50bG4obXVsdGlwbGljYXIoNCwgNikpXG59IiwiY29tcGlsZXJBcmd1bWVudHMiOnt9fQ==)

### Funciones con parámetros por defecto

Kotlin permite asignar valores por defecto a los parámetros de una función. Esto reduce drásticamente la necesidad de sobrecargar métodos (overloading). Además, las funciones de una sola línea pueden omitir las llaves `{}` utilizando el operador `=`.

```kotlin
fun saludar(nombre: String = "Desarrollador"): String = "¡Hola, $nombre!"

fun main() {
    println(saludar()) // Usa el valor por defecto
    println(saludar("Kotlin")) // Pasa un argumento personalizado
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIHNhbHVkYXIobm9tYnJlOiBTdHJpbmcgPSBcIkRlc2Fycm9sbGFkb3JcIik6IFN0cmluZyA9IFwiwqFIb2xhLCAkbm9tYnJlIVwiXG5cbmZ1biBtYWluKCkge1xuICAgIHByaW50bG4oc2FsdWRhcigpKSAvLyBVc2EgZWwgdmFsb3IgcG9yIGRlZmVjdG9cbiAgICBwcmludGxuKHNhbHVkYXIoXCJLb3RsaW5cIikpIC8vIFBhc2EgdW4gYXJndW1lbnRvIHBlcnNvbmFsaXphZG9cbn0iLCJjb21waWxlckFyZ3VtZW50cyI6e319)


### Lambdas básicas

Una lambda es una función anónima que puede almacenarse en una variable.

```kotlin
fun main() {
    val cuadrado = { numero: Int -> numero * numero }

    println(cuadrado(5))
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gICAgdmFsIGN1YWRyYWRvID0geyBudW1lcm86IEludCAtPiBudW1lcm8gKiBudW1lcm8gfVxuXG4gICAgcHJpbnRsbihjdWFkcmFkbyg1KSlcbn0iLCJjb21waWxlckFyZ3VtZW50cyI6e319)

### Uso de it

Cuando una lambda recibe un único parámetro, Kotlin permite usar la palabra reservada `it`.

```kotlin
fun main() {
    val numeros = listOf(1, 2, 3, 4, 5)

    val duplicados = numeros.map { it * 2 }

    println(duplicados)
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gICAgdmFsIG51bWVyb3MgPSBsaXN0T2YoMSwgMiwgMywgNCwgNSlcblxuICAgIHZhbCBkdXBsaWNhZG9zID0gbnVtZXJvcy5tYXAgeyBpdCAqIDIgfVxuXG4gICAgcHJpbnRsbihkdXBsaWNhZG9zKVxufSIsImNvbXBpbGVyQXJndW1lbnRzIjp7fX0=)

---

## Reto

Crea una función llamada `esPar()` que reciba un número entero y devuelva `true` si es par o `false` si es impar.

### Casos esperados

| Entrada | Salida |
|----------|---------|
| 2 | true |
| 5 | false |
| 10 | true |
| 11 | false |

**Reglas:**

- Debes crear una función con valor de retorno
- Debes devolver un Boolean
- No imprimas dentro de la función
- Prueba al menos los cuatro casos indicados

```kotlin
fun esPar(numero: Int): Boolean {
    TODO("Implementa tu solución")
}

fun main() {
    println(esPar(2))
    println(esPar(5))
    println(esPar(10))
    println(esPar(11))
}
```

▶️ [Abrir plantilla en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gICAvKipcbiAgICAqIEFkZCB5b3VyIGNvZGUgaGVyZSEgXG4gICAgKi9cbn0ifQ==)

> 💬 Intenta resolverlo antes de ver la solución.

➡️ [Ver solución](./functions-and-lambdas-solutions.md)