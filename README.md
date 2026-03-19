# adsoftsito.github.io

Sitio público de GitHub Pages que sirve la versión web del proyecto Flutter [adsoftsito/adsoft](https://github.com/adsoftsito/adsoft).

🌐 **URL pública:** [https://adsoftsito.github.io](https://adsoftsito.github.io)

## ⚠️ Configuración inicial obligatoria

Para que el despliegue automático funcione, el dueño del repositorio debe realizar **dos pasos en GitHub** antes de mergear esta rama:

### Paso 1 — Cambiar el origen de GitHub Pages a "GitHub Actions"

> **Settings → Pages → Build and deployment → Source → seleccionar "GitHub Actions"**

Actualmente GitHub Pages está configurado en modo "Deploy from a branch", lo que publica el README.md como página Jekyll. Al cambiar a **"GitHub Actions"**, solo el workflow de esta rama podrá publicar el sitio.

### Paso 2 — Configurar el secret (solo si `adsoftsito/adsoft` es privado)

Si el repositorio fuente es privado, crear un [Personal Access Token (PAT)](https://docs.github.com/en/authentication/keeping-your-account-and-data-safe/managing-your-personal-access-tokens) con permisos de lectura (`repo`) y agregarlo como secret:

```
Settings → Secrets and variables → Actions → New repository secret
Nombre: ADSOFT_REPO_TOKEN
Valor: <tu PAT>
```

### Paso 3 — Mergear esta rama a `main`

Al mergear a `main` se disparará automáticamente el workflow `Deploy Flutter Web to GitHub Pages` que compilará y publicará la app Flutter en https://adsoftsito.github.io.

---

## Cómo funciona el despliegue

El despliegue se realiza automáticamente mediante GitHub Actions cada vez que se hace un `push` a la rama `main` de este repositorio. El workflow se encuentra en [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml).

### Pasos del proceso automatizado

1. Se clona el repositorio fuente [`adsoftsito/adsoft`](https://github.com/adsoftsito/adsoft) (requiere el secret `ADSOFT_REPO_TOKEN` si es privado).
2. Se instala Flutter en su canal `stable`.
3. Se ejecuta `flutter build web --release --base-href "/"`.
4. Los archivos generados en `build/web/` se publican en GitHub Pages.

## Publicación manual

Si se desea publicar manualmente sin esperar el CI:

```bash
# Clonar el proyecto Flutter
git clone https://github.com/adsoftsito/adsoft.git
cd adsoft

# Instalar dependencias y compilar para web
flutter pub get
flutter build web --release --base-href "/"

# Los archivos generados están en build/web/
# Copiarlos al repositorio adsoftsito.github.io y hacer push
```

## Tecnologías

- [Flutter](https://flutter.dev/) — Framework de UI multiplataforma
- [GitHub Pages](https://pages.github.com/) — Hosting estático gratuito
- [GitHub Actions](https://github.com/features/actions) — CI/CD automatizado
