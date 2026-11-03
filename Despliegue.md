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

![Despliegue inicial en Git](https://github.com/user-attachments/assets/75eac0dc-6cf5-4df6-9054-e05f47007823)

---

## 2. Creación y Despliegue en Azure Student

1. **Crear la Aplicación Web Estática:**
   - En el portal de Azure, busca y selecciona **Aplicación web estática** y haz clic en **Crear**.

   ![Creación de Static Web App](https://github.com/user-attachments/assets/1350e980-e3c7-448c-af7d-6bb0e25becc6)

2. **Seleccionar la Suscripción:**
   - Selecciona la suscripción correspondiente a **Azure for Students** y continúa.

   ![Selección de suscripción](https://github.com/user-attachments/assets/2f0a7ae2-672b-4f91-9e6f-cee1c122d187)

3. **Configurar los Parámetros Básicos:**
   - Asigna un nombre (en este caso, `pokedex`).
   - Selecciona **Gratis** como tipo de plan.

   ![Configuración del plan y nombre](https://github.com/user-attachments/assets/bacb3f03-a795-4f86-8b8d-5972334e5f88)

4. **Definir la Ubicación:**
   - Selecciona la región de salida correspondiente y procede a crear el recurso.

   ![Selección de ubicación](https://github.com/user-attachments/assets/a704ca7d-44d7-40cd-9c35-092ab6c9113f)

5. **Revisión y Creación:**
   - Revisa la información resumida y confirma haciendo clic en **Crear**.

   ![Revisión de información](https://github.com/user-attachments/assets/76be57e0-67ea-499d-abcf-9ad73119442c)

6. **Verificación del Despliegue:**
   - Espera a que el proceso en GitHub Actions finalice y muestre el indicador verde de éxito.

   ![Pipeline completado con éxito](https://github.com/user-attachments/assets/9d739b9b-02c8-439d-9c4a-5a10d3f7331c)

7. **Obtención de la URL:**
   - Verifica la información general y copia la **URL** de navegación asignada.

   ![URL de la aplicación](https://github.com/user-attachments/assets/ca3225d6-971a-4b61-9351-fd7db46e8d01)

---

## 3. Configuración de Seguridad desde Visual Studio Code

1. **Actualizar el Repositorio Local:**
   - Ubícate en la carpeta `.github/workflows` dentro del proyecto.
   - Ejecuta un `git pull` para sincronizar los pipelines y habilitar la configuración de Azure Static Web Apps.

   ![Git pull y workflows](https://github.com/user-attachments/assets/7fe711ed-2b49-4b5b-838e-c4ae1a553ae0)

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

   ![Commit de seguridad](https://github.com/user-attachments/assets/a3b85ddd-8eca-4d70-8804-7e9bd90caf1a)

3. **Verificación en GitHub Actions:**
   - Espera a que el flujo de integración continua procese los cambios en la pestaña **Actions** de GitHub hasta obtener el indicador verde.

   ![Acción de GitHub completada](https://github.com/user-attachments/assets/127b4eee-00a7-4755-aa29-81c9bc4b132c)

4. **Ejecución en el Navegador:**
   - Abre la URL del sitio para comprobar que el despliegue funciona correctamente con las nuevas directivas.

   ![Aplicación desplegada y funcionando](https://github.com/user-attachments/assets/fc5cff4c-326f-4195-9ad2-8fd156067c7a)

---

## 4. Verificación de Seguridad (Security Headers)

- Al analizar la URL en herramientas de evaluación de seguridad web (*Security Headers*), se obtiene una calificación de **A+**.

![Calificación A+ en Security Headers](https://github.com/user-attachments/assets/d0da9425-4722-4d17-bfd6-ae4f33d301bf)
