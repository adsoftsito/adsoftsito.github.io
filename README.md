# adsoftsito.github.io

Sitio público de GitHub Pages que sirve la versión web de la aplicación Flutter.

🌐 **URL pública:** [https://adsoftsito.github.io](https://adsoftsito.github.io)

## ⚠️ Configuración inicial obligatoria

Para que el despliegue automático funcione, el dueño del repositorio debe realizar los siguientes pasos en GitHub:

### Paso 1 — Agregar el código fuente Flutter a este repositorio

El código de la aplicación Flutter debe estar en este mismo repositorio (`adsoftsito/adsoftsito.github.io`). Asegúrate de que el archivo `pubspec.yaml` y el código fuente se encuentren en la raíz del repositorio.

### Paso 2 — Cambiar el origen de GitHub Pages a "GitHub Actions"

> **Settings → Pages → Build and deployment → Source → seleccionar "GitHub Actions"**

Actualmente GitHub Pages está configurado en modo "Deploy from a branch", lo que publica el README.md como página Jekyll. Al cambiar a **"GitHub Actions"**, solo el workflow de esta rama podrá publicar el sitio.

### Paso 3 — Mergear esta rama a `main`

Al mergear a `main` se disparará automáticamente el workflow `Deploy Flutter Web to GitHub Pages` que compilará y publicará la app Flutter en https://adsoftsito.github.io.

---

## Cómo funciona el despliegue

El despliegue se realiza automáticamente mediante GitHub Actions cada vez que se hace un `push` a la rama `main` de este repositorio. El workflow se encuentra en [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml).

### Pasos del proceso automatizado

1. Se clona este repositorio (`adsoftsito/adsoftsito.github.io`).
2. Se instala Flutter en su canal `stable`.
3. Se ejecuta `flutter build web --release --base-href "/"`.
4. Los archivos generados en `build/web/` se publican en GitHub Pages.

## Publicación manual

Si se desea publicar manualmente sin esperar el CI:

```bash
# Clonar este repositorio
git clone https://github.com/adsoftsito/adsoftsito.github.io.git
cd adsoftsito.github.io

# Instalar dependencias y compilar para web
flutter pub get
flutter build web --release --base-href "/"

# Los archivos generados están en build/web/
# Hacer push a main para que el workflow los publique automáticamente
```

## Tecnologías

- [Flutter](https://flutter.dev/) — Framework de UI multiplataforma
- [GitHub Pages](https://pages.github.com/) — Hosting estático gratuito
- [GitHub Actions](https://github.com/features/actions) — CI/CD automatizado
