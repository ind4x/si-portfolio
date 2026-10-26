# Systems Information (SI) Laboratory Portfolio

This repository hosts practical implementations, ERP customizations, and enterprise
process architectures developed for the Systems Information and ERP curriculum at
Mundiapolis University, centered on Odoo 17.0 and containerized micro-architectures.

---

## Laboratory Overview

| Module | Category | Core Methodology | Primary Deliverables | Reference |
| :--- | :--- | :--- | :--- | :--- |
| **[odoo-fundamentals](./labs/odoo-fundamentals)** | Laboratory | Odoo ORM models, relational mappings (M2O, O2M, M2M), QWeb views, ACL security groups | Student academic ERP module | [Lab](./labs/odoo-fundamentals/README.md) |
| **[food-quality-management](./projects/food-quality-management)** | Capstone Project | Food safety compliance, automated Cron inspection tickets, logistic shipping security locks, QWeb PDF reporting | Enterprise food quality addon | [Project](./projects/food-quality-management/README.md) |

---

## General Running Instructions

### Prerequisites

- **Docker:** Engine 24.0+ & Docker Compose v2
- **Python:** 3.10+ (for local toolings)
- **PostgreSQL Client** (optional for database inspection)

### Setup and Environment

1. **Clone the repository:**
   ```bash
   git clone git@github.com:ind4x/si-portfolio.git
   cd si-portfolio
   ```

2. **Deploy via Docker Compose:**
   Navigate to the deployment folder:
   ```bash
   cd projects/food-quality-management/deployment
   docker compose up -d
   ```

3. **Access the ERP Instance:**
   Open a web browser at `http://localhost:8069`.
   - **Database Name:** `odoo_si`
   - **Default Login:** `admin` / `admin`

---

## Technology Stack

- **ERP Platform:** Odoo 17.0 (Community Edition)
- **Backend & ORM:** Python 3, PostgreSQL 15
- **Views & UI:** XML, QWeb, Kanban, Graph Views
- **Infrastructure:** Docker, Docker Compose
- **Enterprise Modeling:** BPMN 2.0, UML

---

## Author

- **Author:** Youssef Fellah ([ind4x_](https://github.com/ind4x))
- **Institution:** Mundiapolis University, Engineering Cycle
