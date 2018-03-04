# Transcripción UBports Q&A 24
03 Marzo 2018

- [X] transcripción
- [X] marcas de tiempo
- [X] abierto a traducción

*Palabras clave:        scopes, estadísticas*

Enlace al foro:        [forums.ubports.com/topic/1006/ubuntu-touch-q-a-24-march-3-2018](https://forums.ubports.com/topic/1006/ubuntu-touch-q-a-24-march-3-2018)

Enlace a YouTube:        [youtu.be/JLIkoXvGCiA](https://youtu.be/JLIkoXvGCiA)

Participantes:        Dalton, Florian, Marius

--------

### Trabajo de las últimas (dos) semanas ([00:50](https://youtu.be/JLIkoXvGCiA?t=00m50s))
- Florian: actualmente en España, sin mucho tiempo debido al trabajo, solo ha hecho pequeños ajustes
- Marius: trabajando en Unity8 para Bionic y en Mir (servidor gráfico)
        - Algo de trabajo para Xenial, resueltos algunos errores
        - La mayoría de las aplicaciones están funcionando, excepto OpenStore
- Florian: MTP está funcionando ahora en OnePlus One, agradecimiento a [Chakare](https://github.com/chakare). Era una sencilla cuestión de permisos, el arreglo llegará con la OTA para Xenial.
- Dalton: Portando Nexus 5X, un montón de problemas extraños
        - Se pone en pausa el portado por ahora debido a la enorme cantidad de tiempo que necesita
- Dalton: actualización sobre el desarrollo de Halium ([problema #404](https://github.com/ubports/ubuntu-touch/issues/404))
        - *(sin información sobre el contenido, solo charla sobre tener problemas con código de estatus de http como identificadores*

### Florian hace un anuncio: ([32:38](https://youtu.be/JLIkoXvGCiA?t=32m38s))
- Telegram va a cambiar la API y el protocolo de transporte. La buena noticia es que Telegram está ahora publicando las librerías que ayudarán a reimplementar todo.

## Preguntas:

### ¿Cuál es el estatus sobre la constitución de la Fundación? ([10:12](https://youtu.be/JLIkoXvGCiA?t=10m12s))
- Esperando a que el gobierno alemán confirme todo el papeleo.
- Florian: como cosa buena, ellos no han hecho ninguna pregunta por ahora y esto puede significar que todo va bien

### ¿Algún plan para soportar las impresoras? ([12:14](https://youtu.be/JLIkoXvGCiA?t=12m14s))
- Varios problemas: alimentación, ..., e impresoras son horribles. Canonical ya trabajó en ello. El subsistema de impresión debería venir en 16.04. La ayuda (probando, traduciendo) es apreciada
- https://github.com/ubports/?utf8=%E2%9C%93&q=print

### Traducciones ([15:33](https://youtu.be/JLIkoXvGCiA?t=15m33s))
- Las traducciones tienden a no ser tan recientes (desde Weblate) como se pretende. No se ha perdido nada, solo esperando a sincronizar.
- 16:04 traerá nuevas cadenas que traducir

### En la antigua web, Oneplus 3 ganó la votación de próximo dispositivo a portar, ¿qué significa esto? ([17:04](https://youtu.be/JLIkoXvGCiA?t=17m04s))
- No hay garantía de que vaya a haber un portado oficial, pero Marius ya tiene un portado de la comunidad.

### Ubuntu Personal era el plan de Canonical. Ubuntu con snaps por todas partes. ¿Que ha pasado con esto? ([20:08](https://youtu.be/JLIkoXvGCiA?t=20m08s))
- Murió. Muy difícil hacer funcionar mir con snaps, y para que funcionase tendríamos que pasar a snap todo. Esto es un escenario mas que improbable, así que no ocurrirá. Pero es mas que posible que haya soporte para snap.

### ¿Actualización sobre los scopes? ([since ~2-3~ 8 episodes earlier](https://youtu.be/QjaDZvQljaM?t=51m45s)) ([21:25](https://youtu.be/JLIkoXvGCiA?t=21m25s))
- Los scopes están mayormente muertos
- Plan actual: implementar una interfaz parecida al panel (dash) para móviles, en escritorio algo parecido a los iconos de escritorio. La elección es de la comunidad
- Comentarios de anteriores desarrolladores de scope: nada bueno
- Los Scopes necesitan un montón de trabajo

### ¿Ayudará el proyecto Treble de Google con Halium? ([25:39](https://youtu.be/JLIkoXvGCiA?t=25m39s))
- Marius dice: ¡¡¡¡¡SI!!!!! muy feliz con esto. No mas cambios específicos a Qualcom. Esto ayudará mucho con el portado. Pero para ello necesitamos llegar al punto de soportar Treble y esto será problemático. Podemos llegar en un tiempo razonable. Sin embargo, la prioridad es Xenial.

### ¿Qué pasa con uMatriks, Marius!? ([28:48](https://youtu.be/JLIkoXvGCiA?t=28m48s))
¿Dónde está mi audio y videollamadas? ¿y dónde están mis notificaciones de inserción (push)?
- Las notificaciones push fueron un experimento. Marius prometió volver con uMatriks después de Xenial.

### ¿Estadísticas? ([35:07](https://youtu.be/JLIkoXvGCiA?t=35m07s))
- Trabajaremos en ello más tarde
- Queremos garantizar el envío de datos de forma anónima, los datos se harán públicos, y esto se hará  optando
- UBports no seguirá el mismo camino que Canonical decidió seguir. Solo necesitamos saber qué dispositivos se utilizan para enfocar el desarrollo y tener informes de errores y fallos
- [GH ubports/ubuntu-touch #402](https://github.com/ubports/ubuntu-touch/issues/402)

### ¿Habrá / tendremos paquetes clic en X86 y OpenStore de x86? ([39:41](https://youtu.be/JLIkoXvGCiA?t=39m41s))
- Ahora mismo los desarrolladores pueden generar clics para X86. Desconocemos el estado actual de esto en OpenStore
- ¡Muchas gracias al equipo de OpenStore!
        - También hubo un debate sobre las nuevas políticas de seguridad que son importates principalmente para proteger a las personas que tienen la responsabilidad por el contenido del hosting y su mantenimiento.

### ¿Trabajaremos en Bionic? ([45:53](https://youtu.be/JLIkoXvGCiA?t=45m53s))
- Hay múltiples razones técnicas para no centrarnos aún con Bionic, y también necesitamos seguir dando soporte a los dispositivos legados. Necesitamos más tiempo para poder hacer todo el trabajo necesario para ir a Bionic. No queremos correr hacia Bionic, queremeos avanzar paso a paso hacia Bionic.

> *"Si subes por las escaleras paso a paso, realmente subes, pero si corres por los escalones tienes mucha probabilidad de caer, si encima saltas los escalones igual te caes y ya no te levantas."*
> 
> — Marius Gripsgard, 03. March 2018

- Cuando hablamos de Bionic,  ***no hablamos de***  Android Bionic, sino del próximo  Ubuntu 18.04 Bionic Beaver
        - Cuando hablamos de  Andriod Bionic, vamos a decir tan solo  *Android* Bionic
        - ...o vamos a decir siempre  18.04 cuando tengamos en mente la siguiente versión de  Ubuntu

### ¿Habrá Unity8 para Debian?([51:35](https://youtu.be/JLIkoXvGCiA?t=51m35s))
- Marius dice: SI... Pero  shhh esto es un secreto...
- Un mensaje de agradecimiento  a Simon Quigley por crear el equipo de empaquetamiento para UBports

###¿Cuánto de útil es xenial si quiero trabajar duro en el portado de la PDA de Gemini? ([54:22](https://youtu.be/JLIkoXvGCiA?t=54m22s))
- ~~ al parecer, Marius inmediatamente compraría y portaría cualquier dispositivo móvil que ejecute principalmente un núcleo de Linux.

### Que pasa con  nextcloud/carddav contact﻿ syncronización? ([57:14](https://youtu.be/JLIkoXvGCiA?t=57m14s))
-¡Sería bueno! ¿Quién quiere ocuparse de desarrollar esto? Nos gustaría tenerlo. Lo estamos mirando, probablemente llegue con el tiempo
