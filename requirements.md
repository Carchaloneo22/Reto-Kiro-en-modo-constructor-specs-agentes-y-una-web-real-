# Requirements Document

## Introduction

Esta especificación describe la landing page estática para el evento **"Kiro en modo constructor: specs, agentes y una web real"**, organizado por BucaraTec, AWS User Group Bucaramanga y UNAB TEC. La página tiene como objetivo informar a los asistentes potenciales sobre la agenda, los ponentes, el lugar y el horario del evento, y debe funcionar correctamente tanto en computadores de escritorio como en dispositivos móviles.

**Datos del evento:**
- Fecha: 12 de septiembre de 2026
- Horario: 9:00 a.m. – 11:00 a.m.
- Lugar: UNAB, salón L51

---

## Glossary

- **Landing_Page**: Página web de una sola pantalla que presenta la información del evento.
- **Hero**: Sección principal visible al cargar la página, que muestra la información esencial del evento.
- **Agenda**: Sección que lista los bloques de actividades con su horario correspondiente.
- **Bloque_de_Agenda**: Unidad mínima de la agenda con hora de inicio, hora de fin, tipo de actividad y descripción.
- **Tarjeta_de_Ponente**: Componente visual que muestra el nombre, cargo y tema de un ponente.
- **Pie_de_Página**: Sección al final de la página que muestra los organizadores del evento.
- **Organizador**: Entidad que patrocina o co-organiza el evento.
- **Dispositivo_Móvil**: Pantalla con ancho de visualización menor o igual a 768 px.
- **Escritorio**: Pantalla con ancho de visualización mayor a 768 px.
- **Visitante**: Persona que accede a la Landing_Page a través de un navegador web.

---

## Requirements

---

### Requirement 1: Sección Hero con información esencial del evento

**User Story:** Como visitante, quiero ver de forma inmediata el nombre del evento, la fecha, el horario y el lugar al cargar la página, para decidir rápidamente si me interesa asistir.

#### Acceptance Criteria

1. THE Landing_Page SHALL mostrar el título del evento "Kiro en modo constructor: specs, agentes y una web real" en la sección Hero.
2. THE Landing_Page SHALL mostrar la fecha del evento "12 de septiembre de 2026" en la sección Hero.
3. THE Landing_Page SHALL mostrar el horario del evento "9:00 a.m. – 11:00 a.m." en la sección Hero.
4. THE Landing_Page SHALL mostrar el lugar del evento "UNAB, salón L51" en la sección Hero.
5. WHEN el Visitante carga la Landing_Page, THE Hero SHALL ser visible en su totalidad dentro del viewport inicial sin necesidad de hacer scroll, en resoluciones de escritorio (≥ 1024 px de ancho) y móvil (≥ 320 px de ancho).
6. WHILE la Landing_Page está cargada, THE Hero SHALL presentar el título con un tamaño de fuente al menos 1.5× mayor que cualquier otro texto dentro de la sección Hero.
7. WHEN el Visitante carga la Landing_Page, THE Hero SHALL completar su renderizado y mostrar todos los datos del evento en un tiempo máximo de 3 segundos bajo una conexión de red de 10 Mbps.
8. IF alguno de los datos obligatorios del evento (título, fecha, horario o lugar) no está disponible al cargar la página, THEN THE Landing_Page SHALL mostrar un mensaje de error indicando que la información del evento no está disponible y no SHALL mostrar la sección Hero con datos parciales.

---

### Requirement 2: Agenda completa con todos los bloques de actividades

**User Story:** Como visitante, quiero consultar la agenda completa del evento con todos sus bloques horarios, para planificar mi asistencia y saber qué actividades se realizarán.

#### Acceptance Criteria

