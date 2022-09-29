Movement Types
==============

**Movement Types**
^^^^^^^^^^^^^^^^^^

The GDXR VR Template contains three movement types built directly into the VRPawn Blueprint.
 
- Telleport locomotion
- Smooth locomotion
- Shift locomotion

The template use telleport movement by default but this can be changed as desired.  

There are two ways of switching movement types

- Runtime - Usefull if you want players to choose the movement method they prefer.
- Directly in the VR Pawn - Usefull if you want to choose the method best suited for your project

**Change At Runtime example**

If you wish to change the movement type at runtime there is an exmple for how to do so located inside the UMG Example WB_MovementType.

The example currently uses cast nodes to communicate with the VRPawn blueprint to set the necessey variables. This will be updated to work with Event Dispatchers for easier modification.

located in: Content>VRTemplate>UMG

.. image:: /images/movementimages/movementumgexample.PNG
  :width: 400
  :alt: movement umg example

To change the movement mode in the VRPawn before game play begins, you can check out the sections bellow for each movement type. 

**Telleport Locomotion**
^^^^^^^^^^^^^^^^^^^^^^

1. Open the VRPawn blueprint located in Content>VRTemplate>Blueprints>VRPawn

2. Make sure the "UseShiftLocomotion" variable is set to "False".

.. image:: /images/movementimages/shiftmovementvariable.PNG
  :width: 400
  :alt: Shift movement variable

.. image:: /images/movementimages/shiftmovementvariableFalse.PNG
  :width: 400
  :alt: shift movement variable set to false

--------------------------------------------------------------------------------------------------------------------------------

3. Make sure the "UseSmoothLocomotion" Variable is set to "False"

.. image:: /images/movementimages/smoothlocomotionvariable.PNG
  :width: 400
  :alt: smooth locomotion variable

.. image:: /images/movementimages/smoothmovementvariableFalse.PNG
  :width: 400
  :alt: smooth locomotion variable set to false.

Doing this will enable telleport movement.

**Smooth Locomotion**
^^^^^^^^^^^^^^^^^^^^^



**Shift Locomotion**
^^^^^^^^^^^^^^^^^^
