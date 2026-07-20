# Ingesta — Call Amfays <> PERc (2026-07-17)

- **Fuente (transcript):** [../../source/meetings/2026-07-17-call-amfays-documento-prestamo.md](../../source/meetings/2026-07-17-call-amfays-documento-prestamo.md)
- **Shape:** meeting (relevamiento conjunto del documento de préstamo / ayuda económica con la mutual **AMFAYS**)
- **Participantes:** Olivier (PM Quarks), Marcos Perez (dev Quarks), Sebastián Cárdenas "Seba" (PO PERC), Nicolás Ortiz "Nico" (gestión préstamos/mutual, PERC), + lado **AMFAYS** (la mutual): **Ignacio** (agente comercial), **Guido** ("Mido/Ido"; recibió el Excel de Olivier, resuelve dudas con su compliance), **Lean**, **Federico Fernandez**. *(El transcript solo separa "Me" = Olivier vs. "Them" = todos los demás; no atribuye citas individuales del lado "Them" con fiabilidad.)*
- **Contexto:** Olivier + Marcos bajaron **todos los campos del documento/template de la ayuda económica a un Excel** y lo revisaron **campo por campo con AMFAYS** para definir *(a)* cuáles son **obligatorios** y *(b)* — con Seba — cuáles PERC **ya captura** vs. tiene que integrar al flujo. **Este documento era la dependencia bloqueante "documento AMFAYS" abierta desde 2026-07-08** (ver strategy §Tensions + [pendientes-produccion §15/§4](../../knowledge/product/pendientes-produccion.md)). El call **la destraba parcialmente**: quedan definiciones de compliance de AMFAYS para el lunes 2026-07-20.

---

## 1. Qué es el instrumento (contexto de negocio — NUEVO en el brain)

- **(observation)** **AMFAYS es la mutual** que provee el instrumento. El "préstamo" es técnicamente una **ayuda económica** contra **retención de haberes** por la empresa, bajo un **código de descuento privado aprobado por INAES**. PERC/Quarks construyen el módulo que arma y autocompleta el documento; AMFAYS es el proveedor del crédito, no PERC. — [source](../../source/meetings/2026-07-17-call-amfays-documento-prestamo.md)
- **(observation)** AMFAYS opera con **banca individuo / banca mayorista / fideicomiso financiero**. Tiene experiencia integrando "comercializadores" que generan préstamos desde su propio sistema y migran los datos al de AMFAYS.
- **(observation)** **Segmentación por grupos (A/B/C), no scoring individual:** PERC puede segregar clientes y ofrecer el préstamo (y tasa) por grupo. Consistente con la definición previa del feature ("las 3 opciones se basan en el segmento, no en scoring").
- **(observation)** **Objetivo compartido explícito (AMFAYS lo verbaliza):** que el empleado complete **lo mínimo** — "monto y cantidad de cuotas, y aceptar" — y PERC **autocompleta todo el resto** con lo que ya tiene (algunos campos "hardcodeados", ej. empleador, porque PERC ya sabe la empresa).
- **(observation)** **Securitización / fideicomiso financiero = fondeo a futuro.** Nico: "eso lo vamos a ir viendo más a futuro; la idea es tenerlo preparado". Motiva pedir hoy datos que hoy no parecen necesarios (legajo, CBU larga) por un **riesgo empresa** distinto al riesgo actual.

## 2. ⭐ Clasificación de campos del documento (resultado sustantivo — Type A)

Definición de **obligatoriedad** acordada en el call (columna "disponible en PERC" es indicativa de lo que se dijo; el cruce técnico fino queda para Olivier + Seba). Los marcados **[compliance lunes]** los confirma AMFAYS el 2026-07-20.