1. THE Landing_Page SHALL mostrar una sección de Agenda que contenga exactamente ocho Bloques_de_Agenda.
2. THE Agenda SHALL mostrar el Bloque_de_Agenda "9:00–9:10 | Observar: fundamentos de programación y panorama de SDD, KDD y Vibe Coding".
3. THE Agenda SHALL mostrar el Bloque_de_Agenda "9:10–9:26 | Practicar: requisitos y anatomía de SDD y KDD".
4. THE Agenda SHALL mostrar el Bloque_de_Agenda "9:26–9:46 | Charla invitada: 'Tendencia: Vibecoding', con José Verbel".
5. THE Agenda SHALL mostrar el Bloque_de_Agenda "9:46–9:56 | Crear: ejemplos comparativos en vivo".
6. THE Agenda SHALL mostrar el Bloque_de_Agenda "9:56–10:00 | Reflexionar: cierre y discusión".
7. THE Agenda SHALL mostrar el Bloque_de_Agenda "10:00–10:15 | Refrigerio".
8. THE Agenda SHALL mostrar el Bloque_de_Agenda "10:15–10:55 | Workshop práctico 'Kiro Express': construir Flappy Kiro".
9. THE Agenda SHALL mostrar el Bloque_de_Agenda "10:55–11:00 | Cierre".
10. THE Agenda SHALL presentar los Bloques_de_Agenda en orden cronológico ascendente de inicio de 9:00 a 11:00.
11. WHEN el Visitante accede a la Landing_Page, THE Agenda SHALL mostrar la hora de inicio, la hora de fin y la descripción de la actividad para cada Bloque_de_Agenda, sin requerir interacción adicional del Visitante.
12. IF la sección de Agenda no puede renderizarse, THEN THE Landing_Page SHALL mostrar un mensaje de error indicando que la agenda no está disponible en ese momento, preservando el resto del contenido de la página.
13. THE Agenda SHALL ser completamente visible en viewports de ancho mínimo de 320 px sin requerir desplazamiento horizontal, mostrando todos los Bloques_de_Agenda en una sola columna cuando el ancho disponible sea menor a 768 px.

---

### Requirement 3: Identificación del ponente por bloque de agenda

**User Story:** Como visitante, quiero saber quién habla en cada bloque de la agenda, para conocer a los presentadores y evaluar su relevancia para mí.

#### Acceptance Criteria

1. WHEN el Visitante consulta el Bloque_de_Agenda "9:26–9:46 Charla invitada: 'Tendencia: Vibecoding'", THE Agenda SHALL mostrar el nombre completo del ponente asignado a ese bloque.
2. THE Agenda SHALL diferenciar visualmente los bloques con ponente asignado de los bloques sin ponente asignado, utilizando un indicador visible (como un ícono, etiqueta o sección de nombre, no necesariamente el nombre completo) presente en los bloques con ponente y ausente en los bloques sin ponente.
3. IF un Bloque_de_Agenda no tiene ponente asignado, THEN THE Agenda SHALL omitir el campo de ponente para ese bloque y no mostrar ningún valor vacío, placeholder ni guion en su lugar.

---

### Requirement 4: Sección de ponentes con tarjetas individuales

**User Story:** Como visitante, quiero ver la información de cada ponente en una tarjeta dedicada, para conocer su perfil y el tema que presentará.

#### Acceptance Criteria

1. THE Landing_Page SHALL mostrar una sección de Ponentes que contenga exactamente dos Tarjetas_de_Ponente.
2. THE Landing_Page SHALL mostrar una Tarjeta_de_Ponente para "Juliana Ramirez A." que incluya su nombre, su cargo "Semi Senior Dev FinTech y Líder de AWS User Group Bucaramanga" y el título de su charla.
3. THE Landing_Page SHALL mostrar una Tarjeta_de_Ponente para "José Verbel" que incluya su nombre, su cargo o rol como ponente y el nombre de su charla "Tendencia: Vibecoding".
4. WHILE la sección de Ponentes está visible, THE Landing_Page SHALL presentar las dos Tarjetas_de_Ponente con las mismas dimensiones de contenedor y el mismo nivel de encabezado HTML para el nombre del ponente y el título de la charla.

---

### Requirement 5: Pie de página con organizadores del evento

**User Story:** Como visitante, quiero ver quiénes organizan el evento al final de la página, para conocer las entidades responsables y su credibilidad.

#### Acceptance Criteria

1. THE Landing_Page SHALL mostrar un Pie_de_Página que aparezca al final del contenido de la página; el contenedor del Pie_de_Página SHALL ser visible para el Visitante, y SHALL listar los tres Organizadores del evento de forma simultáneamente visible sin requerir interacción del Visitante.
2. THE Pie_de_Página SHALL incluir el nombre "BucaraTec" como Organizador, con texto legible (tamaño de fuente ≥ 12 px y contraste mínimo de 4.5:1 sobre el fondo del Pie_de_Página).
3. THE Pie_de_Página SHALL incluir el nombre "AWS User Group Bucaramanga" como Organizador, con texto legible (tamaño de fuente ≥ 12 px y contraste mínimo de 4.5:1 sobre el fondo del Pie_de_Página).
4. THE Pie_de_Página SHALL incluir el nombre "UNAB TEC" como Organizador, con texto legible (tamaño de fuente ≥ 12 px y contraste mínimo de 4.5:1 sobre el fondo del Pie_de_Página).

---

### Requirement 6: Diseño responsivo para computador, tablet y dispositivo móvil

**User Story:** Como visitante, quiero que la página se vea correctamente tanto en mi computador como en mi teléfono, para acceder a la información desde cualquier dispositivo.

#### Acceptance Criteria

1. WHILE el Visitante accede a la Landing_Page desde un Escritorio (viewport ≥ 1024 px), THE Landing_Page SHALL mostrar todas las secciones (Hero, Agenda, Ponentes, Pie_de_Página) sin desbordamiento horizontal de contenido.
2. WHILE el Visitante accede a la Landing_Page desde un Dispositivo_Móvil (viewport ≤ 767 px), THE Landing_Page SHALL mostrar todas las secciones (Hero, Agenda, Ponentes, Pie_de_Página) sin desbordamiento horizontal de contenido.
3. WHILE el Visitante accede a la Landing_Page desde un Dispositivo_Móvil (viewport ≤ 767 px), THE Landing_Page SHALL adaptar el layout de las Tarjetas_de_Ponente a una columna única por defecto; THE Landing_Page MAY permitir al Visitante cambiar la disposición de columnas independientemente del dispositivo.
4. WHILE el Visitante accede a la Landing_Page desde un Dispositivo_Móvil (viewport ≤ 767 px), THE Landing_Page SHALL mantener el texto de todos los Bloques_de_Agenda con un tamaño de fuente renderizado mínimo de 16 px sin necesidad de hacer zoom.
5. WHILE el Visitante accede a la Landing_Page desde un Escritorio (viewport ≥ 1024 px), THE Landing_Page SHALL mostrar las Tarjetas_de_Ponente en disposición de dos columnas por defecto; THE Landing_Page MAY ofrecer al Visitante la opción de cambiar la disposición de columnas.
6. WHILE el Visitante accede a la Landing_Page desde una Tablet (viewport entre 768 px y 1023 px), THE Landing_Page SHALL mostrar todas las secciones sin desbordamiento horizontal y adaptar el layout de las Tarjetas_de_Ponente a una o dos columnas según el espacio disponible.

---

### Requirement 7: Accesibilidad básica del contenido

**User Story:** Como visitante, quiero que la página sea accesible con tecnologías de asistencia básicas, para poder consumir el contenido independientemente de mis capacidades.

#### Acceptance Criteria

1. THE Landing_Page SHALL usar exactamente un elemento H1 (título del evento en el Hero), elementos H2 para los encabezados de cada sección principal (Agenda, Ponentes, Pie_de_Página) y elementos H3 para los títulos de subsecciones, sin saltar niveles de jerarquía.
2. THE Landing_Page SHALL asegurar que el contraste entre el color del texto y el color de fondo cumpla una relación mínima de 4.5:1 para texto normal (menor a 18 pt o 14 pt en negrita) y de 3:1 para texto grande (18 pt o más, o 14 pt en negrita o más) en todas las secciones.
3. IF la Landing_Page incluye imágenes informativas o ilustrativas, THEN THE Landing_Page SHALL proveer un atributo `alt` con texto descriptivo no vacío para cada imagen.
4. IF la Landing_Page incluye imágenes puramente decorativas, THEN THE Landing_Page SHALL proveer el atributo `alt=""` en esas imágenes para que sean ignoradas por lectores de pantalla.
5. THE Landing_Page SHALL asegurar que todos los elementos interactivos (enlaces, botones) tengan un nombre accesible (a través de texto visible, `aria-label` o `aria-labelledby`) y sean operables mediante teclado (tecla Tab para foco y Enter/Space para activación).

---

### Requirement 8: Rendimiento de carga de la página

**User Story:** Como visitante, quiero que la página cargue rápidamente, para acceder a la información sin esperas prolongadas.

#### Acceptance Criteria

1. WHEN el Visitante solicita la Landing_Page desde una conexión de banda ancha estándar (velocidad de descarga mínima de 25 Mbps), THE Landing_Page SHALL completar la carga y mostrar el contenido visible inicial (Hero) en un tiempo menor o igual a 3 segundos medido desde el inicio de la solicitud hasta el evento de renderizado del Hero.
2. THE Landing_Page SHALL renderizar y operar sin errores funcionales en las dos versiones estables más recientes de Google Chrome, Mozilla Firefox, Microsoft Edge y Safari disponibles en el momento de la prueba.
3. IF la Landing_Page no completa la carga del Hero en un tiempo menor o igual a 3 segundos bajo las condiciones de red especificadas, THEN THE Landing_Page SHALL mostrar al Visitante un indicador visual de carga activa durante el tiempo de espera.
