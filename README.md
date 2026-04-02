# LINA - Plataforma de Gestion de Soporte IT

**Dashboard Kanban en tiempo real para gestion de tickets de soporte tecnico, conectado a n8n**

[Demo en vivo](https://lina-snowy.vercel.app)

---

## Que es

LINA es una plataforma de gestion de tickets de soporte IT desplegada en produccion para +LATINA. Funciona como un tablero Kanban en tiempo real donde los tecnicos gestionan incidencias, con metricas de rendimiento, cumplimiento de SLAs y conexion directa a WhatsApp para comunicacion con usuarios.

## Funcionalidades

### Tablero Kanban (Drag & Drop)
- 3 columnas: Nuevos, En Proceso, Finalizado
- Drag & drop con Sortable.js
- Al mover a "Finalizado", obliga a documentar la solucion tecnica

### Metricas y KPIs en Tiempo Real
- Tickets pendientes, en proceso, resueltos hoy
- Tiempo promedio de resolucion
- Grafico de volumen semanal (barras apiladas)
- Tickets por categoria (barras horizontales)
- Cumplimiento de SLA (donut: a tiempo vs tardio, umbral = 3 dias)

### Integraciones
- **n8n**: Backend de datos via webhooks (`/get-tickets`, `/solve-ticket`)
- **WhatsApp**: Link directo `wa.me/` en cada ticket para contactar al usuario
- **Google Drive**: Visualizacion de imagenes adjuntas

### Seguridad
- Sanitizacion XSS con DOMPurify en todo texto renderizado
- Modo mock data para desarrollo sin backend

### UX
- Auto-refresh configurable (60s)
- Actualizaciones optimistas con rollback en caso de error
- Alertas de tickets vencidos (>4 horas sin resolver)
- Sistema de notificaciones toast

## Stack Tecnologico

| Componente | Tecnologia |
|-----------|-----------|
| Frontend | Vanilla JavaScript, Bootstrap 5 |
| Charts | Chart.js |
| Drag & Drop | Sortable.js |
| Seguridad | DOMPurify |
| Alertas | SweetAlert2 |
| Backend | n8n (webhooks) |
| Deploy | Vercel |

## Arquitectura

```
[Usuarios] --> [WhatsApp] --> [n8n Workflow] --> [Base de datos]
                                                       |
                                                 [LINA Dashboard]
                                                 (Kanban + Metricas + SLA)
```

## Contexto

Este proyecto nacio de una [propuesta formal](https://github.com/marcosalbinoacosta/propuesta_LINA) presentada a la gerencia de +LATINA para crear un sistema de gestion de soporte con trazabilidad, KPIs y automatizacion. La propuesta fue aprobada y LINA es el producto resultante, actualmente en uso operativo.

---

Desarrollado por [Marcos Acosta](https://www.loomia.ar) | LOOM.IA
