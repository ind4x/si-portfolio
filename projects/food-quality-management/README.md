# Food Quality and Safety Management System

This project implements the `gestion_alimentaire` custom Odoo 17 module engineered to
bridge the gap between standard logistics and stringent food safety regulations, including
perishability thresholds, temperature compliance, allergen tracking, and automated inspections.

---

## Project Structure

```text
food-quality-management/
├── README.md                          # Technical specification and architecture overview
├── deployment/                        # Containerized production runtime
│   ├── docker-compose.yml             # Orchestration for Odoo 17 and PostgreSQL 15
│   └── config/
│       └── odoo.conf                  # Hardened server configuration and addons paths
├── odoo-module/                       # Core 'gestion_alimentaire' custom addon package
│   ├── __manifest__.py                # Module descriptor and dependency graph
│   ├── __init__.py                    # Module init
│   ├── models/                        # Extended standard ORM entities and custom models
│   │   ├── food_quality_control.py    # Quality check tickets and test metrics
│   │   ├── food_allergen.py           # Standardized allergen taxonomy
│   │   ├── product_template.py        # Extensions for perishability, storage temp, and check intervals
│   │   ├── stock_lot.py               # Serialized lot inspection tracking
│   │   └── stock_picking.py           # Logistic dispatch security locks overriding validate()
│   ├── views/                         # Custom XML interfaces
│   ├── security/                      # Quality inspector and manager security groups
│   └── report/                        # QWeb PDF sanitary certificate templates
└── report/                            # Academic project thesis and deliverables
    └── exam-report.pdf                # Formal architectural defense report
```

### File Responsibilities

- **`models/stock_picking.py`**: Overrides `button_validate()` to evaluate all outgoing lots against expiration dates and sanitary inspection states; halts delivery if a non-compliant lot is detected.
- **`models/food_quality_control.py`**: Handles sanitary lifecycle states (`draft`, `in_progress`, `passed`, `failed`).
- **`deployment/docker-compose.yml`**: Provisions isolated networks and persistent volumes for PostgreSQL and Odoo.

---

## System Architecture

```text
+---------------------------------------------------------------+
|                       Supply Chain Flow                       |
|   Inbound Shipment (stock.picking IN)                         |
+---------------------------------------------------------------+
                               |
                               v
+---------------------------------------------------------------+
|                   Sanitary Inspection Gate                    |
|   - Food Quality Ticket Generated (Automated Cron / Trigger)  |
|   - Temperature, Microbiological, and Expiration Check        |
+---------------------------------------------------------------+
            |                                       |
            | PASSED                                | FAILED
            v                                       v
+-----------------------+               +-----------------------+
| Outbound Delivery     |               | Security Lock Active  |
| Dispatch Authorized   |               | Dispatch Blocked      |
+-----------------------+               +-----------------------+
```

---

## Execution Instructions (Docker)

1. Navigate to the deployment directory:
   ```bash
   cd deployment
   ```
2. Start the container stack:
   ```bash
   docker compose up -d
   ```
3. Open your browser at `http://localhost:8069` to initialize your Odoo database.

---

## Technology Stack

- **ERP Framework:** Odoo 17.0
- **Database:** PostgreSQL 15
- **Languages:** Python 3, XML, QWeb
- **Deployment:** Docker Compose

---

## Author

- **Author:** Youssef Fellah ([ind4x_](https://github.com/ind4x))
- **Institution:** Mundiapolis University, Engineering Cycle
