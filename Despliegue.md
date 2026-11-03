
# Guía de Despliegue y Aseguramiento de Pokedex en Azure Static Web Apps

Este documento detalla el paso a paso para el control de versiones en Git, el despliegue de una aplicación web estática en Azure Static Web Apps con suscripción de estudiante, la implementación de políticas de seguridad HTTP y la verificación final con Security Headers.

---

## 1. Despliegue del Repositorio de Pokedex

1. **Inicializar el repositorio local y remoto:**
   - Descarga y extrae el archivo ZIP del proyecto Angular de Pokedex proporcionado en clase.
   - Abre la terminal en la carpeta del proyecto y ejecuta los siguientes comandos:
     ```bash
     git init
     git add .
     git commit -m "proyecto pokedex"
     git remote add origin [https://github.com/orozcomezal-commits/pokedex.git](https://github.com/orozcomezal-commits/pokedex.git)
     git push -u origin main
     ```
   - Espera a que finalice la carga para tener el repositorio configurado correctamente.

---

## 2. Creación y Despliegue en Azure Student

1. **Crear la Aplicación Web Estática:**
   - En el portal de Azure, busca y selecciona **Aplicación web estática** y haz clic en **Crear**.

2. **Seleccionar la Suscripción:**
   - Selecciona la suscripción correspondiente a **Azure for Students** y continúa.

3. **Configurar los Parámetros Básicos:**
   - Asigna un nombre (en este caso, `pokedex`).
   - Selecciona **Gratis** como tipo de plan.

4. **Definir la Ubicación:**
   - Selecciona la región de salida correspondiente y procede a crear el recurso.

5. **Revisión y Creación:**
   - Revisa la información resumida y confirma haciendo clic en **Crear**.

6. **Verificación del Despliegue:**
   - Espera a que el proceso en GitHub Actions finalice y muestre el indicador verde de éxito.

7. **Obtención de la URL:**
   - Verifica la información general y copia la **URL** de navegación asignada.

---

## 3. Configuración de Seguridad desde Visual Studio Code

1. **Actualizar el Repositorio Local:**
   - Ubícate en la carpeta `.github/workflows` dentro del proyecto.
   - Ejecuta un `git pull` para sincronizar los pipelines y habilitar la configuración de Azure Static Web Apps.

2. **Crear el Archivo de Configuración de Seguridad:**
   - Dentro de la carpeta `src`, crea un archivo de configuración llamado `staticwebapp.config.json`.
   - Agrega las políticas de seguridad para proteger la Pokedex:
     - `content-security-policy`
     - `strict-transport-security`
     - `x-frame-options`
     - `x-content-type-options`
     - `referrer-policy`
     - `permissions-policy`
   - Abre la terminal e integra los cambios al repositorio:
     ```bash
     git add .
     git commit -m "seguridad x fullback"
     git push
     ```

3. **Verificación en GitHub Actions:**
   - Espera a que el flujo de integración continua procese los cambios en la pestaña **Actions** de GitHub hasta obtener el indicador verde.

4. **Ejecución en el Navegador:**
   - Abre la URL del sitio para comprobar que el despliegue funciona correctamente con las nuevas directivas.

---

## 4. Verificación de Seguridad (Security Headers)

- Al analizar la URL en herramientas de evaluación de seguridad web (*Security Headers*), se obtiene una calificación de **A+**.
