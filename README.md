# 🛠️ CRM Operativo de Campo — Backend en Python (FastAPI)
> Plataforma modular para gestionar levantamientos, cotizaciones, órdenes de trabajo, reportes operativos y estados de cuenta en servicios técnicos industriales.

---

## 🧠 Objetivo del Proyecto
Construir un **CRM Operativo** especializado para empresas de:

- Instalación de cámaras  
- Redes e infraestructura  
- Servicios técnicos en campo  
- Integración industrial  
- Soporte TI empresarial  

El sistema administra **todo el ciclo operativo de un servicio**, desde el levantamiento inicial hasta la facturación final:

**Levantamiento → Cotización → Orden de Trabajo → Reporte Operativo → Estado de Cuenta → Portal del Cliente**

El backend está desarrollado con **FastAPI**, priorizando escalabilidad, modularidad, seguridad y velocidad.

---

## 🧱 Stack Tecnológico

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)
![FastAPI](https://img.shields.io/badge/FastAPI-Framework-009688?logo=fastapi)
![SQLAlchemy](https://img.shields.io/badge/ORM-SQLAlchemy-red)
![Alembic](https://img.shields.io/badge/Migrations-Alembic-orange)
![PostgreSQL](https://img.shields.io/badge/Database-PostgreSQL-336791?logo=postgresql)
![JWT](https://img.shields.io/badge/Auth-JWT-black?logo=jsonwebtokens)
![Uvicorn](https://img.shields.io/badge/Server-Uvicorn-4B8BBE)
![Docker](https://img.shields.io/badge/Container-Docker-066da5?logo=docker)
![NGINX](https://img.shields.io/badge/Reverse_Proxy-NGINX-009639?logo=nginx)

---

## 🧩 Arquitectura del Proyecto

```bash
crm_campo/
├── app/
│   ├── main.py
│   ├── core/
│   │   ├── config.py
│   │   ├── security.py
│   │   └── auth.py
│   ├── db/
│   │   ├── session.py
│   │   └── base.py
│   ├── models/
│   ├── schemas/
│   ├── api/
│   └── utils/
├── alembic/
├── requirements.txt
└── README.md
```

---

## 🧮 Modelo de Datos (Resumen)

```sql
users(id, full_name, email, hashed_password, role, client_id)
clients(id, name, contact_name, phone, email, address)
service_requests(id, title, description, type, status, priority, client_id, created_by)
quotes(id, service_request_id, total, status, notes)
work_orders(id, quote_id, assigned_to, scheduled_date, status)
operation_reports(id, work_order_id, summary, observations, client_signature)
billing(id, client_id, work_order_id, total, paid, balance, status)
```

---

## 🔌 Endpoints Principales

| Método | Endpoint | Descripción |
|--------|----------|-------------|
| POST | `/api/auth/login` | Login JWT |
| POST | `/api/users` | Registrar usuario |
| POST | `/api/service-requests` | Crear levantamiento |
| GET  | `/api/service-requests` | Listar levantamientos |
| POST | `/api/quotes` | Crear cotización |
| POST | `/api/work-orders` | Crear orden de trabajo |
| POST | `/api/operation-reports` | Crear reporte operativo |
| POST | `/api/billing` | Crear remisión |
| GET  | `/api/client/roadmap/{id}` | Ver roadmap del cliente |

---

## 🚀 Ejecución del Proyecto

```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
alembic upgrade head
uvicorn app.main:app --reload
```

---

## 👨‍💻 Autor

**Emmanuel Campos Genaro**  
CTO — Smart Site Company
