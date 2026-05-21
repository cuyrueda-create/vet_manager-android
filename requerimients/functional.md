# Requerimientos Funcionales

## RF-01: Catálogo de planetas
El sistema debe mostrar una lista de los cuerpos del sistema solar con nombre, tipo, masa, radio y período orbital, consumiendo datos de la API Solar System OpenData.

## RF-02: Detalle de cuerpo celeste
El sistema debe mostrar información detallada de un cuerpo celeste incluyendo masa, densidad, gravedad, período orbital, excentricidad, velocidad de escape y composición atmosférica.

## RF-03: Animación de órbitas
El sistema debe mostrar una animación del sistema solar interior con velocidades proporcionales a los períodos orbitales reales, permitiendo pausar y reanudar.

## RF-04: Imagen astronómica del día
El sistema debe mostrar la imagen o vídeo astronómico del día de la NASA con título, fecha, descripción y créditos, almacenándola en caché local.

## RF-05: Navegación entre APODs anteriores
El sistema debe permitir navegar hasta 30 días hacia atrás en el archivo de imágenes astronómicas utilizando un selector de fecha.

## RF-06: Búsqueda de asteroides
El sistema debe permitir buscar asteroides cercanos a la Tierra filtrando por rango de fechas, mostrando nombre, velocidad, distancia mínima y si es potencialmente peligroso.

## RF-07: Posición de la ISS en tiempo real
El sistema debe mostrar la posición actual de la Estación Espacial Internacional en un mapa, actualizándose cada 5 segundos.

## RF-08: Listado de tripulación de la ISS
El sistema debe mostrar los nombres y naves de las personas actualmente en el espacio, consumiendo la API Open-Notify.

## RF-09: Alertas de tormentas solares
El sistema debe enviar notificaciones locales cuando se detecte un evento de tormenta solar clase M o superior, consultando la API DONKI.

## RF-10: Mapa estelar con sensores
El sistema debe mostrar un mapa estelar que rota según el giroscopio y se inclina según el acelerómetro del dispositivo.

## RF-11: Registro de usuarios
El sistema debe permitir el registro de usuarios con email y contraseña, validando formato de email y longitud mínima de contraseña.

## RF-12: Autenticación biométrica
El sistema debe permitir iniciar sesión mediante huella dactilar o Face ID en dispositivos compatibles.

## RF-13: Diario de observaciones
El sistema debe permitir a los usuarios autenticados crear, editar, eliminar y listar observaciones astronómicas personales.

## RF-14: Comparativa de plataformas
El sistema debe mostrar una pantalla comparativa de comportamiento entre Android, Web e iOS con snippets de código explicativos.

## RF-15: Catálogo de módulos showcase
El sistema debe mostrar un catálogo navegable de todos los módulos del proyecto con nombre, descripción y estado por plataforma.

## RF-16: Información del programa Artemis
El sistema debe mostrar información de las misiones Artemis (nombre, fecha objetivo, estado, tripulación) y una galería de imágenes oficiales de la NASA.