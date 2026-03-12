# 🗒️ Registro de Trabajo en Clase - Taller 4

## 📆 Fecha de la sesión
7/03/2026

## 👥 Integrantes presentes
- Valentina Ruiz
- Darek Aljuri
- Santiago Soler

## 🧠 Actividades realizadas en clase

Durante la sesión el equipo trabajó en el análisis y modelado de la infraestructura tecnológica de la plataforma RedExpress, una aplicación diseñada para gestionar envíos y permitir el rastreo de paquetes en tiempo real mediante una aplicación móvil utilizada por los mensajeros y una plataforma web utilizada por operadores logísticos y clientes.

El objetivo principal de la sesión fue construir un mapa preliminar de infraestructura que permitiera visualizar cómo interactúan los diferentes componentes tecnológicos del sistema, desde los dispositivos móviles que generan las solicitudes hasta los servicios que procesan la información en la nube.

Para ello se analizaron las distintas capas del sistema, incluyendo la infraestructura de red, los centros de distribución físicos, los servidores regionales utilizados para procesamiento logístico y la infraestructura desplegada en la nube. También se evaluaron aspectos clave como la disponibilidad del sistema, la escalabilidad de los servicios y los posibles riesgos operativos asociados a puntos únicos de falla.

El resultado de la sesión fue la construcción de un diagrama de infraestructura que representa la arquitectura del sistema y permite identificar tanto su funcionamiento general como posibles vulnerabilidades en su diseño.

- **¿Qué se discutió con el equipo?**

Cómo podría estar estructurada la infraestructura tecnológica que soporta el funcionamiento de RedExpress, considerando que se trata de una plataforma que debe operar de manera continua y con alta disponibilidad.

Se analizaron los distintos componentes que intervienen en el flujo de información del sistema. En primer lugar, se discutió el papel de los dispositivos móviles utilizados por los mensajeros, los cuales generan constantemente actualizaciones sobre el estado y ubicación de los paquetes. Estas actualizaciones se envían a través de internet hacia la plataforma central.

También se discutió la función de los centros de distribución físicos, que forman parte de la infraestructura logística de la empresa. Estos centros cuentan con elementos de red como routers, switches y firewalls que permiten la comunicación con los sistemas centrales.

Posteriormente se analizaron los servidores regionales, cuya función es procesar información relacionada con rutas de entrega, optimización logística y gestión local de envíos. Estos servidores permiten reducir la carga sobre los sistemas centrales y mejorar la eficiencia operativa en distintas zonas geográficas.

Una parte importante de la discusión se centró en la infraestructura en la nube, donde se ejecutan los servicios principales del sistema. Se analizó cómo los usuarios acceden a la plataforma a través de internet y cómo las solicitudes son gestionadas por un balanceador de carga y un API Gateway antes de llegar a los servicios que procesan la información.

También se discutieron los diferentes módulos funcionales del sistema, entre ellos:

El servicio de procesamiento de rutas, encargado de calcular rutas óptimas para la entrega de paquetes.

El servicio de rastreo en tiempo real, que recibe y procesa las actualizaciones de ubicación enviadas por los mensajeros.

El servicio de gestión de envíos, responsable de registrar y actualizar el estado de los paquetes dentro del sistema.

Además, se analizaron los posibles problemas técnicos que podrían surgir en esta arquitectura, especialmente relacionados con la latencia en el rastreo en tiempo real, la escalabilidad del sistema durante periodos de alta demanda y la existencia de componentes críticos que podrían convertirse en puntos únicos de falla.

- **¿Qué decisiones de modelado se tomaron?**
  
Se decidió modelar el sistema utilizando una arquitectura híbrida, en la cual parte de la infraestructura se encuentra distribuida en instalaciones físicas (centros de distribución y servidores regionales) mientras que los servicios principales se encuentran desplegados en la nube.

En el modelo propuesto, las solicitudes generadas por los usuarios y los dispositivos móviles son enviadas a través de internet hacia la infraestructura del sistema. Estas solicitudes son recibidas inicialmente por un balanceador de carga, cuya función es distribuir el tráfico entre múltiples instancias de los servicios disponibles, evitando que un único servidor reciba todas las solicitudes.

Después del balanceador de carga, las solicitudes pasan por un API Gateway, que actúa como punto de entrada para los servicios del sistema. El API Gateway se encarga de gestionar el acceso a los diferentes microservicios, validar solicitudes y dirigir cada petición al servicio correspondiente.

A partir de este punto, las solicitudes son procesadas por distintos microservicios especializados, cada uno responsable de una función específica dentro de la plataforma. Estos microservicios se ejecutan dentro de contenedores administrados por un cluster de orquestación en la nube.

