# Solución — Clases, objetos y constructores

← [Volver al inicio](../../README.md) · [Volver al tema](./classes-and-objects.md)

---

> **¿Ya intentaste el reto?** Si aún no, regresa al [reto](./classes-and-objects.md) y prueba primero.

---

## Solución

```kotlin
class CuentaBancaria(
    val titular: String,
    saldoInicial: Double
) {

    private var saldo = saldoInicial

    fun depositar(monto: Double) {
        if (monto > 0) {
            saldo += monto
        }
    }

    fun retirar(monto: Double) {
        if (monto > 0 && monto <= saldo) {
            saldo -= monto
        }
    }

    fun obtenerSaldo(): Double {
        return saldo
    }
}

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

▶️ [Ejecutar en Kotlin Playground](https://play.kotlinlang.org/#eyJ2ZXJzaW9uIjoiMi4zLjIxIiwicGxhdGZvcm0iOiJqYXZhIiwiYXJncyI6IiIsIm5vbmVNYXJrZXJzIjp0cnVlLCJ0aGVtZSI6ImlkZWEiLCJjb2RlIjoiLyoqXG4gKiBZb3UgY2FuIGVkaXQsIHJ1biwgYW5kIHNoYXJlIHRoaXMgY29kZS5cbiAqIHBsYXkua290bGlubGFuZy5vcmdcbiAqL1xuY2xhc3MgQ3VlbnRhQmFuY2FyaWEoXG4gICAgdmFsIHRpdHVsYXI6IFN0cmluZyxcbiAgICBzYWxkb0luaWNpYWw6IERvdWJsZVxuKSB7XG5cbiAgICBwcml2YXRlIHZhciBzYWxkbyA9IHNhbGRvSW5pY2lhbFxuXG4gICAgZnVuIGRlcG9zaXRhcihtb250bzogRG91YmxlKSB7XG4gICAgICAgIGlmIChtb250byA+IDApIHtcbiAgICAgICAgICAgIHNhbGRvICs9IG1vbnRvXG4gICAgICAgIH1cbiAgICB9XG5cbiAgICBmdW4gcmV0aXJhcihtb250bzogRG91YmxlKSB7XG4gICAgICAgIGlmIChtb250byA+IDAgJiYgbW9udG8gPD0gc2FsZG8pIHtcbiAgICAgICAgICAgIHNhbGRvIC09IG1vbnRvXG4gICAgICAgIH1cbiAgICB9XG5cbiAgICBmdW4gb2J0ZW5lclNhbGRvKCk6IERvdWJsZSB7XG4gICAgICAgIHJldHVybiBzYWxkb1xuICAgIH1cbn1cblxuZnVuIG1haW4oKSB7XG4gICAgdmFsIGN1ZW50YSA9IEN1ZW50YUJhbmNhcmlhKFwiQW5hXCIsIDEwMDAuMClcblxuICAgIHByaW50bG4oY3VlbnRhLm9idGVuZXJTYWxkbygpKVxuXG4gICAgY3VlbnRhLmRlcG9zaXRhcig1MDAuMClcbiAgICBwcmludGxuKGN1ZW50YS5vYnRlbmVyU2FsZG8oKSlcblxuICAgIGN1ZW50YS5yZXRpcmFyKDMwMC4wKVxuICAgIHByaW50bG4oY3VlbnRhLm9idGVuZXJTYWxkbygpKVxuXG4gICAgY3VlbnRhLnJldGlyYXIoMjAwMC4wKVxuICAgIHByaW50bG4oY3VlbnRhLm9idGVuZXJTYWxkbygpKVxufSIsImNvbXBpbGVyQXJndW1lbnRzIjp7fX0=)

## Explicación paso a paso

### Encapsulación del saldo

```kotlin
private var saldo = saldoInicial
```

El saldo es privado para evitar modificaciones directas desde fuera de la clase.

### Depósitos

```kotlin
if (monto > 0)
```

Solo se aceptan montos positivos.

### Retiros

```kotlin
if (monto > 0 && monto <= saldo)
```

Se valida que exista saldo suficiente antes de descontar dinero.

### Consulta del saldo

```kotlin
fun obtenerSaldo(): Double
```

Permite conocer el saldo actual sin exponer la variable interna.

### Beneficios del diseño

- El saldo siempre permanece consistente.
- Las reglas de negocio están centralizadas.
- Se evita modificar el saldo desde fuera de la clase.

---

## Resumen

| Concepto | Para qué sirve |
|----------|----------------|
| class | Crear nuevos tipos de datos |
| Constructor | Inicializar objetos |
| Objeto | Instancia de una clase |
| Propiedad | Almacenar estado |
| Método | Definir comportamiento |
| private | Restringir acceso |
| Encapsulación | Proteger datos internos |

---

➡️ [Siguiente tema: Colecciones](../05-collections/README.md)