# Usar una imagen base de Windows si estás en un entorno Windows o una base compatible en Linux
FROM mcr.microsoft.com/windows/servercore:ltsc2022

# Instalar .NET Framework
RUN powershell -Command \
    Add-WindowsFeature NET-Framework-45-ASPNET; \
    Add-WindowsFeature Web-Asp-Net45

# Descargar e instalar OpenRPA
RUN powershell -Command \
    Invoke-WebRequest -Uri "https://github.com/open-rpa/openrpa/releases/download/v1.0.10/OpenRPA.msi" -OutFile "C:\\OpenRPA.msi"; \
    Start-Process msiexec.exe -ArgumentList '/i', 'C:\\OpenRPA.msi', '/quiet', '/norestart' -NoNewWindow -Wait

# Establecer la carpeta de trabajo
WORKDIR C:\\Program Files\\OpenRPA

# Comando para ejecutar OpenRPA
ENTRYPOINT ["C:\\Program Files\\OpenRPA\\OpenRPA.exe"]