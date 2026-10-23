# Coyahue Service Desk

Sistema web de mesa de ayuda TI para la gestión de tickets, usuarios, niveles de servicio y soporte interno.

Proyecto académico desarrollado durante **2025** para la **Evaluación 4 de Proyecto Integrado**.

## Autores

- Matías Gajardo
- Jean Pierre Avastia
- Andrés Chandía

Proyecto realizado en equipo como parte del proceso formativo en desarrollo de software.

## Descripción del proyecto

La plataforma fue desarrollada por etapas durante el segundo semestre del segundo año de la carrera, en el marco de la asignatura Proyecto Integrado. El sistema fue implementado para la empresa Coyahue, ubicada en Temuco, Chile, y presentado como una solución tecnológica para la gestión de soporte interno.

La aplicación permite administrar los procesos principales de una mesa de ayuda TI:

- Registro y gestión de usuarios con roles.
- Creación y seguimiento de tickets.
- Gestión de estados, prioridades y categorías.
- Asignación de tickets a técnicos.
- Historial de comentarios y trazabilidad de atención.
- Paneles diferenciados para usuarios, técnicos y administradores.
- Base de conocimiento para la autoayuda de usuarios.
- Recuperación de contraseña y dashboards por perfil.

## Características principales

- Flujo de tickets orientado a soporte TI empresarial.
- Gestión de SLA por prioridad mediante `sla_horas`.
- Estados de SLA: `EN_CURSO`, `ADVERTENCIA`, `VENCIDO` y `CUMPLIDO`.
- Control de permisos según el tipo de usuario.
- Historial de cambios de estado por ticket.
- Comentarios bidireccionales con archivos adjuntos.
- Calificación de satisfacción (CSAT) al cerrar un ticket.
- Notificaciones y gestión de eventos críticos.
- Reportes en dashboard y exportación a Excel y PDF.
- Base de conocimiento con preguntas frecuentes, votación de utilidad y archivos de apoyo.
- API REST con Django REST Framework y autenticación JWT.

## Tecnologías

- Python 3.13
- Django 6.0
- Django REST Framework
- Simple JWT
- HTML, CSS y JavaScript
- Plantillas Django
- SQLite para ejecución local
- PostgreSQL utilizado en el proyecto original
- AWS para el despliegue académico

## Módulos del sistema

- `accounts`: autenticación, registro, perfiles y roles.
- `tickets`: tickets, estados, prioridades y seguimiento.
- `notifications`: notificaciones internas y eventos.
- `knowledge_base`: preguntas frecuentes y archivos de apoyo.
- `config`: configuración principal del proyecto Django.

## Puesta en marcha local

### 1. Crear y activar el entorno virtual

```powershell
python -m venv env
.\env\Scripts\Activate.ps1
```

### 2. Instalar dependencias

```powershell
pip install -r requirements.txt
```

### 3. Aplicar migraciones

```powershell
python manage.py migrate
```

### 4. Iniciar el servidor

```powershell
python manage.py runserver
```

## Rutas principales

| Ruta | Descripción |
|------|-------------|
| `http://127.0.0.1:8000/` | Pantalla de inicio de sesión |
| `http://127.0.0.1:8000/admin/` | Panel de administración Django |

## API de autenticación JWT

- `POST /api/auth/login/`
- `POST /api/auth/refresh/`

## Despliegue y base de datos

El proyecto fue desplegado en AWS durante su etapa académica y presentado como solución para una empresa real. Para facilitar la ejecución y revisión desde este repositorio, la configuración local utiliza SQLite.

Durante el desarrollo original se trabajó con PostgreSQL. La diferencia entre ambas configuraciones se mantiene documentada para distinguir el entorno de despliegue de la versión local disponible.

## Contexto académico

El proyecto se desarrolló en cuatro unidades. Las primeras etapas incluyeron planificación y mockups; posteriormente se presentó una versión base y, durante la Evaluación 4, se consolidó una versión funcional con mejoras de interfaz, validaciones, gestión de SLA, notificaciones, reportes y trazabilidad de tickets.

## Alcance

Este repositorio representa una implementación académica funcional con alcance intermedio-avanzado dentro de la colección de proyectos. Su foco principal está en la gestión de procesos de soporte TI, control de roles, trazabilidad, niveles de servicio y organización modular de una aplicación Django.