| Campo | ¿Obligatorio? | Notas |
|---|---|---|
| Nombre y apellido | Sí | Disponible en PERC |
| DNI / documento de identidad | Sí | Trivial, sin duda |
| Lugar de nacimiento | **[compliance lunes]** | Duda de AMFAYS; a confirmar |
| Datos fiscales (CUIT/CUIL, Banco Central) | Sí | Figura en el DNI |
| Teléfono particular (= celular) | Sí | |
| Redes sociales / referencias | **No** | PERC no las pide por política |
| Edad | Sí | Se deriva de fecha de nacimiento (para seguro) |
| Correo electrónico | **Optativo** | |
| Empleador actual + CUIT empleador + condición | Sí | PERC lo tiene / lo "hardcodea" (conoce la empresa) |
| Antigüedad | Sí | PERC/RRHH lo tiene |
| **Número de legajo** | Sí (condicionado) | Depende de qué exige la empresa/RRHH para el descuento. Olivier: "lo exigían sí o sí para el descuento"; **Seba: está en el endpoint (nº de usuario), disponible, hay que enviarlo.** Comentario acordado: *chequear con RRHH*. |
| Cargo / categoría / sección | **No** (para AMFAYS) | Dato comercial, no operativo; útil solo si PERC quiere segmentar |
| Actividad / profesión | **No** | "Empleado" por default |
| Domicilio laboral (= domicilio de la empresa) | Sí | Por instancia legal/policial |
| Teléfono interno laboral | **No** | |
| **Sueldo NETO** | Sí | Riesgo lo necesita para la matriz (relación cuota/ingreso). **Neto, no bruto.** |
| CVU (billetera, corta) | Sí | Cuenta de la billetera PERC |
| Banco pagador de haberes | Sí | |
| **CBU larga (banco pagador)** | Recomendado / a criterio de riesgo | AMFAYS sugiere capturarla **además** de la CVU corta + dejar espacio para un 2º CBU: plan B de cobranza si el empleado renuncia (cobro por cámara/COELSA) en escenario de securitización. Formulario de autorización existe. |
| **Número SAEM/SAIN** | Sí | Nº **correlativo de 14 dígitos, autogenerado por el sistema de PERC** (no suministrado por persona). AMFAYS lo necesita. |
| Datos del préstamo (monto, cuotas, valor cuota, mes inicio, TNA, CFT, total a reintegrar, comisión precancelación, interés compensatorio) | Sí | **Los completa el Back Office**, no el usuario. Todos disponibles en PERC. |
| Destino de fondos | Sí (parametrizado) | **5 motivos** parametrizables; se llena con **"consumo"** por default |
| Datos familiares / beneficiario / universidad | **No** | |
| Servicios sociales y subsidios | **No** | |
| Declaración jurada PEP | Sí | |
| **Sujeto obligado (sí/no)** | Sí | El campo es obligatorio |
| País + autoridad de emisión + volumen de ingreso + motivo de elección | **Condicional (fila 47)** | Obligatorios **solo si "sujeto obligado" = sí**. AMFAYS: dudan que algún empleado lo sea; se puede correr contra base. |

- **(decision, en principio)** Regla condicional: **"sujeto obligado = sí"** activa como obligatorios los 4 campos de PEP/sujeto-obligado (país, autoridad de emisión, volumen de ingreso, motivo). Si "no", no aplican.
- **(observation → método)** AMFAYS propone un **ida y vuelta**: marcar todo lo dudoso como obligatorio **ahora**, PERC devuelve "estos datos no los tengo", AMFAYS valida con **legales** cuáles se pueden sacar. Segunda revisión.

## 3. Formato del documento (definiciones de diseño — relevante para firma/sábana)

- **(decision, en principio — AMFAYS OK comercial, falta ver modelo final)** Se puede **cambiar el FORMATO** del documento (checkboxes "de lapicera" y campos sí/no → **texto**) para facilitar el **ingreso dinámico** y la **visualización en la app**. Restricción de AMFAYS: **no se puede alterar el CONTENIDO**, solo la forma; y necesitan **ver un modelo final** para verificar.
- **(observation) El usuario final NO carga nada.** PERC **genera el documento final ya autocompletado**; el usuario recibe la versión con todos los datos, aprieta **aceptar**, y **queda guardado**. Consistente con el flujo de firma unificada del MVP.
- **(observation) Multi-formulario → un solo archivo firmado.** El legajo son **8-9 formularios individuales** que **el sistema unifica en UN solo archivo** al momento de firmar; **se firma el conjunto** (no cada uno por separado). **Romper/separar un formulario rompe la validez del legajo.** "Cómo lo arman ustedes es indistinto" mientras se respete no mezclar formularios distintos. → **Informa** la decisión [sábana render-only + N docs](../../decisions/2026-05-20-sabana-no-persiste.md) y la tensión **T&C 5→1**.
- **(observation) El formulario CVU/CBU va SEPARADO** (los bancos lo piden aparte) — es un **anexo**, de uso a criterio de riesgo/futuro (ejecución).

## 4. Firma (aclaración importante — PER-54)

- **(observation) Es firma ELECTRÓNICA, no digital (ley) ni holográfica.** AMFAYS aclara: "le decimos firma digital por costumbre de mercado, pero es un **conjunto de evidencias**" (foto, foto del documento, **prueba de vida** por detección de movimiento, identificación facial) que dan garantía de identidad del firmante.
- **(observation → dependencia de firma) Si los préstamos se securitizan, PERC debe incorporar el proceso de firma/evidencias.** AMFAYS usa su propio proveedor de identidad; sugiere que **PERC use el mismo proveedor/sistema de identidad de su onboarding para la firma**, y que haya una **auditoría** de los métodos de validación de identidad de la billetera para que la firma sea válida (relevante para securitización).

## 5. Prueba en vivo del ida-y-vuelta Mantovana (apertura del call)

- **(observation)** Olivier quiere hacer una **prueba en vivo** del reporte de cuota (mostrar "esto es lo que te va a llegar al mail" con una cuota real). Bloqueado por **falta de entorno**; al generar el archivo **no pudieron hacer entrar una cuota**. Necesitan un **caso de prueba** con reporte → cuota, y a **Gonza** para deployar con mail + forzar un envío. Olivier: "quizás estoy siendo demasiado conservador"; aún no agendó. — Refuerza el bloqueante de **entorno** y el ítem [pendientes §16 (ida-y-vuelta Mantovana)](../../knowledge/product/pendientes-produccion.md).

