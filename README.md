# Sonic Launcher — Chevrolet Sonic 2014 Sedán

Launcher (pantalla de inicio) para radios Android de carro, horizontal, oscuro y minimalista.

**Incluye**
- Modelo 3D del Sonic sedán negro (se gira con el dedo; las ruedas giran con la velocidad real y los faros se encienden con el motor).
- Mapa de Google con estilo oscuro, tráfico, seguimiento GPS con inclinación, velocímetro, búsqueda "¿A dónde vamos?" y botones Casa / Trabajo (navegación con Google Maps o Waze). Mantener presionado el mapa = navegar a ese punto.
- OBD-II por Bluetooth (adaptador ELM327): temperatura del motor, combustible, batería, temperatura de aceite, RPM, velocidad, carga, aire de admisión, testigo Check Engine y lectura/borrado de códigos de falla.
- Mini reproductor que muestra y controla lo que suene en cualquier app (radio del equipo, Spotify, YouTube Music…).
- Accesos a Radio, Música, Video, Navegación y cajón con todas las apps instaladas, con buscador.
- Modo demostración para ver la interfaz sin adaptador OBD.

## 1. Obtener el APK (sin instalar nada en tu PC)

1. Crea una cuenta gratis en https://github.com y un repositorio nuevo (privado o público).
2. Sube el contenido de esta carpeta (botón **Add file → Upload files**, arrastra todo, incluida la carpeta `.github`).
3. (Opcional, para el mapa dentro del launcher) agrega tu clave de Google Maps: **Settings → Secrets and variables → Actions → New repository secret**, nombre `MAPS_API_KEY`.
4. Ve a la pestaña **Actions**: la compilación arranca sola (unos 5 min). Si no, abre "Compilar APK" → **Run workflow**.
5. Descarga `SonicLauncher.apk` desde **Releases** (columna derecha del repositorio).

## 2. Clave de Google Maps (gratis para uso personal)

1. https://console.cloud.google.com → crea un proyecto.
2. **APIs y servicios → Biblioteca** → activa **Maps SDK for Android**.
3. **Credenciales → Crear credenciales → Clave de API**. Copia la clave en el secret `MAPS_API_KEY` y vuelve a ejecutar el workflow.
   Sin clave, el recuadro del mapa abre Google Maps a pantalla completa.

## 3. Instalar en la pantalla del carro

1. Copia el APK a una USB (o descárgalo directo en la pantalla desde Releases).
2. Ábrelo con el administrador de archivos y permite "orígenes desconocidos".
3. Presiona el botón HOME → elige **Sonic Launcher** → **Siempre**.
   En radios FYT/SYU: Ajustes → Configuración de fábrica (clave típica `8888` o `1234`) → Launcher predeterminado.
4. Concede ubicación y Bluetooth. En **Ajustes → Permitir ver la música**, activa Sonic Launcher.

## Foto real de tu Sonic
- En la pantalla: **Ajustes → Foto de mi carro** y elige la foto. Se muestra en lugar del modelo 3D (puedes volver al 3D con "Mostrar foto real del carro").
- Queda mejor una foto de lado o en 3/4, en PNG **sin fondo** (puedes quitarlo gratis con remove.bg o con la opción "copiar sujeto" del celular).
- Para que venga incluida en el APK: guárdala como `app/src/main/assets/car_photo.png` antes de compilar.

## 4. Conectar el OBD

1. Conecta el ELM327 Bluetooth en el puerto OBD (debajo del volante, a la izquierda).
2. En el Bluetooth de la pantalla, emparéjalo (PIN `1234` o `0000`).
3. Sonic Launcher → Ajustes → **Adaptador OBD** → elige el dispositivo (desactiva el modo demostración).

**Notas sobre los datos del Sonic 2014**
- El nivel de aceite **no se transmite por OBD-II estándar** en este modelo; se muestra la temperatura del aceite cuando la ECU la reporta (si no, "N/D").
- La batería se lee con el voltaje del pin 16 del conector (ATRV): ~12,4–12,7 V apagado, 13,8–14,6 V con el motor encendido.
- Usa un ELM327 v1.5 de buena calidad (Vgate iCar, OBDLink); los clones v2.1 baratos fallan con frecuencia.
- Funciona con Bluetooth clásico. Los adaptadores WiFi o sólo BLE no son compatibles en esta versión.

## Compilar en PC (opcional)
Android Studio Hedgehog o superior → abrir la carpeta → `local.properties`: `MAPS_API_KEY=tu_clave` → Run.
