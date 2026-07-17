# Proyecto SAEM
# Sistema de Administración de Edificios Multifamiliares
SAEM es una plataforma web/móvil para la gestión operativa y financiera de un edificio de departamentos. El sistema contará con dos roles principales (Administrador y Copropietario) y se caracterizará por una gestión rotativa de la administración (traspaso anual de mando), verificación de pagos semi-manual mediante QR y procesamiento de consumos indexados (lectura de agua).
## 1. Módulo: Gestión de Usuarios y Autenticación
- Alcance: Controlar el acceso seguro a la plataforma.
- Especificaciones Técnicas:
  - Autenticación basada en JWT (JSON Web Tokens) implementando Access Token de corta duración y Refresh Token para mantener la sesión activa de forma segura.
  - Registro de perfiles vinculados directamente a una unidad habitacional (Departamento X).
  - Dos roles definidos con permisos claramente delimitados: Administrador y Copropietario.
## 2. Módulo: Traspaso de Administración (Roles Rotativos)
- Alcance: Permitir que la administración del edificio cambie de manos anualmente entre los mismos copropietarios.
- Especificaciones Técnicas:
  - Delegación de Rol: El Administrador activo tendrá la facultad de buscar a otro Copropietario en el sistema y delegarle el rol de "Administrador" para el siguiente ciclo.
  - Degradación Automática: Al concretar el traspaso, el administrador saliente pierde los permisos de edición y su cuenta se degrada automáticamente a perfil de Copropietario.
  - Historial de Gestión: El sistema mantendrá una bitácora histórica e inmutable de qué copropietario fue administrador en qué año fiscal, protegiendo la integridad de los registros pasados.
## 3. Módulo: Gastos, Ingresos y Consumos (Libro Diario)
- Alcance: Centralizar las finanzas del edificio, el cálculo de expensas y el consumo de servicios básicos.
- Especificaciones Técnicas:
  - Carga Manual de Facturas: El administrador registrará los gastos comunes del edificio (electricidad de áreas comunes, mantenimiento de ascensor, portería, gastos extras del edificio, etc) adjuntando el monto y la factura digital.
  - Lectura de Medidores de Agua: El administrador ingresará manualmente cada mes la lectura del medidor de agua de cada departamento.
  - Motor de Cálculo: El sistema calculará automáticamente la deuda de cada copropietario sumando: Su consumo individual de agua (según el Medidor) + Su saldo lo que debe y otos gasto como luz, etc.
  - Libro Mayor Simplificado: Un reporte visual e histórico de todos los ingresos (pagos aprobados) y egresos (facturas cargadas).
## 4. Modulo : Reclamos y Multas
- Alcance: Gestionar las incidencias del edificio y aplicar penalizaciones a infractores.
- Especificaciones Técnicas:
  - Gestión de Reclamos: Los copropietarios podrán reportar incidentes (ej. luminarias rotas) redactando un texto y adjuntando una fotografía como evidencia. El administrador recibirá una notificación y podrá marcar el reclamo como "Resuelto" o "En Proceso".
  - Gestion de Multas: El administrador podrá emitir multas monetarias a departamentos específicos (ej. ruidos molestos, daños a áreas comunes). La multa requerirá obligatoriamente: Monto, Descripción y una Imagen de Constancia (evidencia). El monto de la multa se sumará automáticamente al saldo deudor del copropietario para el siguiente periodo de pago.
## 5. Módulo: Cobros y Verificación de Pagos
- Alcance: Facilitar el cobro de expensas y conciliar los ingresos del edificio.
- Especificaciones Técnicas:
  - Pago por QR: El administrador subirá la imagen del código QR de su cuenta bancaria.
  - Pantalla de Pago para el Copropietario: Verá el desglose detallado de su deuda (mantenimiento + agua + multas pendientes). Para pagar, transferirá mediante su app bancaria exterior, subirá una captura de pantalla del comprobante de pago a la app y el estado cambiará a "En Verificación".
  - Conciliación Manual: El administrador visualizará el listado de comprobantes subidos y deberá aprobarlos o rechazarlos manualmente tras verificar su cuenta bancaria real. Una vez aprobado, el saldo del copropietario y le llega una notificacion que fue aprovado su pago.
# 6. Módulo: Personal del Edificio y Registros 
- Alcance: Controlar el historial de visitas de mantenimiento y el personal externo.
- Especificaciones Técnicas:
  - Directorio de Personal: Registro de trabajadores recurrentes (personal de limpieza, seguridad, pintores, plomeros).
  - Bitácora de Eventos ("Registros"): El administrador registrará las actividades del día a día del edificio (ej: "Martes 10:00 - Ingresó el pintor Carlos para mantenimiento de fachada. Salida 16:00"). Este registro servirá como el diario histórico de operaciones del edificio para consulta de todos.