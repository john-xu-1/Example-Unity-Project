# Third-Person Character Controller Scripts

This folder contains two essential scripts for creating a complete third-person character controller system in Unity. Both scripts use Unity's new Input System for modern input handling.

## Scripts Overview

### 1. ThirdPersonController.cs
A comprehensive character controller that handles player movement, jumping, sprinting, and ground detection.

### 2. ThirdPersonCameraController.cs
A sophisticated camera system that provides smooth third-person camera movement with collision detection and zoom functionality.

---

## ThirdPersonController.cs

### Purpose
This script provides complete character movement functionality including walking, running, jumping, and physics-based movement with proper ground detection.

### Key Features
- **Movement**: WASD/Left Stick movement with camera-relative controls
- **Sprinting**: Hold Left Shift/Left Stick Press to run faster
- **Jumping**: Space/South button with coyote time for better feel
- **Physics**: Gravity, air control, and slope handling
- **Ground Detection**: Advanced ground checking with configurable layers

### Setup Instructions

#### 1. Component Requirements
- Add a `CharacterController` component to your player GameObject
- The script will automatically require this component

#### 2. Input System Setup
Create Input Actions for the following:
- **Move Action**: Vector2 input (WASD keys or Left Stick)
- **Jump Action**: Button input (Space key or South button)
- **Sprint Action**: Button input (Left Shift or Left Stick Press)

#### 3. Configuration
**Movement Settings:**
- `moveSpeed`: Base walking speed (default: 4.0)
- `sprintSpeed`: Running speed (default: 6.5)
- `acceleration`: How quickly speed increases (default: 12)
- `deceleration`: How quickly speed decreases (default: 14)
- `airControl`: Movement control while airborne (0-1, default: 0.5)

**Jump & Gravity:**
- `jumpHeight`: How high the character jumps (default: 1.3)
- `gravity`: Downward force strength (default: 20)
- `fallMultiplier`: Extra gravity when falling (default: 1.5)
- `coyoteTime`: Time after leaving ground when jump still works (default: 0.1)

**Grounding:**
- `groundMask`: Which layers count as ground (default: Everything)
- `groundCheckDistance`: How far to check for ground (default: 0.2)
- `slopeLimit`: Maximum walkable slope angle (default: 45°)

**References:**
- `cameraTransform`: Assign your camera transform for movement direction

#### 4. Input Actions Assignment
Assign the created Input Actions to:
- `moveAction`: Your movement Vector2 action
- `jumpAction`: Your jump button action
- `sprintAction`: Your sprint button action

---

## ThirdPersonCameraController.cs

### Purpose
This script provides a smooth, collision-aware third-person camera that orbits around the player with configurable zoom and rotation controls.

### Key Features
- **Orbit Controls**: Mouse/Right Stick camera rotation
- **Zoom**: Mouse scroll/Trigger zoom in/out
- **Collision Detection**: Camera automatically adjusts to avoid walls
- **Smooth Movement**: Damped camera movement for professional feel
- **Cursor Management**: Automatic cursor locking/unlocking

### Setup Instructions

#### 1. Component Requirements
- Attach this script to your Main Camera GameObject
- Ensure the camera is a child of the player or positioned independently

#### 2. Input System Setup
Create Input Actions for the following:
- **Look Action**: Vector2 input (Mouse delta or Right Stick)
- **Zoom Action**: Float input (Mouse scroll or Triggers)
- **Toggle Cursor Action**: Button input (Escape or Start button)

#### 3. Target Assignment
- `target`: Assign your player's Transform
- `targetOffset`: Adjust camera pivot point relative to player (default: 0, 1.6, 0)

#### 4. Configuration

**Orbit Settings:**
- `mouseXSensitivity`: Horizontal mouse sensitivity (default: 150)
- `mouseYSensitivity`: Vertical mouse sensitivity (default: 120)
- `minPitch`: Minimum vertical angle (default: -35°)
- `maxPitch`: Maximum vertical angle (default: 70°)
- `rotationDamp`: How smooth camera rotation is (default: 12)

**Zoom Settings:**
- `minDistance`: Closest camera distance (default: 1.2)
- `maxDistance`: Farthest camera distance (default: 6.0)
- `distanceDamp`: How smooth zoom changes are (default: 10)

**Collision Settings:**
- `collisionMask`: Which layers block camera (default: Everything)
- `collisionRadius`: Camera collision sphere size (default: 0.25)
- `collisionBuffer`: Extra space from walls (default: 0.1)

**Input Actions Assignment:**
- `lookAction`: Your look Vector2 action
- `zoomAction`: Your zoom float action
- `toggleCursorAction`: Your cursor toggle button action

**Cursor Settings:**
- `lockCursorOnStart`: Whether to lock cursor when game starts (default: true)

---

## Complete Setup Guide

### Step 1: Create Your Player
1. Create an empty GameObject for your player
2. Add a `CharacterController` component
3. Add the `ThirdPersonController` script
4. Configure the CharacterController's center, radius, and height appropriately

### Step 2: Set Up the Camera
1. Create a Main Camera (or use existing)
2. Add the `ThirdPersonCameraController` script
3. Assign the player's Transform to the `target` field

### Step 3: Configure Input System
1. Open Window > Input System > Input Actions
2. Create a new Input Action Asset
3. Create the following actions:
   - **Move** (Vector2): WASD + Left Stick
   - **Look** (Vector2): Mouse Delta + Right Stick
   - **Jump** (Button): Space + South Button
   - **Sprint** (Button): Left Shift + Left Stick Press
   - **Zoom** (Float): Mouse Scroll + Triggers
   - **Toggle Cursor** (Button): Escape + Start Button

### Step 4: Assign Input Actions
1. In both scripts, assign the corresponding Input Actions
2. Test the controls in Play mode

### Step 5: Fine-tune Settings
- Adjust movement speeds to match your game's feel
- Adjust camera sensitivity and limits
- Configure collision layers for camera and ground detection
- Test and adjust damping values for smooth movement

---

## Troubleshooting

### Common Issues

**Camera doesn't follow player:**
- Ensure the `target` is assigned in ThirdPersonCameraController
- Check that the camera script is enabled

**Movement feels wrong:**
- Verify Input Actions are properly assigned
- Check that the camera transform is assigned to the controller
- Ensure CharacterController settings are appropriate

**Camera clips through walls:**
- Adjust `collisionMask` to include wall layers
- Increase `collisionRadius` if needed
- Check that walls have colliders

**Input not working:**
- Ensure Input Actions are enabled
- Check that the Input System package is installed
- Verify action bindings are correct

### Performance Tips
- Use appropriate collision layers to avoid unnecessary raycasts
- Adjust damping values for your target framerate
- Consider using LOD systems for distant objects

---

## Advanced Features

### Extending the Controller
Both scripts are designed to be easily extensible:
- Add animation integration in the movement script
- Implement camera shake or effects in the camera script
- Add additional input actions for special abilities
- Integrate with UI systems for settings menus

### Customization Examples
- Modify jump behavior for double-jumping
- Add camera shake on landing
- Implement camera transitions for cutscenes
- Add movement states for different animations

This system provides a solid foundation for third-person games and can be extended based on your specific needs.


