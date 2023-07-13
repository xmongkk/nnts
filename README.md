# Open NGROK
<!--[NGROK](https://ngrok.com/)-->
Sign up in <a href="https://ngrok.com/"><img src="https://i.ibb.co/HpCw3jR/fg.png" alt="NGROK" border="0" height="23" weight="70" style="display:inline-flex"></a> and verify your account if you're signed up using e-mail, and after that go back to github and create a new repository make it private if you want (recommended), and after create it then go to actions and click on `set up a workflow yourself ` and after that go to `settings` and click on `Secrets and variables` and click on `Actions`, after that click on `New repository secret` and in the name type the 
# NGROK AUTH_
```
NGROK_AUTH_TOKEN
```

`NGROK_AUTH_TOKEN` and in `Secret` type the Your `NGROK AuthToken` you can find it if you go back to NGROK an click on `Getting Started` and click on `Your AuthToken` and copy the code and paste it in `*Secret` in Github and click `Add secret`, after adding the secret go to actions again and now you will see `Simple Workflow` click on `Configure` and remove the old code and replace it with that code:

# RDP Configure Yaml Code

```
name: CI


on: [push, workflow_dispatch]


jobs:

  build:


    runs-on: windows-latest


    steps:

    - name: Download

      run: Invoke-WebRequest https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-windows-amd64.zip -OutFile ngrok.zip

    - name: Extract

      run: Expand-Archive ngrok.zip

    - name: Auth

      run: .\ngrok\ngrok.exe authtoken $Env:NGROK_AUTH_TOKEN

      env:

        NGROK_AUTH_TOKEN: ${{ secrets.NGROK_AUTH_TOKEN }}

    - name: Enable TS

      run: Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server'-name "fDenyTSConnections" -Value 0

    - run: Enable-NetFirewallRule -DisplayGroup "Remote Desktop"

    - run: Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp' -name "UserAuthentication" -Value 1

    - run: Set-LocalUser -Name "runneradmin" -Password (ConvertTo-SecureString -AsPlainText "P@ssw0rd!" -Force)

    - name: Create Tunnel

      run: .\ngrok\ngrok.exe tcp 3389

```

Copy the code and replace it with the old code

<img src="https://i.ibb.co/vYSDx5g/asd.png" alt="paste it here" border="0">

And click on `Commit changes`

<img src="https://i.ibb.co/wMVrQwL/z.png" alt="z" border="0">

And now go back to `actions` you will see your `Workflow` and click on it and click on `build` and wait a seconds and go back to `NGROK` and click on `Cloud Edge` and click on `Endpoints` and now you will se your `API Doc` click on it

<img src="https://i.ibb.co/vPhzf9h/xc.png" alt="API Doc" border="0">

And copy the URL after `top://` like this:

<img src="https://i.ibb.co/Czh4prc/sd.png" alt="Copy it" border="0">

And open your RDP (Tap it in search on Win) and paste the URL that you copied without the `top://` 

<img src="https://i.ibb.co/D4sPts5/as.png" alt="RDP - Remote Desktop Protocol" border="0">

And in `Username` type this username :

# Username
```
runneradmin
```

And in the Password type this password

# Password
```
P@ssw0rd!
```

And That's it!!

<img src="https://i.ibb.co/vczxndN/aaaa.png" alt="RDP Lifetime" border="0">


Hope that helps You all :)

# Donate&#10084;

 `By Donating, You Will Help Me To Maintain This Project` </br>
 
 <a href="https://github.com/sponsors/REBLOX01"><img src="https://camo.githubusercontent.com/2bfa6102e99ff9a137185897b0a566aa0977a4790348c462e6951829e787af8f/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f446f6e6174652d50617950616c2d677265656e2e737667" alt="Donate" data-canonical-src="https://img.shields.io/badge/Donate-PayPal-green.svg" style="max-width: 100%;" class="hoverZoomLink"></a>

</br>

 `Buy me a Coffee` </br>
 
<a href="https://www.buymeacoffee.com/arosck1"><img src="https://img.buymeacoffee.com/button-api/?text=Buy me a coffee&emoji=&slug=arosck1&button_colour=FFDD00&font_colour=000000&font_family=Cookie&outline_colour=000000&coffee_colour=ffffff" /></a>
