# Control de Facturas - Distrito XIV

## Contenido del zip
- `index.html` — la aplicación (modo usuario + modo admin).
- `firestore.rules` — reglas de seguridad de Firestore (pegar en Firebase Console).
- `storage.rules` — reglas de seguridad de Storage (pegar en Firebase Console).

## Puesta en marcha

### 1. Configurar Firebase Authentication
1. Ve a la [Consola de Firebase](https://console.firebase.google.com/) → tu proyecto `facturas-distrito-xiv`.
2. **Authentication → Sign-in method** → activa "Correo electrónico/contraseña".
3. **Authentication → Users → Add user** → crea la cuenta de admin (tu email + una contraseña fuerte). Esa será la única cuenta que pueda entrar al panel de administración.

### 2. Publicar las reglas de seguridad
1. **Firestore Database → Reglas** → copia el contenido de `firestore.rules` → Publicar.
2. **Storage → Reglas** → copia el contenido de `storage.rules` → Publicar.

### 3. Subir el código a GitHub
```bash
git init
git add .
git commit -m "Control de facturas con login de admin"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/facturas-distrito-xiv.git
git push -u origin main
```

### 4. Publicar con GitHub Pages (enlace público)
1. En GitHub, ve a **Settings → Pages**.
2. En "Branch" selecciona `main` y carpeta `/root`, guarda.
3. GitHub te dará una URL tipo `https://TU_USUARIO.github.io/facturas-distrito-xiv/`. Compártela con quien deba subir facturas.

## Uso
- **Modo Usuario**: cualquiera con el enlace puede subir una factura (ID de usuario, establecimiento, importe y foto).
- **Modo Admin**: pulsa "Modo Admin", inicia sesión con el email/contraseña creados en el paso 1, y podrás ver, filtrar, exportar a CSV y borrar facturas.

## Notas de seguridad
- La `apiKey` de Firebase visible en `index.html` no es un secreto: es normal y esperado que sea pública en apps web de Firebase. La seguridad real la dan las reglas (`firestore.rules` y `storage.rules`), que solo permiten leer/borrar datos a quien haya iniciado sesión como admin.
- Si algún día quieres añadir más administradores, simplemente crea más usuarios en Authentication → Users; no hace falta tocar el código.
