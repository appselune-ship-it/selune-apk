# Selune APK — WebView Android

App Android que abre https://app.seluneapp.com a pantalla completa.

## Cómo obtener el APK (sin instalar nada)

### 1. Crea un repositorio en GitHub

Ve a https://github.com/new y crea un repositorio **privado** llamado `selune-apk`.

### 2. Sube este proyecto

En tu máquina, desde la carpeta donde descomprimiste el ZIP:

```bash
cd selune-apk
git init
git add .
git commit -m "Selune APK inicial"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/selune-apk.git
git push -u origin main
```

> Sustituye `TU_USUARIO` por tu usuario de GitHub.

### 3. GitHub compila el APK automáticamente

En cuanto hagas el push, GitHub Actions lanza la compilación.
Puedes verlo en: `https://github.com/TU_USUARIO/selune-apk/actions`

Tarda ~3-5 minutos.

### 4. Descarga el APK

Cuando el workflow termine (círculo verde ✅):

1. Entra en la acción terminada
2. Baja hasta la sección **Artifacts**
3. Descarga **Selune-APK**
4. Descomprime el ZIP — dentro está `app-release-unsigned.apk`

### 5. Instala en Android

1. Pasa el APK al móvil (por email, Google Drive, cable USB…)
2. En el móvil: **Ajustes → Seguridad → Instalar apps de origen desconocido** (actívalo)
3. Abre el APK desde el gestor de archivos → Instalar

---

## Qué incluye la app

- Abre `https://app.seluneapp.com` a pantalla completa
- JavaScript, cookies y almacenamiento local activados
- Pull-to-refresh (arrastrar hacia abajo para recargar)
- El botón Atrás navega dentro de la web
- Soporte para subir fotos (input file)
- Barra de estado y navegación en color navy `#1b2540`
- Solo HTTPS (sin tráfico en claro)

---

## Para actualizar la URL o el nombre

Edita `app/src/main/java/com/selune/app/MainActivity.java`, línea:

```java
private static final String APP_URL = "https://app.seluneapp.com";
```

Y `app/src/main/res/values/strings.xml` para cambiar el nombre visible.

Luego haz commit + push y GitHub vuelve a compilar automáticamente.

---

## Estructura del proyecto

```
selune-apk/
├── .github/workflows/build.yml     ← Compilación automática
├── app/
│   ├── build.gradle
│   └── src/main/
│       ├── AndroidManifest.xml
│       ├── java/com/selune/app/
│       │   └── MainActivity.java   ← Lógica WebView
│       └── res/
│           ├── layout/activity_main.xml
│           ├── values/strings.xml
│           ├── values/styles.xml
│           ├── values/colors.xml
│           ├── xml/network_security_config.xml
│           └── mipmap-*/ic_launcher*.png
├── build.gradle
├── settings.gradle
└── gradle/wrapper/gradle-wrapper.properties
```
