## Aplicación Contable para Clínica

## Visión General

Este repositorio contiene la aplicación web "contable-clinic-app", diseñada para gestionar la actividad administrativa y contable de una clínica especializada en cirugía estética y reconstructiva. La aplicación utiliza los servicios de Google (Sheets y Apps Script) para proporcionar una solución robusta y fácil de mantener.

## Características

- Registro detallado de pacientes
- Control de ingresos y egresos
- Seguimiento de consultas (nuevas y de control) y cirugías
- Gestión de insumos médicos (compra y venta)
- Registro de diferentes formas de pago (efectivo, transferencia, criptomoneda)
- Cálculo automático de saldos a favor o en contra
- Generación de reportes diarios, semanales y mensuales
- Integración con Google Sheets para almacenamiento de datos
- Copias de seguridad automáticas en Google Drive

## Requisitos

- Cuenta de Google
- Navegador web moderno (Chrome, Firefox, Safari, Edge)
- Conexión a internet estable
- Node.js y npm (para desarrollo local)

## Instalación y Configuración

1. Clona este repositorio:
 contable-clinic-app
 Repositorio para almacenar archivos administrativo para gestionar actividad clinica

2. Instala las dependencias:

3. Configura las credenciales de Google:
- Crea un proyecto en [Google Cloud Console](https://console.cloud.google.com/)
- Habilita las APIs de Google Sheets y Google Drive
- Crea credenciales (OAuth 2.0) y descarga el archivo JSON
- Renombra el archivo a `credentials.json` y colócalo en la raíz del proyecto

4. Configura la hoja de cálculo de Google:
- Crea una nueva hoja de cálculo en Google Sheets
- Copia el ID de la hoja de cálculo (está en la URL)
- Pega el ID en el archivo `config.js`:
  ```javascript
  module.exports = {
    spreadsheetId: 'TU_ID_DE_HOJA_DE_CALCULO'
  };
  ```

5. Inicia el servidor de desarrollo:

6. 
## Estructura del Proyecto


## Uso

### Registro de Pacientes

Para registrar un nuevo paciente, utiliza la función `addPatient`:

```javascript
function addPatient(name, date, regNumber) {
  const sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName('Pacientes');
  sheet.appendRow([name, date, regNumber]);
}

addPatient('Juan Pérez', '2023-08-11', 'REG001');
function addIncome(patientName, amount, paymentType, activityType) {
  const sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName('Ingresos');
  const date = new Date().toISOString().split('T')[0];
  sheet.appendRow([date, patientName, amount, paymentType, activityType]);
}
addIncome('Juan Pérez', 1000, 'Efectivo', 'Consulta Nueva');



Este README más extenso proporciona una visión detallada del proyecto, incluyendo instrucciones de instalación más específicas, ejemplos de código para las funciones principales, una estructura del proyecto, comandos útiles, y secciones adicionales como solución de problemas y agradecimientos. Puedes ajustar aún más este contenido según las necesidades específicas de tu aplicación y agregar o modificar secciones según sea necesario.

Entendido. Voy a elaborar una lista detallada de comandos que se pueden ejecutar en este proyecto. Estos comandos abarcarán desde la configuración inicial hasta las tareas de desarrollo y despliegue. Aquí tienes la lista:

```markdown
# Lista de Comandos para contable-clinic-app

## Configuración Inicial

1. Clonar el repositorio:
   ```
   git clone https://github.com/panacea-app/contable-clinic-app.git
   cd contable-clinic-app
   ```

2. Instalar dependencias:
   ```
   npm install
   ```

3. Configurar variables de entorno:
   ```
   cp .env.example .env
   nano .env
   ```

## Desarrollo

4. Iniciar servidor de desarrollo:
   ```
   npm run dev
   ```

5. Ejecutar pruebas:
   ```
   npm test
   ```

6. Ejecutar linter:
   ```
   npm run lint
   ```

7. Corregir problemas de linting automáticamente:
   ```
   npm run lint:fix
   ```

## Construcción y Despliegue

8. Construir para producción:
   ```
   npm run build
   ```

9. Previsualizar la versión de producción localmente:
   ```
   npm run preview
   ```

10. Desplegar en Google App Engine:
    ```
    gcloud app deploy
    ```

## Gestión de Google Apps Script

11. Inicializar proyecto de Apps Script:
    ```
    clasp create --title "Contable Clinic App" --rootDir ./src/appscript
    ```

12. Subir cambios a Apps Script:
    ```
    clasp push
    ```

13. Abrir el editor de Apps Script en el navegador:
    ```
    clasp open
    ```

## Gestión de Base de Datos (Google Sheets)

14. Crear una nueva hoja en Google Sheets:
    ```
    node scripts/create-sheet.js
    ```

15. Importar datos de muestra:
    ```
    node scripts/import-sample-data.js
    ```

## Utilidades

16. Generar reporte diario:
    ```
    node scripts/generate-daily-report.js
    ```

17. Realizar copia de seguridad:
    ```
    node scripts/backup.js
    ```

18. Restaurar desde copia de seguridad:
    ```
    node scripts/restore.js --date 2023-08-11
    ```

## Gestión de Versiones

19. Crear una nueva versión:
    ```
    npm version patch
    ```

20. Publicar una nueva versión:
    ```
    git push origin main --tags
    ```

## Mantenimiento

21. Actualizar dependencias:
    ```
    npm update
    ```

22. Verificar vulnerabilidades:
    ```
    npm audit
    ```

23. Corregir vulnerabilidades automáticamente (cuando sea posible):
    ```
    npm audit fix
    ```

## Documentación

24. Generar documentación API:
    ```
    npm run docs
    ```

25. Servir documentación localmente:
    ```
    npm run docs:serve
    ```

## Contenedores (si se utiliza Docker)

26. Construir imagen
