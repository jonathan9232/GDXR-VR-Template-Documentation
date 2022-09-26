Build Updates
=============

GDXR VR Template Version 0.1 Download
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Download Link 
https://www.patreon.com/posts/ue5-gdxr-vr-wip-70242913?utm_medium=clipboard_copy&utm_source=copyLink&utm_campaign=postshare_creator

What It Includes

**Movement**
------------

⦁ Movement type can be selected during runtime by pressing the menu button on the Oculus Controller. If you want to only use one type of movement you can open the VR_Pawn and select the boolean "Use Smooth Locomotion" and set it to true.
⦁ If you want Swift movement by default (Currently needs more work) you can set the "Use Smooth Locomotion" boolean to False and Set "UseShiftMovement" To True.
⦁ Setting Both "Use Smooth Locomotion" and "UseShiftMovement" to False will enable teleportation as the default movement method. 

**Snap Move to Location**
-------------------------

If you with the player to snap to a specific location in the world when Pointed at you can give the actor the tag  "SnapLocation" The VR Pawn will use the 0,0,0 space to move the player there.

**VR Hud**
----------

⦁ By default, there is a VR Hud that is on screen when the project starts its just a UMG Button currently. You can remove this by opening the VR pawn and deleting the VRHudComponent. If you want to use the hud and modify it, you can do this by modifying the WB_VRHud Widget. Make sure VRHud Component is a child of VRHudOffset(Don't delete this). You can move the arrow to control how far away the hud is from the player's camera as it exists in 3D Space.

**Gaze interaction Component**
--------------------------

⦁ The Gaze Interaction component must be a child of the VRPawn Camera if it's being used. (I recommend not using it) as it's currently the only addition that runs on its own event tick.
⦁ With the gaze component, I built in a timer so you can choose how long the user must look at the actor before it activates. Currently set to 2 seconds you can change this duration inside the VRPawn by selecting the GazeInteractionComponent. 
⦁ To activate an actor with it, give the actor the Blueprint interface "VRGaze BPI"
You can then use the event Gaze Hover to receive the activate message. Check out the example Blueprint "BP_GazeExample"

**Climbing**
------------

⦁ Currently, a work in progress as I need to fix a 2 handed issue. There are two methods of climbing included with the template.
⦁ The First method is based on an actor Tag, you can give a static actor the tag "CanClimb" This is enabled on the White cube under the spectator camera actor.
⦁ The Second Method uses a Physics material to detect the grab. Let's say you have an actor which only has specific areas you want to climb on, you can add the "PM_Climbing" Physics material to it and that will let you climb on anything with that material. The yellow actors can be seen as an example of this.

**Draws and Levers**
--------------------

⦁ These are going to need to be explained in a video. If you need to use them simply duplicate the ones which currently exist and swap out the static meshes. 
[12:01 AM]Jonathan (GDXR): Grab Component
⦁ The Grab component contains most of the logic used in the project acting like a middle man for anything interactive.
⦁ The grab component can be applied to any movable actor and must be a child of the skeletal or static mesh you want to interact with. Rotating the grab component after adding it as a child will update the rotation for the held object.
⦁ Every interactable object must have sockets applied to it.
three in total
- GripPoint
- RightHand
- LeftHand

⦁ These are used to set the position of the skeletal hand meshes. I recommend viewing the sword mesh SM_Sword_01 to see how it's set up there. (I will create a video on this).
⦁ Once the grab component is a child of the static mesh or skeletal mesh I recommend selecting the component and changing the Grab Type to "SnapVRHands(Custom Anim)" You can also set the Handheld Anim to grab or another animation if it exists.
⦁ This will be all you need for a single animation object.
⦁ If you want to play another animation using the controller trigger after grabbing it you can Enable "Use Trigger Animation" and then select a trigger animation to use from the drop-down.

**Using VR Hands**
------------------

⦁ To use the VR skeletal mesh hands by Default you can open the VRPawn and Change the Boolean "Use Controllers" to False.
⦁ To interact with UMG while using your hands you can hold the grip button and touch (Not Pull) the trigger to point. Touch the UMG and you should interact with it. 
