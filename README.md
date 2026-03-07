# 🛠️ Taller 4: Mapa de Infraestructura y Diagnóstico Técnico

## 🎯 Objetivo

Construir el mapa lógico y/o físico de la infraestructura tecnológica del sistema base y realizar un diagnóstico de debilidades, cuellos de botella y oportunidades de mejora.

---

## 🚚 Caso base de referencia: RedExpress (Plataforma de Logística)

RedExpress cuenta con una infraestructura híbrida que incluye servidores regionales, servicios en la nube, centros de distribución físicos y dispositivos móviles utilizados por los mensajeros. La plataforma digital debe garantizar alta disponibilidad y rendimiento, especialmente durante campañas promocionales o temporadas de alto volumen como Navidad. El mapa de infraestructura y el diagnóstico técnico permitirán visualizar riesgos como puntos únicos de falla, cuellos de botella en bases de datos, y limitaciones en la escalabilidad horizontal de servicios críticos.

**Contexto:**
- RedExpress gestiona paquetes y rastreo de envíos mediante una app móvil y una plataforma web.
- La infraestructura actual incluye servicios desplegados en la nube, servidores regionales para procesamiento de rutas, y una base de datos centralizada.

**Elementos esperados para modelar:**

- Componentes de infraestructura:
  - Balanceadores de carga
  - Base de datos distribuida
  - API Gateway
  - Servicios de monitoreo y alertas
  - Módulos de procesamiento de rutas y estados de paquetes

- Áreas críticas a diagnosticar:
  - Latencia en rastreo en tiempo real
  - Riesgo de puntos únicos de falla
  - Escalabilidad por zonas geográficas

---

## 🧪 Parte 1: Trabajo en Clase

Durante la clase se espera que el equipo:

- Modele un mapa de infraestructura preliminar de RedExpress.
- Identifique zonas sensibles de carga, disponibilidad, monitoreo o redundancia.
- Use papel, draw.io o cualquier herramienta visual para registrar su análisis.
- Documente posibles problemas y cómo podrían abordarse.
- Reciba retroalimentación en vivo del docente.

---

## 🧠 Parte 2: Aplicación al Cliente Real

Después de la clase, el equipo debe:

- Elaborar el mapa de infraestructura del sistema real del cliente.
- Identificar debilidades o cuellos de botella reales o potenciales.
- Redactar un informe explicando el diagnóstico técnico.
- Complementar con una pequeña investigación sobre buenas prácticas de arquitectura de infraestructura (cloud, on-premise, híbrida).

---

## 📁 Estructura esperada del repositorio

```
taller-04-infraestructura/
├── README.md
├── clase/
│   ├── mapa-borrador.drawio
│   └── notas.md
├── entrega/
│   ├── mapa-final.drawio
│   ├── informe.md
│   └── referencias.md
```

---

## 📤 Entregables

- Mapa de infraestructura del sistema del cliente
- Informe de diagnóstico técnico
- Documento de referencias/investigación

---

## 📊 Rúbrica de Evaluación

| Criterio                            | Excelente (5)                                                             | Aceptable (3) / Insuficiente (1–2)                         |
|-------------------------------------|----------------------------------------------------------------------------|-------------------------------------------------------------|
| Mapa de infraestructura (caso base) | Representa claramente componentes, nodos y servicios críticos             | Elementos incompletos o mal estructurados                  |
| Análisis de cuellos de botella      | Se identifican y justifican problemas técnicos reales o simulados         | Diagnóstico débil o poco argumentado                       |
| Adaptación al cliente real          | El modelo refleja la infraestructura del cliente con lógica y detalle     | Adaptación superficial o desconectada                      |
| Investigación técnica               | Se apoya en buenas prácticas (cloud, escalabilidad, redundancia, etc.)    | Investigación poco clara o sin fuentes aplicadas           |

---

## ✅ Licencia

Este taller hace parte del curso de Arquitectura Empresarial - Universidad de La Sabana. Uso académico bajo licencia MIT.
