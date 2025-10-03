# Use the Windows Server Core LTSC2022 base image
FROM mcr.microsoft.com/windows/servercore:ltsc2022

# Set environment variables
ENV LIBREOFFICE_VERSION=7.6.2
ENV LIBREOFFICE_URL=https://download.documentfoundation.org/libreoffice/stable/25.8.1/win/x86_64/LibreOffice_25.8.1_Win_x86-64.msi

# Create a temp folder for the installer
RUN mkdir C:\install

# Use PowerShell to download LibreOffice installer
RUN powershell -Command Invoke-WebRequest -Uri $Env:LIBREOFFICE_URL -OutFile C:\install\LibreOffice.msi

# Install LibreOffice silently
RUN msiexec /i "C:\install\LibreOffice.msi" /quiet /norestart

# Clean up installer to reduce image size
RUN rmdir /s /q C:\install

# Set LibreOffice in PATH (optional)
ENV PATH="C:\\Program Files\\LibreOffice\\program;${PATH}"

# Default command (optional)
CMD ["cmd.exe"]
