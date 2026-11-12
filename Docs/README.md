# Autobattler de danzas del Perú

Proyecto de un autobattler para PC inspirado en el modo estándar de Teamfight Tactics. El primer set se inspira en danzas folclóricas peruanas y usa personajes, habilidades y arenas de ficción. El nombre comercial queda por definir.

## Documentos

| Documento | Contenido |
| --- | --- |
| [Diseño del juego](01-diseno.md) | Experiencia objetivo, alcance de referencia y reglas iniciales del prototipo. |
| [Arquitectura](02-arquitectura.md) | Responsabilidades en Unreal Engine, simulación, datos y red. |
| [Set 1](03-set-1.md) | Propuesta cultural, unidades candidatas y criterios de producción. |
| [Ruta de desarrollo](04-ruta.md) | Hitos, verificaciones y primera sesión de trabajo. |

## Decisiones iniciales

Windows y Unreal Engine 5 son las propuestas de plataforma y motor. Usaremos C++ para las reglas y Blueprints para la presentación. La partida estándar de ocho participantes es el objetivo de diseño. El primer prototipo permitirá que una persona pruebe el ciclo de compra, formación y combate frente a un bot.

Al comienzo de cada hito, registraremos en el documento correspondiente las reglas que se van a probar. Los valores provisionales pueden cambiar tras jugar. Las decisiones que afecten a partidas guardadas, datos de contenido o red también se reflejarán en la arquitectura.
