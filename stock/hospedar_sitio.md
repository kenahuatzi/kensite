Para hospedar tu sitio de Hugo en GitHub Pages utilizando un dominio personalizado, sigue los pasos a continuación. Vamos a configurar una página de usuario, lo que significa que tu repositorio debe ser `nombreusuario.github.io`. Luego, ajustaremos la configuración para usar tu propio dominio comprado a través de Google Domains.

### 1. Configura Tu Repositorio en GitHub

1. **Crea un Nuevo Repositorio**:

   - En GitHub, crea un nuevo repositorio con el nombre `nombreusuario.github.io`, donde `nombreusuario` es tu nombre de usuario de GitHub.

### 2. Construye Tu Sitio de Hugo

Primero, genera los archivos estáticos de tu sitio de Hugo.

1. **Navega al Directorio de Tu Sitio Hugo**:

   ```bash
   cd ruta/a/tu/sitio/hugo
   ```

2. **Construye el Sitio**: Esto generará los archivos estáticos en el directorio `public`.

   ```bash
   hugo
   ```

### 3. Configura el Dominio Personalizado

1. **Crea un Archivo `CNAME`**:

   En el directorio `public`, crea un archivo llamado `CNAME` que contenga tu dominio personalizado (por ejemplo, `tudominio.com`).

   ```bash
   echo "tudominio.com" > public/CNAME
   ```

### 4. Publica en GitHub Pages

1. **Inicializa un Repositorio Git en el Directorio `public`**:

   ```bash
   cd public
   git init
   ```

2. **Añade el Repositorio Remoto de GitHub**:

   ```bash
   git remote add origin https://github.com/nombreusuario/nombreusuario.github.io.git
   ```

3. **Añade, Confirma y Envía los Archivos**:

   ```bash
   git add .
   git commit -m "Commit inicial"
   git branch -M main
   git push -u origin main
   ```

### 5. Configura GitHub Pages para el Dominio Personalizado

1. **Configuración en GitHub**:

   - Ve a la configuración del repositorio en GitHub.
   - En la sección **Pages**, asegúrate de que la rama `main` esté seleccionada como fuente.
   - Especifica tu dominio personalizado en la sección de dominios personalizados.

2. **Configura DNS en Google Domains**:

   - Inicia sesión en Google Domains.
   - Navega a la configuración de DNS de tu dominio.
   - Añade los siguientes registros DNS:
     - **CNAME**: Añade un registro CNAME apuntando `www` a `nombreusuario.github.io`.
     - **A Records**: Añade cuatro registros A apuntando a las siguientes direcciones IP:
       - `185.199.108.153`
       - `185.199.109.153`
       - `185.199.110.153`
       - `185.199.111.153`

### Script `.sh` para Publicar Cambios

Puedes automatizar el proceso de construcción y despliegue con un script de shell:

```bash
#!/bin/bash

# Construye el sitio de Hugo
hugo

# Navega al directorio public
cd public

# Añade y confirma los cambios
git add .
git commit -m "Actualizar sitio"

# Envía los cambios al repositorio de GitHub
git push origin main

# Regresa al directorio raíz del sitio
cd ..
```

Guarda este script como `deploy.sh` en el directorio raíz de tu proyecto y asegúrate de darle permisos de ejecución:

```bash
chmod +x deploy.sh
```

Ahora, cada vez que realices cambios en tu sitio, simplemente ejecuta `./deploy.sh` para construir y publicar los cambios en GitHub Pages.

Con estos pasos, tendrás tu sitio de Hugo publicado en GitHub Pages usando tu propio dominio. Si tienes alguna pregunta o necesitas más ayuda, házmelo saber.
