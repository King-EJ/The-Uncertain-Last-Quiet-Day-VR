# The-Uncertain-Last-Quiet-Day-VR
VR Mod for The Uncertain: Last Quiet Day "Developer: ComonGames "

THE UNCERTAIN VR  -  VR mod for "The Uncertain: Last Quiet Day" (Unity 5.3.4, 64-bit)
=====================================================================================

Version 0.1.11 (test build).

WHAT IT DOES
------------
* Full stereo VR through OpenXR (SteamVR, Meta/Oculus, Virtual Desktop, WMR...).
* Three ways to watch the game (right stick click: tap = Cinematic <-> First person, hold = third person):
  - Cinematic (default): you stand where the game's camera is, so every fixed camera angle
    becomes a 3D diorama you can look around in. The view turns with the camera only when the
    shot changes (CameraYaw), so it stays comfortable.
  - First person: you are the robot (its head is hidden). Snap turn with the right stick.
    The game's camera follows your headset, so you can point at anything you see and the
    interaction wheel appears on it.
  - Follow: the view floats behind the robot (third person), with snap turn.
* The left stick walks where you are looking.
* Point with your right controller: the game's cursor goes where you point. Point at objects to
  get their interaction icons, and pull the trigger to use them. Point at menus and dialogue
  choices and click them with the trigger.
* Menus, subtitles and the game's icons appear on a screen placed exactly where the flat game's
  picture would be, so icons sit on top of the objects they belong to.
* Fades to black are shown in the headset.
* Bloom, tone mapping and fog are copied from the game camera to the headset.

INSTALL
-------
1. Remove any other VR mod or IPA / VRGIN plugin from the game folder first.
2. Copy EVERYTHING in this zip into the game folder (next to the game's .exe), overwrite.
   Important: this includes BepInEx\config\BepInEx.cfg - it tells BepInEx to start in a way that
   works with this old Unity version (the normal way gives a black screen).
3. IMPORTANT - in Steam: right-click The Uncertain > Properties > Launch Options, enter
       -force-gfx-direct
   (this old Unity version can only hand its picture to the headset when it renders on the main
   thread; without it the game crashes on the first VR frame, so the mod will not start VR).
4. Start Steam and SteamVR (or your OpenXR runtime), then launch the game FROM STEAM
   (the Steam version quits if it is started without Steam).

CONTROLS (right-handed default; the game runs in its gamepad mode)
------------------------------------------------------------------
Right trigger ........ Point at a menu button / an icon of the interaction wheel and pull to click it.
                       Pointing at an object shows its interaction wheel: click an icon with the
                       trigger, or press A / B / X / Y like on a gamepad.
A .................... InteractionA (confirm, skip line)
B .................... InteractionB / back
X / Y ................ InteractionX / InteractionY (the other interaction choices)
Left stick ........... Walk (towards where you look). Also navigates menus.
Left grip ............ Run
Left trigger ......... Show all hotspots
Left stick click ..... Tap: Menu (pause).  Hold: skip cutscene
Right stick L/R ...... Snap turn
Right stick up/down .. Scroll
Right stick click .... Tap: Cinematic <-> First person.  Hold: third person (Follow) <-> First person
Both stick clicks .... Re-centre the view

CONFIG  -  BepInEx\config\uncertain.vr.cfg  (created on first launch; edits apply live)
---------------------------------------------------------------------------------------
[General]   ViewMode (Cinematic / Follow), CameraYaw (OnCut / Always / Never),
            MovementDirection (Head / OffHand / Game), SnapTurn, LeftHanded, MirrorToDesktop
[Camera]    WorldScale (if the world feels too big / small), CinematicHeightOffset,
            FollowDistance / FollowHeight, CopyCameraEffects / SkipCameraEffects, ShowFades
[FirstPerson] HideHead, EyeHeight (0 = automatic), ForwardOffset, StayInCutscenes,
            GameCameraFollowsHead, GameCameraFov (size of the icon / subtitle screen in first person)
[Pointer]   HandPointer, ShowPointer, AimRotationOffset (angle of the beam in your hand)
[UI]        FollowMode (Auto / Camera / Lazy / Head / GunHand / OffHand), CameraScreenDistance,
            BackgroundOpacity (0.5 = dark backing behind the menus), FlipGameGUI
[Controls]  which VR control presses each of the game's actions, e.g.  Run = OffStickClick
            (Main... = right hand, Off... = left hand; add :tap or :hold; comma = any of them)

TROUBLESHOOTING
---------------
* Log: BepInEx\LogOutput.log - please send it with any report (close the game first).
  If the game crashes, also send BepInEx\UncVR_trace.log.
* Nothing happens at all (no LogOutput.log): rename winhttp.dll to version.dll and try again.
* Black screen / the game does not start properly: open BepInEx\config\BepInEx.cfg and under
  [Preloader.Entrypoint] change  Type = Camera  to  Type = MonoBehaviour.  If it crashes, also send
  the game's Unity log (TUE1_Data\output_log.txt, next to the .exe).
* The picture looks too bright / too dark: set [Camera] CopyCameraEffects = None and tell me.
* Menus, icons or the cursor appear upside down on the VR screen: set [UI] FlipGameGUI = true.
* The game freezes or crashes when a menu opens: set [UI] ShowGameGUI = false and tell me.
* The screen with the menus is hard to see: try [UI] FollowMode = Lazy (floats in front of you).

CREDITS & LICENCES
------------------
* The Uncertain: Last Quiet Day belongs to ComonGames.
* OpenXR.dll (native OpenXR bridge) by Astien (c) 2025 - free, non-commercial redistribution,
  see BepInEx\plugins\UncVR\LICENSES. This mod must stay free.
* BepInEx - LGPL 2.1. This is a fan-made, non-commercial mod.
