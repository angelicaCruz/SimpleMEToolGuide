# Question and Answer

### HoloLens appears offline?
```
1. Make sure your HoloLens is connnected to the correct WiFi (same one the PC is connected to).
2. Try to restart your HoloLens and LiveAgent via Device portal (go to http://your-hololens-ip in your browser, and restart DataMeshLiveAgent at the "App" tab).   
3. Contact technician to check the IP configuration for your HoloLens.
```

### No streaming video signal from camera? 
```
1. Check if the HDMI/SDI cables are connected to the right ports and try to reconnect.   
2. Use the Blackmagic Media Express software from the Windows Start Menu to see if there is a live stream displayed under the "Log and Capture" tab.
3. If nothing shows up in the second step, try to restart your PC and the camera.
```

### PC app frozen with "loading cursor"?
```
1. When it happens, it means that MeshExpertServer is not connected. Make sure to have a valid MeshExpert License installed and it has not expired.
2. Check the "MeshExpert Center" dashboard to make sure the Services are running.
3. To make sure it's not your Firewall that caused the problem, turn it of and restart the application.
```

### Holograms not showing on the screen?
```
1. Anchor must be out of view. Delete the file under "SaveData" folder under the App root folder.
```