Para representar la infraestructura en la nube se decidió modelar una arquitectura basada en servicios del proveedor Google Cloud Platform. Dentro de esta infraestructura se incluyó una región de nube que contiene múltiples zonas de disponibilidad, lo que permite distribuir los servicios en distintos centros de datos para mejorar la disponibilidad del sistema.

Dentro de cada zona de disponibilidad se modeló un cluster de contenedores administrado mediante Google Kubernetes Engine, el cual se encarga de ejecutar los microservicios del sistema y gestionar su escalabilidad.

A su vez, este cluster se ejecuta sobre un conjunto de máquinas virtuales proporcionadas por Google Compute Engine, que representan los servidores sobre los cuales se ejecutan los contenedores. Esta estructura permite representar cómo la aplicación funciona realmente dentro de la infraestructura cloud, donde los servicios se ejecutan en contenedores que corren sobre nodos virtuales distribuidos en diferentes zonas.

Finalmente, se incluyó una base de datos centralizada replicada, encargada de almacenar la información de los envíos, estados de los paquetes y registros de rastreo. También se incorporaron servicios de monitoreo y alertas que permiten supervisar el funcionamiento del sistema y detectar posibles fallos.

- **Identificación de puntos únicos de falla (SPOF)**
  
Un punto único de falla es un componente cuya caída podría provocar la interrupción total o parcial del sistema. Identificar estos puntos es fundamental para mejorar la disponibilidad y resiliencia de la infraestructura.

Uno de los posibles SPOF identificados fue la base de datos centralizada, ya que si esta base de datos fallara, los servicios del sistema no podrían acceder a la información necesaria para procesar envíos o rastrear paquetes. Para mitigar este riesgo se propuso el uso de replicación de base de datos, donde una instancia secundaria puede asumir el rol de la instancia principal en caso de falla.

Otro posible SPOF identificado fue el API Gateway, ya que actúa como punto central de acceso a los servicios. Si el API Gateway fallara, las solicitudes de los usuarios no podrían ser procesadas. Para reducir este riesgo se planteó la posibilidad de desplegar múltiples instancias del API Gateway distribuidas entre distintas zonas de disponibilidad.

El balanceador de carga también se identificó como un componente crítico, ya que es responsable de distribuir el tráfico hacia los servicios disponibles. En arquitecturas cloud modernas este componente suele implementarse como un servicio distribuido que funciona en múltiples nodos, reduciendo así el riesgo de fallos.

Adicionalmente se identificaron posibles riesgos en los servidores regionales, que podrían afectar las operaciones locales si llegaran a fallar. En este caso se discutió la posibilidad de implementar redundancia o replicación de servicios entre distintas regiones.


- **¿Qué herramientas se usaron?**
  
Para realizar el trabajo se utilizó la herramienta **draw.io**, en la cual se empezó a construir el diagrama de infraestructura que muestra los diferentes componentes del sistema y sus conexiones.

- **¿Qué parte del trabajo se alcanzó a desarrollar?**
  
Durante la sesión se logró construir una primera versión del mapa de infraestructura de RedExpress, en el cual se representaron los principales componentes tecnológicos del sistema y el flujo de comunicación entre ellos.

Este diagrama permitió visualizar de manera clara cómo interactúan los dispositivos móviles, la infraestructura de red, los servidores regionales y los servicios desplegados en la nube. Además, permitió identificar zonas críticas del sistema donde podrían presentarse problemas de rendimiento o disponibilidad.

Entre los aspectos más relevantes que se lograron identificar se encuentran los posibles cuellos de botella en la base de datos, los riesgos asociados a la latencia en el rastreo en tiempo real y la existencia de puntos únicos de falla en algunos componentes clave.

Este análisis preliminar servirá como base para futuras mejoras en la arquitectura del sistema, con el objetivo de aumentar la escalabilidad, disponibilidad y resiliencia de la plataforma.

## 🧩 Boceto inicial del modelo

> (Puede insertar aquí una imagen del boceto, una captura de pantalla o un diagrama preliminar si ya fue hecho en digital)

## Flujo de funcionamiento del sistema

Para comprender mejor el funcionamiento de la infraestructura propuesta, se analizó el flujo de comunicación que sigue una solicitud desde que es generada por un usuario o mensajero hasta que es procesada por los servicios del sistema.

El proceso puede describirse de la siguiente manera:

