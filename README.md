# Bypass a la protección de capturas de pantalla de una única visualización usando Geanymotion. #


## Introducción ##

**WhatsApp** ha implementado en sus últimas versiones la característica de [visualización única](https://faq.whatsapp.com/1077018839582332?helpref=faq_content) una funcionalidad en la que las imágenes y vídeos que se envían a un contacto sean visto únicamente una sola vez, además de implementar distintos mecanismos de bloqueo que evitan que el archivo multimedia sea capturado mediante la pulsación de los botones, aplicaciones de grabación o que reflejen la pantalla del móvil. Sin embargo, **es posible saltarse estas protecciones utilizando un emulador como [Geanymotion](https://www.genymotion.com/) que permita desplegar dispositivos virtuales Android.**

 Una vez instalado WhatsApp en un **emulador Android**, se podrá utilizar la función **nativa de captura de pantalla del propio emulador**; realizando capturas de pantalla de las imágenes configuradas por el remitente para visualizarse una única vez, eludiendo el destinatario la protección *anti-capturas* de pantalla y *anti-grabación*, WhatsApp no detectará este mecanismo de evasión y la captura de pantalla que era de visualización única y protegida de capturas de pantalla ahora estará disponible para ser visualizada y distribuirla tantas veces como se desee.

![](https://github.com/msegoviag/WhatsApp_PoC_Once_Image/blob/main/00_portada.jpg?raw=true)

## Conociendo las protecciones ##

Cuando se recibe una imagen programada para ser visualizada una única vez esta implementa una serie de medidas para evitar que pueda ser capturada y guardada en la galería de imágenes del dispositivo:


- **Protección contra usuarios que haga una captura de pantalla utilizando los botones superior/lateral + Inicio/subir volumen del dispositivo.**
- **Protección contra las grabaciones de pantalla de la aplicación en el dispositivo.**
- **Protección contra las capturas de pantalla realizadas desde el *switcher* de aplicaciones, cuando la aplicación no está en primer plano.**
- **Protección contra la grabación de un vídeo de la pantalla usando *QuickTime Movie Recording* (iOS / MacOS).**
- **Protección de duplicación de pantalla contra los intentos de utilizar *AirPlay Screen Mirroring* para copiar contenido sensible (iOS / MacOS).**
- **Protección contra captura de pantallas efectuadas con un *IDE* de desarrollo de aplicaciones como Xcode (MacOS).**

![](https://github.com/msegoviag/WhatsApp_PoC_Once_Image/blob/main/01.jpg?raw=true)

Si intentamos capturar la pantalla de una imagen de una única visualización no podremos efectuar la acción usando los **típicos botones,** tampoco mediante **software integrado en el sistema operativo o de terceros que tienen la función de capturar la pantalla**. Al intentar efectuar una captura de pantalla con algunos de los métodos expuestos más arriba veremos la siguiente advertencia:


![](https://github.com/msegoviag/WhatsApp_PoC_Once_Image/blob/main/02.jpg?raw=true)

Se podría pensar que quizás usando **WhatsApp Web / PC** y abriendo la imagen podríamos realizar una captura de pantallas pero esto ha sido tenido en cuenta por el equipo de Meta y esta funcionalidad no está habilitada en esta plataforma, únicamente en dispositivos móviles. Veremos el siguiente mensaje en lugar de la foto de una única visualización:

> Recibiste un mensaje en tu teléfono, pero no es compatible con esta versión de WhatsApp web. Haz clic aquí para actualizar.

![](https://github.com/msegoviag/WhatsApp_PoC_Once_Image/blob/main/03.jpg?raw=true)

## Evadiendo las protecciones ##

Desde la web de [Geanymotion](https://www.genymotion.com/download/) se descargará el instalador del emulador, es posible descargar una versión con **VirtualBox** y otra sin VirtualBox, si ya se tiene VirtualBox instalado bastará con descargar la versión más ligera e instalarla. Durante la instalación hay que especificar que el **uso que se hará será personal para poder usar la aplicación gratuitamente**.

![](https://github.com/msegoviag/WhatsApp_PoC_Once_Image/blob/main/04.jpg?raw=true)

Se añade un nuevo dispositivo virtual, se elegirá uno compatible con WhatsApp, para poner en práctica esta prueba de concepto se recomienda el dispositivo **Google Pixel XL 10.0 API 29**.

![](https://github.com/msegoviag/WhatsApp_PoC_Once_Image/blob/main/06.jpg?raw=true)

Una vez descargado e instalado el dispositivo virtual se ejecuta y se instalan las [GApps](https://opengapps.org/) desde el menú lateral vertical situado a la derecha. Tras la instalación se habilitará Google Play, se introducen las credenciales de Gmail y se descarga WhatsApp, aunque también es posible instalar WhatsApp desde un .APK para evitar la instalación de las **GApps**.

![](https://github.com/msegoviag/WhatsApp_PoC_Once_Image/blob/main/07.jpg?raw=true)

Durante el proceso de registro con el número de teléfono WhatsApp detectará que se está realizando en un dispositivo virtual o ROM, se seguirá con el proceso hasta finalizar el registro en el dispositivo y poder hacer uso normal de WhatsApp como se haría con un móvil físico.

![](https://github.com/msegoviag/WhatsApp_PoC_Once_Image/blob/main/08.jpg?raw=true)

Una vez el entorno configurado en esta **prueba de concepto** se procede a enviar a un **contacto malintencionado** una imagen de una única visualización, la cual no debería poder ver más de una vez, efectuar captura de pantalla ni compartirla.

![](https://github.com/msegoviag/WhatsApp_PoC_Once_Image/blob/main/09.jpg?raw=true)

El contacto al que se le envía la imagen de una única visualización ha configurado un entorno con Geanymotion, tal y como como el que se ha descrito anteriormente para así poder interceptar las imágenes de una única visualización, una vez recibida solo debe abrir la utilidad de **captura nativa** de Geanymotion para efectuar la captura de pantalla o incluso captura de vídeo que se le guardará en la galería del dispositivo virtual.

![](https://github.com/msegoviag/WhatsApp_PoC_Once_Image/blob/main/10.jpg?raw=true)

Una vez efectuada la adquisición de la imagen haciendo uso de la opción de captura de pantalla nativa de Geanymotion la imagen estará disponible en la galería del dispositivo virtual. Se podrá visualizar tantas veces como se desee y compartirla con cualquiera.

![](https://github.com/msegoviag/WhatsApp_PoC_Once_Image/blob/main/11.jpg?raw=true)

Esta prueba de concepto finaliza reenviando al usuario la misma imagen protegida contra múltiples visualizaciones.

![](https://github.com/msegoviag/WhatsApp_PoC_Once_Image/blob/main/12.jpg?raw=true)

## ¿Cómo podría mitigarse? ##

Una solución podría ser implementar una restricción específica para ROMs y emuladores de Android y así evitar que las imágenes y vídeos que solo se pueden reproducir una vez se reproduzcan directamente en entornos móviles auténticos. La capacidad de detección ya está implementada, como se puede ver en el apartado **Conociendo las protecciones** de este artículo, solo es necesario activar esta restricción, al igual que ya se hace en WhatsApp Web / PC, donde se impide al usuario ver la imagen si no es en un móvil (con la intención de evitar capturas de pantalla desde PC)


## Respuesta de Meta ##

Este *glitch* fue reportado mediante el *[Bug Bounty Program](https://www.facebook.com/whitehat)* al equipo de Meta Security en el mes de diciembre de 2022. Obteniendo la siguiente respuesta: 
> Debido a la naturaleza de internet no siempre es posible impedir retroactivamente que una persona acceda a una foto después de haberla recibido en su dispositivo. Puede que se haya guardado localmente, en la caché del navegador o temporalmente en una red de distribución de contenidos (CDN) cercana. Estos factores nos impiden restringir retroactivamente el acceso a estos datos. Hacemos todo lo posible por conseguirlo, pero no es infalible. Su informe describe uno de los escenarios sobre los que no tenemos ningún control.

![](https://github.com/msegoviag/WhatsApp_PoC_Once_Image/blob/main/MetaResponse.jpg?raw=true)


## Conclusión ##

Enviar imágenes comprometedoras o con información sensible con la intención de que sólo pueda ser reproducida una vez por la persona a la que se le envía no garantiza la privacidad, ya que se ha demostrado que un destinatario o contacto malintencionado podría configurar una ROM personalizada o simplemente usar un emulador como el demostrado para capturar la imagen y distribuirla.

## Advertencia ##

El autor no se hace responsable de los daños que pueda causar el uso de las herramientas y pasos anteriores. El propósito de esta prueba de concepto es puramente educativo, el objetivo final es concienciar a los usuarios sobre la ciberseguridad y hacerles entender que enviar contenido multimedia privado, secreto o comprometedor con la garantía de que serán vistos una vez y nunca más, es un error. La privacidad absoluta no existe en Internet y eliminar de la red los contenidos que se han subido es casi imposible.

## Más información ##
- https://faq.whatsapp.com/1077018839582332/
- https://screenshieldkit.com/
