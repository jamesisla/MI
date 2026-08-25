# 📍 MInfra — Estado Operativo & Continuidad

* **Proyecto:** MInfra (CAD, Space Management & Facility Management Universitario)
* **Versión Actual:** `v4.3.0`
* **Repositorio:** `https://github.com/jamesisla/MI.git`
* **Rama:** `main`
* **Última Actualización:** 2026-08-25

---

## 🎯 Estado Actual (Sprint Activo)
* **Completado:**
  * ✅ Módulo 0: Visor CAD interactivo DXF con desacoplamiento de capas SVG y rotación 90/180/270°.
  * ✅ Módulo 1: Directorio de Unidades Organizacionales, Personas y Asignación de Roles en Espacio.
  * ✅ Módulo 2: Inventario de Bienes/Activos con trazabilidad de movimientos y códigos patrimoniales.
  * ✅ Módulo 3: Repositorio de Documentos de Compliance normativo (SEC, seguros, permisos) con semáforos de vencimiento y visor PDF embebido.
  * ✅ Demo 1-Click login para Admin y Alumno.

---

## 📋 Próximos Pasos (Backlog Inmediato)
1. [ ] Optimizar el parser de DXF para bloques anidados y cotas complejas.
2. [ ] Añadir reporte exportable en Excel/PDF de la matriz institucional de compliance.
3. [ ] Probar sincronización en vivo mediante WebSockets para traslados de activos.

---

## 🖥️ Despliegue en Servidor OCI
```bash
cd /var/www/sdd-project
bash scripts/deploy.sh
```
