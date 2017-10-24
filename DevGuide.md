# MeshExpert Live: Quick Guide for Developers

## RIG Ready

First get your Rig ready and have MeshExpert software installed and configured, like the following:


<p align="center">
<img src="https://user-images.githubusercontent.com/7636848/26872303-9d9425d0-4ba8-11e7-8e90-80e7389a41e2.png" width="500">
<p align="center"><em>Get Rig Ready</em></p>
</p>


## Import METoolkit

1. Download METoolkit  from DataMesh Download Center.
2. Import METoolkit. (a snapshot here)
3. Find MEHoloEntrance, drag into Scene. Add **AppID** then, **CreateAllMEHoloModule**. Decide which modules to enable. Have in mind the dependencies.

## Use METoolkit

simple instructions about writing code.

## Run and Debug

1. Compile the project to target multiple platforms (HoloLens, PC, UWP).
2. Run balabala (show the snapshoots)
3. For Debugging









- Install MeshExpert Center. 

- Import METoolkit.
- Find MEHoloEntrance, drag into Scene.
  Add **AppID** then, **CreateAllMEHoloModule**.
  Decide which moduled to enable. Have in mind
  the dependencies. 

- Find *Streamig Assets** and then open
  **MEConfigNetwork.ini**. Make sure that 
  Server_Host = ServiceIP(MeshExpert Portal).

- MEConfigNetwork.ini is the same for every applciation
  regardless of the device. 
  If the application is not runnin in Unity or in 
  any standalone device, you can find the configuration 
  file in **PersistentDataPath**.

- See Assets->DataMesh->Samples
  for coding and modules samples. 

- For debugging: 
    - Make sure Hololens and WorkStation belong to the same
      network. 
    - To make sure that the application is connected to the
      server, check the Delay value on Console or in the 
      Output screen. 

