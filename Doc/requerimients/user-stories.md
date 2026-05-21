# Épica 1 — Autenticación y Gestión de Usuarios

## HU-001 — Registro de Clientes

Como recepcionista o administrador,
quiero registrar nuevos clientes desde la app previa autenticación,
para asociar correctamente pacientes y citas.

### Criterios de aceptación:

- [ ] La pantalla de registro valida nombre, identificación, teléfono, correo y estado del cliente.
- [ ] Los datos se guardan localmente con SQLite y se sincronizan con Supabase cuando hay conexión.
- [ ] Se muestra un mensaje de éxito con animación nativa de Android.

**Estimación:** M (Media)
**Módulo:** auth/, clients/

## HU-002 — Edición de Clientes

Como recepcionista o administrador,
quiero editar la información de clientes desde la app,
para mantener los datos actualizados.

### Criterios de aceptación:

- [ ] Al tocar un cliente se abre la pantalla de edición.
- [ ] Los cambios se guardan en caché local y se sincronizan en segundo plano.
- [ ] Se implementa Swipe-to-refresh para actualizar datos.

**Estimación:** S (Pequeña)
**Módulo:** clients/

## HU-003 — Eliminación Lógica de Clientes

Como administrador,
quiero desactivar clientes sin borrar su historial,
para conservar la trazabilidad desde la app móvil.

### Criterios de aceptación:

- [ ] Se confirma la acción con un diálogo nativo (AlertDialog).
- [ ] El cliente desactivado ya no aparece en búsquedas pero su historial es visible.
- [ ] Solo administradores ven la opción de desactivar.

**Estimación:** S (Pequeña)
**Módulo:** clients/

# Épica 2 — Gestión de Pacientes

## HU-004 — Registro de Pacientes

Como recepcionista o administrador,
quiero registrar pacientes asociados a clientes desde la app,
para gestionar la atención médica.

### Criterios de aceptación:

- [ ] Se selecciona el cliente dueño desde un spinner o autocompletado.
- [ ] Se ingresa nombre, especie, raza, edad y estado de salud.
- [ ] La cámara permite tomar foto del paciente opcionalmente.

**Estimación:** M (Media)
**Módulo:** patients/, camera/

## HU-005 — Edición de Pacientes

Como veterinario o administrador,
quiero modificar los datos del paciente,
para actualizar su estado de salud.

### Criterios de aceptación:

- [ ] La edición es posible desde el detalle del paciente.
- [ ] Los cambios quedan registrados con timestamp.
- [ ] Solo veterinarios y admin pueden editar.

**Estimación:** S (Pequeña)
**Módulo:** patients/

# Épica 3 — Gestión de Veterinarios

## HU-006 — Registro de Veterinarios

Como administrador,
quiero registrar veterinarios y sus especialidades,
para organizar la atención médica.

### Criterios de aceptación:**

- [ ] Se ingresa nombre, especialidad, horarios de atención y contacto.
- [ ] Los veterinarios aparecen en el selector de citas.
- [ ] Solo administradores acceden a esta pantalla.

**Estimación:** S (Pequeña)
**Módulo:** veterinarians/

## HU-007 — Edición de Veterinarios

Como administrador,
quiero actualizar los datos de los veterinarios,
para mantener la información correcta.

### Criterios de aceptación:

- [ ] Se puede modificar especialidad, horarios y contacto.
- [ ] Los cambios afectan citas futuras programadas.

**Estimación:** XS (Muy pequeña)
**Módulo:** veterinarians/

# Épica 4 — Gestión de Citas Médicas

## HU-008 — Gestión de Citas Médicas

Como recepcionista o administrador,
quiero programar citas médicas desde la app,
para coordinar la atención veterinaria.

### Criterios de aceptación:

- [ ] Se usa un DatePicker y TimePicker nativos de Android.
- [ ] No se permiten solapamientos de horario para un mismo veterinario.
- [ ] Se envía notificación push al cliente al agendar.

**Estimación:** M (Media)
**Módulo:** appointments/, notifications/

## HU-009 — Modificación de Citas

Como recepcionista o administrador,
quiero reprogramar citas médicas,
para ajustar cambios de horario.

### Criterios de aceptación:

- [ ] Se puede cambiar fecha, hora o veterinario.
- [ ] Se registra historial de modificaciones visible.
- [ ] Se notifica al cliente por notificación push.

**Estimación:** S (Pequeña)
**Módulo:** appointments/

## HU-010 — Cancelación de Citas

Como recepcionista o administrador,
quiero cancelar citas con historial,
para controlar las cancelaciones.

### Criterios de aceptación:

- [ ] La cita cambia a estado "cancelada".
- [ ] Se guarda motivo de cancelación en un BottomSheet.
- [ ] El cliente recibe notificación de cancelación.

**Estimación:** S (Pequeña)
**Módulo:** appointments/

# Épica 5 — Servicios y Facturación

## HU-011 — Registro de Servicios

Como administrador,
quiero registrar servicios veterinarios,
para definir las prestaciones ofrecidas.

### Criterios de aceptación:

- [ ] Se ingresa nombre, descripción, precio y duración estimada.
- [ ] Los servicios se listan en la pantalla de asignación.
- [ ] Solo administradores pueden crear servicios.

**Estimación:** S (Pequeña)
**Módulo:** services/

## HU-012 — Asignación de Servicios a Citas

Como veterinario o administrador,
quiero asociar servicios a una cita,
para registrar la atención brindada.

### Criterios de aceptación:

- [ ] Se pueden seleccionar múltiples servicios con checkboxes.
- [ ] El total se calcula automáticamente y se muestra en tiempo real.
- [ ] Los servicios asignados quedan en el historial de la cita.

**Estimación:** S (Pequeña)
**Módulo:** appointments/, services/

## HU-013 — Facturación de Servicios

Como cajero o administrador,
quiero generar facturas desde la app,
para cobrar los servicios realizados.

### Criterios de aceptación:

- [ ] La factura incluye cliente, servicios, montos, descuentos y método de pago.
- [ ] Se puede compartir la factura como PDF por WhatsApp o email.
- [ ] Se genera un número de factura único incremental.

**Estimación:** M (Media)
**Módulo:** billing/, sharing/

## HU-014 — Registro de Pagos

Como cajero o administrador,
quiero registrar pagos y saldos,
para controlar los ingresos.

### Criterios de aceptación:

- [ ] Se registra forma de pago (efectivo, tarjeta, transferencia).
- [ ] Se muestra el saldo pendiente actualizado.
- [ ] Se genera un comprobante de pago visible en el historial.

**Estimación:** M (Media)
**Módulo:** billing/

# Épica 6 — Historial Clínico

## HU-015 — Generación de Historial Clínico

Como veterinario,
quiero registrar diagnósticos y tratamientos,
para crear el historial clínico del paciente.

### Criterios de aceptación:

- [ ] Se asocia a un paciente y una cita existente.
- [ ] Se permite agregar fotos de la consulta desde la cámara.
- [ ] Los datos se guardan de forma segura con RLS.

**Estimación:** M (Media)
**Módulo:** medical-records/, camera/

## HU-016 — Visualización del Historial Clínico

Como veterinario,
quiero consultar el historial clínico,
para mejorar la atención médica.

### Criterios de aceptación:

- [ ] Se puede ver el historial completo usando un RecyclerView.
- [ ] Se filtran por fecha usando un DatePicker.
- [ ] Solo veterinarios autorizados pueden acceder.

**Estimación:** S (Pequeña)
**Módulo:** medical-records/

# Épica 7 — Control de Inventario

## HU-017 — Control de Inventario

Como administrador,
quiero registrar productos y cantidades,
para controlar las existencias.

### Criterios de aceptación:

- [ ] Se ingresa nombre, categoría, cantidad disponible y stock mínimo.
- [ ] Se pueden buscar productos con SearchView.
- [ ] La lista se actualiza en tiempo real con LiveData.

**Estimación:** M (Media)
**Módulo:** inventory/

## HU-018 — Actualización de Inventario

Como sistema o administrador,
quiero descontar productos automáticamente,
para mantener el inventario actualizado.

### Criterios de aceptación:

- [ ] Al facturar un servicio, se descuentan los productos usados.
- [ ] Si no hay stock suficiente, se muestra un Snackbar con advertencia.
- [ ] Se puede ajustar inventario manualmente desde la app.

**Estimación:** M (Media)
**Módulo:** inventory/, billing/

## HU-019 — Alerta de Bajo Inventario

Como sistema o administrador,
quiero recibir alertas de stock mínimo,
para reabastecer a tiempo.

### Criterios de aceptación:

- [ ] Cuando un producto baja del stock mínimo, se muestra notificación push.
- [ ] La alerta también aparece como badge en el Drawer.
- [ ] Se puede ver la lista de productos críticos en una pantalla dedicada.

**Estimación:** S (Pequeña)
**Módulo:** inventory/, notifications/

## HU-020 — Gestión de Productos y Precios

Como administrador,
quiero gestionar productos y precios,
para mantener el catálogo actualizado.

### Criterios de aceptación:

- [ ] Se puede crear, modificar y eliminar productos.
- [ ] Los precios se actualizan y afectan futuras ventas.
- [ ] Se confirma eliminación con AlertDialog.