1. Generación de la solicitud desde el dispositivo móvil

  El proceso comienza cuando un mensajero utiliza la aplicación móvil para registrar una actualización del estado de un paquete o para consultar información sobre una entrega. Esta información puede incluir la ubicación del paquete, el estado de la entrega o datos relacionados con la ruta de distribución. La aplicación móvil envía esta información a través de internet utilizando protocolos seguros de comunicación, generalmente mediante HTTPS, para garantizar la confidencialidad e integridad de los datos transmitidos.

2. Recepción del tráfico en la infraestructura de la nube

  Una vez que la solicitud llega a internet, esta es dirigida hacia la infraestructura en la nube donde se encuentran los servicios principales del sistema. El primer componente que recibe el tráfico es el balanceador de carga, que tiene la función de distribuir las solicitudes entrantes entre múltiples instancias del sistema para evitar que un único servidor se sobrecargue. Esto permite mejorar el rendimiento del sistema y aumentar su disponibilidad. En el caso de RedExpress, el balanceador de carga actúa como el punto de entrada principal hacia la infraestructura desplegada en la nube.

3. Gestión de solicitudes mediante el API Gateway

  Después de pasar por el balanceador de carga, las solicitudes son dirigidas al API Gateway, que funciona como intermediario entre los clientes y los servicios internos del sistema. El API Gateway se encarga de gestionar el acceso a los diferentes microservicios disponibles, validar las solicitudes recibidas y dirigir cada petición hacia el servicio correspondiente. Este componente también puede encargarse de tareas adicionales como autenticación, control de acceso y limitación de tráfico.

4. Procesamiento de solicitudes

  Una vez que la solicitud ha sido dirigida al servicio correspondiente, esta es procesada por uno de los servicios del sistema. Cada uno tiene una responsabilidad específica dentro de la plataforma, el servicio de procesamiento de rutas calcula rutas óptimas para la entrega de paquetes, el servicio de rastreo en tiempo real procesa las actualizaciones de ubicación enviadas por los mensajeros y el servicio de gestión de envíos registra y actualiza el estado de los paquetes dentro del sistema. Estos servicios se ejecutan dentro de contenedores administrados por un cluster de orquestación en la nube, lo que permite escalar automáticamente la capacidad del sistema cuando aumenta la carga de trabajo.

5. Ejecución de servicios dentro del cluster en la nube

  Los servicios del sistema se ejecutan dentro de un cluster de contenedores administrado por Google Kubernetes Engine, que se encarga de gestionar el despliegue, la escalabilidad y la disponibilidad de los servicios. Este cluster funciona sobre un conjunto de nodos que corresponden a máquinas virtuales proporcionadas por Google Compute Engine. Estas máquinas virtuales representan los servidores sobre los cuales se ejecutan los contenedores que contienen los servicios. El uso de un cluster permite distribuir los servicios entre múltiples nodos, lo que mejora la tolerancia a fallos y permite que el sistema continúe funcionando incluso si uno de los nodos deja de estar disponible.


6. Interacción con la base de datos

Durante el procesamiento de las solicitudes, los servicios acceden a la base de datos del sistema para consultar o actualizar información relacionada con los envíos, la base de datos almacena datos críticos como:

- información de los paquetes
- estados de entrega
- ubicaciones reportadas por los mensajeros
registros históricos de envíos

Para mejorar la disponibilidad del sistema, se utiliza una base de datos con replicación, donde una instancia secundaria mantiene una copia actualizada de la información almacenada en la instancia principal.

7. Monitoreo y supervisión del sistema

Finalmente, toda la infraestructura es supervisada mediante servicios de monitoreo y alertas que permiten observar el estado del sistema en tiempo real. Estos servicios recopilan métricas relacionadas con el rendimiento de los servidores, el uso de recursos, el tráfico de red y posibles errores en los servicios. Cuando se detecta una anomalía o fallo en algún componente, el sistema puede generar alertas para que el equipo técnico pueda intervenir rápidamente. El monitoreo es una parte fundamental de la infraestructura, ya que permite identificar problemas antes de que afecten significativamente el funcionamiento del sistema.


## 🔁 Tareas definidas para complementar el taller

Anote las responsabilidades acordadas entre los miembros del equipo para completar la entrega final:

| Tarea asignada | Responsable | Fecha estimada |
|----------------|-------------|----------------|
| Modelado final en draw.io | darek aljuri | 7/03 |
| Redacción del informe     | Valentina Ruiz | 7/03 |
| Investigación y referencias | Santiago Soler | 7/03 |

---

_Este documento resume el trabajo colaborativo realizado durante la sesión del taller X en el curso AREM - Universidad de La Sabana._
