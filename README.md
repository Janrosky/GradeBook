# 📚 GradeBook

Sistema de calificaciones para profesores. Gestión completa de semestres, materias, alumnos y notas — sin backend, sin cuentas, corre directo en el navegador.

## ¿Qué hace?

Permite al profesor estructurar sus materias por semestre, registrar alumnos, ingresar calificaciones y calcular automáticamente qué nota necesita cada alumno en los entregables pendientes para aprobar.

## Módulos

### 🗓 Semestres
- Varios semestres guardados, uno activo a la vez
- Switcheable desde el sidebar sin perder datos
- Todos los datos (materias, alumnos, notas) están aislados por semestre

### 📖 Materias
- Nombre, código identificador y color visual por materia
- Entregables personalizados: el profesor define cuántos quiere, cómo se llaman (Examen, Tarea, Proyecto, Quiz, etc.) y cuánto vale cada uno
- Validación en tiempo real de que los porcentajes sumen exactamente 100%
- Vista expandible por materia

### 👥 Alumnos
- Nombre completo, carné/ID, correo y grupo
- Vista de detalle por alumno: todas sus notas, aporte por entregable y cálculo de qué necesita para pasar en cada materia
- Editable en cualquier momento

### ✏️ Calificaciones
- Tabla cruzada alumno × entregable por materia
- Ingreso directo en celda — sin modales, sin clics extra
- Celdas se colorean en verde (≥ 70) o rojo (< 70) al instante
- Columna **"Para pasar"** se actualiza en tiempo real mostrando cuánto necesita sacar en el porcentaje pendiente para alcanzar el 70

### 📊 Reportes
- Estadísticas del grupo: promedio general, cantidad de aprobados y reprobados
- Tabla completa con nota por entregable, promedio final, estado y nota necesaria para pasar
- **Exportar PDF** (orientación horizontal, con colores por estado)
- **Imprimir** directamente desde el navegador

### 🏠 Dashboard
- Resumen del semestre activo
- Contador de notas pendientes por ingresar
- Lista de entregables con alumnos sin calificar

## Lógica de aprobación

La nota mínima para aprobar es **70 de 100**.

El cálculo de "para pasar" funciona así:

```
nota_actual = Σ (nota_obtenida × peso_entregable / 100)
porcentaje_restante = Σ pesos de entregables sin nota
nota_necesaria = (70 - nota_actual) / (porcentaje_restante / 100)
```

Si `nota_necesaria > 100` → es matemáticamente imposible aprobar.
Si `nota_necesaria ≤ 0` → el alumno ya tiene asegurado pasar.

## Stack

HTML · CSS · JavaScript vanilla · [jsPDF](https://github.com/parallax/jsPDF) · [jsPDF-AutoTable](https://github.com/simonbengtsson/jsPDF-AutoTable) — sin dependencias propias, sin build, sin backend.

## Persistencia

Todo se guarda en `localStorage` del navegador. Los datos persisten aunque cerrés el navegador o reiniciés el equipo. No hay sincronización entre dispositivos ni entre navegadores.

## Uso

Abrí `index.html` en cualquier navegador moderno. No necesita servidor ni instalación.

## Autor

Hecho para uso personal por **Janrosky** 🇨🇷 · Cartago, Costa Rica
