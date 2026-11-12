# Arquitectura técnica

## Proyecto Unreal

Comenzaremos con un proyecto C++ de Unreal Engine 5. Fijaremos la versión del motor y el SDK de Windows cuando comprobemos el entorno. El primer proyecto puede tener un solo módulo de juego con carpetas por responsabilidad. Separaremos módulos cuando exista una necesidad concreta de compilación o reutilización.

| Responsabilidad | Propuesta |
| --- | --- |
| Reglas C++ | Estructuras para partida, jugador, tienda, tablero y combate. La lógica opera sobre datos y puede probarse sin cargar un mapa. |
| Autoridad de partida | `GameMode` dirige las fases y ejecuta las órdenes. Las acciones del bot usan los mismos validadores que las del jugador. |
| Estado visible | `GameState` publica fase, ronda y plazo. `PlayerState` mantiene los datos públicos, como vida y puesto. El controlador entrega al dueño las ofertas y los datos privados. |
| Interacción | `PlayerController` recibe comandos de compra, venta, movimiento y confirmación. La interfaz muestra el resultado confirmado por la autoridad. |
| Presentación | Actores, Blueprints, UMG y audio representan el tablero y los eventos. La animación puede seguir el ritmo musical de cada unidad. |
| Contenido | Data Assets y tablas describen unidades, rasgos, objetos y reglas por set. Referencias estables enlazan las definiciones con el arte y el audio. |

## Flujo de una ronda

1. La autoridad abre la preparación, actualiza ingresos y tiendas según las reglas y publica el plazo.
2. Valida cada comando con identidad, fase, saldo, capacidad, propiedad y ocupación. Una compra aceptada debita oro y mueve una copia en una sola operación. Una acción rechazada conserva el estado anterior.
3. Al cerrar la fase, captura las formaciones y resuelve el combate con pasos fijos, semilla registrada, orden estable y desempates explícitos. La simulación emite eventos ordenados de movimiento, impacto, habilidad y resultado.
4. La presentación reproduce los eventos. La autoridad aplica daño, bajas del lobby y devoluciones a la reserva cuando corresponda, y abre la siguiente fase o publica el resultado final.

La simulación usa coordenadas enteras y evita que el framerate, el reloj de la interfaz o la física visual determinen un resultado. Cada ejecución registra versión de reglas, semilla y formaciones iniciales. El objetivo inicial es obtener el mismo resultado con la misma versión y entradas en la plataforma de prueba.

## Contratos de datos

- **Definición de unidad** con ID, coste, estadísticas, rasgos, habilidad y referencias de presentación.
- **Instancia de unidad** con ID de instancia, ID de definición, dueño, ubicación y nivel de estrellas. La salud y el maná de combate viven en un estado temporal.
- **Reserva compartida** con copias disponibles, ofertadas y adquiridas por definición. Las futuras mejoras por copias conservarán el número de copias base consumidas para devolverlas correctamente.
- **Configuración de set** con versión, catálogo, tablas de tienda y curvas de ronda. Una partida fija su versión al iniciar.

## Red y distribución

La partida local ejecuta la misma lógica de autoridad dentro del juego. Para la prueba de red, cada cliente envía intenciones y recibe el estado que le corresponde. El servidor procesa comandos secuencialmente, descarta duplicados y valida el plazo con su reloj. Para reconectar, enviará una instantánea autorizada con fase, plazo y estado visible. Se comprobará con dos clientes antes de subir a ocho. El flujo oficial de Epic para compilar un servidor dedicado requiere un proyecto C++ y Unreal compilado desde código fuente. [Epic Games, servidores dedicados](https://dev.epicgames.com/documentation/unreal-engine/setting-up-dedicated-servers-in-unreal-engine?lang=en-US)

La primera entrega de Windows será un paquete Development con ejecutable y datos, comprobado fuera del editor. La entrega instalable añade un asistente que instala el paquete Shipping, crea un acceso directo y permite desinstalar. La herramienta de instalación se elegirá al preparar esa entrega. [Epic Games, empaquetado de proyectos](https://dev.epicgames.com/documentation/en-us/unreal-engine/packaging-your-project)
