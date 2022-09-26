Build Updates
=============

**GDXR VR Template Version 0.3.6**
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Project Files Download Link:
https://www.patreon.com/posts/gdxr-vr-template-72325309?utm_medium=clipboard_copy&utm_source=copyLink&utm_campaign=postshare_creator

**Updates and Extra Features**

**GrabComponent Re-design**
---------------------------

- Re designed the Grab component to only require blend space 1D animations for grabbing and playing trigger animations. This makes creating and modifying animations much easier. Blend space animations can use only one animation if the grabbed actor doesn't need a trigger animation. All blend Space 1D’s must have there maximum axis value set to “1”
- Input Axis Trigger now runs through the Grab component and then to the grab components owned actor.
- Simplified Grabbing components code such as Sliding objects, levers and draws now select the grab component set the grab type to Use Component and set the grab component class to Sliding Component or Lever Component
- Simplified Grab Component Try Grab Function. Completely removed the snap VRHands code from the grab component. Now you just use snap and It will handle hands and controller positions. Previous code was just doing the same thing twice.
- In the Grab component - Converted the Set hand and grip states into a function to allow for easier use. It also removes duplicated code cluttering the grab component Try Grab Function.

**VR Hands**
------------
- Added - Check to see if mesh/skeleton has sockets for skeletal mesh hands to attach too. If not we notify developer using print string and set the skeletal mesh animation to grab animation.

**Torch Example**
-----------------

-Added a Torch example that can be picked up and turned on and off using the trigger. Check user notes for more info

**Weapon Update**
-----------------

⦁ Replaced and removed the Pistol Projectile (Yellow Sphere) with a line trace component. This allows us to cause damage to hit actors and provides an example on how to do damage to actors.

**Gun Range**
-------------

- Added Small Gun range so users can shoot weapons and look at how to cause damage to actors. (Work in Progress - Will be used as a save game example). 

**Fixes**
---------
- Fixed - Weapons/Grab components firing twice.
- Fixed - Grab firing twice when using grab from distance.
- Fixed - Skeletal mesh Hands now default to grab only Animation inside GrabComponent
- Fixed - Environment Lighting
- Fixed - Removed Cast to VR pawn node in grab component. Now utilised VRInteractionBPI to reset player Skeletal mesh hands to there correct location on release. Now located in the VRPawn Blueprint
- Fixed - Removed Cast node in Grab Component Try Grab. Now we get the motion controller only once directly from the VR Pawn.
- Fixed - Hands now release from draws.
- Fixed - Grab component class is now hidden by default 
- Fixed - Player no longer moves backwards when grabbing from a distance with the left hand.

**User Notes**
--------------

I enabled Support Moveable Spotlights in Project settings > Rendering > Mobile Shader Permutation Reduction to create the torch example. If you don't need the torch on Quest or movable spot lights I highly recommend disabling this option.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------

**GDXR VR Template Version 0.3**
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Project Files Download Link:
https://www.patreon.com/posts/gdxr-vr-template-71744206?utm_medium=clipboard_copy&utm_source=copyLink&utm_campaign=postshare_creator

**Updates and Extra Features**

**New Load Screen Example**
---------------------------

- Added Load Screen example is activated with the VR_GameInstance on initialize and removed after 5 seconds of player loading from inside VR_Pawn (From begin play exec).
- Added Custom Blueprint Function Library to allow loading screens to be activated from any actor.

**New UMG Screen Fade Example**
-------------------------------

- Added UMG screen fade example to have custom fade effects. Check out the APK bellow to see it in action.
- UMG restart button shows screen fade and load screen examples. 
- Added screen fade example to UMG restart button.

**Grab From Distance Update**
-----------------------------

_ Converted all grab from distance logic into a component to clean up the VR pawn and for easier readability.
_ added the ability to disable Grab From a distance without having to remove components. - Select GFDControllerComponent in VR pawn components list and set “Use Grab From Distance to False”
- Disabled Teleportation when grabbing from a distance.
- Disabled grabbing from a distance when menu is open.

**Inputs**
----------

- Grab right and grab left Input Actions now use an interface to activate, Required for grabbing from a distance as grab pressed needs to be automatically fired. this stops events being repeated.

