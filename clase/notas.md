# 🗒️ Registro de Trabajo en Clase - Taller 4

## 📆 Fecha de la sesión
7/03/2026

## 👥 Integrantes presentes
- Valentina Ruiz
- Darek Aljuri
- Santiago Soler

## 🧠 Actividades realizadas en clase

Describa brevemente qué se hizo durante la sesión:

- **¿Qué se discutió con el equipo?**
  
Durante la sesión se discutió cómo podría estar estructurada la infraestructura tecnológica de la plataforma RedExpress. Analizamos los componentes principales que permitirían el funcionamiento del sistema, como los servidores en la nube, servidores regionales, la base de datos centralizada, el API Gateway, los balanceadores de carga y los dispositivos móviles utilizados por los mensajeros. También se habló sobre posibles problemas que podrían surgir, como la latencia en el rastreo en tiempo real y los puntos únicos de falla.

- **¿Qué decisiones de modelado se tomaron?**
  
Se decidió representar una arquitectura híbrida donde los usuarios acceden al sistema a través de la aplicación móvil o la plataforma web. Estas solicitudes pasan por un balanceador de carga y un API Gateway antes de llegar a los diferentes servicios del sistema, como el módulo de procesamiento de rutas y el módulo de seguimiento de paquetes. Además, se incluyó una base de datos centralizada y servicios de monitoreo y alertas para supervisar el funcionamiento de la infraestructura.

- **¿Qué herramientas se usaron?**
Para realizar el trabajo se utilizó la herramienta **draw.io**, en la cual se empezó a construir el diagrama de infraestructura que muestra los diferentes componentes del sistema y sus conexiones.

- **¿Qué parte del trabajo se alcanzó a desarrollar?**
Durante la clase se logró crear una primera versión del mapa de infraestructura del sistema RedExpress. En este diagrama se identificaron los principales componentes del sistema y algunas zonas críticas que podrían presentar problemas, como posibles cuellos de botella en la base de datos y riesgos de disponibilidad si algún componente clave falla.


## 🧩 Boceto inicial del modelo

> (Puede insertar aquí una imagen del boceto, una captura de pantalla o un diagrama preliminar si ya fue hecho en digital)

## 🔁 Tareas definidas para complementar el taller

Anote las responsabilidades acordadas entre los miembros del equipo para completar la entrega final:

| Tarea asignada | Responsable | Fecha estimada |
|----------------|-------------|----------------|
| Modelado final en draw.io | darek aljuri | 7/03 |
| Redacción del informe     | Valentina Ruiz | 7/03 |
| Investigación y referencias | Santiago Soler | 7/03 |

---

_Este documento resume el trabajo colaborativo realizado durante la sesión del taller X en el curso AREM - Universidad de La Sabana._
