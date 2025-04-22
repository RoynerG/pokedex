# Despliegue en Azure ☁

1.  Se prepara el proyecto de trabajo en Angular

- Se instalan las dependencias del proyecto: **npm install**
- Se verifica que funcione correctamente en local: **npm start**
- Se crea la carpeta de despliegue usando el comando: **npm run build**

2. Creamos un **Static Web Apps** desde **Microsoft Azure**
3. Se coloca el nombre de la **Static Web App**: pokedex-roy
4. Se escoge el plan **Free: For hobby or personal projects**
5. Se coloca como recurso **GitHub**
6. En **Build Presets** se escoge **Angular**
7. En App location se ingresa la ruta donde esta la aplicacion que en mi caso fue la construida con el comando **npm run build**: **/pokedex-angular**
8. Hacemos clic en el boton de **review & create** para que todo este correcto
9. Luego de ver que todo este correcto hacemos clic en el botón crear para desplegar el proyecto
10. Nos saldra una pantalla donde dirá que **Your deployment is complete** esto significará que el despligue de nuestra pokedex con Angular fue exitosa.
11. Revisamos que nuestra aplicación cargue y con esto concluimos todo.
12. Ingresamos nuestra aplicacion en scanner de seguridad para ver como esta en esos terminos y nos encontramos que no esta totalmente segura 😭.

# Seguridad de nuestra aplicacion 🔐

Este tutorial sencillo se los estaré explicando en mi otro archivo **Security.md**. Les invito a leer porque es muy importante en nuestros sitios para poder detectar y minimizar ataques de piratas. 💙
