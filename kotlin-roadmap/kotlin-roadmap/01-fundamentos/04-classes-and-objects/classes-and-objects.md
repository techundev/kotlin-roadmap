# 04 · Clases, objetos y constructores

← [Volver al inicio](../../README.md) · [← Anterior](../03-functions-and-lambdas/functions-and-lambdas.md)

---

## Objetivo

Aprender a modelar información utilizando clases y objetos. Comprender cómo funcionan los constructores y cómo encapsular datos y comportamiento dentro de una misma entidad.

---

## ¿Qué vas a aprender?

- Qué es una clase
- Cómo crear objetos
- Constructores primarios
- El uso de bloques init para lógica de inicialización.
- La declaración de constructores secundarios utilizando la palabra clave constructor.
- La definición de propiedades con visibilidad básica y argumentos con valores por defecto en objetos.
- Propiedades y métodos
- Uso de `this`
- Modelado básico de entidades


## Teoría y ejemplos

### Clases y Constructor Primario
En Kotlin, el constructor primario se declara directamente en la cabecera de la clase. Las propiedades declaradas con `val` o `var` dentro del constructor primario se generan e inicializan de forma automática.

```kotlin
class Usuario(val id: Int, var nombre: String, val rol: String = "Estudiante")

fun main() {
    val usuario1 = Usuario(1, "Carlos")
    val usuario2 = Usuario(2, "Ana", "Administrador")
    println("Usuario: ${usuario1.nombre}, Rol: ${usuario1.rol}")
    println("Usuario: ${usuario2.nombre}, Rol: ${usuario2.rol}")
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuY2xhc3MgVXN1YXJpbyh2YWwgaWQ6IEludCwgdmFyIG5vbWJyZTogU3RyaW5nLCB2YWwgcm9sOiBTdHJpbmcgPSBcIkVzdHVkaWFudGVcIilcblxuZnVuIG1haW4oKSB7XG4gICAgdmFsIHVzdWFyaW8xID0gVXN1YXJpbygxLCBcIkNhcmxvc1wiKVxuICAgIHZhbCB1c3VhcmlvMiA9IFVzdWFyaW8oMiwgXCJBbmFcIiwgXCJBZG1pbmlzdHJhZG9yXCIpXG4gICAgcHJpbnRsbihcIlVzdWFyaW86ICR7dXN1YXJpbzEubm9tYnJlfSwgUm9sOiAke3VzdWFyaW8xLnJvbH1cIilcbiAgICBwcmludGxuKFwiVXN1YXJpbzogJHt1c3VhcmlvMi5ub21icmV9LCBSb2w6ICR7dXN1YXJpbzIucm9sfVwiKVxufSIsImNvbXBpbGVyQXJndW1lbnRzIjp7fX0=)

### Propiedades modificables

Las propiedades declaradas con `var` pueden cambiar su valor.

```kotlin
class Contador(
    var valor: Int
)

fun main() {
    val contador = Contador(0)

    contador.valor++

    println(contador.valor)
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuY2xhc3MgQ29udGFkb3IoXG4gICAgdmFyIHZhbG9yOiBJbnRcbilcblxuZnVuIG1haW4oKSB7XG4gICAgdmFsIGNvbnRhZG9yID0gQ29udGFkb3IoMClcblxuICAgIGNvbnRhZG9yLnZhbG9yKytcblxuICAgIHByaW50bG4oY29udGFkb3IudmFsb3IpXG59IiwiY29tcGlsZXJBcmd1bWVudHMiOnt9fQ==)

### Métodos dentro de una clase 

Las clases también pueden contener funciones. 

```kotlin
class Persona(
    val nombre: String
) {
    fun presentarse() {
        println("Hola, soy $nombre")
    }
}

fun main() {
    val persona = Persona("Carlos")
    persona.presentarse()
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuY2xhc3MgUGVyc29uYShcbiAgICB2YWwgbm9tYnJlOiBTdHJpbmdcbikge1xuICAgIGZ1biBwcmVzZW50YXJzZSgpIHtcbiAgICAgICAgcHJpbnRsbihcIkhvbGEsIHNveSAkbm9tYnJlXCIpXG4gICAgfVxufVxuXG5mdW4gbWFpbigpIHtcbiAgICB2YWwgcGVyc29uYSA9IFBlcnNvbmEoXCJDYXJsb3NcIilcbiAgICBwZXJzb25hLnByZXNlbnRhcnNlKClcbn0iLCJjb21waWxlckFyZ3VtZW50cyI6e319)

### Uso de this

La palabra clave `this` permite referirse al objeto actual.

```kotlin
class Producto(
    nombre: String
) {
    private val nombreInterno = nombre

    fun mostrarNombre() {
        println(this.nombreInterno)
    }
}

fun main() {
    val producto = Producto("Laptop")

    producto.mostrarNombre()
}
```

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuY2xhc3MgUHJvZHVjdG8oXG4gICAgbm9tYnJlOiBTdHJpbmdcbikge1xuICAgIHByaXZhdGUgdmFsIG5vbWJyZUludGVybm8gPSBub21icmVcblxuICAgIGZ1biBtb3N0cmFyTm9tYnJlKCkge1xuICAgICAgICBwcmludGxuKHRoaXMubm9tYnJlSW50ZXJubylcbiAgICB9XG59XG5cbmZ1biBtYWluKCkge1xuICAgIHZhbCBwcm9kdWN0byA9IFByb2R1Y3RvKFwiTGFwdG9wXCIpXG5cbiAgICBwcm9kdWN0by5tb3N0cmFyTm9tYnJlKClcbn0iLCJjb21waWxlckFyZ3VtZW50cyI6e319)

---

## Reto

Desarrolla una clase llamada `CuentaBancaria`.

La clase debe tener:

- Titular
- Saldo inicial

Además debe implementar los siguientes métodos:

- `depositar(monto: Double)`
- `retirar(monto: Double)`
- `obtenerSaldo(): Double`

Reglas de negocio:

- No se puede depositar un monto menor o igual a cero.
- No se puede retirar más dinero del disponible.
- Si una operación es inválida, el saldo debe permanecer igual.
- El saldo nunca puede ser negativo.

### Casos esperados

| Operación | Saldo esperado |
|------------|----------------|
| Crear cuenta con 1000 | 1000 |
| Depositar 500 | 1500 |
| Retirar 300 | 1200 |
| Retirar 2000 | 1200 |

**Reglas:**

- Debes crear una clase
- Debes utilizar un constructor
- Debes encapsular la lógica dentro de métodos
- No utilices variables globales
- Prueba los cuatro casos indicados

```kotlin
fun main() {
    val cuenta = CuentaBancaria("Ana", 1000.0)

    println(cuenta.obtenerSaldo())

    cuenta.depositar(500.0)
    println(cuenta.obtenerSaldo())

    cuenta.retirar(300.0)
    println(cuenta.obtenerSaldo())

    cuenta.retirar(2000.0)
    println(cuenta.obtenerSaldo())
}
```

▶️ [Abrir plantilla en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuZnVuIG1haW4oKSB7XG4gICAvKipcbiAgICAqIEFkZCB5b3VyIGNvZGUgaGVyZSEgXG4gICAgKi9cbn0iLCJjb21waWxlckFyZ3VtZW50cyI6e319)

> Intenta resolverlo antes de ver la solución.

➡️ [Ver solución](./classes-and-objects-solutions.md)
