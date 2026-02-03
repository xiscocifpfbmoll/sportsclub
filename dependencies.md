# Gestión de vulnerabilidades en dependencias

## Herramienta de GitHub para escanear dependencias

GitHub tiene una herramienta llamada **Dependabot**, que revisa automáticamente las dependencias del proyecto buscando vulnerabilidades conocidas y propone actualizaciones mediante alertas o pull requests.

---

## Cómo activamos Dependabot

1. Hicimos fork del repositorio.
2. Entramos en **Settings → Security → Code security**.
3. Activamos:
   - Dependency graph
   - Dependabot alerts
   - Dependabot security updates
4. Creamos el archivo `.github/dependabot.yml` con esta configuración:

```yaml
version: 2
updates:
  - package-ecosystem: "pip"
    directory: "/"
    schedule:
      interval: "weekly"
