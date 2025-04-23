# 🚀 **Despliegue en Azure con Angular**

---

## 🔧 **1. Preparar el proyecto Angular**

- Instalar dependencias:
  ```
  npm install
  ```
- Ejecutar en local:
  ```
  npm start
  ```
- Generar carpeta de producción:
  ```
  npm run build
  ```

---

## ☁️ **2. Crear Static Web App en Azure**

1. Accede al portal de **Azure**.
2. Busca **Static Web Apps** y crea una nueva.
3. Configura lo siguiente:
   - **Nombre:** `pokedex-roy`
   - **Plan:** Free (para proyectos personales)
   - **Origen del código:** GitHub
4. En **Build Presets**, selecciona `Angular`.
5. En **App location**, escribe:
   ```
   /
   ```
6. Haz clic en **Review & Create**.
7. Si todo está correcto, presiona **Create**.

---

## ✅ **3. Verificar el despliegue**

- Verás el mensaje:
  > `Your deployment is complete` 🎉
- Abre la URL generada y valida que tu app funcione correctamente.

---

## 🔐 **4. Escanear la seguridad**

- Realiza un análisis de seguridad web.
- Resultado actual: 😭 No está completamente segura.

> 💡 Consulta el archivo [`Security.md`](./Security.md) donde colocare el tutorial que hice para la seguridad de mi aplicacion💙

---

🎉 ¡Listo! Tu **Pokedex Angular** ya está desplegada con éxito en **Azure**.
