Informe Técnico: Gestor RallySprint ASE 2026

1. Introducción

El Gestor RallySprint 2026 es una aplicación web autónoma diseñada para la gestión integral de competiciones de Slot (Scalextric). Permite el cronometraje en vivo, la gestión de inscritos por categorías (WRC y Clásicos) y el cálculo automático de clasificaciones basadas en un reglamento específico.

2. Características Principales

A. Gestión de Categorías Diferenciada

El sistema separa estrictamente a los competidores en dos ligas:

WRC: Vehículos modernos de alto rendimiento.

Clásicos: Vehículos históricos.
Cada piloto puede estar inscrito en ambas, pero sus puntos se calculan de forma independiente.

B. Sistema de Puntuación y Reglas

Puntuación: 20, 16, 13, 10, 8, 6, 4, 3, 1 puntos para los 9 primeros respectivamente.

Descarte: Solo computan los 5 mejores resultados de la temporada para la clasificación final.

Quórum Mínimo: Si una prueba tiene menos de 4 participantes, se marca como "DESIERTA" y no otorga puntos para el campeonato, aunque se mantienen los tiempos registrados.

C. Estadísticas de Eficiencia de Vehículos

Presenta dos bloques de análisis (uno por categoría) que muestran:

Ratio Pts/Uso: Indica qué modelo de coche es más efectivo matemáticamente.

Victorias y Podios: Conteo de éxitos por modelo.

D. Exportación Profesional

Genera un informe en formato PDF A4 diseñado con estética de competición (patrón de meta, tipografías robustas y jerarquía visual clara) listo para impresión o envío por redes sociales.

3. Manual de Uso

Registro de Pilotos

En la barra superior, introduzca el Nombre del Piloto y su Escudería.

Al pulsar Registrar, el sistema crea automáticamente dos entradas para el piloto (una en WRC y otra en Clásicos).

Introducción de Tiempos

Haga clic en una de las pruebas del calendario (arriba) para activarla.

Pulse sobre el nombre de un piloto en cualquier tabla para abrir el Panel de Edición.

Introduzca los tiempos de las 4 mangas (P1 y P2 de la Pasada 1, P1 y P2 de la Pasada 2).

Introduzca el Modelo de Coche usado en esa prueba específica.

El sistema sumará los tiempos automáticamente y reasignará las posiciones en tiempo real.

Gestión de Datos

Cargar: Permite importar un archivo .json previo para restaurar la base de datos.

Backup: Descarga el estado actual en un archivo .json para evitar pérdidas de datos.

Exportar PDF: Genera el documento visual final.

Navegación del Calendario

El calendario superior indica el estado de las pruebas:

Gris/Blanco: Prueba no disputada.

Negro: Prueba activa (actual).

Rojo: Prueba finalizada.

Línea Discontinua: Prueba desierta por falta de quórum.

Análisis Técnico: Gestor RallySprint ASE 2026

Este análisis examina la estructura, lógica y capacidades del archivo index.htlm proporcionado, el cual funciona como una aplicación web de una sola página (SPA) para la gestión de competiciones de Slot.

1. Arquitectura Técnica

Tecnologías: HTML5, CSS3 (Variables CSS para tematización) y JavaScript Vanilla (ES6+).

Dependencias Externas: html2pdf.js para la generación de informes en formato PDF.

Persistencia: Uso de localStorage (ase_rally_scx_v8) para mantener los datos de los pilotos y resultados de forma local en el navegador sin necesidad de servidor.

2. Componentes del Interfaz (UI)

Barra de Administración: Control de registro de pilotos (nombre y escudería), gestión de archivos (Cargar/Backup) y botón de exportación.

Selector de Calendario: Navegador visual de 8 pruebas que indica dinámicamente el estado de cada carrera (Activa, Finalizada o Desierta).

Panel de Clasificación en Vivo: Muestra los tiempos actuales de la carrera seleccionada, diferenciando por iconos el estado de cada piloto (Completo o en curso).

Tablas de Estadísticas y Rankings: - Top 5 Absoluto (Scratch).

Eficiencia de Vehículos (Ratio Puntos/Uso).

Top 5 por Categoría (WRC y Clásicos).

Tablas completas del Campeonato.

3. Lógica de Negocio y Algoritmos

Sistema de Puntuación: Implementa un POINTS_MAP que otorga puntos del 1º al 9º puesto (20, 16, 13, 10, 8, 6, 4, 3, 1).

Regla de Descarte: El cálculo de puntos totales (getCategoryPoints) ordena los resultados de mayor a menor y solo suma los 5 mejores.

Cálculo de Posiciones: La función autoCalculate procesa todos los tiempos, determina si una prueba es "Desierta" (menos de 4 participantes) y asigna posiciones solo en pruebas válidas.

Validación de Carrera: isRaceFinished verifica que todos los pilotos que iniciaron una prueba hayan completado las 4 mangas requeridas.

4. Funcionalidad de Usuario

Registro Dual: Al registrar un piloto, el sistema crea automáticamente dos entradas idénticas, una para la categoría WRC y otra para CLASICOS.

Edición Modal: Permite la entrada de tiempos precisos (hasta milésimas) para 4 mangas (2 pasadas con 2 carriles/tramos cada una).

Portabilidad de Datos: El sistema permite exportar todo el estado de la aplicación a un archivo .json para copias de seguridad o para mover la base de datos a otro dispositivo.

5. Diseño y Maquetación

Responsive: Utiliza unidades relativas y grid/flexbox para adaptarse a diferentes pantallas.

Estética "Racing": Uso de patrones de bandera de cuadros, tipografías robustas y esquemas de color contrastados (rojo, oscuro y oro).

Optimización de Impresión: Incluye una capa de estilos @media print que oculta los controles administrativos y ajusta el informe al formato A4 exacto.