**Estimación:** S (Pequeña)
**Módulo:** inventory/

# Épica 8 — Reportes y Estadísticas

## HU-021 — Reportes de Ventas

Como administrador,
quiero generar reportes de ventas,
para analizar los ingresos.

### Criterios de aceptación:

- [ ] Se filtran por fecha usando DateRangePicker.
- [ ] Se muestran totales y gráficos con MPAndroidChart.
- [ ] Se puede exportar a PDF o Excel.

**Estimación:** M (Media)
**Módulo:** reports/, charts/

## HU-022 — Reportes de Citas

Como administrador,
quiero generar reportes de citas,
para evaluar la demanda.

### Criterios de aceptación:

- [ ] Se muestran citas programadas, realizadas o canceladas.
- [ ] Se pueden ver en formato lista o gráfico de barras.
- [ ] La información se puede compartir como PDF.

**Estimación:** M (Media)
**Módulo:** reports/

## HU-023 — Reportes Clínicos

Como veterinario o administrador,
quiero generar reportes clínicos,
para analizar las atenciones.

### Criterios de aceptación:

- [ ] Se filtran por paciente o veterinario.
- [ ] Incluyen diagnósticos, tratamientos y fechas.
- [ ] Se puede enviar por email al cliente.

**Estimación:** M (Media)
**Módulo:** reports/, medical-records/

# Épica 9 — Notificaciones y Recordatorios

## HU-024 — Recordatorios de Citas

Como cliente o sistema,
quiero recibir recordatorios automáticos en mi dispositivo,
para evitar ausencias en las citas.

### Criterios de aceptación:

- [ ] Se envía notificación push 24 horas antes de la cita.
- [ ] Al tocar la notificación, se abre el detalle de la cita.
- [ ] El cliente puede configurar preferencias desde la app.

**Estimación:** M (Media)
**Módulo:** notifications/, firebase/

## HU-025 — Notificaciones Internas

Como cliente o sistema,
quiero recibir notificaciones al abrir la app,
para mantenerme informado.

### Criterios de aceptación:

- [ ] Se muestran citas próximas y alertas de inventario en un BottomSheet.
- [ ] Las notificaciones se guardan en una bandeja de entrada.
- [ ] Se pueden marcar como leídas deslizando.

**Estimación:** S (Pequeña)
**Módulo:** notifications/

# Épica 10 — Seguridad y Autenticación

## HU-026 — Gestión de Usuarios

Como administrador,
quiero crear y administrar usuarios desde la app,
para controlar los accesos al sistema.

### Criterios de aceptación:

- [ ] Se asignan roles y permisos (admin, recepcionista, veterinario, cajero).
- [ ] Se pueden desactivar usuarios sin eliminar su historial.
- [ ] La pantalla usa un RecyclerView con opciones de edición.

**Estimación:** M (Media)
**Módulo:** auth/

## HU-027 — Actualización de Perfil

Como cliente,
quiero actualizar mis datos y contraseña,
para mantener la seguridad de mi cuenta.

### Criterios de aceptación:

- [ ] Se puede modificar información personal.
- [ ] Para cambiar contraseña, se requiere verificar la actual.
- [ ] Se implementa biometría (huella/FaceID) para acciones sensibles.

**Estimación:** S (Pequeña)
**Módulo:** auth/, biometrics/

## HU-028 — Cierre de Sesión

Como cliente o sistema,
quiero cerrar sesión de forma segura,
para proteger mi información.

### Criterios de aceptación:

- [ ] Al cerrar sesión, se invalidan tokens de autenticación.
- [ ] Se limpia la caché local de datos sensibles.
- [ ] Se redirige a la pantalla de login.

**Estimación:** XS (Muy pequeña)
**Módulo:** auth/

# Épica 11 — Dashboard y Exportación

## HU-029 — Panel de Estadísticas

Como administrador,
quiero visualizar estadísticas gráficas,
para tomar decisiones basadas en datos.

### Criterios de aceptación:

- [ ] Se muestran gráficos de ventas, citas, servicios e inventario.
- [ ] Se pueden filtrar por período con DatePicker.
- [ ] El dashboard usa ViewPager2 para navegar entre gráficos.

**Estimación:** M (Media)
**Módulo:** dashboard/, charts/

## HU-030 — Exportación de Reportes

Como administrador,
quiero exportar reportes en PDF o Excel,
para compartir la información fácilmente.

### Criterios de aceptación:

- [ ] Los reportes se pueden exportar en ambos formatos.
- [ ] La exportación incluye filtros aplicados.
- [ ] Se puede compartir usando el ShareSheet nativo de Android.

**Estimación:** S (Pequeña)
**Módulo:** reports/, sharing/