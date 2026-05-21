# Requisitos Funcionales — VET-MANAGER

**Proyecto:** VET-MANAGER — Sistema de gestión veterinaria para Android  
**Versión:** 1.0  
**Fecha:** Mayo 2026  
**Clasificación:** Académico  

---

## RF-01 — Autenticación y Usuarios

| ID | Requisito | Métrica |
|---|---|---|
| RF-01 | La app debe permitir el registro de nuevos usuarios con email, contraseña (mínimo 8 caracteres) y selección de rol. | Tasa de éxito ≥ 99% |
| RF-02 | La app debe permitir el inicio de sesión con email y contraseña validando credenciales contra Supabase. | Respuesta < 2 segundos |
| RF-03 | El sistema debe soportar autenticación biométrica (huella/FaceID) en dispositivos compatibles. | Éxito ≥ 95% |
| RF-04 | El administrador debe poder crear, editar y desactivar usuarios con asignación de roles. | Operación < 1 segundo |
| RF-05 | El usuario debe poder actualizar su perfil (nombre, email, contraseña) previa validación de identidad. | Confirmación inmediata |
| RF-06 | El sistema debe cerrar sesión de forma segura invalidando tokens JWT y limpiando caché local. | Redirección a login < 1 s |
| RF-07 | La app debe mostrar listado de usuarios con búsqueda por nombre o email (solo para admin). | Filtro < 500 ms |
| RF-08 | El sistema debe registrar en logs las acciones importantes (login, creación de usuarios, eliminaciones). | Trazabilidad 100% |

---

## RF-02 — Gestión de Clientes

| ID | Requisito | Métrica |
|---|---|---|
| RF-09 | La app debe permitir registrar clientes con: nombre completo, identificación, teléfono, correo y estado. | Validación en tiempo real |
| RF-10 | El sistema debe permitir editar la información de clientes existentes. | Sincronización < 2 s |
| RF-11 | El administrador debe poder desactivar clientes sin eliminar su historial de citas y facturas. | Baja lógica |
| RF-12 | La app debe mostrar listado de clientes con búsqueda por nombre o identificación. | Filtro < 500 ms |
| RF-13 | El sistema debe almacenar clientes en SQLite local y sincronizar con Supabase en segundo plano. | Sincronización asíncrona |
| RF-14 | La app debe mostrar el detalle completo del cliente incluyendo sus pacientes asociados. | Carga < 2 segundos |
| RF-15 | El sistema debe permitir exportar lista de clientes a PDF o Excel. | Exportación < 5 segundos |

---

## RF-03 — Gestión de Pacientes

| ID | Requisito | Métrica |
|---|---|---|
| RF-16 | La app debe permitir registrar pacientes asociados a un cliente dueño con: nombre, especie, raza, edad y estado de salud. | Relación cliente-paciente 1:N |
| RF-17 | El sistema debe permitir tomar foto del paciente desde la cámara y asociarla a su perfil. | Captura < 3 segundos |
| RF-18 | Los veterinarios y administradores deben poder editar los datos de los pacientes. | Permisos por rol |
| RF-19 | La app debe mostrar historial clínico completo del paciente con filtros por fecha. | Carga < 2 segundos |
| RF-20 | El sistema debe permitir buscar pacientes por nombre, especie o cliente dueño. | Filtro < 500 ms |
| RF-21 | La app debe mostrar listado de pacientes activos e inactivos (baja lógica). | Estado visible |

---

## RF-04 — Gestión de Veterinarios

| ID | Requisito | Métrica |
|---|---|---|
| RF-22 | El administrador debe poder registrar veterinarios con: nombre, especialidad, horarios de atención y contacto. | CRUD completo |
| RF-23 | El sistema debe permitir editar la información de veterinarios existentes. | Actualización < 1 s |
| RF-24 | Los veterinarios deben aparecer en el selector de asignación de citas. | Listado en tiempo real |
| RF-25 | El sistema debe permitir asignar horarios de atención por día de la semana. | Validación de solapamiento |
| RF-26 | La app debe mostrar listado de veterinarios con filtro por especialidad. | Filtro < 500 ms |

---

## RF-05 — Gestión de Citas Médicas

| ID | Requisito | Métrica |
|---|---|---|
| RF-27 | La app debe permitir programar citas asignando: cliente, paciente, veterinario, fecha y hora. | DatePicker/TimePicker nativo |
| RF-28 | El sistema debe validar que no haya solapamiento de horario para un mismo veterinario. | Validación < 500 ms |
| RF-29 | La app debe permitir reprogramar fecha, hora o veterinario de una cita existente. | Historial de cambios |
| RF-30 | El sistema debe permitir cancelar citas registrando motivo de cancelación. | Estado "cancelada" |