**Draws/Sliding Actors**
------------------------

- Stopped Draws/sliding objects from snapping to the hand position on first grabbed. Now they smoothly move to it.

**Gaze Interaction Component**
------------------------------
- Added the ability to disable the gaze component without removing it from the VRPawn Components list. - Select GazeInteractionComponent and disable/enable “Use Gaze Component”, This will also disable the gaze components event tick so it will be cheaper. (Cannot be changed at runtime).

**Fixes**
---------
⦁ Fixed - a bug where objects grabbed from a distance would bounce if the thumbstick was pushed while held.
⦁ Fixed - hand not switching when grabbing objects/actors from a distance.
⦁ Fixed - hand animations not playing correctly after releasing Grabbed from distance actor.
⦁ Fixed - a bug where grab from distance trace would disappear after ending over lap of an actor/object
⦁ Fixed - Draws not returning to correct position
⦁ Fixed - Reference issue with WB_VRHud. not getting player reference on creation. Now does a pure cast to get player.
⦁ Fixed - hands not appearing after switching to controllers and back again.
⦁ Fixed - Objects not falling if hit from grab from distance trace.
⦁ Fixed - Made variables not used in components private for easier readability and to stop accidental modification

**User Notes**

I’ve converted the project to use Vulkan preview rendering level to get color to work better on Quest two. VR Preview does not work on pc with it enable (Shows Black Screen) so make sure to disable it in editor before trying to play on PC. The lighting will become bright as I’m upping it for Quest as it can be dark. To set it to normal. Find the Directional light in Outliner and set intensity to 5. 

To simply load new level and activate screen fade and load screen. From any actor/blueprint Get player pawn, cast to VR pawn (Convert to pure cast) and then can load new level event. place the level you wan to load in the name box. When level loads the load screen will automatically be removed after 3 seconds and call the fade to scene interface being listened to by the WB_Screenfade.

I've also just got my hands on some OG Vive controllers so I can begin looking at setting up the project for Vive and Valve Index Inputs.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------

**GDXR VR Template Version 0.2**
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Download Link:
https://www.patreon.com/posts/gdxr-vr-template-71442004?utm_medium=clipboard_copy&utm_source=copyLink&utm_campaign=postshare_creator

**Updates and Extra Features**

**Player Health**
-----------------
- Added player health bar example to WB_VRHud (Which pulls health data from Game Instance).
- Implemented Damage System example (UE5’s Default System).
- Damage Health Pad Example
- Heal Health Pad Example

**Grab From Distance Rebuild**
------------------------------
- Re-Built Grab from distance code. Use the grip button to activate pointer when hitting Grab from distance object pull back on thumbstick to snap object to your hand. (This took the most amount of time - Sorry).
- Added Grab From Distance VFX Pointer

**New Mobile VR Graphics Showcase**
-----------------------------------
- New Mobile Graphics Showcase (Localized Reflection Example = Material based Reflections similar to the Quest 2 game "Red Matter") - This will be moved to a new level as its own dedicated example. 

**VR hands**
------------
- Fixed hand mesh staying attached to actors after swapping hands.
- Re organized C_SkeletHand Component to stop confusion. Default skeletal mesh can now be seen in the VR pawn hand component. 

