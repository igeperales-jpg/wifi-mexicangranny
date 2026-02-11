# 📱 WiFi NFC - Mexican Granny
## Guía Completa para Programar Tarjetas NFC NTAG216

---

## � Bitácora de cambios
### v2.2 — 11 de febrero de 2026
**Fondo más claro**

Cambios realizados:
- **Fondo gris cálido**: Se cambió el fondo de negro profundo (#0a0a0a) a un gris oscuro cálido (#1b1b20). Las tarjetas (#242429) y elementos elevados (#2e2e34) se ajustaron proporcionalmente para mantener contraste sin ser tan oscuro.
- **Theme-color actualizado**: La barra del navegador móvil ahora coincide con el nuevo fondo.
### v2.1 — 11 de febrero de 2026
**Tarjeta web principal + nuevo fondo**

Cambios realizados:
- **Nuevo fondo**: Gradientes radiales cálidos (terracota/dorado/verde) reemplazando los orbes verdes fríos. Mesh gradient sutil estilo mexicano.
- **Tarjeta web principal arriba del todo**: Nueva tarjeta destacada `web-hero` con el logo oficial de Mexican Granny (`logo-mexican-granny.png` cargado desde mexicangranny.com), nombre del restaurante, URL y botón CTA grande "Ver nuestra carta y más" en color terracota.
- **Logo oficial**: Se muestra el logo real del negocio (72x72px) con fondo blanco y sombra.
- **Features badges**: Se añadieron 3 mini-badges debajo del botón: "Auténtica", "Recetas caseras", "Desde 1966".
- **Hero simplificado**: Se eliminó el emoji de taco y se redujo el hero a solo badge WiFi + título "Conéctate al WiFi" + subtítulo. Más limpio y enfocado.
- **Sección web antigua eliminada**: Se removió la tarjeta pequeña de web que estaba entre WiFi y valoraciones (ahora está arriba como protagonista).
### v2.0 — 11 de febrero de 2026
**Rediseño completo de la landing page + Sección de valoraciones**

Cambios realizados:
- **Diseño completamente nuevo**: Estilo dark/glassmorphism moderno con fondo oscuro (#0a0a0a), orbes de luz ambiental animados, tarjetas con bordes sutiles y tipografía Inter + Playfair Display.
- **Iconografía profesional**: Se reemplazaron los emojis por iconos SVG de Lucide Icons para una apariencia más limpia y consistente.
- **Fuente monoespaciada**: La contraseña ahora usa JetBrains Mono para mejor legibilidad.
- **Animaciones scroll-reveal**: Los elementos aparecen con fade-in conforme el usuario hace scroll.
- **Orbes de luz ambiental**: Esferas de color verde, dorado y rojo animadas en el fondo para dar profundidad.
- **Sección de reseñas Google Maps**: Tarjeta con logo oficial de Google (SVG a 4 colores) y 5 estrellas doradas. Enlaza directamente a: `https://g.page/r/CeYUEbRsBPKQEBM/review`
- **Sección de reseñas Tripadvisor**: Tarjeta con icono del búho de Tripadvisor (SVG) y 5 burbujas verdes. Enlaza a la ficha del restaurante en Tripadvisor.
- **Banner motivacional**: Sección "¿Te ha gustado?" con mensaje que invita a dejar reseña en 30 segundos.
- **Animación pulse**: Las tarjetas de reseña tienen una animación sutil de pulso dorado para atraer la atención.
- **Toast mejorado**: Notificación de "copiado" ahora en verde con icono check, estilo pill flotante.
- **Compatibilidad iPhone**: Se mantiene la sección oculta con perfil .mobileconfig que aparece solo en iOS.
- **Backup**: Se guardó la versión anterior como `index_backup_v1.html`.

### v1.0 — 11 de febrero de 2026
**Versión inicial**
- Landing page con datos WiFi (SSID + contraseña) con botones de copiar.
- Código QR WiFi generado automáticamente.
- Perfil .mobileconfig para conexión automática en iOS.
- Enlace a mexicangranny.com.
- Instrucciones de conexión paso a paso.
- Herramienta generador-qr.html para imprimir QR.

---

## �📋 Datos de configuración

| Campo | Valor |
|-------|-------|
| **SSID (nombre red)** | `Clientes Mexican Granny` |
| **Contraseña** | `ClientesMexican1966` |
| **Seguridad** | WPA2/WPA3 |
| **Web del negocio** | https://mexicangranny.com/ |

---

## 🏗️ Estructura del proyecto

```
wifi_mexican/
├── index.html                      ← Landing page v2 (diseño dark moderno + reseñas)
├── index_backup_v1.html             ← Backup de la versión original
├── wifi-mexican-granny.mobileconfig ← Perfil iOS para conexión WiFi automática
├── generador-qr.html               ← Herramienta para generar QR imprimible
├── generate_index.py               ← Script generador del index.html
├── README.md                        ← Este archivo (con bitácora)
└── assets/                          ← (opcional) imágenes y recursos
```

---

## 🎯 OPCIÓN A: Programar NFC con URL a Landing Page (RECOMENDADO)

> **Esta es la mejor opción** porque funciona igual en iPhone y Android, muestra la
> información WiFi, un QR de conexión, y un enlace a tu web.

### Paso 1: Sube la landing page a internet

Necesitas hospedar `index.html` y `wifi-mexican-granny.mobileconfig` en un servidor web.
Opciones gratuitas:

#### Opción más fácil: GitHub Pages
1. Crea una cuenta en [github.com](https://github.com) (si no tienes una)
2. Crea un repositorio nuevo llamado `wifi-mexicangranny`
3. Sube los archivos `index.html` y `wifi-mexican-granny.mobileconfig`
4. Ve a **Settings → Pages** → selecciona `main` branch → **Save**
5. Tu página estará en: `https://tuusuario.github.io/wifi-mexicangranny/`

#### Otras opciones:
- **Netlify**: Arrastra la carpeta a [app.netlify.com/drop](https://app.netlify.com/drop)
- **Tu propio hosting**: Sube los archivos por FTP a tu servidor
- **Firebase Hosting**: `firebase deploy` (gratis)

### Paso 2: Programar la tarjeta NFC con NFC Tools

1. **Abre la app NFC Tools** en tu teléfono
2. Ve a la pestaña **"Escribir"** (Write)
3. Toca **"Agregar un registro"** (Add a record)
4. Selecciona **"URL / URI"**
5. Escribe la URL de tu landing page:
   ```
   https://tuusuario.github.io/wifi-mexicangranny/
   ```
   _(reemplaza con tu URL real)_
6. Toca **"OK"** / **"Aceptar"**
7. Toca **"Escribir"** (Write)
8. **Acerca la tarjeta NTAG216** al teléfono
9. ¡Espera la confirmación de escritura! ✅

### ¿Qué pasa cuando un cliente toca la tarjeta?
1. Su teléfono detecta la tarjeta NFC automáticamente
2. Se abre el navegador con la landing page
3. Ve los datos WiFi, puede copiar la contraseña, escanear el QR
4. Puede tocar el enlace para visitar mexicangranny.com

---

## 🎯 OPCIÓN B: Programar WiFi directo en NFC (Solo Android)

> **⚠️ Importante:** Esta opción SOLO funciona en Android. Los iPhones NO pueden
> conectarse a WiFi automáticamente desde una tarjeta NFC.

### Programar con NFC Tools:

1. **Abre NFC Tools**
2. Ve a **"Escribir"** (Write)
3. Toca **"Agregar un registro"** (Add a record)
4. Selecciona **"WiFi"** (o "Red WiFi")
5. Completa los campos:
   - **SSID**: `Clientes Mexican Granny`
   - **Contraseña**: `ClientesMexican1966`
   - **Tipo de autenticación**: WPA2
   - **Tipo de cifrado**: AES
6. Toca **"OK"**
7. **(Opcional)** Agrega otro registro → **URL**: `https://mexicangranny.com/`
8. Toca **"Escribir"** → Acerca la tarjeta

### Resultado en Android:
- El teléfono se conecta automáticamente al WiFi ✅
- Si agregaste la URL, también abre la web ✅

### Resultado en iPhone:
- ❌ No se conecta al WiFi (iOS no soporta registros WiFi NFC)
- ✅ Si hay URL, la abre

---

## 🎯 OPCIÓN C: Combinación Inteligente (Avanzado)

Puedes programar **dos registros** en la misma tarjeta NTAG216:

1. **Registro 1 - WiFi** (para Android)
2. **Registro 2 - URL** a tu landing page (para todos)

### En NFC Tools:
1. Agregar registro → **WiFi** (con los datos de arriba)
2. Agregar registro → **URL** → tu landing page
3. Escribir en la tarjeta

> **Nota:** El NTAG216 tiene 888 bytes. Un registro WiFi + URL cabe perfectamente.
> El comportamiento varía: Android puede ejecutar el WiFi y mostrar la URL,
> mientras iPhone solo abrirá la URL.

---

## 🔧 Configuración Avanzada

### Proteger la tarjeta contra escritura

Después de programar la tarjeta, puedes **bloquearla** para que nadie la reprograme:

1. En NFC Tools, ve a **"Otras"** (Other)
2. Selecciona **"Hacer solo lectura"** (Make read only)
3. Acerca la tarjeta

> **⚠️ ATENCIÓN:** Esta acción es **IRREVERSIBLE**. La tarjeta no podrá volver a
> escribirse nunca más. Asegúrate de que todo funciona correctamente antes de bloquearla.

### Cambiar datos WiFi en el futuro

Si cambias la contraseña del WiFi:
- **Con Opción A (URL)**: Solo actualiza el `index.html` en tu hosting. Las tarjetas
  siguen funcionando sin reprogramarlas  ✅
- **Con Opción B/C (WiFi directo)**: Necesitas reprogramar TODAS las tarjetas ❌

> **Por esto la Opción A es la mejor:** puedes cambiar los datos WiFi sin tocar
> las tarjetas NFC.

---

## 📱 Compatibilidad de dispositivos

### iPhone (iOS)
| Función | Soporte |
|---------|---------|
| Leer URL desde NFC | ✅ iPhone 7 y superior |
| Conectar WiFi desde NFC | ❌ No soportado |
| Escanear QR WiFi desde cámara | ✅ iOS 11+ |
| Instalar perfil .mobileconfig | ✅ Todas las versiones |

### Android
| Función | Soporte |
|---------|---------|
| Leer URL desde NFC | ✅ Android 5+ con NFC |
| Conectar WiFi desde NFC | ✅ Android 5+ con NFC |
| Escanear QR WiFi desde cámara | ✅ Android 10+ |

---

## 🛠️ Solución de problemas

### "NFC Tools no detecta la tarjeta"
- Asegúrate de que el NFC está **activado** en los Ajustes del teléfono
- En Android: **Ajustes → Conexiones → NFC → Activar**
- En iPhone: NFC siempre está activo (iPhone 7+)
- Coloca la tarjeta en la parte **superior trasera** del teléfono
- Mantén la tarjeta quieta durante la escritura

### "Error de escritura" / "Write error"
- La tarjeta puede estar **bloqueada** (solo lectura)
- Asegúrate de no alejar la tarjeta durante la escritura
- Intenta con otra tarjeta nueva

### "El teléfono del cliente no lee la tarjeta"
- iPhone: Debe acercar la parte **superior del teléfono** a la tarjeta
- Android: La ubicación del sensor NFC varía, generalmente en el **centro trasero**
- Que retire la funda si es muy gruesa
- NFC debe estar activado en el teléfono del cliente

### "La URL no abre"
- Verifica que la landing page esté correctamente subida al hosting
- Comprueba la URL en un navegador primero
- Asegúrate de incluir `https://` al programar la URL

---

## 💡 Consejos para el negocio

1. **Coloca las tarjetas** en las mesas, mostrador, o cerca de la entrada
2. **Agrega un letrerito** al lado de la tarjeta que diga:
   > 📱 **WiFi Gratis** - Acerca tu teléfono aquí
3. **Programa varias tarjetas** antes de bloquearlas
4. **Prueba cada tarjeta** con iPhone Y Android antes de bloquearla
5. **Usa la Opción A (URL)** para poder cambiar datos sin reprogramar

---

## 📄 Licencia

Proyecto creado para Mexican Granny. Uso libre.
