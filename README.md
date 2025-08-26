BOCETO INICIAL:
Alcance 

Gestionar proyectos audiovisuales: planificación, recursos, versiones/aprobaciones y finanzas hasta la entrega.

Actores

Cliente · Productor/Jefe de Proyecto · Técnicos/Editor · Administración · Proveedor · Sistemas externos (pagos, nube).

Casos de uso (core)

Crear/planificar proyecto

Asignar tareas y reservar personas/equipos

Subir versiones, comentar y aprobar

Presupuestar, facturar y registrar pagos/gastos

Entregar y cerrar proyecto

Clases (agrupadas)

Proyecto & ejecución

Proyecto, Tarea, Rodaje, Ubicacion, PermisoRodaje

Recurso (abstracta) → Persona | Equipo

ReservaRecurso (bloqueos calendario)

Usuario, Rol, Auditoria

Media & aprobación

ActivoMultimedia, Version, ComentarioRevision, Aprobacion, Entrega

Finanzas

Cliente, Presupuesto, Factura, Pago, Gasto, Proveedor

Relaciones (clave)

Cliente 1—* Proyecto

Proyecto 1—* (Rodaje, Tarea, Activo, Entrega, Presupuesto, Factura, Gasto)

Rodaje 1—* ReservaRecurso; ReservaRecurso *—1 Recurso (Persona/Equipo)

Activo 1—* Version —* ComentarioRevision; Version —0..1 Aprobacion → Entrega

Factura 1—* Pago; Gasto *—1 Proveedor

Reglas/invariantes

Sin solapes: un Recurso no puede tener dos Reservas confirmadas en el mismo intervalo.

Permisos: Rodaje confirmado requiere PermisoRodaje válido.

Entrega: solo una Version aprobada se marca para entrega final.

Costos: costoReal Proyecto = Σ Gastos + reservas (tarifa×duración) ± otros ítems.

No funcionales mínimos

Roles/ACL, auditoría de cambios, media en nube (guardar metadatos/URLs), validaciones de reservas
