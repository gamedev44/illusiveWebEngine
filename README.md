# A WEB-GPU PORT OF ILLUSION SDK.
![Illusion Game Engine Logo](https://github.com/gamedev44/IE/blob/main/illusionlogo.png?raw=true)

## by: Mr. Asterisk

# Engine Documentation

## Overview

The Illusion Engine is a browser-based game engine built on top of Babylon.js and Three.js, designed to simplify the creation of 3D scenes and prototypes. This engine was created single-handedly by Asterisk, also known as GameDev44, during their free time. It aims to address the hassles of large downloads, steep learning curves, lack of control, and frequent bugs and crashes found in traditional game engines. The Illusion Engine sets an example for future engines by providing a lightweight, easy-to-use platform for game development directly in the browser.

## Features

### Scene Creation

- **Automatic Scene Setup**: Initialize a basic scene with default lighting and a camera.
- **Custom Scripting**: Use Illusion's custom syntax to create and manipulate objects in the scene.
- **Live Execution**: Toggle live script execution to see changes in real-time.
- **Object Selection**: Select and manipulate objects using Gizmo controls.
- **Delete Function**: Delete the selected object from the scene with a confirmation prompt.
- **Import Models**: Import OBJ and FBX models directly into the scene.
- **Lighting and Cameras**: Add different types of lights and cameras to the scene using the custom syntax.
- **Physics**: Enable physics and add physics properties to objects.
- **Audio**: Add and control audio within the scene.

### Modes

- **Modeling Mode**: Switch to a 3D modeling interface.
- **Style Mode**: Edit materials and shaders.
- **Shadeup Mode**: Advanced shader editing.
- **Audio Mode**: Create and manage audio assets.
- **Animation Mode**: Animate models using keyframes.
- **Map Mode**: Create and edit landscape elements.
- **Logic Graph Mode**: Visual scripting with logic graphs.
- **Text Editor Mode**: Write and execute custom scripts.

## Illusion to Babylon.js Translation Chart

| **Illusion Syntax**                  | **Description**               | **Babylon.js Equivalent**                  |
|--------------------------------------|-------------------------------|---------------------------------------------|
| `createBox(name)`                    | Create a box                  | `BABYLON.MeshBuilder.CreateBox(name, {}, scene)` |
| `createSphere(name)`                 | Create a sphere               | `BABYLON.MeshBuilder.CreateSphere(name, {diameter: 2}, scene)` |
| `createGround(name)`                 | Create a ground plane         | `BABYLON.MeshBuilder.CreateGround(name, {width: 100, height: 100}, scene)` |
| `createCylinder(name)`               | Create a cylinder             | `BABYLON.MeshBuilder.CreateCylinder(name, {height: 2, diameter: 2}, scene)` |
| `createCapsule(name)`                | Create a capsule              | `BABYLON.MeshBuilder.CreateCapsule(name, {height: 2, radius: 1}, scene)` |
| `createPlane(name)`                  | Create a plane                | `BABYLON.MeshBuilder.CreatePlane(name, {size: 2}, scene)` |
| `move(obj, x, y, z)`                 | Move an object                | `obj.position.set(x, y, z)`                 |
| `rotate(obj, x, y, z)`               | Rotate an object              | `obj.rotation.set(x, y, z)`                 |
| `scale(obj, x, y, z)`                | Scale an object               | `obj.scaling.set(x, y, z)`                  |
| `addHemisphericLight(name)`          | Add hemispheric light         | `new BABYLON.HemisphericLight(name, new BABYLON.Vector3(1, 1, 0), scene)` |
| `addPointLight(name, x, y, z)`       | Add point light               | `new BABYLON.PointLight(name, new BABYLON.Vector3(x, y, z), scene)` |
| `addArcRotateCamera(name, x, y, z)`  | Add arc rotate camera         | `new BABYLON.ArcRotateCamera(name, -Math.PI / 2, Math.PI / 2, 10, new BABYLON.Vector3(x, y, z), scene)` |
| `addFollowCamera(name, target)`      | Add follow camera             | `new BABYLON.FollowCamera(name, new BABYLON.Vector3(0, 10, -10), scene, { radius: 10, heightOffset: 10, cameraAcceleration: 0.1, maxCameraSpeed: 10 }).lockedTarget = target` |
| `importOBJ(name, path)`              | Import OBJ model              | `BABYLON.SceneLoader.ImportMesh("", path, "", scene, function (newMeshes) { name = newMeshes[0]; })` |
| `importFBX(name, path)`              | Import FBX model              | `new THREE.FBXLoader().load(path, function (object) { object.name = name; scene.add(object); })` |
| `addAudio(name, path)`               | Add audio                     | `new BABYLON.Sound(name, path, scene, null, { autoplay: true })` |
| `setGravity(x, y, z)`                | Set scene gravity             | `scene.gravity = new BABYLON.Vector3(x, y, z)` |
| `enablePhysics()`                    | Enable physics                | `scene.enablePhysics(new BABYLON.Vector3(0, -9.81, 0), new BABYLON.CannonJSPlugin())` |
| `addPhysics(obj)`                    | Add physics to an object      | `obj.physicsImpostor = new BABYLON.PhysicsImpostor(obj, BABYLON.PhysicsImpostor.BoxImpostor, { mass: 1, restitution: 0.9 }, scene)` |

## Example Illusion Script

```javascript
// Create a base scene
createBox('box1');
createSphere('sphere1');
move(box1, 1, 2, 3);
rotate(sphere1, 0.1, 0.2, 0.3);
addHemisphericLight('light1');
addArcRotateCamera('camera1', 0, 0, 0);
importOBJ('obj1', 'path/to/model.obj');
addAudio('audio1', 'path/to/audio.mp3');
setGravity(0, -9.81, 0);
enablePhysics();
addPhysics(box1);
```

## How to Use the Custom Syntax

### Creating Shapes

- **Boxes**: Use `createBox(name)` to create a box.
- **Spheres**: Use `createSphere(name)` to create a sphere.
- **Ground Planes**: Use `createGround(name)` to create a ground plane.
- **Cylinders**: Use `createCylinder(name)` to create a cylinder.
- **Capsules**: Use `createCapsule(name)` to create a capsule.
- **Planes**: Use `createPlane(name)` to create a plane.

### Transformations

- **Move**: Use `move(obj, x, y, z)` to move an object.
- **Rotate**: Use `rotate(obj, x, y, z)` to rotate an object.
- **Scale**: Use `scale(obj, x, y, z)` to scale an object.

### Lighting and Cameras

- **Hemispheric Light**: Use `addHemisphericLight(name)` to add a hemispheric light.
- **Point Light**: Use `addPointLight(name, x, y, z)` to add a point light.
- **Arc Rotate Camera**: Use `addArcRotateCamera(name, x, y, z)` to add an arc rotate camera.
- **Follow Camera**: Use `addFollowCamera(name, target)` to add a follow camera.

### Importing Models

- **OBJ Models**: Use `importOBJ(name, path)` to import an OBJ model.
- **FBX Models**: Use `importFBX(name, path)` to import an FBX model.

### Audio

- **Add Audio**: Use `addAudio(name, path)` to add audio to the scene.

### Physics

- **Set Gravity**: Use `setGravity(x, y, z)` to set the scene gravity.
- **Enable Physics**: Use `enablePhysics()` to enable physics in the scene.
- **Add Physics to Object**: Use `addPhysics(obj)` to add physics properties to an object.

## Common Templates

### Basic Scene

```javascript
createBox('box1');
createSphere('sphere1');
addHemisphericLight('light1');
addArcRotateCamera('camera1', 0, 0, 0);
```

### Third Person Controlled Character

```javascript
createCapsule('character');
addFollowCamera('followCam', character);
move(character, 0, 1, 0);
setGravity(0, -9.81, 0);
enablePhysics();
addPhysics(character);

// Add controls for movement
document.addEventListener('keydown', function(event) {
    switch (event.key) {
        case 'w':
            character.position.z += 0.1;
            break;
        case 's':
            character.position.z -= 0.1;
            break;
        case 'a':
            character.position.x -= 0.1;
            break;
        case 'd':
            character.position.x += 0.1;
            break;
        case ' ':
            character.position.y += 0.1; // Jump
            break;
    }
});
```

### Car Template

```javascript
// Create the car body
createBox('carBody');
move(carBody, 0, 1, 0);
scale(carBody, 2, 0.5, 1);

// Create the wheels
createCylinder('wheel1');
move(wheel1, 1, 0.5, 1);
rotate(wheel1, Math.PI / 2, 0, 0);

createCylinder('wheel2');
move(wheel2, -1, 0.5, 1);
rotate(wheel2, Math.PI / 2, 0, 0);

createCylinder('wheel3');
move(wheel3, 1, 0.5, -1);
rotate(wheel3, Math.PI / 2, 0, 0);

createCylinder('wheel4');
move(wheel4, -1, 0.5, -1);
rotate(wheel4, Math.PI / 2, 0, 0);

// Add lighting and camera
addHemisphericLight('light1');
addArcRotateCamera('camera1', 0, 5, -10);

// Add physics to the car body and wheels
enablePhysics();
addPhysics(carBody);
addPhysics(wheel1);
addPhysics(wheel2);
addPhysics(wheel3);
addPhysics(wheel4);

// Set gravity
setGravity(0, -9.81, 0);

// Add controls for car movement
document.addEventListener('keydown', function(event) {
    switch (event.key) {
        case 'w':
            carBody.position.z += 0.1; // Move forward
            break;
        case 's':
            carBody.position.z -= 0.1; // Move backward
            break;
        case 'a':
            carBody.position.x -= 0.1; // Move left
            break;
        case 'd':
            carBody.position.x += 0.1; // Move right
            break;
    }
});
```
## Contribute

**License:** This project is semi-open source. Access will be granted to selected individuals and organizations after its initial release.

**Contact:** For inquiries and collaborations, please contact Mr. Asterisk at [herrell4@gmail.com](mailto:herrell4@gmail.com).

---
[GitHub](https://github.com/gamedev44)  
gamedev44 - Overview  
gamedev44 has 34 repositories available. Follow their code on GitHub...