**Movement**
------------
- Fixed Swift locomotion speed an accuracy so you move to intended location, not short of it.
- Fixed Smooth Locomotion Sprinting. You can now sprint by pressing the Right Thumbstick on Quest 2. (I need to set up input for different HMD's) 

**VR Pawn**
-----------
- Organized The VRPawn Variables

**Game Instance**
-----------------
- Added A Game Instance to the project for storing variables. Health example included and a variable to store the VR pawn. You can see how these examples work by opening the WB_VRHud. Where I use the game instance to access the VR pawn where health is updated via an event dispatcher. 
- Attach the GrabFromDistanceComponent to any movable skeletal or static mesh with the GrabComponent

- Ability to mirror skeletal hand animations (Requested).
- Added the ability to use mirrored hand animations to make creating animations easier so you don't have to make animations twice unless you need to or want to.

**How To Mirror Hands**
-----------------------

- In VR pawn select the hand you want to mirror, I recommend selecting the left hand (No particular reason). 
- Set the skeletal mesh to the same as the opposite hand, in this case VR_Hand_Right
- Change the Animation Class to AB_RightHand_C 
- Change the left hand components Y Scale value to minus the number in the slot. In the template this would be -0.9 
- You now have mirrored hand setup. 

Let me know of any bugs you find over in gdxr_vr_template

--------------------------------------------------------------------------------------------------------------------------------------------------------------------

**GDXR VR Template Version 0.1**
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Download Link 
https://www.patreon.com/posts/ue5-gdxr-vr-wip-70242913?utm_medium=clipboard_copy&utm_source=copyLink&utm_campaign=postshare_creator

What It Includes

**Movement**
------------

- Movement type can be selected during runtime by pressing the menu button on the Oculus Controller. If you want to only use one type of movement you can open the VR_Pawn and select the boolean "Use Smooth Locomotion" and set it to true.
- If you want Swift movement by default (Currently needs more work) you can set the "Use Smooth Locomotion" boolean to False and Set "UseShiftMovement" To True.
- Setting Both "Use Smooth Locomotion" and "UseShiftMovement" to False will enable teleportation as the default movement method. 

**Snap Move to Location**
-------------------------

- If you with the player to snap to a specific location in the world when Pointed at you can give the actor the tag  "SnapLocation" The VR Pawn will use the 0,0,0 space to move the player there.

**VR Hud**
----------

- By default, there is a VR Hud that is on screen when the project starts its just a UMG Button currently. You can remove this by opening the VR pawn and deleting the VRHudComponent. If you want to use the hud and modify it, you can do this by modifying the WB_VRHud Widget. Make sure VRHud Component is a child of VRHudOffset(Don't delete this). You can move the arrow to control how far away the hud is from the player's camera as it exists in 3D Space.

**Gaze interaction Component**
--------------------------

- The Gaze Interaction component must be a child of the VRPawn Camera if it's being used. (I recommend not using it) as it's currently the only addition that runs on its own event tick.
- With the gaze component, I built in a timer so you can choose how long the user must look at the actor before it activates. Currently set to 2 seconds you can change this duration inside the VRPawn by selecting the GazeInteractionComponent. 
- To activate an actor with it, give the actor the Blueprint interface "VRGaze BPI"
You can then use the event Gaze Hover to receive the activate message. Check out the example Blueprint "BP_GazeExample"

**Climbing**
------------

- Currently, a work in progress as I need to fix a two handed issue. There are two methods of climbing included with the template.
- The First method is based on an actor Tag, you can give a static actor the tag "CanClimb" This is enabled on the White cube under the spectator camera actor.
- The Second Method uses a Physics material to detect the grab. Let's say you have an actor which only has specific areas you want to climb on, you can add the "PM_Climbing" Physics material to it and that will let you climb on anything with that material. The yellow actors can be seen as an example of this.

**Draws and Levers**
--------------------

- These are going to need to be explained in a video. If you need to use them simply duplicate the ones which currently exist and swap out the static meshes. 

**Grab Component**
------------------

- The Grab component contains most of the logic used in the project acting like a middle man for anything interactive.
- The grab component can be applied to any movable actor and must be a child of the skeletal or static mesh you want to interact with. Rotating the grab component after adding it as a child will update the rotation for the held object.
- Every interactable object must have sockets applied to them, three in total.
  - GripPoint
  - RightHand
  - LeftHand

- These are used to set the position of the skeletal hand meshes. I recommend viewing the sword mesh SM_Sword_01 to see how it's set up there. (I will create a video on this).
- Once the grab component is a child of the static mesh or skeletal mesh I recommend selecting the component and changing the Grab Type to "SnapVRHands(Custom Anim)" You can also set the Handheld Anim to grab or another animation if it exists.
- This will be all you need for a single animation object.
- If you want to play another animation using the controller trigger after grabbing it you can Enable "Use Trigger Animation" and then select a trigger animation to use from the drop-down.

**Using VR Hands**
------------------

- To use the VR skeletal mesh hands by Default you can open the VRPawn and Change the Boolean "Use Controllers" to False.
- To interact with UMG while using your hands you can hold the grip button and touch (Not Pull) the trigger to point. Touch the UMG and you should interact with it. 
