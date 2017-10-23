#METool Guide for Developers

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
