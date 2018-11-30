# three-combo-controls

> Orbit &amp; first person camera controller for [three.js](https://threejs.org/)

---

## Install

```
$ npm install @cognite/three-combo-controls
```

or 

```
$ yarn add @cognite/three-combo-controls
```

## Usage
```js

import ComboControls from '@cognite/three-combo-controls';

const controls = new ComboControls(camera, domElement);

function animate() {
  controls.update();
  // ...
}
```

Mouse actions:
  - Left click & drag to rotate
  - Right click & drag to pan
  - Wheel to zoom

Touch actions:
  - One finger to rotate
  - Two fingers to pan & zoom (pinch)

Keyboard actions:
  - w & s to zoom
  - a, d, q & e to pan
  - Arrows to rotate (first person)

## Usage (advance)

```js
controls.dispose();

controls.addEventListener('cameraChange', (event) => {
  const { position, target } = event.camera;
  // position & target in world space and instanceof THREE.Vector3
});

// options with default values
controls.enabled = true; // enable / disable all interactions
controls.enableDamping = true; // enable / disable smooth transitions
controls.dampingFactor = 0.1; // smooth transition factor (<= 1). Move (targetState - currentState) * dampingFactor for each `controls.update` call
controls.dynamicTarget = false; // possible to zoom past the target (will move the target if you are closer than minDistance to the target)
controls.dollyFactor = 0.98; // zoom factor (when zooming one step the distance to the target will be distance = oldDistance * dollyFactor)

controls.minDistance = 1; // minimum distance to the target (see also dynamicTarget)
controls.maxDistance = Infinity; // maximum distance to the target

controls.minPolarAngle = 0; // minium polar angle around the target (radians)
controls.maxPolarAngle = Math.PI; // maximum polar angle around the target (radians)
controls.minAzimuthAngle = -Infinity; // minimum azimuth angle around the target (radians)
controls.maxAzimuthAngle = Infinity; // maximum azimuth angle around the target (radians)

controls.keyboardPanSpeed = 10; // using keyboard ('A' & 'D') to pan will be equal to keyboardPanSpeed pixels mouse pan
controls.firstPersonRotationFactor = 0.4; // rotation speed in first person mode

controls.pinchPanSpeed = 1; // pinch (touch) pan speed
controls.pinchEpsilon = 2; // minimum pixels change for pinch (touch & pan) to trigger pinch action 
controls.pointerRotationSpeedPolar = Math.PI / 360; // rotation speed for touch in radians per pixel
controls.pointerRotationSpeedAzimuth = Math.PI / 360; // rotation speed for touch in radians per pixel

controls.keyboardRotationSpeedAzimuth = 5 * Math.PI / 360; // rotation speed for keyboard first person mode (arrow-keys).
controls.keyboardRotationSpeedPolar = 5 * Math.PI / 360; // rotation speed for keyboard first person mode (arrow-keys).
```

## License

[Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0)

## Development

```
$ npm install
$ npm run start
```