---

## RF-06 — Servicios y Facturación

| ID | Requisito | Métrica |
|---|---|---|
| RF-31 | El administrador debe poder registrar servicios con: nombre, descripción, precio y duración estimada. | CRUD completo |
| RF-32 | El sistema debe permitir asignar uno o más servicios a una cita programada. | Checkboxes múltiples |
| RF-33 | Al asignar servicios, el costo total debe calcularse automáticamente. | Cálculo en tiempo real |
| RF-34 | La app debe generar factura automática al finalizar una cita con los servicios realizados. | Número único incremental |
| RF-35 | La factura debe incluir: cliente, servicios, subtotal, descuentos, IVA, total y método de pago. | Cálculo automático |
| RF-36 | El sistema debe permitir registrar pagos parciales mostrando saldo pendiente. | Campo "saldo" actualizado |
| RF-37 | La app debe permitir compartir factura como PDF por WhatsApp, email o Drive. | ShareSheet nativo |
| RF-38 | El sistema debe generar comprobante de pago con número de transacción y fecha. | Trazabilidad 100% |

---

## RF-07 — Historial Clínico

| ID | Requisito | Métrica |
|---|---|---|
| RF-39 | El veterinario debe poder registrar diagnósticos, tratamientos y observaciones en el historial del paciente. | Asociado a cita |
| RF-40 | El sistema debe permitir adjuntar fotos al historial clínico desde cámara o galería. | Subida < 5 segundos |
| RF-41 | La app debe mostrar el historial clínico completo ordenado cronológicamente. | Filtros por fecha |
| RF-42 | Solo veterinarios y administradores deben tener acceso al historial clínico. | RLS en Supabase |
| RF-43 | El sistema debe permitir imprimir o exportar el historial clínico a PDF. | Exportación < 5 s |

---

## RF-08 — Control de Inventario

| ID | Requisito | Métrica |
|---|---|---|
| RF-44 | El administrador debe poder registrar productos con: nombre, categoría, cantidad disponible y stock mínimo. | CRUD completo |
| RF-45 | El sistema debe descontar automáticamente productos usados en servicios al facturar. | Actualización en tiempo real |
| RF-46 | Si el stock baja del mínimo, el sistema debe mostrar alerta en el panel y enviar notificación. | Alerta inmediata |
| RF-47 | La app debe permitir buscar productos por nombre o categoría con SearchView. | Filtro < 300 ms |
| RF-48 | El sistema debe permitir ajuste manual de inventario (entradas/salidas) con registro de movimientos. | Trazabilidad 100% |
| RF-49 | La app debe mostrar listado de productos críticos (stock bajo) en el dashboard. | Actualización automática |

---

## RF-09 — Reportes y Estadísticas

| ID | Requisito | Métrica |
|---|---|---|
| RF-50 | El administrador debe poder generar reportes de ventas filtrados por fecha, servicio o veterinario. | Exportable a PDF/Excel |
| RF-51 | El sistema debe mostrar gráficos de ventas, citas y servicios más demandados (MPAndroidChart). | Visualización en dashboard |
| RF-52 | La app debe permitir generar reportes de citas (programadas, realizadas, canceladas) por rango de fechas. | Filtro por fecha |
| RF-53 | El sistema debe generar reportes clínicos por paciente o veterinario exportables a PDF. | Exportación < 5 s |
| RF-54 | El dashboard principal debe mostrar KPI: ingresos del día, citas hoy, productos críticos. | Actualización automática |

---

## RF-10 — Notificaciones y Offline

| ID | Requisito | Métrica |
|---|---|---|
| RF-55 | El sistema debe enviar recordatorio de cita 24 horas antes por notificación push (Firebase). | Entrega ≥ 99% |
| RF-56 | La app debe mostrar notificaciones internas (citas próximas, alertas de inventario) en un panel. | Badge en Drawer |
| RF-57 | El usuario debe poder marcar notificaciones como leídas deslizando. | Persistencia local |
| RF-58 | Al tocar una notificación, la app debe abrir la pantalla relacionada (cita, producto). | Deep linking |
| RF-59 | La app debe funcionar offline almacenando datos en SQLite (clientes, pacientes, citas). | Operación local 100% |
| RF-60 | Cuando haya conexión, el sistema debe sincronizar automáticamente cambios pendientes con Supabase. | Sincronización en segundo plano |