## 6. Acciones

- **AMFAYS (Guido) →** resolver campos dudosos con su **compliance** y devolver **lunes 2026-07-20** (lugar de nacimiento, datos sensibles, sujeto obligado).
- **AMFAYS (todos) →** agregar/comentar campos faltantes en el **Excel compartido** (link en el chat del call).
- **Olivier →** enviar **mail entre hoy y el martes** confirmando si hay cambios y cerrando el set de datos.
- **Olivier + Seba →** definir **cómo se consiguen técnicamente** los datos: cuáles ya se capturan, cuáles integrar al flujo de captación, cuáles automatizar, cómo se cruzan los sistemas.
- **Etapa 2 (IT, más adelante) →** cómo se renderiza en la app y con qué formato (sistemas de ambos lados).
- **Olivier →** coordinar con **Gonza** la prueba en vivo del reporte Mantovana (requiere entorno + mail).

## 7. Ruteo — destinos durables (PROPUESTOS, requieren OK del PM — Autonomy = propose-and-wait)

- **`knowledge/` — NUEVO (org/negocio): `knowledge/org/amfays.md`** (o `knowledge/market/`) — perfil de **AMFAYS = la mutual proveedora del instrumento**: ayuda económica vía código de descuento privado INAES; banca individuo/mayorista/fideicomiso; su propio compliance, proveedor de firma/identidad y depositario de formularios; segmentación por grupos; securitización como fondeo futuro. Es contexto estructural nuevo.
- **`stakeholders/` — NUEVOS:** `guido-panella.md` (AMFAYS, dueño del relevamiento/compliance del documento; resuelve el lunes) y `ignacio-<apellido>.md` (AMFAYS, agente comercial). *(Apellido de Ignacio no capturado — dejar TODO.)* + fila en `stakeholders/INDEX.md`.
- **`stakeholders/` touchpoints 2026-07-17:** `sebastian` (confirma legajo en endpoint + disponibilidad técnica), `nicolas-ortiz` (framing del instrumento + fondeo/securitización), `marcos-perez` (armó el Excel, presentó formato). Actualizar last-touched.
- **`knowledge/product/features/flujo-credito.md`:**
  - **§Dependencies / §Timeline:** entrada 2026-07-17 — **documento AMFAYS destrabado parcialmente** (relevamiento de campos hecho; definiciones de compliance de AMFAYS el 2026-07-20).
  - **Nueva subsección "Documento / campos AMFAYS"** con la tabla de obligatoriedad (§2) y las definiciones de formato (§3) y firma electrónica (§4).
  - **§Open questions:** nuevos — nº SAEM/SAIN correlativo 14 dígitos autogenerado; CBU larga (criterio de riesgo); campos [compliance lunes].
- **`knowledge/product/pendientes-produccion.md`:** actualizar **§4 (documentos/firma)** y **§15** con el estado del relevamiento; agregar nº SAEM y CBU larga como sub-ítems de captura.
- **`knowledge/strategy.md` §Tensions:** anotar en la tensión del deadline / la de T&C 5→1 que el **relevamiento del documento AMFAYS ya se hizo** (el bloqueante muta de "no entregado" a "definiciones de compliance pendientes lunes 20/7").
- **`decisions/`:** por ahora **no** abrir decisión formal — las definiciones de obligatoriedad/formato son propiedad de AMFAYS y varias quedan pendientes del lunes. Candidata a decisión una vez cerrado: *"Formato del documento a texto + nº SAEM autogenerado + set de campos obligatorios AMFAYS"*.
- **INDEX:** `stakeholders/INDEX.md` (2 nuevos + last-touched); si se crea `knowledge/org/amfays.md`, referenciarlo desde el INDEX de área correspondiente.

## 8. Contradicciones / tensiones con evidencia previa

- **Legajo (§2) — refuerza, no contradice:** confirma el ítem abierto "[Finegans resuelve por legajo; lo levanta Quarks](../../knowledge/product/features/flujo-credito.md)" (2026-06-16) y [pendientes §14](../../knowledge/product/pendientes-produccion.md). AMFAYS lo pide **también** para su lado (descuento + plan B securitización). Sigue pendiente el OK formal de Fefe + el dato.
- **Multi-formulario → 1 archivo (§3) vs. decisión sábana + T&C 5→1:** **coherente** con "sábana render-only + N docs persistidos". Agrega el matiz de AMFAYS: no se pueden **mezclar/separar** formularios sin romper la validez del legajo. No resuelve la tensión T&C 5→1 (número final de docs) pero **acota** el principio: unificar para firmar sí, fusionar el contenido de formularios distintos no. Preservado como refinamiento.
- **Firma electrónica (§4):** alinea con el modelo tentativo "iniciales tipo DocuSign / conjunto de evidencias" (PER-54). Agrega el requisito nuevo de **auditar el proveedor de identidad de la billetera** de cara a securitización. No contradice; amplía la open question legal de firma.
- **Sin tensión estratégica nueva.** El relevamiento es avance esperado sobre una dependencia ya tensionada, no una señal conflictiva.
