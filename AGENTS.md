# AGENTS.md - Módulo Solicitud Internas

## Información del Proyecto

- **Módulo**: solicitud_internas
- **Versión de Odoo**: 19
- **Stack**: Odoo 19 + PostgreSQL 16
- **Tipo**: Módulo personalizado para gestionar solicitudes internas

## Funcionalidad

Permite registrar y gestionar solicitudes internas de diferentes departamentos:
- IT
- RRHH
- Compras

## Estructura

```
solicitud_internas/
├── __init__.py
├── __manifest__.py
├── data/
│   └── secuencia.xml
├── models/
│   ├── __init__.py
│   └── solicitud.py
├── security/
│   └── ir.model.access.csv
└── views/
    ├── __init__.py
    ├── solicitud_menu.xml
    └── solicitud_views.xml
```

## Modelos

### solicitud.interna
Modelo principal para solicitudes internas.
- Estados: borrador, enviada, en_revision, aprobada, proceso, finalizada, rechazada, cancelada
- Categorías: IT, RRHH, Compras

### solicitud.interna.category
Modelo para clasificar categorías de solicitudes.

## Comandos Útiles

### Instalar módulo
```bash
docker exec odoo bash -c "cd /mnt/extra-addons && ./scaffold solicitud_internas"
```

### Actualizar módulo
```bash
docker exec odoo odoo -d db_name -u solicitud_internas -i
```

### Reiniciar Odoo
```bash
docker restart odoo
```

## Notas

- El usuario indicará las tareas específicas que debe realizar el módulo
- El módulo incluye integración con mail para chatter y actividades
- Control de acceso configurado en security/ir.model.access.csv