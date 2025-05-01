![TiltJSLogo720](https://github.com/user-attachments/assets/2626a47d-0316-438e-8e06-990b7f0e62b7)

# Tilt.js

## Introduction
Tilt.js is a lightweight and versatile JavaScript library that adds interactive 3D tilt effects to your UI elements. It enhances user experience by creating dynamic, responsive elements that react to mouse movements on desktop and device orientation on mobile devices. Created by KaliforniaGator, this library supports both jQuery and vanilla JavaScript implementations, making it flexible for a wide range of projects.

## Overview
Tilt.js transforms ordinary UI elements into engaging 3D components without the complexity of WebGL or Three.js. It uses CSS 3D transforms to create realistic depth and movement based on user interaction, whether through mouse movement, touch, or device orientation.

## Features
- **Cross-platform support**: Works on both desktop and mobile devices
- **Multiple input methods**: 
  - Mouse tracking on desktop
  - Touch input on mobile
  - Device orientation (accelerometer) on compatible devices
- **Framework agnostic**: Works with both jQuery and vanilla JavaScript
- **Customizable settings**: Easily adjust rotation limits, perspective, smoothing, and sensitivity
- **Mobile optimization**: 
  - Intelligent mode detection (touch vs. orientation)
  - Calibration system for device orientation
  - Permission request handling for iOS devices
- **Smooth animations**: Configurable smoothing for fluid transitions
- **Lightweight**: No external dependencies beyond optional jQuery
- **Clean API**: Simple initialization and teardown

## Usage

### Basic Implementation

```javascript
// Vanilla JS
const tilt = TiltEffect.init();

// Or with jQuery
$(document).ready(function() {
    const tilt = TiltEffect.init();
});

// With custom settings (Vanilla JS)
const tilt = TiltEffect.init({
    container: document.querySelector('#my-container'),
    element: document.querySelector('#my-element'),
    maxRotation: 10,
    perspective: 1200,
    smoothingFactor: 0.15
});

// With custom settings (jQuery)
const tilt = TiltEffect.init({
    container: $('#my-container'),
    element: $('#my-element'),
    maxRotation: 10,
    perspective: 1200,
    smoothingFactor: 0.15
});

// Clean up when no longer needed
tilt.destroy();
```

### Selector Usage

```javascript
// Vanilla JS - using CSS selector strings
const tilt = TiltEffect.init({
    container: '.preview-container',
    element: '#previewBox'
});

// jQuery - using jQuery objects
const tilt = TiltEffect.init({
    container: $('.preview-container'),
    element: $('#previewBox')
});
```

### Multiple Instances

```javascript
// Vanilla JS - multiple tilt effects
const tiltElements = document.querySelectorAll('.tilt-container');
const tiltInstances = [];

tiltElements.forEach(container => {
    const element = container.querySelector('.tilt-element');
    tiltInstances.push(TiltEffect.init({
        container: container,
        element: element
    }));
});

// jQuery - multiple tilt effects
$('.tilt-container').each(function() {
    const $container = $(this);
    const $element = $container.find('.tilt-element');
    TiltEffect.init({
        container: $container,
        element: $element
    });
});
```

### HTML Structure

```html
<div class="preview-container">
    <div id="previewBox">
        <!-- Your content here -->
    </div>
</div>
```

### Available Options

```javascript
const tilt = TiltEffect.init({
    container: '.preview-container', // Container selector
    element: '#previewBox',          // Element to apply the tilt to
    permissionButtonClass: 'tilt3d-permission-button', // Class for permission button
    calibrateButtonClass: 'tilt3d-calibrate-button',   // Class for calibrate button
    maxRotation: 15,                 // Maximum rotation for desktop (degrees)
    mobileMaxRotation: 25,           // Maximum rotation for mobile (degrees)
    perspective: 1000,               // Perspective value for 3D effect
    smoothingFactor: 0.2,            // Lower = smoother but slower transitions
    sensitivityMultiplier: 1.8,      // Multiplier for mobile orientation sensitivity
    mobileInputMode: 'auto'          // Mobile input mode: 'touch', 'orientation', 'both', or 'auto'
});
```

### Mobile Input Modes

- `'touch'`: Use only touch input on mobile
- `'orientation'`: Use only device orientation (if available)
- `'both'`: Use both touch and orientation inputs
- `'auto'`: Automatically choose the best input method (default)

### CSS Integration

For best results, add these CSS styles:

```css
.tilt3d-container {
    position: relative;
    overflow: hidden;
}

.tilt3d-element {
    will-change: transform;
    transition: transform 0.1s ease-out;
}
```

## Terms of Use

Tilt.js is freely available for both personal and commercial projects with the following conditions:

1. You are permitted to use Tilt.js in commercial projects.
2. Attribution to the original author (KaliforniaGator) must be maintained in your project.
3. The attribution can be included in your project's credits, about section, or documentation.

### Suggested Attribution Format:
```
3D Tilt effects powered by Tilt.js by KaliforniaGator
```

---

Created by KaliforniaGator | © 2025 All Rights Reserved
