# Diseño del juego

Ocho participantes reclutan danzantes ficticios, administran su economía y forman comparsas. Durante la preparación pueden cambiar su alineación. Al cerrarse el plazo, el enfrentamiento se resuelve automáticamente y las derrotas reducen la vida del participante. El último con vida gana.

La referencia inicial es el modo estándar de TFT. Antes de cerrar las reglas del modo completo, se fijará un set o parche de referencia para revisar variantes como el carrusel, los encuentros y la mecánica estacional. [Riot Games, ejemplo de mecánicas de set](https://teamfighttactics.leagueoflegends.com/en-us/news/game-updates/mechanics-cyber-city/)

## Inventario inicial de mecánicas

| Sistema | Objetivo del modo estándar | Primera validación |
| --- | --- | --- |
| Partida | Ocho participantes, fases por etapa, rondas PvP y PvE, emparejamiento, daño, eliminación y puestos. | Prototipo de dos participantes. Después, simulación de ocho con bots y reglas de número impar. |
| Economía | Ingresos, interés, rachas, compra, venta, experiencia, niveles y límite de despliegue. | Compra, venta, ingresos y límite fijo. Luego interés, rachas y niveles. |
| Tienda | Ofertas según nivel, rarezas, renovación, bloqueo, reserva compartida y devolución de copias. | Tres ofertas con reserva compartida, renovación y reposición. Luego tablas por nivel y bloqueo. |
| Formación | Banca, tablero hexagonal, movimiento, intercambio, exploración de rivales y mejoras por copias. | Colocar, mover y retirar. Luego combinar copias y explorar tableros. |
| Combate | Objetivos, movimiento, ataques, maná, habilidades, efectos, desempates y límite de ronda. | Ataques y una habilidad simple. Después se amplían efectos y reglas de combate. |
| Composición | Rasgos por umbral, roles y sinergias que abren rutas de composición. | Dos rasgos de prueba, con un umbral cada uno. |
| Recompensas | Botín PvE, inventario, componentes, recetas, objetos especiales y reglas al vender. | Tras el prototipo se añade botín, equipamiento y una receta completa. |
| Elecciones | Aumentos, fases de selección compartida y una mecánica propia del set. | Se prueban después de estabilizar economía y combates. |
| Experiencia en línea | Sala, partida privada, reconexión y observación. Clasificatorias como etapa de producto. | Dos clientes en una partida privada antes de la prueba con ocho. |

La auditoría contra el parche de referencia definirá la cobertura final. Modos alternativos como Double Up se decidirán por separado.

## Contrato jugable del prototipo

- Dos participantes, una persona y un bot. Cada uno empieza con 15 de vida y 5 monedas. Tras cada combate reciben 3 monedas si la partida sigue.
- Tablero de combate de 5 × 4 hexágonos, dos filas de despliegue por lado, banca de cuatro espacios y hasta tres unidades desplegadas. Cada combate genera una formación enfrentada a partir de las posiciones de preparación.
- Catálogo de seis unidades de prueba a 1 o 2 monedas, con seis copias de cada una en la reserva. Cada tienda muestra hasta tres ofertas según disponibilidad. Cada oferta reserva una copia. Al renovar por 2 monedas o al comenzar una preparación se liberan las ofertas pendientes antes de volver a sortear. Comprar transfiere la copia a la banca y vender la devuelve por su precio original.
- La preparación termina cuando el usuario pulsa «Combatir» o vence el temporizador. El bot prepara su formación con las mismas reglas de compra y colocación. El combate usa estado temporal y la formación original se recupera al acabar.
- Cada unidad selecciona el enemigo accesible más cercano, con desempate por identificador estable. Ataca cuando entra en alcance y avanza cuando existe un camino libre. Si ambos bandos siguen vivos al vencer el límite, o caen en el mismo paso, hay empate y ambos pierden 1 de vida. El perdedor de un combate normal pierde 3. Si ambos llegan a cero en la misma ronda, la partida termina empatada.
- La partida de prueba se considera completa cuando se puede comprar, desplegar, combatir, ver el resultado, pasar a la siguiente ronda y reiniciar tras el resultado final. Los números son hipótesis de prueba.
