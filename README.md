# Pipeline de Calidad – Proyecto de Gestión de Usuarios

Este repositorio implementa un pipeline de **Integración Continua (CI)** utilizando  
**GitHub Actions** y permite ejecutarlo localmente con **nektos/act**.  
Incluye:

- Linter obligatorio (Checkstyle + Super-Linter)
- Pruebas unitarias (JUnit 5)
- Reporte de cobertura (JaCoCo)
- Validación automática de umbral mínimo de cobertura
- Proceso de compilación con Maven
- Ejecución local del mismo pipeline mediante `act`

---

## 🧩 Parte 1 – Estrategia

### 1. Diferencia entre CI y CD
- **CI (Integración Continua)**: cada cambio enviado al repositorio se integra automáticamente y se valida con linters, pruebas, build y cobertura. Trabaja sobre la calidad del código.
- **CD (Entrega/Despliegue Continuo)**: automatiza el despliegue del software después de pasar CI. Puede desplegar en un servidor, contenedor o nube.

En este parcial solo se implementa CI.

### 2. Lenguaje, linter y herramienta de cobertura

- **Lenguaje:** Java 17  
  Justificación: es el lenguaje usado en clase, tiene integración nativa con Maven y herramientas maduras para pruebas y cobertura.

- **Linter:**  
  - *Checkstyle:* valida estilo y convenciones.  
  - *Super-Linter (modo Java y otros archivos):* verifica errores comunes de sintaxis y estilo en todo el repositorio.

- **Cobertura:**  
  - *JaCoCo:* plugin estándar en Maven, genera reportes en `target/site/jacoco`.

### 3. Umbral mínimo de cobertura

El umbral definido es **90% de cobertura de líneas**.  
Justificación: garantiza que la mayoría del código está cubierto por pruebas, sin ser un valor tan alto que bloquee el proyecto.

---

## 🧩 Parte 2 – Workflow CI/CD

El archivo del pipeline es:

