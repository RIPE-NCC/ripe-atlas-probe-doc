# Sondas Atlas RIPE

RIPE Atlas es una red global de sondas que mide la conectividad y la accesibilidad a través de Internet en tiempo real. Estas sondas son hospedadas mayoritariamente por voluntarios. Si alojas una sonda, recibirás créditos (consulta más sobre el [sistema de créditos](https://atlas.ripe.net/docs/credits/)) que se pueden utilizar más tarde para ejecutar tus propias mediciones en la red de RIPE Atlas.

Este documento describe los pasos que debes seguir para conectar tu enrutador como sonda a la red RIPE Atlas.

## Instalación

Para instalar la sonda, ve al menú *reForis*  *Package Management* → * Packages* y selecciona *RIPE Atlas SW Probe*.

Después de eso, debes conectarte a tu enrutador a través de SSH e iniciar el servicio `atlas`.

Habilite y ejecute el demonio con estos comandos:

```
/etc/init.d/atlas enable
/etc/init.d/atlas start
```

La sonda se comunica con los servidores Atlas a través de un túnel SSH. La clave SSH se genera después de la primera ejecución del demonio.

Después de iniciar el demonio, ejecuta el comando `get_key` para obtener la clave pública SSH generada. Necesitarás esta clave para registrar tu sonda bajo tu cuenta en el sitio web de RIPE.


`/etc/init.d/atlas get_key`

Se necesitan unos segundos para generar la clave.

## Registro de la sonda

Para registrar tu sonda, debes tener una cuenta en el [sitio web de RIPE NCC](https://access.ripe.net/registration).

Una vez que hayas iniciado sesión en tu cuenta en el [sitio web de RIPE Atlas](https://access.ripe.net/registration), completa el formulario en [este enlace](https://atlas.ripe.net/apply/swprobe/). En el campo del formulario *Public Key* copia la clave obtenida por el comando `get_key`.

Consulta los [Términos y Condiciones del Servicio RIPE Atlas](https://www-static.ripe.net/static/rnd-ui/atlas/media/legal/RIPEAtlasServiceTermsandConditionsV2.0.pdf), si estás de acuerdo con esto, compruébalo y haz clic en el botón *Submit your application*.

## Configuración

La configuración se encuentra en `/etc/config/atlas`. Contiene solo una opción booleana `rxtxrpt` que define si se enviarán estadísticas de tráfico de la interfaz de red como resultado de la medición de la sonda.

## Identificación y medición de la sonda

Después del registro de la sonda, deberías recibir un correo electrónico con el asunto **Your new RIPE Atlas software probe is created**, donde puedes encontrar el ID de tu sonda y el enlace para administrarla.

También puede utilizar este comando para obtener el ID de la sonda:

```
/etc/init.d/atlas probeid
```

Las mediciones de tu sonda se encuentran en la web (donde <ID> es el ID de tu sonda).

```
https://atlas.ripe.net/measurements/<ID>/
```
