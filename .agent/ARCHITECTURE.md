# 🏛️ MInfra — Arquitectura y Topología

## 🌐 Visión General
Monorepo de Space Management, Facility Management y Visor CAD interactivo para instituciones universitarias y corporativas.

---

## 📂 Mapa del Monorepo
```
MI/
├── .agent/                      # Memoria de trabajo (RULES, STATE, ARCHITECTURE)
├── apps/
│   ├── web/                     # Frontend Next.js 14 (App Router, Tailwind, Zustand)
│   │   ├── app/                 # Rutas de página (Dashboard, Visor CAD, Compliance)
│   │   └── components/          # dxf-viewer.tsx, item-info-popup.tsx, compliance-view.tsx
│   └── api/                     # Backend FastAPI (Python 3.12, AsyncPG, Alembic, ezdxf)
│       ├── app/
│       │   ├── api/v1/routes/   # auth, spaces, people, assets, documents
│       │   ├── models/          # SQLAlchemy async models
│       │   └── services/        # dxf_processor, compliance_service
│       └── alembic/versions/    # Migraciones 0001 a 0005
├── packages/
│   └── shared-types/            # Interfaces y tipos compartidos en TypeScript
└── scripts/
    ├── dev.sh                   # Iniciar desarrollo local unificado
    ├── deploy.sh                # Despliegue automático en OCI
    └── db-reset.sh              # Reset y seed de base de datos
```

---

## 🗄️ Jerarquía del Modelo de Datos
```
Sede ──> Edificio ──> Piso ──> Espacio ──┬──> PlanoItem (Geometría SVG)
                                        ├──> EspacioPersona (Responsable / Ocupante)
                                        ├──> Bien / Activo (Patrimonio / QR)
                                        └──> Documento (Certificado / Semáforo)
```
