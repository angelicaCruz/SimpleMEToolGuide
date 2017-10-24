# MeshExpert Live: Quick Guide for Developers

## RIG Ready

First get your Rig ready and have **MeshExpert software** installed and configured, like the following:

<p align="center">
<img src="https://user-images.githubusercontent.com/7636848/26872303-9d9425d0-4ba8-11e7-8e90-80e7389a41e2.png" width="500">
<p align="center"><em>Get Rig Ready</em></p>
</p>


## Import METoolkit

1. Download METoolkit from DataMesh Download Center.
2. Import METoolkit.

<p align="center">
<img src="https://user-images.githubusercontent.com/26377727/31927182-7359d4ce-b8c5-11e7-92a7-8c2b3dffa84b.png" width="500">
<p align="center"><em>Import METoolkit</em></p>
</p>

3. Find MEHoloEntrance, drag into Scene. Add **AppID** then,**CreateAllMEHoloModule**. Decide which modules to enable. 
   Have in mind the module dependencies.
<p align="center">
<img src="https://user-images.githubusercontent.com/26377727/31932222-539ade72-b8d8-11e7-9908-fae149f5ee0c.png" />
<img src="https://user-images.githubusercontent.com/26377727/31932223-53cced2c-b8d8-11e7-8645-c432767c9ddd.png"  width="300" height="412">
<p align="center"><em>Create All MEHolo Module & Set App ID</em></p>
</p>
   
4. Modify **MEConfigNetwork.ini** accordingly to your server's IP address. 
   This file needs to correct as it will be the same for every build regardless of the target device.
   
## Use METoolkit
Below is a sample code where **Collaboration Module** is used. 
```c#
using System.Collections;(....)

public class GettingStartedSample : MonoBehaviour, IMessageHandler
{
    public GameObject cube;
    private CollaborationManager collaborationManager;

    void Start()
    {
        StartCoroutine(WaitForInit());
    }

    //initialize modules and variables
    private IEnumerator WaitForInit()
    {
        MEHoloEntrance entrance = MEHoloEntrance.Instance;
        while (!entrance.HasInit)
        {
            yield return null;
        }
        collaborationManager = CollaborationManager.Instance;
        collaborationManager.AddMessageHandler(this);
        //message creation
        MsgEntry entry = new MsgEntry();
        //add enty fields
        ShowObject showObject = new ShowObject(entry);
        SceneObject roomData = new SceneObject();
        roomData.ShowObjectDic.Add(showObject.ShowId, showObject);        
        collaborationManager.roomInitData = roomData;
        collaborationManager.TurnOn();
    }
    (...)   
    //create message for collaboration
    public void DealMessage(SyncProto proto)
    {
        Google.Protobuf.Collections.RepeatedField<MsgEntry> messages = proto.SyncMsg.MsgEntry;
        if (messages == null)
            return;
        for (int i = 0; i < messages.Count; i++)
       {
            MsgEntry msg = messages[i];
            //use msg fields
            Debug.Log("Receive Message! " + msg.Pr);
        }
    }
    
    //message creation in case of new message recieved
    void Update()
    {
        if (collaborationManager != null)
        {
            if (collaborationManager.enterRoomResult == EnterRoomResult.EnterRoomSuccess)
            {
                MsgEntry entry = new MsgEntry();
                SyncMsg msg = new SyncMsg();
                msg.MsgEntry.Add(entry);
                collaborationManager.SendMessage(msg);
            }
        }
    }
}
```
For more samples, check out **Samples** folder in the METoolkit.

## Run and Debug
1. Compile the project to target multiple platforms (HoloLens, PC, UWP).
2. Start MeshExpert Center. Run the application in Unity. Build and deploy application in HoloLens(or any target device.)
3. For debugging chech the following values in the **Console** for Unity and in the **Output** window in VisualStudio for Hololens: 
   ```
   Delay : if zero, then app is not connected to the server
   ip 
   app
   IP and app information appear only if the application is connected to the server.
   ```
<p align="left">
  <img src="https://user-images.githubusercontent.com/26377727/31928385-8dbec4c8-b8ca-11e7-801f-98ee1f412fc2.png" width="425" />
  <img src="https://user-images.githubusercontent.com/26377727/31934172-fc6395a8-b8dd-11e7-9f4f-dbd5b7f2d66d.png" width="450" height="170">
  <p align="center"><em>Unity Console & VisualStudio Output Window</em></p>
</p>
