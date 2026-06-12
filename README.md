# Talento Lab – Informe de QA (Proyecto Final)

![Status](https://img.shields.io/badge/status-completado-brightgreen)
![Tipo](https://img.shields.io/badge/QA-Manual-blue)
![Cobertura](https://img.shields.io/badge/cobertura-100%25-success)
![Bugs](https://img.shields.io/badge/bugs%20encontrados-4-orange)

Proyecto final del curso de QA Manual. Documentación, plan de pruebas, ejecución, defectos y análisis de responsividad sobre **[Talento Lab](https://talentolab-test.netlify.app/)**, una plataforma de búsqueda de empleo.

**Autor:** Matías De Arriba
**Contacto:** matiasdearriba10@gmail.com | [LinkedIn](https://www.linkedin.com/in/matias-de-arriba/)

---

## Índice
- [Contexto (Storytelling)](#contexto-storytelling)
- [Plan de Pruebas](#plan-de-pruebas)
- [Resultados de Ejecución](#resultados-de-ejecución)
- [Métricas del Ciclo](#métricas-del-ciclo)
- [Defectos Encontrados](#defectos-encontrados)
- [Responsividad](#responsividad)
- [Gestión de Defectos (Jira)](#gestión-de-defectos-jira)
- [Estructura del Repositorio](#estructura-del-repositorio)
- [Cómo reproducir](#cómo-reproducir)

---

## Contexto (Storytelling)

Valentina es una desarrolladora front-end de 27 años que siente haber llegado a un techo profesional en las agencias donde trabajó. Buscando un cambio, descubre **Talento Lab**, una plataforma que le permite registrarse, cargar su CV y postularse a ofertas de forma simple.

Desde QA, este escenario es la base para validar los flujos críticos del sistema: **registro, login, recuperación de contraseña y responsividad**, asegurando que la experiencia de Valentina (y la de cualquier usuario real) sea estable y sin fricciones.

## Plan de Pruebas

Detalle completo en [`Modelo Entrega Testing de MATIAS DE ARRIBA.xlsx`](./Modelo%20Entrega%20Testing%20de%20MATIAS%20DE%20ARRIBA.xlsx).

**Alcance:**
- Registro e inicio de sesión
- Recuperación de contraseña
- Responsividad general (desktop / tablet / mobile)

**Objetivos:**
- Validar que cada módulo cumpla los criterios de aceptación funcionales definidos en las User Stories.
- Verificar criterios no funcionales: tiempos de respuesta, compatibilidad y accesibilidad.
- Identificar, reproducir y documentar defectos (funcionales y de UI/UX).
- Garantizar una experiencia coherente entre dispositivos.

**Estrategia:**
- **Funcionales:** test cases positivos y negativos sobre registro, login y carga de CV.
- **No funcionales:** tiempos de carga (objetivo < 3s), compatibilidad Chrome/Firefox/Safari, comportamiento en red media.
- **Exploratorias:** registro con correos inválidos, intento de recuperación de contraseña.

## Resultados de Ejecución

5 de 5 casos planificados ejecutados → **100% de cobertura de ejecución**.

| ID | Caso | Prioridad | Resultado |
|---|---|---|---|
| CP-001 | Registro de nuevo usuario | Alta | ✅ Aprobado |
| CP-002 | Recuperación de contraseña | Alta | ❌ Fallido |
| CP-003 | Validación del campo Email | Media | ❌ Fallido |
| CP-004 | Botón "Registrarse" — tiempo de respuesta | Media | ⚠️ Aprobado con observación |
| CP-005 | Visualización en dispositivo móvil | Baja | ✅ Aprobado |

> Detalle de pasos, datos y resultado esperado/obtenido de cada caso en la hoja **Test Set** del Excel.

**Evidencia de los casos fallidos:**

<img src="./capturas/CP-002 Recuperación de contraseña si un usuario se la olvidó.jpg" width="450" alt="CP-002 - No existe botón de recuperar contraseña">
<img src="./capturas/CP-003 Validación del campo “Email” en el registro.jpg" width="450" alt="CP-003 - Email inválido sin mensaje de error">


## Métricas del Ciclo

| Métrica | Valor |
|---|---|
| Casos totales | 5 |
| Casos ejecutados | 5 |
| Casos exitosos | 2 |
| Aprobados con observación | 1 |
| Casos fallidos | 2 |
| % Éxito | 40% |
| % Fallos | 40% |
| Tiempo estimado | 50 min |
| Tiempo real | 60 min |
| % Desviación | 20% |

**Conclusión:** la cobertura funcional planificada se completó al 100%, pero el 40% de los casos detectó defectos en flujos críticos (login y validación de email). Se recomienda ampliar el set de pruebas con más escenarios negativos antes de un release.

<img src="./capturas/Cobertura de pruebas.jpg" width="500" alt="Gráfico de cobertura de pruebas">

## Defectos Encontrados

Detalle completo en la hoja **Bug Report** del Excel.

| ID | Título | Severidad | Prioridad |
|---|---|---|---|
| BUG-001 | No existe el botón "Olvidé mi contraseña" en login | Alta | Alta |
| BUG-002 | El campo Email acepta formatos inválidos (sin "@") | Media | Alta |
| BUG-003 | El botón "Enviar" del registro no responde al primer clic | Media | Media |
| BUG-004 | El diseño no se adapta correctamente en pantallas pequeñas | Baja | Baja |

BUG-001 y BUG-002 están directamente vinculados a los casos fallidos CP-002 y CP-003. BUG-003 y BUG-004 se detectaron durante las pruebas exploratorias y de responsividad.

## Responsividad

Se evaluaron 4 módulos en 3 breakpoints (1440px desktop, 768px tablet, 500px móvil), verificando criterios de aceptación específicos por dispositivo:

| Módulo | Foco de validación |
|---|---|
| Navegación principal | Menú horizontal en desktop → hamburguesa en tablet/móvil, "Carga tu CV" siempre accesible |
| Sección "Servicios" | Grid de 4 tarjetas → 2x2 en tablet → 1 por fila en móvil, sin solapamientos |
| Formulario de contacto | Campos visibles con teclado virtual activo, validación de email antes de habilitar "Enviar" |
| CTA "Carga tu CV" | Selector de archivos nativo en los 3 tamaños, solo acepta PDF/DOCX, feedback de éxito/error |

Resultado general: **Aprobado** (CP-005), sin superposición de elementos ni scroll horizontal indebido.

<img src="./capturas/tabla responsividad.jpg" width="700" alt="Tabla resumen de responsividad">
<img src="./capturas/1. Navegación principal – Móvil (500px).jpg" width="200" alt="Navegación - móvil 500px">
<img src="./capturas/2. Sección Servicios - Movil 500px.jpg" width="200" alt="Sección Servicios - móvil 500px">
<img src="./capturas/3. Formulario de contacto - Movil 500px.jpg" width="200" alt="Formulario contacto - móvil 500px">
<img src="./capturas/4. CTA Carga tu CV — Móvil (500px).jpg" width="200" alt="CTA Carga tu CV - móvil 500px">

## Gestión de Defectos (Jira)

Flujo seguido para cada defecto encontrado:

1. **Detección** durante la ejecución de los casos de prueba.
2. **Registro** en Jira: resumen, descripción, pasos para reproducir, severidad, prioridad, entorno y evidencia.
3. **Asignación** según el módulo afectado.
4. **Corrección** por parte de desarrollo, actualizando el estado del ticket.
5. **Verificación**: el tester re-ejecuta el caso relacionado; si pasa, el ticket pasa de "Testing" a "Listo".
6. **Cierre** una vez validado.

<img src="./capturas/Jira Backlog Matias.jpg" width="450" alt="Jira - Backlog">
<img src="./capturas/Jira Tablero Matias.jpg" width="450" alt="Jira - Tablero">

## Estructura del Repositorio

```
.
├── Informe QA Final Matias De Arriba.docx   # Informe narrativo completo
├── Modelo Entrega Testing de MATIAS DE ARRIBA.xlsx
│   ├── Story Telling
│   ├── Epics, Features y User Stories
│   ├── Criterios de aceptación
│   ├── Test Set            (5 casos ejecutados)
│   ├── Test Responsive      (4 módulos x 3 breakpoints)
│   ├── Bug Report           (4 defectos)
│   ├── Cobertura de Pruebas
│   └── Reporte de Ciclo de Pruebas
└── capturas/                 # Evidencia visual (.jpg) referenciada desde el Excel
```

## Cómo reproducir

1. Abrir el sitio: **https://talentolab-test.netlify.app/**
2. Seguir los pasos de cada caso en la hoja **Test Set** del Excel, en orden de prioridad (Alta → Media → Baja).
3. Comparar el resultado obtenido contra el esperado y registrar el estado.
4. Si se detecta un defecto, documentarlo siguiendo el formato de la hoja **Bug Report** y adjuntar captura en `/capturas`.
