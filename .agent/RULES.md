# 📋 MInfra — Reglas del Asistente & Convenciones

## 🛠️ Stack Tecnológico
* **Frontend:** Next.js 14 (App Router), React, TypeScript, Tailwind CSS, Zustand.
* **Backend:** Python 3.12+, FastAPI, SQLAlchemy (AsyncPG), Alembic, Pydantic v2, ezdxf.
* **Monorepo:** Turborepo + pnpm workspaces.
* **Base de Datos:** PostgreSQL 16 + PostGIS (opcional para geo).
* **Puertos Locales:**
  * Web Frontend: `http://localhost:3000`
  * Backend API: `http://localhost:8000` (Docs en `/docs`)

---

## 📐 Convenciones de Monorepo & Código
1. **Desacoplamiento Geometría/Negocio:**
   * La re-subida de planos DXF solo regenera `PlanoItem` (SVG); jamás debe alterar las asignaciones de `Espacio`, `Persona`, `Bien` o `Documento`.
2. **Tipos Compartidos:**
   * Toda estructura que viaje entre API y Frontend debe reflejarse en `packages/shared-types`.
3. **Migraciones:**
   * Cualquier cambio de modelo en `apps/api/app/models/` debe acompañarse de una migración de Alembic versionada en `apps/api/alembic/versions/`.
4. **Proxy Interno:**
   * `apps/web/next.config.js` reenvía `/api/:path*` a `http://127.0.0.1:8000`.

---

## 🛡️ Barrera Arquitectónica de MInfra (Protección Estricta)
* 🔒 **Stack Inmutable:** El stack oficial de MInfra es **Python 3.12+ FastAPI + PostgreSQL + Next.js 14**. Queda estrictamente prohibido cambiar el stack o sustituir componentes clave a menos que el usuario lo solicite de manera explícita y masiva desde `Projects`.
* 🔒 **Motor CAD / DXF Blindado:** El pipeline de procesamiento de planos (`ezdxf`, algoritmos de ray-casting espacial, detección de capas, normalización de coordenadas y renderizado vectorial SVG) es crítico y estable. No debe ser modificado, refactorizado ni alterado durante tareas generales de workspace o ajustes transversales.

---

## 🚫 Restricciones Obligatorias
* ❌ **NO cambies el stack backend de MInfra:** Mantener siempre FastAPI + AsyncPG + Alembic.
* ❌ **NO modifiques el motor de interpretación DXF:** Mantener el parser `ezdxf` y su lógica de coordenadas y capas.
* ❌ **NO instales paquetes con npm/yarn:** Usar siempre `pnpm`.
* ❌ **NO agregues dependencias innecesarias:** Mantener el bundle liviano para servidor OCI micro.
* ❌ **NO alteres la jerarquía espacial:** Sede -> Edificio -> Piso -> Espacio.

---

## 🔄 Protocolo de Sesión
1. **Al iniciar:** Leer `.agent/STATE.md`.
2. **Al finalizar:** Actualizar `.agent/STATE.md` con las tareas realizadas y pendientes.

