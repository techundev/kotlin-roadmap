# Solución — Funciones y lambdas básicas

← [Volver al tema](./functions-and-lambdas.md) · [Volver al inicio](../../README.md)

---

> **¿Ya intentaste el reto?** Si aún no, regresa al [Funciones y lambdas básicas](./functions-and-lambdas.md) y prueba primero.

---

## Solución

```kotlin
fun esPar(numero: Int): Boolean {
    return numero % 2 == 0
}

fun main() {
    println(esPar(2))
    println(esPar(5))
    println(esPar(10))
    println(esPar(11))
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIGVzUGFyKG51bWVybzogSW50KTogQm9vbGVhbiB7XG4gICAgcmV0dXJuIG51bWVybyAlIDIgPT0gMFxufVxuXG5mdW4gbWFpbigpIHtcbiAgICBwcmludGxuKGVzUGFyKDIpKVxuICAgIHByaW50bG4oZXNQYXIoNSkpXG4gICAgcHJpbnRsbihlc1BhcigxMCkpXG4gICAgcHJpbnRsbihlc1BhcigxMSkpXG59IiwiY29tcGlsZXJBcmd1bWVudHMiOnt9fQ==)

---

## Explicación paso a paso

### 1. Recibir el número

```kotlin
fun esPar(numero: Int): Boolean
```

La función recibe un entero y devuelve un valor booleano.

### 2. Utilizar el operador módulo

```kotlin
numero % 2
```

El operador `%` devuelve el residuo de una división.

### 3. Verificar si el residuo es cero

```kotlin
numero % 2 == 0
```

Si el residuo es cero significa que el número es divisible entre dos y por lo tanto es par.

### 4. Retornar el resultado

```kotlin
return numero % 2 == 0
```

La expresión ya produce un `Boolean`, por lo que puede retornarse directamente.

---

## Resumen

| Concepto | Para qué sirve |
|----------|----------------|
| fun | Declarar funciones |
| Parámetros | Recibir datos de entrada |
| return | Devolver resultados |
| Funciones de expresión | Simplificar funciones cortas |
| Lambda | Crear funciones anónimas |
| it | Referirse al único parámetro de una lambda |

---

➡️ [Siguiente tema: Clases y objetos](../04-classes-and-objects/README.md)