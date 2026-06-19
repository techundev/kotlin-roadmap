# Solución — Control de flujo

← [Volver al tema](./control-flow.md) · [Volver al inicio](../../README.md)

---

> ⚠️ **¿Ya intentaste el reto?** Si aún no, regresa al [Control de flujo](./control-flow.md) y prueba primero.

---

## Solución

```kotlin
fun clasificarTemperatura(temperatura: Int): String {
    return when {
        temperatura < 0 -> "Congelación"
        temperatura <= 15 -> "Frío"
        temperatura <= 25 -> "Templado"
        else -> "Calor"
    }
}

fun main() {
    println(clasificarTemperatura(-5))
    println(clasificarTemperatura(10))
    println(clasificarTemperatura(20))
    println(clasificarTemperatura(35))
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gICAgcHJpbnRsbihjbGFzaWZpY2FyVGVtcGVyYXR1cmEoLTUpKVxuICAgIHByaW50bG4oY2xhc2lmaWNhclRlbXBlcmF0dXJhKDEwKSlcbiAgICBwcmludGxuKGNsYXNpZmljYXJUZW1wZXJhdHVyYSgyMCkpXG4gICAgcHJpbnRsbihjbGFzaWZpY2FyVGVtcGVyYXR1cmEoMzUpKVxufVxuXG5mdW4gY2xhc2lmaWNhclRlbXBlcmF0dXJhKHRlbXBlcmF0dXJhOiBJbnQpOiBTdHJpbmcge1xuICAgIHJldHVybiB3aGVuIHtcbiAgICAgICAgdGVtcGVyYXR1cmEgPCAwIC0+IFwiQ29uZ2VsYWNpw7NuXCJcbiAgICAgICAgdGVtcGVyYXR1cmEgPD0gMTUgLT4gXCJGcsOtb1wiXG4gICAgICAgIHRlbXBlcmF0dXJhIDw9IDI1IC0+IFwiVGVtcGxhZG9cIlxuICAgICAgICBlbHNlIC0+IFwiQ2Fsb3JcIlxuICAgIH1cbn1cbiIsImNvbXBpbGVyQXJndW1lbnRzIjp7fX0=)

---

## Explicación paso a paso

### 1. La función recibe un parámetro

```kotlin
fun clasificarTemperatura(temperatura: Int): String
```

Recibe un número entero y devuelve un texto con la clasificación correspondiente.

### 2. Utilizamos when

```kotlin
when {
    temperatura < 0 -> "Congelación"
    temperatura <= 15 -> "Frío"
    temperatura <= 25 -> "Templado"
    else -> "Calor"
}
```

Cada condición se evalúa de arriba hacia abajo.

Cuando una condición es verdadera, Kotlin devuelve inmediatamente el resultado asociado.

### 3. El bloque else

```kotlin
else -> "Calor"
```

Captura cualquier valor que no haya coincidido con las condiciones anteriores.

### 4. Probamos varios casos

```kotlin
println(clasificarTemperatura(-5))
println(clasificarTemperatura(10))
println(clasificarTemperatura(20))
println(clasificarTemperatura(35))
```

Esto permite verificar que todas las rutas posibles funcionan correctamente.

---

## Resumen

| Concepto | Para qué sirve |
|----------|----------------|
| if | Tomar decisiones simples |
| if como expresión | Devolver valores según una condición |
| when | Manejar múltiples casos de forma clara |
| for | Repetir acciones recorriendo rangos o colecciones |
| while | Repetir acciones mientras una condición sea verdadera |
| else | Manejar escenarios no contemplados |

---

➡️ [Siguiente tema: Funciones y lambdas](../03-functions-and-lambdas/README.md)