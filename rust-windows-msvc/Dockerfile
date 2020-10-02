# escape=`

FROM mcr.microsoft.com/windows/servercore:1903

# Reset the shell.
SHELL ["cmd", "/S", "/C"]

# Set up environment to collect install errors.
RUN mkdir "C:\\TEMP"
# COPY ./integration_testing/Install.cmd "C:\\TEMP"
# ADD https://aka.ms/vscollect.exe "C:\\TEMP\\collect.exe"

# Download channel for fixed install.
ARG CHANNEL_URL=https://aka.ms/vs/15/release/channel
ADD ${CHANNEL_URL} "C:\\TEMP\\VisualStudio.chman"

# Download and install Build Tools for Visual Studio 2017.
# This takes years
# RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `

ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --channelUri "C:\\TEMP\\VisualStudio.chman" `
    --installChannelUri "C:\\TEMP\\VisualStudio.chman" `
    --add Microsoft.VisualStudio.Workload.ManagedDesktopBuildTools `
    --add Microsoft.Net.Component.3.5.DeveloperTools `
    --add Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools `
    --add Microsoft.Net.ComponentGroup.TargetingPacks.Common `
    --add Microsoft.VisualStudio.Component.TestTools.BuildTools `
    --add Microsoft.VisualStudio.Workload.VCTools `
    --add Microsoft.VisualStudio.Component.VC.140 `
    --add Microsoft.VisualStudio.Component.VC.ATL `
    --add Microsoft.VisualStudio.Component.VC.CLI.Support `
    --add Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop `
    --add Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP `
    --add Microsoft.VisualStudio.Workload.NodeBuildTools `
    --installPath "C:\\BuildTools"

# RUST UP INSTALL 
ADD https://win.rustup.rs C:/TEMP/rustup-init.exe
RUN C:/TEMP/rustup-init.exe --default-toolchain stable -y
