# Universal Robot Control - FactoryTalk Optix Library Procedure
## Creating the Library
The following steps define how to create a reusable library based on the v3.01 URC Library. These steps only need to be executed once but may require modification in future releases of the URC Library.
1.	Open the Robotics_v3_01.optix project that is attached to the ACM project.
2.	Find and Replace *../../../../../UI/FwkUISession* with *{Session}* on the **TeachObjectScreen** Folder

![S1-2](https://github.com/cdal3/FTOptixImportURCProcedure/blob/main/Images/1-2.png)

3.	Find and Replace *../../../../../UI/FwkUISession* with *{Session}* on the **ZoneScreen** Folder

![S1-3](https://github.com/cdal3/FTOptixImportURCProcedure/blob/main/Images/1-3.png)

4.	Create a Folder in the UI Folder called *UI_URC* and a sub-folder called *Screens*. Drag all Screens from the **UI/Screens** folder to the **UI/UI_URC/Screens** folder. Select **Move** when prompted.

![S1-4](https://github.com/cdal3/FTOptixImportURCProcedure/blob/main/Images/1-4.png)

5.	Drag the remaining UI Folders (**Stylesheets, Framework, and Panels**) to the **UI_URC** folder. Select **Move** when prompted.

![S1-5](https://github.com/cdal3/FTOptixImportURCProcedure/blob/main/Images/1-5.png)

6.	Create a Folder in the Model Folder called *Model_URC* and drag all Folders from the **Model** Folder into the newly created **Model/Model_URC** Folder. Select **Move** when prompted.

![S1-6](https://github.com/cdal3/FTOptixImportURCProcedure/blob/main/Images/1-6.png)

7.	Drag the **Model/Model_URC** Folder into the **UI/UI_URC** Folder. Select **Move** when prompted.

![S1-7](https://github.com/cdal3/FTOptixImportURCProcedure/blob/main/Images/1-7.png) 

8.	Save the project.
9.	Open the Template Libraries and create a new Library with a custom name to define your URC library.

![S1-9](https://github.com/cdal3/FTOptixImportURCProcedure/blob/main/Images/1-9.png)

10.	Drag the **UI/FwkUISession (type), UI/UI_URC Folder, and Retentivity/RoboticsApplicationRetentivityStorage** objects into the newly created Library.

![S1-10](https://github.com/cdal3/FTOptixImportURCProcedure/blob/main/Images/1-10.png) 
 
## Using the Library
The following steps define how to instantiate the library elements into an existing or new project.
1.	Open an existing or new project.
2.	Ensure the Project has the following configured
-	NativePresentationEngine
-	WebPresentationEngine
-	RAEtherNet_IPStation with the URC Device Handler and Robot rOS program tags imported
-	A PanelLoader named *PanelLoader_Main* on the **MainWindow**
> [!Note] 
> If you choose to place the URC content elsewhere, see **Appendix A** for reconfiguring the navigation buttons
3.	Open the URC Template Library.
4.	Drag **FwkUISession** and **UI_URC** into the **UI** Folder.

![S2-4](https://github.com/cdal3/FTOptixImportURCProcedure/blob/main/Images/2-4.png)

5.	Drag **RoboticsApplicationRetentivityStorage** into the **Retentivity** Folder. Select **Import as Instance** when prompted.

![S2-5](https://github.com/cdal3/FTOptixImportURCProcedure/blob/main/Images/2-5.png)

6.	Resolve the following Dynamic Links on **Retentivity/RoboticsApplicationRetentivityStorage1**:
-	Nodes/Node1: **UI/UI_URC/Model_URC/URC**

![S2-6](https://github.com/cdal3/FTOptixImportURCProcedure/blob/main/Images/2-6.png)

7.	Resolve the following Dynamic Links on **UI/FwkUISession (type)**:
-	_CurrentScreen: **UI/UI_URC/Screens/Robot_Screen1**
-	Ref_NativePresentationEngine: **UI/NativePresentationEngine**
-	Ref_WebPresentationEngine: **UI/WebPresentationEngine**
-	Ref_FrameworkFolder: **UI/UI_URC/Framework**
-	Ref_StyleSheetsFolder: **UI/StyleSheets**
-	Ref_RobotObj: **UI/UI_URC/Model_URC/URC/raR_Robot_Robot1**

![S2-7](https://github.com/cdal3/FTOptixImportURCProcedure/blob/main/Images/2-7.png)

8.	Set the **NativePresentationEngine and WebPresentationEngine Session** to **FwkUISession** and the **Style sheet** to your needs.

![S2-8](https://github.com/cdal3/FTOptixImportURCProcedure/blob/main/Images/2-8.png)

9.	Set the **MainWindow/PanelLoader_Main Panel property** to **UI/UI_URC/Screens/Splash_Screen**.
> [!Note]
> If your PanelLoader is not called *PanelLoader_Main* and is not on the **MainWindow**, see additional steps in **Appendix A**.

![S2-9](https://github.com/cdal3/FTOptixImportURCProcedure/blob/main/Images/2-9.png)

10.	Set the **UI/UI_URC/Model_URC/URC/raR_Robot_Robot1 Ref_rOS and Ref_rDH** to the appropriate Tag folders from your RAEtherNet_IPStation.

![S2-10](https://github.com/cdal3/FTOptixImportURCProcedure/blob/main/Images/2-10.png)

 
## Appendix A: Modifying the Default PanelLoader_Main
The URC Splash_Screen contains a button to launch the associated robot screens. It is hardcoded to the {PanelLoader_Main}/ChangePanel method to change screens. The following will guide you through pointing this to a different PanelLoader.
1.	Open the Properties for **UI/UI_URC/Framework/RobotInstance_Navigation/Button_NavToRobotInstance**
2.	Under **Events**, Double Click **{PanelLoader_Main}/ChangePanel** and select the desired PanelLoader.
> [!Note]
> The change will not be reflected until you navigate away from the **RobotInstance_Navigation** object and return.

![Sa-2](https://github.com/cdal3/FTOptixImportURCProcedure/blob/main/Images/a-2.png)

3.	Set the Panel property to **UI/UI_URC/Screens/Splash_Screen** on your custom PanelLoader

![Sa-3](https://github.com/cdal3/FTOptixImportURCProcedure/blob/main/Images/a-3.png)
---

 
