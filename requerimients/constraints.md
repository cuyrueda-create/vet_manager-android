# Restricciones del Proyecto — VET-MANAGER

**Proyecto:** VET-MANAGER — Sistema de gestión veterinaria para Android  
**Versión:** 1.0  
**Fecha:** Mayo 2026  
**Clasificación:** Académico  

---

## RSP-01 — Restricciones Tecnológicas

| ID | Restricción | Justificación |
|---|---|---|
| RSP-01.1 | La app debe desarrollarse con **React Native** (versión 0.72 o superior). | Multiplataforma Android/iOS |
| RSP-01.2 | Backend debe usar **Supabase** (autenticación, base de datos PostgreSQL, RLS, almacenamiento). | Open source, fácil integración |
| RSP-01.3 | Almacenamiento local debe ser **SQLite** con `expo-sqlite` o `react-native-sqlite-storage`. | Offline first |
| RSP-01.4 | Notificaciones push deben usar **Firebase Cloud Messaging (FCM)**. | Estándar en Android |
| RSP-01.5 | Gráficos estadísticos con **MPAndroidChart** (React Native wrapper). | Visualización nativa |
| RSP-01.6 | Cámara y galería con `expo-camera` o `react-native-image-picker`. | Captura de fotos paciente/historial |

---

## RSP-02 — Restricciones de Arquitectura

| ID | Restricción | Justificación |
|---|---|---|
| RSP-02.1 | La app debe seguir patrón **Clean Architecture** (capa de datos, dominio, presentación). | Mantenibilidad y pruebas |
| RSP-02.2 | Manejo de estado global con **Zustand** o **Context API**. | Simplicidad y rendimiento |
| RSP-02.3 | Navegación con **React Navigation 6** (Stack, Drawer, Tabs). | Estándar en React Native |
| RSP-02.4 | Consultas a APIs y caché con **TanStack Query**. | Sincronización y caché |
| RSP-02.5 | Los módulos deben ser independientes y reutilizables. | Escalabilidad |

---

## RSP-03 — Restricciones de Seguridad

| ID | Restricción | Justificación |
|---|---|---|
| RSP-03.1 | Las contraseñas deben encriptarse con **bcrypt** (manejado por Supabase Auth). | Seguridad de credenciales |
| RSP-03.2 | **Row Level Security (RLS)** obligatorio en todas las tablas de Supabase. | Aislamiento de datos por usuario/rol |
| RSP-03.3 | Los tokens de autenticación (JWT) deben almacenarse de forma segura (SecureStore/Keychain). | Prevención de ataques |
| RSP-03.4 | Las peticiones a Supabase deben ir cifradas por **HTTPS**. | Comunicación segura |
| RSP-03.5 | No se debe almacenar información sensible en caché o AsyncStorage. | Privacidad del usuario |

---

## RSP-04 — Restricciones de Rendimiento

| ID | Restricción | Métrica |
|---|---|---|
| RSP-04.1 | La pantalla de inicio debe cargar en menos de **2 segundos** en Android gama media (4GB RAM). | Medición con `performance.now()` |
| RSP-04.2 | Las listas (RecyclerView/FlatList) deben mantener **60 fps** durante scroll. | FPS ≥ 60 |
| RSP-04.3 | El tiempo de respuesta de operaciones CRUD debe ser **< 1 segundo** en condiciones normales. | Con conexión estable |
| RSP-04.4 | La app no debe consumir más de **150 MB de RAM** en uso normal. | Monitorización |
| RSP-04.5 | El tamaño de la APK no debe superar los **50 MB** (sin recursos adicionales). | Bundle optimizado |

---

## RSP-05 — Restricciones de Usabilidad

| ID | Restricción | Justificación |
|---|---|---|
| RSP-05.1 | La app debe ser intuitiva, requiriendo **menos de 10 minutos** de capacitación para roles básicos. | UI/UX clara |
| RSP-05.2 | Los mensajes de error deben ser en **español**, claros y con opciones de acción. | Experiencia de usuario |
| RSP-05.3 | La app debe soportar **modo oscuro/claro** (Material Design 3). | Accesibilidad |
| RSP-05.4 | Los botones principales deben tener tamaño mínimo **48x48 dp**. | Estándar de accesibilidad Android |
| RSP-05.5 | Debe haber indicadores de carga (Skeleton/ProgressBar) en operaciones asíncronas. | Feedback al usuario |

---

## RSP-06 — Restricciones de Disponibilidad y Offline

| ID | Restricción | Métrica |
|---|---|---|
| RSP-06.1 | La app debe ser usable **sin conexión a internet** (lectura de datos locales). | Offline first |
| RSP-06.2 | Sincronización automática al recuperar conexión, sin pérdida de datos. | Resolución de conflictos |
| RSP-06.3 | La app debe tener **99.5% de disponibilidad** en horario laboral (8:00 - 20:00). | Uptime garantizado |
| RSP-06.4 | En caso de caída del servidor, la app debe mostrar mensaje amigable y reintentar. | Exponential backoff |

---

## RSP-07 — Restricciones de Compatibilidad

| ID | Restricción | Justificación |
|---|---|---|
| RSP-07.1 | La app debe ser compatible con **Android 8.0 (API 26) en adelante**. | Cobertura del 95%+ de dispositivos |
| RSP-07.2 | Debe funcionar en resoluciones **desde 720x1280 hasta 1440x3120**. | Responsive design |
| RSP-07.3 | Soporte para **dispositivos con y sin giroscopio** (si se usa funcionalidad opcional). | Degradación elegante |
| RSP-07.4 | La app debe adaptarse a **modo tableta** (layout en dos paneles cuando aplique). | Material Design |

---

## RSP-08 — Restricciones de Desarrollo y Entrega

| ID | Restricción | Justificación |
|---|---|---|
| RSP-08.1 | El código debe estar comentado en español explicando funcionalidades complejas. | Showcase académico |
| RSP-08.2 | El repositorio debe incluir este archivo de restricciones en `docs/requirements/`. | Requisito del profesor |
| RSP-08.3 | La app debe ser entregable como **APK firmada** para instalación directa. | Evaluación en dispositivos reales |
| RSP-08.4 | El proyecto debe incluir **README.md** con instrucciones de instalación y ejecución. | Documentación |
| RSP-08.5 | El código debe pasar **ESLint** sin errores graves. | Calidad de código |
| RSP-08.6 | Pruebas unitarias con **Jest** y pruebas de componentes con **React Native Testing Library**. | Mínimo 60% de cobertura |