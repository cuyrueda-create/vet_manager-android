# Requisitos No Funcionales — VET-MANAGER

**Proyecto:** VET-MANAGER — Sistema de gestión veterinaria para Android  
**Versión:** 1.0  
**Fecha:** Mayo 2026  
**Clasificación:** Académico  

---

## RNF-01 — Rendimiento

| ID | Requisito | Métrica |
|---|---|---|
| RNF-01 | La pantalla de inicio (Dashboard) debe renderizarse en menos de 2 segundos en dispositivos Android de gama media. | Tiempo de renderizado ≤ 2 s |
| RNF-02 | Las listas (clientes, pacientes, citas) no deben caer por debajo de 60 fps durante el scroll. | FPS ≥ 60 |
| RNF-03 | Las operaciones de facturación y registro de pagos deben procesarse en menos de 1 segundo. | Tiempo de respuesta ≤ 1 s |
| RNF-04 | El tiempo de respuesta de las consultas a Supabase no debe superar los 2 segundos. | Timeout ≤ 2 s |
| RNF-05 | La búsqueda de clientes por nombre o identificación debe filtrar en menos de 500 ms. | Filtro ≤ 500 ms |
| RNF-06 | La app no debe consumir más de 150 MB de RAM en uso normal. | Memoria ≤ 150 MB |

---

## RNF-02 — Seguridad

| ID | Requisito | Métrica |
|---|---|---|
| RNF-07 | Las contraseñas deben almacenarse encriptadas (Supabase Auth con bcrypt). | Encriptación estándar |
| RNF-08 | La app debe implementar autenticación biométrica (huella/FaceID) para acciones sensibles. | Éxito ≥ 95% |
| RNF-09 | El sistema debe aplicar Row Level Security (RLS) en todas las tablas de Supabase. | Aislamiento por rol |
| RNF-10 | Los tokens JWT deben almacenarse en SecureStore (Android) de forma segura. | Sin exposición en logs |
| RNF-11 | Todas las peticiones entre app y Supabase deben ir cifradas mediante HTTPS. | Comunicación segura |
| RNF-12 | El sistema debe cerrar sesión automáticamente después de 30 minutos de inactividad. | Timeout de sesión |

---

## RNF-03 — Usabilidad

| ID | Requisito | Métrica |
|---|---|---|
| RNF-13 | La interfaz debe seguir Material Design 3 con soporte para modo oscuro/claro. | Estándar Google |
| RNF-14 | El sistema debe ser intuitivo, requiriendo menos de 15 minutos de capacitación para recepcionistas. | Curva de aprendizaje baja |
| RNF-15 | Los mensajes de error deben ser claros, en español y con opciones de acción. | UX clara |
| RNF-16 | Los botones principales deben tener tamaño mínimo 48x48 dp (estándar de accesibilidad). | Touch target ≥ 48 dp |
| RNF-17 | La app debe mostrar indicadores de carga (ProgressBar/Skeleton) en operaciones asíncronas. | Feedback inmediato |
| RNF-18 | Los formularios largos deben guardar progreso automáticamente cada 30 segundos. | Auto-save |

---

## RNF-04 — Disponibilidad

| ID | Requisito | Métrica |
|---|---|---|
| RNF-19 | El sistema debe tener una disponibilidad del 99.5% en horario laboral (8:00 a 20:00). | Uptime ≥ 99.5% |
| RNF-20 | La app debe ser usable sin conexión a internet (modo offline con SQLite). | Operación local 100% |
| RNF-21 | En caso de caída del servidor, la app debe reintentar automáticamente con exponential backoff. | Reintentos: 3 intentos |
| RNF-22 | La sincronización offline debe completarse en menos de 10 segundos al recuperar conexión. | Sincronización ≤ 10 s |
| RNF-23 | El sistema debe mostrar indicador visual (icono de nube) cuando está en modo offline. | UX clara |

---

## RNF-05 — Mantenibilidad

| ID | Requisito | Métrica |
|---|---|---|
| RNF-24 | El código debe seguir estándares ESLint (configuración recomendada para React Native). | 0 errores críticos |
| RNF-25 | Los componentes de React Native deben ser reutilizables y estar correctamente modularizados. | DRY principle |
| RNF-26 | La base de datos Supabase debe estar normalizada al menos hasta 3FN. | Integridad referencial |
| RNF-27 | El código debe incluir comentarios en español explicando lógica compleja. | Documentación inline |

---

## RNF-06 — Compatibilidad y Portabilidad

| ID | Requisito | Métrica |
|---|---|---|
| RNF-28 | La app debe ser compatible con Android 8.0 (API 26) en adelante. | Cobertura ≥ 95% dispositivos |
| RNF-29 | Debe funcionar correctamente en resoluciones desde 720x1280 hasta 1440x3120. | Responsive design |
| RNF-30 | La app debe poder desplegarse como APK firmada para instalación directa. | Build release configurado |