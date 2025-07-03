# Tutorial: Instalar Docker en Windows usando WSL2 (Paso a Paso)

Este tutorial te guía para instalar Docker Desktop y WSL2 en Windows 10/11 y así ejecutar cualquier proyecto que use Docker, incluyendo stacks como PHP + MongoDB.

---

## 1. Pre-Requisitos

- **Windows 10** (versión 1903 o superior) o **Windows 11**
- Una cuenta con permisos de administrador

---

## 2. Habilitar WSL2 y Virtualización

### a) Activar la virtualización en BIOS

1. Reinicia tu PC y entra a la BIOS (normalmente presionando `DEL`, `F2`, `F10` o `ESC` al arrancar).
2. Busca la opción “Intel VT-x”, “Intel Virtualization Technology” o “AMD-V” y actívala.
3. Guarda y sal.

### b) Instalar WSL y una distro (Ubuntu recomendado)

1. Abre **PowerShell como administrador** y ejecuta:
   ```powershell
   wsl --install
   ```
   > Si tu Windows no reconoce este comando, ejecuta:
   ```powershell
   dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
   dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
   ```
   Reinicia el equipo y luego instala Ubuntu desde la Microsoft Store.

2. Asegúrate de que WSL2 es la versión predeterminada:
   ```powershell
   wsl --set-default-version 2
   ```

3. Abre Ubuntu desde el menú de inicio y crea tu usuario.

---

## 3. Instalar Docker Desktop

1. Descarga Docker Desktop desde la [página oficial](https://www.docker.com/products/docker-desktop/).
2. Ejecuta el instalador y sigue los pasos.  
   - Marca la opción **"Use WSL2 instead of Hyper-V"** cuando lo pida.
   - Si te pide instalar el kernel de WSL2, acepta y sigue el enlace.

3. Finaliza la instalación y **reinicia tu computadora** si es necesario.

---

## 4. Configurar Docker Desktop para WSL2

1. Abre **Docker Desktop**.
2. Ve a **Settings > Resources > WSL Integration**.
3. Activa tu distro (por ejemplo, "Ubuntu").
4. Opcional: en Settings > General, activa “Start Docker Desktop when you log in”.

---

## 5. Probar la instalación

1. Abre una terminal de Ubuntu (WSL).
2. Escribe:
   ```bash
   docker --version
   docker run hello-world
   ```
   Deberías ver un mensaje de éxito.

---

## 6. Ejecutar tu proyecto Docker

1. Navega a la carpeta de tu proyecto (por ejemplo, `mongodb-store`):
   ```bash
   cd ~/ruta/a/tu/proyecto/mongodb-store
   ```
2. Ejecuta:
   ```bash
   docker compose up --build
   ```
   o si usas un archivo `docker-compose.yml` (más antiguo):
   ```bash
   docker-compose up --build
   ```
3. Abre tu navegador en [http://localhost](http://localhost) para ver tu app.

---

## 7. Recursos y ayuda

- [Documentación oficial de Docker Desktop](https://docs.docker.com/desktop/)
- [WSL2 en Microsoft Docs](https://learn.microsoft.com/es-es/windows/wsl/)
- [Solución de problemas comunes de Docker en WSL2](https://docs.docker.com/desktop/troubleshoot/overview/)

---

¡Listo! Ya puedes ejecutar cualquier proyecto Docker en Windows usando WSL2.
