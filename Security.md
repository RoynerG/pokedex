# 🚀 Guía Práctica: De Calificación C a A+ en Seguridad Web para Azure Static Apps

**Por:** Royner Guardi  
**Fecha:** Abril 2025

---

## 📝 Introducción

¡Hola compañeros! Si están leyendo esto es porque al igual que yo, sufrieron con los headers de seguridad en Azure. Después de 3 días de prueba y error (y mucho café), logré llevar mi aplicación de **calificación C a A+** en [SecurityHeaders.com](https://securityheaders.com). Aquí les comparto mi experiencia paso a paso.

---

## 🔧 Herramientas Usadas

- Azure Static Web Apps  
- Angular (aunque aplica para cualquier framework)  
- Visual Studio Code  
- Postman para pruebas

---

## 🔍 Paso 1: Diagnóstico Inicial

**Problema:** Mi aplicación mostraba **calificación C** por estos headers faltantes:

```bash
❌ Content-Security-Policy (CSP)
❌ X-Frame-Options
❌ Permissions-Policy
❌ Cross-Origin headers
```

**Cómo lo verifiqué:**

- Entré a [SecurityHeaders.com](https://securityheaders.com)
- Pegué mi URL: `https://mi-app.azurestaticapps.net`
- ¡Sorpresa! Calificación C 😅

---

## 🛠️ Paso 2: Configuración Básica

### Archivo `staticwebapp.config.json`

Creen este archivo en la raíz de su proyecto (junto a `package.json`):

```json
{
  "globalHeaders": {
    "Content-Security-Policy": "default-src 'self'; script-src 'self'; style-src 'self'; img-src 'self'",
    "X-Frame-Options": "DENY",
    "Permissions-Policy": "geolocation=()"
  }
}
```

> ⚠️ ¡CUIDADO! Esto romperá su aplicación porque es demasiado restrictivo. Pero es nuestro punto de partida.

---

## 💥 Paso 3: Solucionando Errores (La Parte Difícil)

### ❌ Error 1: Angular no funciona

```bash
Refused to execute inline script because of CSP
```

**Solución:**

```json
"script-src 'self' 'unsafe-inline' 'unsafe-eval'"
```

---

### ❌ Error 2: Google Fonts bloqueadas

```bash
Refused to load font from 'https://fonts.gstatic.com'
```

**Solución:**

```json
"style-src 'self' 'unsafe-inline' https://fonts.googleapis.com";
"font-src 'self' https://fonts.gstatic.com"
```

---

### ❌ Error 3: API externa bloqueada

```bash
Refused to connect to 'https://api.externa.com'
```

**Solución:**

```json
"connect-src 'self' https://api.externa.com"
```

---

## 🎯 Configuración Final Optimizada

Después de 15 intentos, esta fue la configuración que me dio **A+**:

```json
{
  "globalHeaders": {
    "Content-Security-Policy": "default-src 'self'; script-src 'self' 'unsafe-inline' 'unsafe-eval'; style-src 'self' 'unsafe-inline' https://fonts.googleapis.com; font-src 'self' https://fonts.gstatic.com; img-src 'self' data: https://*.dominio-externo.com; connect-src 'self' https://api.externa.com; frame-src 'none'; object-src 'none'",
    "X-Frame-Options": "SAMEORIGIN",
    "Permissions-Policy": "geolocation=(), microphone=(), camera=(), payment=()",
    "Referrer-Policy": "strict-origin-when-cross-origin",
    "X-Content-Type-Options": "nosniff",
    "Strict-Transport-Security": "max-age=63072000; includeSubDomains; preload"
  }
}
```

---

## 📌 Tips que Hubiera Querido Saber Antes

- **Azure Cache:** Los cambios pueden tardar hasta 10 minutos en aplicarse.
- **Modo Report-Only:** Usen primero `Content-Security-Policy-Report-Only` para probar.
- **Errores 404:** Verifiquen bien las URLs de sus recursos externos.
- **Nonces:** Para A+ sin warnings, necesitarán implementar `nonces` (eso es para otro tutorial).

---

## ✅ Checklist Final

Antes de entregar el proyecto:

- [x] Verificar en [SecurityHeaders.com](https://securityheaders.com)  
- [x] Probar todas las funcionalidades  
- [x] Chequear la consola del navegador  
- [x] Validar imágenes y fuentes externas

---

## 🎓 Conclusión

Llevar mi aplicación de C a A+ fue un proceso de mucho ensayo y error, pero valió la pena.  
Espero que esta guía les ahorre tiempo a ustedes. ¡Nos vemos en clases!

**PD:** Si tienen dudas, me encuentran en el laboratorio de computación los jueves por la tarde.  
¡Suerte con sus proyectos! 💻
