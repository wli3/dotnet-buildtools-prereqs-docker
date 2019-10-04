# escape=`

# Use the latest Windows Server Core image with .NET Framework 4.8.
FROM mcr.microsoft.com/dotnet/framework/sdk:4.8-20190923-windowsservercore-ltsc2019

SHELL ["powershell"]

RUN Invoke-WebRequest 'https://github.com/git-for-windows/git/releases/download/v2.12.2.windows.2/MinGit-2.12.2.2-64-bit.zip' -OutFile MinGit.zip

RUN Expand-Archive c:\MinGit.zip -DestinationPath c:\MinGit; `
        $env:PATH = $env:PATH + ';C:\MinGit\cmd\;C:\MinGit\cmd'; `
        Set-ItemProperty -Path 'HKLM:\SYSTEM\CurrentControlSet\Control\Session Manager\Environment\' -Name Path -Value $env:PATH

# Restore the default Windows shell for correct batch processing.
SHELL ["cmd", "/S", "/C"]
# Install 4.7.2 SDK

RUN `
    # Install VS Build Tools
    curl -fSLo vs_BuildTools.exe https://go.microsoft.com/fwlink/?linkid=874338 `
    && start /w vs_BuildTools.exe ^ `
       /install /quiet