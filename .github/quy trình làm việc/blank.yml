name: Windows-RDP

on: workflow_dispatch

jobs:
  build:

    runs-on: windows-latest
    timeout-minutes: 9999

    steps:
    - name: Download Ngrok.
      run: |
        Invoke-WebRequest https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-windows-amd64.zip -OutFile ngrok.zip
        Invoke-WebRequest https://raw.githubusercontent.com/DinhPhuc/windows-rdp/main/start.bat -OutFile start.bat
        Invoke-WebRequest https://raw.githubusercontent.com/DinhPhuc/windows-rdp/main/wallpaper.png -OutFile wallpaper.png
        Invoke-WebRequest https://raw.githubusercontent.com/DinhPhuc/windows-rdp/main/wallpaper.bat -OutFile wallpaper.bat
        Invoke-WebRequest https://raw.githubusercontent.com/DinhPhuc/windows-rdp/main/loop.bat -OutFile loop.bat
    - name: Download Launcher.
      run: |
        Invoke-WebRequest https://raw.githubusercontent.com/DinhPhuc/windows-rdp/main/launcher/Node.js.lnk -OutFile Node.js.lnk
        Invoke-WebRequest https://raw.githubusercontent.com/DinhPhuc/windows-rdp/main/launcher/Visual%20Studio%202019.lnk -OutFile "Visual Studio 2019.lnk"
        Invoke-WebRequest https://github.com/DinhPhuc/windows-rdp/raw/main/launcher/Ganti%20Password.exe -OutFile "Ganti Password.exe"
    - name: Extract Ngrok File.
      run: Expand-Archive ngrok.zip
    - name: Connect Ngrok.
      run: .\ngrok\ngrok.exe authtoken $Env:NGROK_AUTH_TOKEN
      env:
        NGROK_AUTH_TOKEN: ${{ secrets.NGROK_AUTH_TOKEN }}
    - name: Action Access RDP.
      run: | 
        Set-Ite
