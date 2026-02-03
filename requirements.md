# Análisis de seguridad del requirements.txt

## Problemas de seguridad del archivo original
- Versiones incorrectas o inexistentes (Django 6.0)
- Sin hashes → riesgo de ataques supply-chain
- Mezcla de dependencias de desarrollo y producción
- No hay procedimiento claro para actualizaciones

## Version pinning vs hashing
- Version pinning: fijar cada dependencia evita cambios inesperados
- Hashing: asegura que el contenido del paquete no fue modificado

## Lock files vs input files
- Input file: lista de dependencias
- Lock file: versiones exactas + hashes → más seguro y reproducible

## Cómo generé el nuevo requirements.txt
1. Crear entorno virtual
2. Instalar dependencias
3. Corregir versiones y eliminar inseguras
4. Hacer pip freeze para fijarlas

## Procedimiento recomendado en producción
- Separar dependencias dev/prod
- Revisar actualizaciones periódicamente
- Test en staging antes de producción
- Documentar cambios y monitorizar vulnerabilidades

## Escenarios que prevenimos
- Supply-chain attacks
- Paquetes vulnerables o obsoletos
- Builds inconsistentes
- Cambios inesperados que rompan la app
