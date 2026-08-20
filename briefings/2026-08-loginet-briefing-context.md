# Briefing PRE — Loginet — 2026-08-19

**Cliente:** Loginet (razón social: LoginetSA)
**Contactó:** a preguntar — el input recibido fue únicamente el nombre del cliente y la URL de su web (`Loginet https://loginetsa.com/`), sin quién hizo el contacto ni por qué canal.
**Asistentes Quarks:** a preguntar — no provisto.
**Asistentes Loginet:** a preguntar — no se identificó ningún nombre propio en la web pública ni en el input.
**Página del cliente:** [loginetsa.com](https://loginetsa.com/)
**Disparador declarado:** a preguntar — el input crudo no incluye el motivo del contacto ("me llamó tal persona porque tiene tal problema"). Este es el gap más grande de este documento: todo lo que sigue está inferido de la web pública de la empresa y de conocimiento de industria, no de nada que el cliente haya dicho todavía.

> **Nota de proceso:** con un input tan mínimo (nombre + URL, sin trigger, sin asistentes), este documento se apoya casi enteramente en investigación externa (web del cliente + búsqueda de industria). Todo lo que no sea observación directa de la web pública está marcado como interpretación o como gap explícito. La reunión de briefing en sí debe cerrar la mayoría de los huecos de este documento.

---

## 1. Contexto de empresa y rubro

**Observación (web pública, [loginetsa.com](https://loginetsa.com/)).** Loginet es un operador logístico argentino especializado en comercio exterior: transporte marítimo, aéreo y terrestre, gestión aduanal y depósitos fiscales. La web menciona explícitamente servicios de consolidación/desconsolidación de mercadería, exportación de perecederos y carga general, transporte multimodal, y asesoría en documentación de comercio exterior para el despacho aduanero. La empresa se presenta como fundada por profesionales con trayectoria en el mercado local — la web da cifras distintas según la fuente (una versión dice "+25 años de experiencia", otra referencia externa dice "+15 años"; **a confirmar** cuál es la correcta).

**Observación.** Mencionan tres pilares corporativos ("Conocimiento, Conducta, Actitud proactiva") y un "servicio inteligente que se adapta a las políticas y estrategias" del cliente, además de "acuerdos con socios estratégicos a nivel global" sin nombrarlos.

**Interpretación.** Loginet es un **operador logístico / freight forwarder de tamaño chico-a-mediano**, no una naviera ni un despachante de aduana per se (aunque ofrece el servicio de gestión aduanal, probablemente vía despachante asociado — **a confirmar**). Vende principalmente a empresas que exportan/importan (perecederos y carga general), sin un vertical de cliente único declarado. (chat, no artefacto — inferido de la web, 2026-08-19)

**Gap.** No se sabe: tamaño del equipo, facturación, volumen de operaciones mensuales, si tienen oficinas fuera de Argentina, ni si el "acuerdo con socios estratégicos globales" implica partners tecnológicos o solo comerciales/navieras.

## 2. Glosario específico del cliente y del rubro

| Término | Significado en este contexto |
| --- | --- |
| **Freight forwarder / operador logístico** | Intermediario que organiza el transporte de mercadería entre exportador e importador, sin ser el transportista final. Rol que ocupa Loginet. |
| **Despachante de aduana** | Profesional matriculado habilitado para representar al importador/exportador ante la Aduana. La web de Loginet no aclara si tienen despachante propio o tercerizado — **a preguntar**. |
| **Depósito fiscal** | Recinto habilitado por AFIP/Aduana donde la mercadería permanece bajo control aduanero antes de nacionalizarse o exportarse. Loginet lo ofrece como servicio ("red nacional de alianzas"). |
| **Consolidado / desconsolidado** | Agrupar cargas de varios clientes en un mismo contenedor/envío (consolidado) o separarlas al llegar a destino (desconsolidado). Servicio explícito de Loginet. |
| **Multimodal** | Transporte que combina más de un medio (marítimo + terrestre, por ejemplo) bajo una sola gestión. |
| **VUCEA (Ventanilla Única de Comercio Exterior Argentina)** | Plataforma estatal que centraliza trámites de comercio exterior entre organismos públicos. Prorrogada hasta el 31/12/2026, con foco en interoperabilidad. (industry-knowledge) |
| **VUMA / VUA** | Ventanillas únicas sectoriales en desarrollo: VUMA para operatoria portuaria/marítima, VUA para el equivalente aéreo. (industry-knowledge) |
| **Declaración Aduanera Digital / Carpeta Digital** | Iniciativas de Aduana Argentina hacia un esquema 100% electrónico de declaración y documentación del operador, en curso durante 2026. (industry-knowledge) |
| **OEA (Operador Económico Autorizado)** | Certificación aduanera que simplifica controles para operadores de bajo riesgo verificado; su programa se está ampliando en 2026. (industry-knowledge) |
| **OLES (Operadores Logísticos Habilitados)** | Figura que consolida la operatoria de depósitos/logística habilitada ante Aduana. Relevante si Loginet opera depósito fiscal propio. (industry-knowledge) |
| **MIP** | Nuevo sistema en desarrollo por Aduana para regímenes especiales (importación temporal, drawback, zonas francas). (industry-knowledge) |

## 3. Dolores del rubro y del caso

**Del rubro (interpretación, industry-knowledge).** El comercio exterior argentino está en medio de una ola de digitalización estatal fuerte para 2026 (VUCEA, VUMA, VUA, Declaración Aduanera Digital, Carpeta Digital, MIP, expansión de OEA, y discusión de un nuevo Código Aduanero). Esto típicamente genera dos tipos de dolor en operadores logísticos chicos/medianos: (a) presión para digitalizar procesos internos y de cara al cliente al mismo ritmo que exige el Estado, y (b) fragmentación — múltiples sistemas/ventanillas que un operador tiene que operar o integrar en paralelo, muchas veces a mano (Excel, mail, WhatsApp) por no tener sistema propio.

**Del caso puntual.** **Gap total** — no hay ninguna transcripción ni comunicación del cliente todavía. La web no menciona ningún sistema, portal de cliente, tracking online propio (más allá de "seguimiento 24/7" y "sistema de rastreo de contenedores", que suena más a mensajería informal con el cliente que a un portal self-service). Es una **hipótesis a validar en la reunión**, no un hecho: el disparador del contacto podría ser (i) construir un portal/tracking propio para sus clientes, (ii) digitalizar el back-office de gestión de embarques/documentación, (iii) algo completamente distinto no relacionado a comex (ej. un sistema interno de RRHH o facturación). **No inventar el motivo antes de la reunión.**

## 4. Usuarios

**Interpretación, no confirmada.** Si el proyecto toca la operación de Loginet, los roles típicos de un operador logístico de este tipo serían: personal de operaciones/comex (arma los embarques, gestiona documentación), personal comercial (cotiza y sigue clientes), y clientes finales (exportadores/importadores que quieren visibilidad de su carga). **Gap explícito:** no se sabe si el proyecto involucra usuarios externos (clientes de Loginet con acceso a un portal) o es 100% interno.

## 5. Stakeholders / personas en la mesa

**Gap total.** No hay ningún nombre de persona disponible — ni en el input, ni en la web pública de Loginet (no tiene una sección de equipo/quiénes-somos con nombres identificados). **A preguntar antes o al inicio de la reunión:** quién de Loginet participa (rol/cargo) y quién de Quarks va a asistir.

## 6. Riesgos y restricciones relevantes

- **Regulatorio — eje probablemente relevante, profundidad a confirmar en la reunión.** Cualquier sistema que toque documentación de embarques, depósito fiscal o gestión aduanal en Argentina corre bajo el paraguas de AFIP/Aduana (Código Aduanero, VUCEA y las ventanillas sectoriales en desarrollo). Si el proyecto es un portal de tracking o gestión documental, hay que entender si necesita integrarse (o al menos coexistir) con estas plataformas estatales, y si Loginet ya tiene certificación OEA u opera bajo el régimen OLES. (industry-knowledge)
- **Legal.** Sin datos aún — depende de qué tan integrado esté el sistema propuesto con datos de terceros (clientes de Loginet, navieras, Aduana). A relevar en la reunión.
- **Stack tecnológico.** La web no menciona ningún sistema/plataforma existente más allá de "seguimiento" y "rastreo" genéricos — no hay evidencia de un TMS, ERP o CRM propio. **Pregunta central a resolver:** ¿parten de cero (Excel/mail/WhatsApp) o ya tienen algún sistema que haya que integrar o reemplazar?
- **Horizonte de tiempo / urgencia.** A preguntar — sin ningún dato. Dado el contexto regulatorio 2026 (VUCEA prorrogada a fin de año, nuevas ventanillas en rollout), vale la pena indagar explícitamente si alguna fecha de Aduana está empujando el timeline del cliente.

## 7. Perfil de experiencia previa

**Gap total — no hay evidencia para inferir un arquetipo.** No se sabe si Loginet viene de un desarrollo fallido con otro proveedor, si es greenfield (probable, dado que no se detecta sistema propio en la web), o si es una empresa consolidada innovando dentro de su operación. Es una de las primeras preguntas a hacer en la reunión, no algo para asumir de antemano.

## 8. Preguntas de discovery contextualizadas

**Contexto de la empresa**
- ¿A qué tipo de cliente le dan servicio hoy — exportadores de perecederos, carga general, ambos por igual? ¿Hay un sector que concentre la mayoría de la facturación?
- ¿Manejan depósito fiscal propio o tercerizado ("red nacional de alianzas")?
- ¿Tienen despachante de aduana propio o trabajan con uno externo por operación?

**Problema / objetivo de la reunión**
- ¿Qué los trajo a buscar ayuda ahora? ¿Hay algo puntual que cambió (un cliente grande que lo pide, un problema operativo recurrente, presión de Aduana/VUCEA) o es una inquietud general de modernizarse?
- ¿Qué esperan que salga de esta primera reunión — un diagnóstico, ya vienen con una idea de sistema en mente, o quieren explorar posibilidades?
- Hoy, ¿cómo hacen el seguimiento de un embarque de punta a punta — Excel, mail, WhatsApp, algún sistema?

**Usuarios**
- ¿El sistema que tienen en mente es para uso interno de Loginet, para que sus clientes vean el estado de su carga, o ambos?
- Si hay usuarios externos: ¿cuántos clientes activos tienen hoy, y qué tan seguido piden información de estado?

**Horizonte de tiempo / urgencia**
- ¿Con qué plazo cuentan para este proyecto? ¿Hay alguna fecha externa que los presione (un compromiso ya asumido con un cliente, un cambio regulatorio de Aduana, un cierre de ejercicio)?
- ¿Qué pasa si esto no se resuelve en ese plazo?

**Factibilidad / stack**
- ¿Tienen algún sistema hoy (TMS, ERP, planillas compartidas) que haya que integrar o reemplazar?
- ¿Trabajan ya con VUCEA / alguna de las ventanillas sectoriales (VUMA, VUA) de forma directa, o eso queda del lado del despachante?
- ¿Tienen certificación OEA o participan del régimen de Operadores Logísticos Habilitados?

**Experiencia previa**
- ¿Es la primera vez que encaran un desarrollo de software a medida, o ya intentaron algo antes (con otro proveedor o con equipo propio) que no funcionó?

---

## Competidores

**No corresponde en esta etapa.** Sin saber el objetivo de la reunión, no se puede determinar si el proyecto ayuda a Loginet a competir con otros operadores logísticos (caso en que aplicaría) o si es un problema puramente interno (caso en que no aplica). Retomar después de la reunión si corresponde.

---

## Gaps a cerrar en la reunión (resumen)

1. Quién contactó y por qué canal.
2. Motivo/disparador real del contacto (hoy 100% desconocido).
3. Asistentes de ambos lados.
4. Objetivo concreto de la reunión.
5. Horizonte de tiempo / urgencia.
6. Perfil de experiencia previa del cliente.
7. Sistema(s) actuales, si los hay.
8. Si el proyecto involucra usuarios externos (clientes de Loginet) o es 100% interno.

---

*Fuentes consultadas: [loginetsa.com](https://loginetsa.com/), [loginetsa.com/servicios](https://loginetsa.com/servicios/), búsqueda web sobre Loginet Argentina y sobre digitalización de comercio exterior/aduana en Argentina 2026 (VUCEA, VUMA, VUA, OEA, Declaración Aduanera Digital).*
