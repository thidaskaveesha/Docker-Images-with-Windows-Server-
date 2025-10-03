# Use the Windows Server Core LTSC2022 base image
FROM mcr.microsoft.com/windows/servercore:ltsc2022

# Set environment variables
ENV LIBREOFFICE_VERSION=7.6.2
ENV LIBREOFFICE_URL=https://download.documentfoundation.org/libreoffice/stable/25.8.1/win/x86_64/LibreOffice_25.8.1_Win_x86-64.msi

ENV PYTHON_VERSION=3.13.7
ENV PYTHON_URL=https://www.python.org/ftp/python/3.13.7/python-3.13.7-amd64.exe

# Create a folder for temporary installers
RUN mkdir C:\install

# Download LibreOffice installer
RUN powershell -Command Invoke-WebRequest -Uri $Env:LIBREOFFICE_URL -OutFile C:\install\LibreOffice.msi

# Install LibreOffice silently
RUN msiexec /i "C:\install\LibreOffice.msi" /quiet /norestart

# Download Python installer
RUN powershell -Command Invoke-WebRequest -Uri $Env:PYTHON_URL -OutFile C:\install\python-installer.exe

# Install Python silently
RUN C:\install\python-installer.exe /quiet InstallAllUsers=1 PrependPath=1 Include_test=0

# Clean up installer files
RUN rmdir /s /q C:\install

# Add LibreOffice and Python to PATH
ENV PATH="C:\\Program Files\\LibreOffice\\program;C:\\Program Files\\Python313\\Scripts;C:\\Program Files\\Python313;${PATH}"

# Default command
CMD ["cmd.exe"]
