# Propuesta — Norton, Fuerza de Ventas Inteligente

**Tipo:** cara al cliente · **Deriva de:** [build-context](./2026-09-norton-build-context.md)
**Para:** Martín (cc Tomás)
**De:** Quarks

---

## 1. Lo que entendimos

Hoy la fuerza de ventas de Norton cuenta con información sólida (los tableros que ya arma el equipo de sistemas en Power BI), pero no hay tiempo dedicado a convertir esa información en decisiones del día a día: qué cliente visitar, cuándo, y con qué prioridad. El resultado es que el análisis de performance del equipo termina recayendo en un trabajo manual, la venta se concentra hacia el cierre de cada mes, y oportunidades puntuales (un cliente que dejó de comprar, un producto sin cobertura en un punto de venta) se pierden en el volumen.

## 2. La solución en una frase

Una capa de inteligencia comercial que convierte los datos que Norton ya genera en una **agenda diaria de visitas** para cada vendedor y en un **reporte de eficiencia** para cada jefe de área, sin reemplazar ningún sistema existente.

Tiene dos caras: **A. Vista para el vendedor** (qué hacer hoy) y **B. Panel para el jefe de área** (cómo viene performando el equipo).

## 3. Qué hace: funcionalidad del MVP

**A. Vista para el vendedor**
- Agenda diaria sugerida: qué clientes visitar, priorizados por recencia de compra, comportamiento histórico y comparación contra presupuesto.
- Ruteo por zona, para ordenar las visitas del día de forma eficiente.
- Sugerencia de pedido por cliente, basada en su historial de compra.

**B. Panel para el jefe de área**
- Reporte de eficiencia por vendedor: cumplimiento de visitas, conversión comprador/no comprador, frecuencia, surtido, margen.
- Vista comparativa del equipo, pensada para preparar la reunión de ventas sin necesitar un análisis manual previo.
- Seguimiento de incorporación de nuevos clientes.

**Fuera del MVP (fases futuras)**
- Registro fotográfico y relevamiento en el punto de venta (precio, posicionamiento, competencia).
- Inteligencia competitiva en campo.
- Captura y seguimiento de oportunidades de distribución no cubiertas (puntos de venta sin presencia de la marca).
- Integración con el canal indirecto/distribuidores.

## 4. Cómo se integra con los sistemas de Norton

Esta solución no reemplaza ni Arbalón ni el futuro QAD: **consume** la información que el equipo de sistemas ya modela en Power BI y la transforma en agenda y reportes, sin duplicar ni mover la fuente de verdad de los datos. Está pensada para convivir con la implementación de QAD en curso, y para poder ensamblarse con sus módulos de CRM cuando estén disponibles, en vez de competir con ellos.

## 5. Cómo trabajamos

- **Alineación inicial.** Antes de escribir una línea de código, nos sentamos con el equipo de sistemas y con la fuerza de ventas para confirmar accesos, reglas de negocio (qué define prioridad de visita, cómo se calculan los KPIs) y expectativas de uso diario.
- **Metodología ágil, por fases.** Trabajamos en sprints cortos, con entregas visibles y revisables, para que el equipo de Norton vea avances concretos desde temprano en vez de esperar a un lanzamiento único.
- **Gestión transparente.** Reuniones periódicas, documentación viva del proceso y visibilidad total del estado del proyecto para el equipo de Norton.
- **Validación en campo.** Antes de escalar a toda la fuerza de ventas, probamos la herramienta con un grupo piloto de vendedores y jefes de área, para ajustar antes de un rollout completo.
- **Ownership de largo plazo.** No instalamos algo y desaparecemos: capacitamos al equipo en el proceso, para que la herramienta se sostenga con el uso diario, no con una persona dedicada a mantenerla.

## 6. Roadmap futuro

Una vez validada la base de agenda y eficiencia, el camino natural de expansión incluye:
- Tareas de campo con evidencia fotográfica (precio, posicionamiento, competencia) en el punto de venta.
- Captura y seguimiento de oportunidades de distribución no cubiertas, asignables al vendedor de zona.
- Incorporación del canal indirecto, cuando exista la conectividad necesaria con la red de distribuidores.
- Integración más profunda con los módulos de QAD a medida que su implementación avance.

## 7. Próximos pasos

- Norton comparte el material de base: capturas de los tableros de Power BI en uso, el reporte de cobertura ya armado, el detalle de los 3 canales de venta y el tamaño real de la fuerza de ventas.
- Coordinamos una conversación breve con el equipo de sistemas (Fede Pinto) para confirmar accesos técnicos y el alcance del módulo CRM de QAD.
- Con eso, arrancamos un discovery corto para cerrar reglas de negocio y accesos, y dar inicio a la primera fase.

---

**Falta antes de enviar:** hoja de presupuesto (equipo/tiempo/costo, a criterio del PM), diagramas de flujo si se quieren sumar como apéndice, y una revisión/"endulzada" de lenguaje con el equipo antes de mandarla. El cliente todavía tiene que confirmar el material pedido en la minuta — sin eso, el discovery de la sección 7 no puede arrancar en los tiempos que sugiere el texto.
