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

## Alternativas a Dependabot en entornos privados

Si el repositorio estuviera en un servidor privado o en una nube privada y no pudiéramos usar GitHub Dependabot, se podrían usar herramientas como:

1. Snyk

Pros: fácil de usar, integración CI/CD, alertas automáticas

Contras: versión gratuita limitada

Comunidad: grande y activa

2. Trivy

Pros: ligero, open-source, rápido, detecta vulnerabilidades en paquetes y contenedores

Contras: menos detallado que Snyk

Comunidad: en crecimiento, muy usada en DevOps

3. OWASP Dependency-Check

Pros: open-source, respaldado por OWASP, compatible con Python, Maven, Gradle

Contras: configuración más compleja

Comunidad: amplia, enfocada en seguridad

4. Renovate

Pros: actualizaciones automáticas de dependencias

Contras: requiere configuración en repos privados

Comunidad: activa, open-source

## Herramienta elegida y ejecución

Para este proyecto se eligió Trivy:

