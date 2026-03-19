# adsoftsito.github.io

Sitio público de GitHub Pages que sirve la versión web del proyecto Flutter [adsoftsito/adsoft](https://github.com/adsoftsito/adsoft).

🌐 **URL pública:** [https://adsoftsito.github.io](https://adsoftsito.github.io)

## Cómo funciona el despliegue

El despliegue se realiza automáticamente mediante GitHub Actions cada vez que se hace un `push` a la rama `main` de este repositorio. El workflow se encuentra en [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml).

### Pasos del proceso automatizado

1. Se clona el repositorio fuente [`adsoftsito/adsoft`](https://github.com/adsoftsito/adsoft) (requiere el secret `ADSOFT_REPO_TOKEN` si es privado).
2. Se instala Flutter en su canal `stable`.
3. Se ejecuta `flutter build web --release --base-href "/"`.
4. Los archivos generados en `build/web/` se publican en GitHub Pages.

## Configuración inicial requerida

### 1. Habilitar GitHub Pages con GitHub Actions

En la configuración del repositorio (`Settings → Pages`), seleccionar **Source: GitHub Actions**.

### 2. Configurar el secret de acceso al repositorio fuente (si es privado)

Si el repositorio `adsoftsito/adsoft` es privado, es necesario crear un [Personal Access Token (PAT)](https://docs.github.com/en/authentication/keeping-your-account-and-data-safe/managing-your-personal-access-tokens) con permisos de lectura (`repo`) y agregarlo como secret en este repositorio:

```
Settings → Secrets and variables → Actions → New repository secret
Nombre: ADSOFT_REPO_TOKEN
Valor: <tu PAT>
```

### 3. Disparar el primer despliegue

Ejecutar el workflow manualmente desde `Actions → Deploy Flutter Web to GitHub Pages → Run workflow`, o hacer cualquier push a `main`.

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
