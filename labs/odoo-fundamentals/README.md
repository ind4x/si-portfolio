# Odoo 17 Fundamentals Lab

This laboratory implements the `gestion_etudiants_manuel` custom addon for Odoo 17.0,
exploring core ERP architecture: ORM relational modeling, XML view inheritance,
integrity constraints, and role-based access control (RBAC).

---

## Lab Structure

```text
odoo-fundamentals/
├── README.md                          # Technical specification and laboratory overview
├── odoo-module/                       # Custom Odoo 17 Addon package
│   ├── __manifest__.py                # Module metadata, dependencies, and view declarations
│   ├── __init__.py                    # Python package entrypoint
│   ├── models/                        # ORM Business Entities
│   │   ├── etudiant.py                # Student model with relational and computed fields
│   │   ├── professeur.py              # Professor model with contact and department relations
│   │   └── cours.py                   # Academic course entity with schedule mappings
│   ├── views/                         # XML User Interface Definitions
│   │   ├── etudiant_view.xml          # Tree, Form, Kanban, and Search views for students
│   │   ├── professeur_view.xml        # Tree and Form views for faculty
│   │   └── cours_view.xml             # Course listings and schedule forms
│   └── security/                      # Authorization & Security Configuration
│       ├── security.xml               # Role groups (Student, Professor, Academic Admin)
│       └── ir.model.access.csv        # Access Control List (ACL) permission matrix
└── reports/                           # Academic analysis and exercise responses
    ├── TP1-TP2-REPONSES.md            # Installation, Docker provisioning, and baseline models
    ├── TP3_REPONSES.md                # Python @api.constrains vs PostgreSQL SQL constraints
    ├── TP4-REPONSES.md                # Advanced UX: Kanban cards, Graph metrics, Search filters
    └── TP5-REPONSES.md                # Multi-level security, record rules, and group policies
```

### File Responsibilities

- **`models/`**: Implements business logic using `@api.depends`, `@api.onchange`, and `@api.constrains`.
- **`views/`**: Declares declarative UI screens utilizing responsive bootstrap-based Odoo form components.
- **`security/ir.model.access.csv`**: Granular CRUD permission matrices mapping user groups to internal tables.

---

## Architecture & Relational Schema

```text
+-------------------+        1:N         +-------------------+
|     cours.py      |<-------------------|   professeur.py   |
| - nom             |                    | - nom             |
| - code            |                    | - departement     |
| - credits         |                    | - email           |
+-------------------+                    +-------------------+
          |
          | N:M (enrollments)
          v
+-------------------+
|    etudiant.py    |
| - matricule       |
| - nom, prenom     |
| - date_naissance  |
| - moyenne (comp)  |
+-------------------+
```

---

## Execution Instructions

1. Copy or mount `odoo-module/` into your Odoo addons path:
   ```bash
   cp -r odoo-module /path/to/odoo/custom_addons/gestion_etudiants
   ```
2. Update the apps list in Odoo Developer Mode:
   - Navigate to **Apps** -> **Update Apps List**.
   - Search for `gestion_etudiants_manuel` and click **Activate**.

---

## Technology Stack

- **Platform:** Odoo 17.0 Community
- **Backend:** Python 3, PostgreSQL
- **Frontend:** XML, QWeb

---

## Author

- **Author:** Youssef Fellah ([ind4x_](https://github.com/ind4x))
- **Institution:** Mundiapolis University, Engineering Cycle
