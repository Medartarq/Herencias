# Ruta de desarrollo

Cada hito termina con una demostración que podemos revisar juntos. Si una regla cambia al probarla, se actualiza primero su descripción y después la implementación.

| Hito | Trabajo | Criterio de salida |
| --- | --- | --- |
| 0. Diseño y entorno | Revisar las reglas de la primera partida, fijar la referencia de TFT y comprobar Unreal, compilador, SDK y espacio disponible. | Versión de herramientas registrada y reglas del prototipo acordadas. |
| 1. Proyecto base | Crear proyecto C++, mapa de pruebas, cámara y tablero seleccionable. Configurar el control de versiones para código, configuración y recursos. | Compila, abre el mapa y cada casilla se identifica correctamente. |
| 2. Partida local | Banca, tienda, reserva, formación, bot, combate, daño y resultado. | Una persona completa varias partidas. Se verifica que la reserva conserva copias, que las compras inválidas conservan el saldo y que una semilla repetida reproduce el combate. |
| 3. Modo estándar con bots | Ocho participantes, economía completa, progresión, mejoras por copias, emparejamientos, rasgos, PvE, objetos, aumentos y selección compartida. | Una partida completa produce puestos válidos. Se comprueban eliminaciones simultáneas, número impar de participantes y devolución de copias. |
| 4. Primera versión de red | Partida privada con autoridad en servidor, estados privados y reconexión. | Dos clientes completan una partida y se reconectan en preparación y combate. Luego se prueba un lobby de ocho. |
| 5. Primer set e instalador | Finalizar contenido, balance, tutorial y paquete Shipping para Windows. | Instalar, jugar y desinstalar en un equipo de prueba sin Unreal Editor. |

En el hito 2 se puede generar un paquete Development para descubrir temprano problemas de mapas o recursos en el ejecutable. La investigación cultural avanza desde el hito 0, de modo que el primer contenido original pueda incorporarse tan pronto como se pueda probar en partida.

## Primera sesión

1. Abrir el [contrato del prototipo](01-diseno.md#contrato-jugable-del-prototipo) y recorrer una ronda con papel o fichas. Comprar, llenar la banca, desplegar y resolver un combate. Registrar cualquier regla ambigua.
2. Comprobar si el equipo ya tiene Epic Games Launcher, Unreal Engine 5 y herramientas C++ para Windows. Anotar versión del motor, RAM, GPU y espacio libre antes de elegir la instalación.
3. Acordar la versión inicial del motor. En el siguiente hito, crear el proyecto y verificar una compilación antes de implementar reglas.
