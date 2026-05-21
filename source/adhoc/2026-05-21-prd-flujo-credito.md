# **Documento de Requerimiento de Producto**

# **Flujo Crédito \- Préstamos**

| Información Clave |  |
| :---- | :---- |
| **Proyecto** | Flujo Crédito \- Préstamos |
| **Foco Estratégico** | Digitalización del proceso, Trazabilidad y Control Interno |
| **Versión** | 2.0 |
| **Últimas Modificaciones** | 19/11/25 Creación del Documento 18/12/25 Se agrega la sección “Dependencias e Incertidumbres” 30/12/25 Se agrega la medida de éxito de la funcionalidad. 26/01/26 Definición del MVP ajustando secciones 4 y 5\. 12/02/26 Ajustes de alcance del requerimiento. Se marcan necesidades de definiciones. Se actualiza estado de dependencias 08/04/26 Armado final del PRD |

## **1\. Visión y Propósito**

**Propósito:** Transformar el proceso de solicitud, gestión y administración de crédito/préstamos en un servicio autónomo y digital para el Empleado de Grupo.

**Visión:** El empleado podrá autogestionar su solicitud, recibiendo una oferta calculada automáticamente por el sistema de manera general (no distinguida por cliente) y los fondos de manera eficiente. El Backoffice obtendrá control y la capacidad de gestionar casos especiales y cumplimiento de compliance. El sistema debe proyectarse como multitenant, permitiendo que en el futuro se ofrezca el servicio a empresas externas al grupo, separando los usuarios por organización (tenant).

## **2\. Objetivo e Impacto Estratégico**

| Objetivo (El "Qué") | Impacto (El "Por Qué") |
| :---- | :---- |
| **Aumentar la Adopción** | Acceso inmediato a beneficios crediticios. |
| **Mejorar la Eficiencia** | Reducción de carga manual en Backoffice. |
| **Garantizar el Compliance** | Centralización de T\&C y documentos auditables. |

## 

## **3\. Alcance del Producto (MVP)**

### **A. Experiencia del Usuario (APP)**

* **Call to Action (CTA)**: El usuario visualiza en el Home la posibilidad de tomar un crédito.  
* **Opciones de Crédito**: Se presentan **3 opciones** preaprobadas basadas en el segmento del usuario.  
* **Firma Unificada**:  
  * El proceso de aceptación utiliza una "firma unificada" que, legalmente, dispara la firma de 5 documentos distintos.  
  * Para el usuario es un solo flujo; el resultado es un único PDF con los 5 documentos embebidos para descarga.  
* **Confirmación y Desembolso**: Una vez confirmada la operación, el sistema crea el préstamo y dispara la transferencia de fondos al empleado desde la cuenta recaudadora.

### **B. Backoffice de Gestión (Probablemente en Watson)**

* **Configuración de Préstamos (ABM)**:  
  * Permitir crear nuevas versiones de préstamos (tasas, plazos).  
  * Los cambios de tasa no son retroactivos; solo aplican a nuevos créditos.  
  * Soportar sistemas de amortización (Francés inicialmente, con estructura para cuotas variables en el futuro).  
* **Gestión de Usuarios**:  
  * Habilitar/deshabilitar usuarios aptos para crédito (Flags).  
  * Visualizar documentos asociados y estados de deuda.  
* **Gestión Operativa de Novedades**:  
  * Generar y enviar manualmente un archivo de "novedades" (solo préstamos nuevos) a la Mantovana alrededor del día 20 dade ca mes.  
  * El matching de usuarios se realizará por **CUIL/DNI**.

### 

### 

### 

### 

### **C. Ciclo de Cobro y Liquidación**

* **Recupero por Nómina**: El descuento de las cuotas se realiza a través de la liquidación de sueldo ejecutada por la Mantovana.  
* **Doble Check (Conciliación)**: El sistema de préstamos debe recibir la información de liquidación para confirmar que la cuota fue efectivamente retenida y actualizar el estado del préstamo.  
* **Transferencia Global**: Mensualmente, la Mantovana .transfiere a PERc el monto total recaudado por todos los créditos descontados ese mes

## **4\. Casos Excepcionales y Cancelación**

* **Derecho de Arrepentimiento (10 días)**:  
  * Por ley, el usuario tiene 10 días para arrepentirse sin costo.  
  * Este flujo será **manual** debido a la complejidad de revertir pagos y descuentos ya informados a la nómina.  
* **Cancelación Anticipada**: Se define como un tipo de resolución operativa distinta al arrepentimiento, que puede incluir costos asociados o multas. **Manual**  
* **Incidencias (Despidos/Mora)**:  
  * En caso de despido, se puede cobrar el saldo desde la liquidación final. **Manual**  
  * El Backoffice debe permitir bloquear usuarios por incidencias o mora. **Manual**

## 

## **5\. Definiciones Técnicas y Dependencias**

* **Tecnología**: Pendiente de definición (Lambda, Java, TypeScript), sujeto a las capacidades de integración con Watson.  
* **Fondeo**: Los préstamos se realizan desde la **cuenta recaudadora de PERc**.  
* **Validación de Saldo**: Si no hay fondos suficientes en la cuenta recaudadora, rechaza la tx y queda en pendiente.  
* **Discovery**: Se planea un mes inicial de entendimiento técnico y definición del pipeline de CI/CD antes de comprometer estimaciones finales.

## 

## **6\. Fuera de Scope y Próximas Etapas (Roadmap Sugerido)**

* **Que el usuario calcule su propio préstamo.**  
* **Notificar por medio de push.**  
* **Solicitar cancelación parcial.**  
* **Préstamos Personalizado desde el lado de BO.**  
* **Scoring en Tiempo Real.**  
* **Créditos Múltiples.**  
* **Créditos Simultáneos.**  
* **Expansión a Terceros. Solo se contempla la posible estructura Multitenant.**  
* **V2: Préstamos entre rangos**: El usuario podrá elegir el monto dentro de un rango preaprobado (en lugar de 3 opciones fijas).  
* **V3: Préstamos Custom**: Definición de préstamos a medida desde el Backoffice (fuera de scope inicial).