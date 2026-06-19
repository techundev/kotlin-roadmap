# Solución — Colecciones: List, Map, Set

← [Volver al tema](./collections.md) · [Volver al inicio](../../README.md)

---

> **¿Ya intentaste el reto?** Si aún no, regresa al [reto](./collections.md) y prueba primero.

---

## Solución

```kotlin
fun generarReporteVentas(
    ventas: List<Double>
): Map<String, Double> {

    val totalVentas = ventas.sum()

    val promedioVentas = if (ventas.isNotEmpty()) {
        ventas.average()
    } else {
        0.0
    }

    val ventaMayor = ventas.maxOrNull() ?: 0.0

    val cantidadVentas = ventas.size.toDouble()

    return mapOf(
        "totalVentas" to totalVentas,
        "promedioVentas" to promedioVentas,
        "ventaMayor" to ventaMayor,
        "cantidadVentas" to cantidadVentas
    )
}

fun main() {
    println(generarReporteVentas(listOf(100.0, 200.0, 300.0)))
    println(generarReporteVentas(listOf(50.0, 50.0, 50.0, 50.0)))
    println(generarReporteVentas(listOf(1000.0)))
    println(generarReporteVentas(emptyList()))
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIGdlbmVyYXJSZXBvcnRlVmVudGFzKFxuICAgIHZlbnRhczogTGlzdDxEb3VibGU+XG4pOiBNYXA8U3RyaW5nLCBEb3VibGU+IHtcblxuICAgIHZhbCB0b3RhbFZlbnRhcyA9IHZlbnRhcy5zdW0oKVxuXG4gICAgdmFsIHByb21lZGlvVmVudGFzID0gaWYgKHZlbnRhcy5pc05vdEVtcHR5KCkpIHtcbiAgICAgICAgdmVudGFzLmF2ZXJhZ2UoKVxuICAgIH0gZWxzZSB7XG4gICAgICAgIDAuMFxuICAgIH1cblxuICAgIHZhbCB2ZW50YU1heW9yID0gdmVudGFzLm1heE9yTnVsbCgpID86IDAuMFxuXG4gICAgdmFsIGNhbnRpZGFkVmVudGFzID0gdmVudGFzLnNpemUudG9Eb3VibGUoKVxuXG4gICAgcmV0dXJuIG1hcE9mKFxuICAgICAgICBcInRvdGFsVmVudGFzXCIgdG8gdG90YWxWZW50YXMsXG4gICAgICAgIFwicHJvbWVkaW9WZW50YXNcIiB0byBwcm9tZWRpb1ZlbnRhcyxcbiAgICAgICAgXCJ2ZW50YU1heW9yXCIgdG8gdmVudGFNYXlvcixcbiAgICAgICAgXCJjYW50aWRhZFZlbnRhc1wiIHRvIGNhbnRpZGFkVmVudGFzXG4gICAgKVxufVxuXG5mdW4gbWFpbigpIHtcbiAgICBwcmludGxuKGdlbmVyYXJSZXBvcnRlVmVudGFzKGxpc3RPZigxMDAuMCwgMjAwLjAsIDMwMC4wKSkpXG4gICAgcHJpbnRsbihnZW5lcmFyUmVwb3J0ZVZlbnRhcyhsaXN0T2YoNTAuMCwgNTAuMCwgNTAuMCwgNTAuMCkpKVxuICAgIHByaW50bG4oZ2VuZXJhclJlcG9ydGVWZW50YXMobGlzdE9mKDEwMDAuMCkpKVxuICAgIHByaW50bG4oZ2VuZXJhclJlcG9ydGVWZW50YXMoZW1wdHlMaXN0KCkpKVxufSIsImNvbXBpbGVyQXJndW1lbnRzIjp7fX0=)

---

## Explicación paso a paso

### 1. Calcular el total de ventas

```kotlin
val totalVentas = ventas.sum()
```

La función `sum()` recorre todos los elementos de la lista y devuelve la suma total de los valores.

Ejemplo:

```kotlin
listOf(100.0, 200.0, 300.0).sum()
```

Resultado:

```text
600.0
```

---

### 2. Calcular el promedio

```kotlin
val promedioVentas = if (ventas.isNotEmpty()) {
    ventas.average()
} else {
    0.0
}
```

La función `average()` calcula el promedio de todos los elementos.

Antes de llamarla verificamos que la lista no esté vacía para evitar resultados inesperados.

Ejemplo:

```kotlin
listOf(100.0, 200.0, 300.0).average()
```

Resultado:

```text
200.0
```

---

### 3. Obtener la venta más alta

```kotlin
val ventaMayor = ventas.maxOrNull() ?: 0.0
```

La función `maxOrNull()` devuelve el valor más grande de la colección.

Si la lista está vacía, devuelve `null`, por lo que usamos el operador Elvis (`?:`) para retornar `0.0`.

Ejemplo:

```kotlin
listOf(100.0, 200.0, 300.0).maxOrNull()
```

Resultado:

```text
300.0
```

---

### 4. Obtener la cantidad de ventas

```kotlin
val cantidadVentas = ventas.size.toDouble()
```

La propiedad `size` devuelve la cantidad de elementos de la lista.

Se convierte a `Double` porque todos los valores almacenados en el `Map` son de tipo `Double`.

Ejemplo:

```kotlin
listOf(100.0, 200.0, 300.0).size
```

Resultado:

```text
3
```

---

### 5. Construir el reporte

```kotlin
return mapOf(
    "totalVentas" to totalVentas,
    "promedioVentas" to promedioVentas,
    "ventaMayor" to ventaMayor,
    "cantidadVentas" to cantidadVentas
)
```

`mapOf()` crea un `Map` utilizando pares clave-valor.

Cada clave representa una métrica del reporte y cada valor contiene el resultado calculado.

---

## Resultado de las pruebas

```text
{totalVentas=600.0, promedioVentas=200.0, ventaMayor=300.0, cantidadVentas=3.0}

{totalVentas=200.0, promedioVentas=50.0, ventaMayor=50.0, cantidadVentas=4.0}

{totalVentas=1000.0, promedioVentas=1000.0, ventaMayor=1000.0, cantidadVentas=1.0}

{totalVentas=0.0, promedioVentas=0.0, ventaMayor=0.0, cantidadVentas=0.0}
```

---

## Resumen

| Concepto | Para qué sirve |
|----------|----------------|
| List | Almacenar una colección ordenada de elementos |
| sum() | Obtener la suma de todos los valores |
| average() | Calcular el promedio de una colección numérica |
| maxOrNull() | Obtener el valor más alto de una colección |
| size | Obtener la cantidad de elementos |
| Map | Almacenar información en pares clave-valor |
| ?: | Proporcionar un valor por defecto cuando el resultado es null |

---

➡️ [Siguiente tema: Programación Orientada a Objetos](../../etapa-02-poo/object-oriented-programming/README.md)