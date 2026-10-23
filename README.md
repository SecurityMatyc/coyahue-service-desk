# Coyahue Service Desk

Sistema web de mesa de ayuda TI para registrar, clasificar, asignar y dar seguimiento a solicitudes de soporte interno.

Proyecto académico desarrollado durante **2025** para la **Evaluación 4 de Proyecto Integrado**.

## Estado del proyecto

Implementación académica funcional de alcance intermedio-avanzado dentro de la colección de proyectos. La solución fue desarrollada por etapas y presentada en un contexto empresarial real para la organización Coyahue, ubicada en Temuco, Chile.

La versión disponible en este repositorio está preparada para ejecución local y revisión técnica. El proyecto fue desplegado en AWS durante su etapa académica.

## Contexto y objetivo

El proyecto buscó centralizar la atención de solicitudes de soporte TI en una plataforma que permitiera reemplazar procesos dispersos por un flujo trazable de tickets.

El objetivo principal fue facilitar la gestión de usuarios, técnicos, prioridades, estados, niveles de servicio, comunicaciones y documentación de soporte desde una única aplicación web.

## Autores

- Matías Gajardo
- Jean Pierre Avastia
- Andrés Chandía

Proyecto realizado en equipo como parte del proceso formativo en desarrollo de software.

## Funcionalidades principales

### Gestión de usuarios y acceso

- Registro y gestión de usuarios.
- Perfiles diferenciados para usuarios, técnicos y administradores.
- Control de permisos según el tipo de usuario.
- Inicio de sesión y recuperación de contraseña.
- Autenticación JWT para los endpoints de la API.

### Gestión de tickets

- Creación y seguimiento de solicitudes de soporte.
- Clasificación por categoría, subcategoría y prioridad.
- Asignación de tickets a técnicos.
- Gestión de estados del ticket.
- Comentarios bidireccionales con archivos adjuntos.
- Historial de cambios y trazabilidad de atención.
- Calificación de satisfacción (CSAT) al cerrar un ticket.

### Gestión de niveles de servicio

- Configuración de SLA según prioridad mediante `sla_horas`.
- Estados de seguimiento del SLA:
  - `EN_CURSO`
  - `ADVERTENCIA`
  - `VENCIDO`
  - `CUMPLIDO`
- Identificación de eventos críticos y notificaciones internas.

### Gestión del conocimiento y reportes

- Base de conocimiento con preguntas frecuentes.
- Votación de utilidad de los artículos.
- Archivos de apoyo en formatos de imagen y PDF.
- Dashboards diferenciados por perfil.
- Exportación de información a Excel y PDF.

## Flujo general de atención

1. Un usuario autenticado registra una solicitud de soporte.
2. El ticket se clasifica según categoría, subcategoría y prioridad.
3. El ticket se asigna a un técnico responsable.
4. El técnico actualiza el estado y registra avances mediante comentarios.
5. El sistema controla el cumplimiento del SLA asociado a la prioridad.
6. El usuario puede consultar la evolución de la solicitud y responder al ticket.
7. Al cerrar la atención, el usuario puede registrar una calificación de satisfacción.

## Arquitectura y módulos

El proyecto está organizado como una aplicación Django modular:

- `accounts`: autenticación, registro, perfiles y control de roles.
- `tickets`: lógica principal de tickets, estados, prioridades y seguimiento.
- `notifications`: notificaciones internas y gestión de eventos.
- `knowledge_base`: preguntas frecuentes y archivos de apoyo.
- `config`: configuración principal del proyecto Django.

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

| Método | Endpoint | Descripción |
|--------|----------|-------------|
| `POST` | `/api/auth/login/` | Inicio de sesión y obtención de tokens |
| `POST` | `/api/auth/refresh/` | Renovación del token de acceso |

## Base de datos y despliegue

Durante el desarrollo y el despliegue original se trabajó con **PostgreSQL** y **AWS**. Para facilitar la ejecución desde este repositorio, la configuración local utiliza **SQLite** y no requiere servicios externos.

La configuración local y la configuración utilizada durante la etapa de despliegue representan entornos diferentes. Por ese motivo, las credenciales, variables de entorno y servicios externos no se incluyen en este README.

## Alcance y limitaciones

Este repositorio representa una solución académica funcional presentada en un contexto empresarial. No debe interpretarse como una plataforma lista para producción sin revisar previamente:

- Configuración segura de variables de entorno.
- Gestión de secretos y credenciales.
- Endurecimiento de la configuración de Django.
- Configuración de almacenamiento de archivos.
- Políticas de respaldo y recuperación.
- Monitoreo, registros y controles de seguridad.
- Configuración de PostgreSQL y servicios de AWS.

## Contexto académico

El desarrollo se realizó durante cuatro unidades de la asignatura Proyecto Integrado. Las primeras etapas incluyeron planificación y elaboración de mockups; posteriormente se presentó una versión base y, durante la Evaluación 4, se consolidó una versión funcional con mejoras de interfaz, validaciones, gestión de SLA, notificaciones, reportes y trazabilidad.
