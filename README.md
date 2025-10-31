<div align="center">

# VIKS ANIMATION JS

[![License: MIT](https://img.shields.io/badge/License-MIT-black.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E.svg?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Sass](https://img.shields.io/badge/Sass-CC6699.svg?style=for-the-badge&logo=sass&logoColor=white)](https://sass-lang.com/)
[![No Dependencies](https://img.shields.io/badge/Dependencies-Zero-success?style=for-the-badge)](https://www.npmjs.com/)

**Modern scroll-triggered animations with inline configuration — Zero dependencies**

[Quick Start](#-quick-start) • [Documentation](#-documentation) • [Examples](#-examples) • [API](#-api-reference)

</div>

---

## 📖 Table of Contents

- [What is VIKS?](#-what-is-viks)
- [Key Features](#-key-features)
- [Quick Start](#-quick-start)
- [Installation](#-installation)
- [Basic Usage](#-basic-usage)
- [Inline Configuration](#-inline-configuration-modern-syntax)
- [Animation Types](#-animation-types)
- [Configuration Options](#️-configuration-options)
- [Easing Functions](#-easing-functions)
- [Device Detection](#-device-detection)
- [Anchor Placement](#-anchor-placement)
- [Events & Callbacks](#-events--callbacks)
- [API Reference](#-api-reference)
- [Advanced Features](#-advanced-features)
- [Performance](#-performance)
- [Troubleshooting](#-troubleshooting)
- [Browser Support](#-browser-support)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🎯 What is VIKS?

VIKS Animation is a lightweight, vanilla JavaScript library that brings your website to life with smooth scroll-triggered animations. Write animations directly in your HTML attributes with an intuitive inline syntax, or use the traditional data attribute approach.

### Why VIKS?

- **🚀 Modern Inline Syntax** - `data-viks="fade-up duration-1000 delay-500"`
- **⚡ Zero Dependencies** - Pure vanilla JavaScript
- **🎨 30+ Animations** - Fade, zoom, slide, flip with variants
- **🎭 21 Easing Functions** - From linear to elastic curves
- **📱 Smart Device Detection** - Disable animations per device type
- **🔄 Auto-Refresh** - MutationObserver detects dynamic content
- **🎪 Event System** - Track animation lifecycle with custom events
- **⚙️ Highly Configurable** - Global defaults + per-element overrides

---

## ✨ Key Features

### Inline Configuration (Modern)
```html
<div data-viks="fade-up duration-1000 delay-500 easing-ease-out-back once-true">
  All settings in one attribute!
</div>
```

### Traditional Configuration (Still Supported)
```html
<div data-viks="fade-up"
     data-viks-duration="1000"
     data-viks-delay="500">
  Separate attributes work too
</div>
```

### Smart Device Detection
```javascript
VIKS.init({
  disable: 'mobile' // Automatically disable on mobile devices
});
```

### Event Tracking
```javascript
document.addEventListener('viks:in', (e) => {
  console.log('Element animated in!', e.detail);
});
```

---

## 🚀 Quick Start

### 1. Include CSS & JS

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>VIKS Animation Demo</title>
  
  <!-- VIKS CSS -->
  <link rel="stylesheet" href="path/to/viks.css">
</head>
<body>
  
  <h1 data-viks="fade-up">Hello World!</h1>
  <p data-viks="fade-left duration-1000">Smooth animations made easy</p>
  
  <!-- VIKS JavaScript -->
  <script src="path/to/viks.js"></script>
  <script>
    // Initialize VIKS
    VIKS.init();
  </script>
</body>
</html>
```

### 2. That's It! 🎉

Scroll and watch your elements animate into view.

---

## 📦 Installation

### Option 1: Manual Download

1. Download the latest release files:
   - `viks.js` (or `viks.min.js`)
   - `viks.css` (or `viks.min.css`)

2. Include in your project:
```html
<link rel="stylesheet" href="path/to/viks.min.css">
<script src="path/to/viks.min.js"></script>
```

### Option 2: NPM (If Published)

```bash
npm install viks-animation
```

```javascript
// ES6 Module
import VIKS from 'viks-animation';
import 'viks-animation/dist/viks.css';

VIKS.init();
```

### Option 3: Module System

```javascript
// CommonJS
const VIKS = require('viks-animation');

// ES6 Module (if exported)
import VIKS from './viks.js';
```

---

## 🎨 Basic Usage

### Simple Animation

```html
<div data-viks="fade-up">
  This element fades up when scrolled into view
</div>
```

### With Duration & Delay

```html
<h1 data-viks="fade-up duration-1200 delay-200">
  Slower fade with delay
</h1>
```

### With Custom Easing

```html
<button data-viks="zoom-in duration-800 easing-ease-out-back">
  Bouncy button
</button>
```

### Staggered Animation

```html
<div class="cards">
  <div data-viks="fade-up delay-0">Card 1</div>
  <div data-viks="fade-up delay-100">Card 2</div>
  <div data-viks="fade-up delay-200">Card 3</div>
  <div data-viks="fade-up delay-300">Card 4</div>
</div>
```

---

## ✨ Inline Configuration (Modern Syntax)

VIKS supports a modern inline syntax where you can configure all animation parameters in a single `data-viks` attribute.

### Syntax Format

```
data-viks="{animation} {param1-value1} {param2-value2} ..."
```

### Available Parameters

| Parameter | Syntax | Example | Description |
|-----------|--------|---------|-------------|
| **Animation** | `{name}` | `fade-up` | Animation type (required, first) |
| **Duration** | `duration-{ms}` | `duration-1000` | Animation duration in milliseconds |
| **Delay** | `delay-{ms}` | `delay-500` | Delay before animation starts |
| **Offset** | `offset-{px}` | `offset-200` | Trigger distance from viewport |
| **Easing** | `easing-{name}` | `easing-ease-out-back` | Timing function |
| **Once** | `once-{bool}` | `once-true` | Animate only once (true/false) |
| **Mirror** | `mirror-{bool}` | `mirror-true` | Reverse on scroll up (true/false) |
| **Anchor** | `anchor-{selector}` | `anchor-#hero` | Custom trigger element |
| **Anchor Placement** | `anchor-placement-{pos}` | `anchor-placement-top-center` | Trigger position |
| **ID** | `id-{name}` | `id-hero-title` | Custom identifier for events |

### Examples

```html
<!-- Basic animation with duration -->
<div data-viks="fade-up duration-1000">
  Content
</div>

<!-- Full configuration -->
<div data-viks="slide-up duration-1500 delay-200 easing-ease-in-out-back offset-100 once-true">
  Complex animation
</div>

<!-- With custom trigger element -->
<div id="trigger-point"></div>
<div data-viks="fade-up anchor-#trigger-point anchor-placement-center-center">
  Triggered by another element
</div>

<!-- With event tracking -->
<div data-viks="zoom-in duration-800 id-hero-cta">
  Track this element
</div>
```

### Order Independence

Parameters can be in any order (except animation name must be first):

```html
<!-- These are all equivalent -->
<div data-viks="fade-up duration-1000 delay-500 easing-ease-out"></div>
<div data-viks="fade-up easing-ease-out delay-500 duration-1000"></div>
<div data-viks="fade-up delay-500 duration-1000 easing-ease-out"></div>
```

---

## 🎭 Animation Types

VIKS includes 30+ pre-built animations in 4 categories:

### Fade Animations (9 variants)

Opacity transitions with directional movement.

```html
<div data-viks="fade">Simple fade</div>
<div data-viks="fade-up">From bottom</div>
<div data-viks="fade-down">From top</div>
<div data-viks="fade-left">From right</div>
<div data-viks="fade-right">From left</div>
<div data-viks="fade-up-right">Diagonal bottom-left</div>
<div data-viks="fade-up-left">Diagonal bottom-right</div>
<div data-viks="fade-down-right">Diagonal top-left</div>
<div data-viks="fade-down-left">Diagonal top-right</div>
```

**Movement Distance:** `$viks-distance: 100px` (configurable in SASS)

### Zoom Animations (10 variants)

Scale-based transitions with optional direction.

```html
<div data-viks="zoom-in">Scale from small</div>
<div data-viks="zoom-in-up">Scale from small + bottom</div>
<div data-viks="zoom-in-down">Scale from small + top</div>
<div data-viks="zoom-in-left">Scale from small + right</div>
<div data-viks="zoom-in-right">Scale from small + left</div>

<div data-viks="zoom-out">Scale from large</div>
<div data-viks="zoom-out-up">Scale from large + bottom</div>
<div data-viks="zoom-out-down">Scale from large + top</div>
<div data-viks="zoom-out-left">Scale from large + right</div>
<div data-viks="zoom-out-right">Scale from large + left</div>
```

**Scale Values:** 
- `zoom-in`: Scale from 0.6
- `zoom-out`: Scale from 1.2

### Slide Animations (4 directions)

Full-distance slide transitions.

```html
<div data-viks="slide-up">From bottom edge</div>
<div data-viks="slide-down">From top edge</div>
<div data-viks="slide-left">From right edge</div>
<div data-viks="slide-right">From left edge</div>
```

**Distance:** 100% of element size

### Flip Animations (4 directions)

3D rotation-based transitions.

```html
<div data-viks="flip-up">Rotate X-axis from bottom</div>
<div data-viks="flip-down">Rotate X-axis from top</div>
<div data-viks="flip-left">Rotate Y-axis from right</div>
<div data-viks="flip-right">Rotate Y-axis from left</div>
```

**Perspective:** `2500px`
**Rotation:** `100deg`

---

## ⚙️ Configuration Options

### Global Configuration

Configure default values for all animations:

```javascript
VIKS.init({
  // Animation Settings
  duration: 400,                    // Default duration (ms)
  delay: 0,                         // Default delay (ms)
  easing: 'ease',                   // Default easing function
  offset: 120,                      // Trigger offset (px from viewport)
  
  // Behavior
  once: false,                      // Animate only once
  mirror: false,                    // Animate on scroll up too
  anchorPlacement: 'top-bottom',    // Default trigger position
  
  // Device Control
  disable: false,                   // Disable animations
                                    // Options: false | true | 'mobile' | 'phone' | 'tablet' | function
  
  // Events
  startEvent: 'DOMContentLoaded',   // When to initialize
  
  // CSS Classes
  animatedClassName: 'viks-animate', // Class when animated
  initClassName: 'viks-init',        // Class on initialization
  useClassNames: false,              // Use animation name as class
  
  // Performance
  throttleDelay: 99,                 // Scroll event throttle (ms)
  debounceDelay: 50,                 // Resize event debounce (ms)
  disableMutationObserver: false     // Disable auto-refresh
});
```

### Configuration Priority

Settings are applied in this order (highest to lowest):

1. **Inline parameters** (highest)
   ```html
   <div data-viks="fade-up duration-2000">
   ```

2. **Separate attributes**
   ```html
   <div data-viks="fade-up" data-viks-duration="1500">
   ```

3. **Global configuration**
   ```javascript
   VIKS.init({ duration: 1000 });
   ```

4. **Default values** (lowest)
   ```javascript
   // Built-in defaults
   duration: 400
   ```

### Device-Specific Control

```javascript
// Disable on all mobile devices (phone + tablet)
VIKS.init({
  disable: 'mobile'
});

// Disable on phones only
VIKS.init({
  disable: 'phone'
});

// Disable on tablets only
VIKS.init({
  disable: 'tablet'
});

// Custom disable logic
VIKS.init({
  disable: function() {
    // Your custom logic
    return window.innerWidth < 768;
  }
});

// Disable completely
VIKS.init({
  disable: true
});
```

---

## 🎨 Easing Functions

VIKS includes 21 built-in easing functions based on cubic-bezier curves.

### Standard Easing

```javascript
'linear'        // cubic-bezier(0.250, 0.250, 0.750, 0.750)
'ease'          // cubic-bezier(0.250, 0.100, 0.250, 1.000) - Default
'ease-in'       // cubic-bezier(0.420, 0.000, 1.000, 1.000)
'ease-out'      // cubic-bezier(0.000, 0.000, 0.580, 1.000)
'ease-in-out'   // cubic-bezier(0.420, 0.000, 0.580, 1.000)
```

### Back Easing (Overshoot Effect)

```javascript
'ease-in-back'      // cubic-bezier(0.600, -0.280, 0.735, 0.045)
'ease-out-back'     // cubic-bezier(0.175, 0.885, 0.320, 1.275) ⭐ Popular
'ease-in-out-back'  // cubic-bezier(0.680, -0.550, 0.265, 1.550)
```

### Sine Easing (Smooth)

```javascript
'ease-in-sine'      // cubic-bezier(0.470, 0.000, 0.745, 0.715)
'ease-out-sine'     // cubic-bezier(0.390, 0.575, 0.565, 1.000)
'ease-in-out-sine'  // cubic-bezier(0.445, 0.050, 0.550, 0.950)
```

### Quad Easing

```javascript
'ease-in-quad'      // cubic-bezier(0.550, 0.085, 0.680, 0.530)
'ease-out-quad'     // cubic-bezier(0.250, 0.460, 0.450, 0.940)
'ease-in-out-quad'  // cubic-bezier(0.455, 0.030, 0.515, 0.955)
```

### Cubic Easing

```javascript
'ease-in-cubic'      // cubic-bezier(0.550, 0.085, 0.680, 0.530)
'ease-out-cubic'     // cubic-bezier(0.250, 0.460, 0.450, 0.940) ⭐ Smooth
'ease-in-out-cubic'  // cubic-bezier(0.455, 0.030, 0.515, 0.955)
```

### Quart Easing (Strong)

```javascript
'ease-in-quart'      // cubic-bezier(0.550, 0.085, 0.680, 0.530)
'ease-out-quart'     // cubic-bezier(0.250, 0.460, 0.450, 0.940)
'ease-in-out-quart'  // cubic-bezier(0.455, 0.030, 0.515, 0.955)
```

### Usage

```html
<!-- Inline syntax -->
<div data-viks="fade-up easing-ease-out-back">Bouncy</div>

<!-- Attribute syntax -->
<div data-viks="fade-up" data-viks-easing="ease-out-sine">Smooth</div>

<!-- Global default -->
<script>
VIKS.init({
  easing: 'ease-out-cubic'
});
</script>
```

---

## 📱 Device Detection

VIKS includes a sophisticated `Detector` class that uses multiple signals for accurate device detection.

### Detection Methods

The Detector uses:
- ✅ Touch points (`navigator.maxTouchPoints`)
- ✅ Screen size (`window.innerWidth`)
- ✅ User agent analysis
- ✅ Platform detection
- ✅ Orientation API
- ✅ Pixel ratio

### Available Methods

```javascript
// Access the detector
const detect = new Detector();

// Device type detection
detect.mobile();    // true/false - Any mobile device
detect.phone();     // true/false - Phone specifically
detect.tablet();    // true/false - Tablet specifically

// Device info
detect.getDeviceType();  // 'phone' | 'tablet' | 'desktop' | 'unknown'
detect.isTouchDevice();  // true/false

// Browser detection
detect.getBrowserInfo(); 
// Returns: { browser: 'Chrome', version: '120' }

// OS detection
detect.getOSInfo();
// Returns: { os: 'Windows', version: '10/11' }

// Screen information
detect.getScreenInfo();
// Returns: {
//   width: 1920,
//   height: 1080,
//   pixelRatio: 2,
//   orientation: 'landscape',
//   touchPoints: 0
// }

// Complete device information
detect.getDeviceInfo();
// Returns all information combined

// Legacy support
detect.ie11(); // true/false - Internet Explorer 11 detection
```

### Device-Based Animations

```javascript
// Disable animations on mobile
VIKS.init({
  disable: 'mobile' // Uses detect.mobile()
});

// Disable on phones only
VIKS.init({
  disable: 'phone' // Uses detect.phone()
});

// Disable on tablets only
VIKS.init({
  disable: 'tablet' // Uses detect.tablet()
});

// Custom logic with detector
VIKS.init({
  disable: function() {
    const detect = new Detector();
    
    // Disable on mobile + IE11
    return detect.mobile() || detect.ie11();
  }
});
```

### Cache Management

The Detector caches results for performance. Cache is automatically cleared on:
- Window resize
- Orientation change

Manual cache clearing:
```javascript
detect.clearCache();
```

---

## 📍 Anchor Placement

Control exactly when animations trigger with 9 anchor positions.

### Position Reference

| Position | Element Part | Viewport Part |
|----------|--------------|---------------|
| `top-bottom` | Top | Bottom (default) |
| `top-center` | Top | Center |
| `top-top` | Top | Top |
| `center-bottom` | Center | Bottom |
| `center-center` | Center | Center |
| `center-top` | Center | Top |
| `bottom-bottom` | Bottom | Bottom |
| `bottom-center` | Bottom | Center |
| `bottom-top` | Bottom | Top |

### Visual Guide

```
Viewport
┌─────────────────┐ ← top
│                 │
│                 │
│   center ───────┼─── center-center triggers here
│                 │
│                 │
└─────────────────┘ ← bottom (top-bottom triggers here)

Element scrolls from bottom to top ↑
```

### Usage Examples

```html
<!-- Early trigger (element barely visible) -->
<div data-viks="fade-up anchor-placement-bottom-bottom">
  Triggers when element bottom enters viewport bottom
</div>

<!-- Middle trigger (element half visible) -->
<div data-viks="fade-up anchor-placement-center-center">
  Triggers when element center reaches viewport center
</div>

<!-- Late trigger (element fully visible) -->
<div data-viks="fade-up anchor-placement-top-top">
  Triggers when element top reaches viewport top
</div>

<!-- Global default -->
<script>
VIKS.init({
  anchorPlacement: 'center-center'
});
</script>
```

### Custom Anchor Element

Trigger animation based on a different element:

```html
<!-- Trigger element -->
<div id="trigger-section" style="height: 100vh;">
  Scroll through this...
</div>

<!-- Animated element -->
<div data-viks="fade-up anchor-#trigger-section">
  ...triggers this animation
</div>
```

---

## 🎯 Events & Callbacks

VIKS fires custom events during the animation lifecycle.

### Global Events

```javascript
// Element enters viewport (animation starts)
document.addEventListener('viks:in', (event) => {
  console.log('Animated in!');
  console.log(event.detail); // Element node
});

// Element leaves viewport (animation reverses)
document.addEventListener('viks:out', (event) => {
  console.log('Animated out!');
  console.log(event.detail); // Element node
});
```

### Element-Specific Events

Use the `id-{name}` parameter to track specific elements:

```html
<div data-viks="fade-up id-hero">Hero Section</div>
<div data-viks="zoom-in id-cta-button">CTA Button</div>
```

```javascript
// Listen to specific element
document.addEventListener('viks:in:hero', (event) => {
  console.log('Hero appeared!');
  // Start video, trigger confetti, etc.
});

document.addEventListener('viks:out:hero', (event) => {
  console.log('Hero disappeared!');
});

document.addEventListener('viks:in:cta-button', (event) => {
  console.log('CTA visible!');
  // Track with analytics
});
```

### Event Properties

```javascript
document.addEventListener('viks:in', (event) => {
  const element = event.detail;
  
  console.log(element);                           // DOM node
  console.log(element.getAttribute('data-viks')); // Animation name
  console.log(element.classList);                 // Current classes
});
```

### Real-World Examples

#### Video Autoplay

```html
<section data-viks="fade-up id-video-section">
  <video id="promo-video" src="video.mp4" muted loop></video>
</section>

<script>
document.addEventListener('viks:in:video-section', (e) => {
  const video = e.detail.querySelector('video');
  video.play();
});

document.addEventListener('viks:out:video-section', (e) => {
  const video = e.detail.querySelector('video');
  video.pause();
});
</script>
```

#### Analytics Tracking

```javascript
document.addEventListener('viks:in', (event) => {
  const element = event.detail;
  const animationType = element.getAttribute('data-viks');
  
  // Google Analytics
  gtag('event', 'scroll_animation', {
    animation_type: animationType,
    element_id: element.id
  });
});
```

#### Progress Indicator

```javascript
let visibleCount = 0;
const totalElements = document.querySelectorAll('[data-viks]').length;

document.addEventListener('viks:in', () => {
  visibleCount++;
  updateProgress(visibleCount / totalElements * 100);
});

function updateProgress(percent) {
  document.querySelector('.progress-bar').style.width = percent + '%';
}
```

---

## 🔧 API Reference

### VIKS.init(config)

Initialize VIKS with optional configuration.

**Parameters:**
- `config` (Object, optional) - Configuration object

**Returns:** Array of animated elements

**Example:**
```javascript
const elements = VIKS.init({
  duration: 1000,
  easing: 'ease-out-back',
  offset: 150
});

console.log(`Initialized ${elements.length} elements`);
```

### VIKS.refresh(initialize)

Soft refresh - recalculates trigger positions for existing elements.

**Parameters:**
- `initialize` (Boolean, optional) - Force initialization if not done

**Returns:** Array of animated elements

**Use when:**
- Element positions change (accordion opened, tabs switched)
- Window resized (handled automatically)
- Layout shifts

**Example:**
```javascript
// After opening accordion
accordion.addEventListener('opened', () => {
  VIKS.refresh();
});
```

### VIKS.refreshHard()

Hard refresh - re-queries DOM for all `[data-viks]` elements.

**Returns:** Array of animated elements

**Use when:**
- New elements added to DOM
- Elements removed from DOM
- Route change in SPA
- Content loaded via AJAX

**Example:**
```javascript
// After loading content
fetch('/api/posts')
  .then(res => res.json())
  .then(posts => {
    posts.forEach(post => {
      container.innerHTML += `
        <article data-viks="fade-up">
          ${post.content}
        </article>
      `;
    });
    
    // Re-scan DOM
    VIKS.refreshHard();
  });
```

### When to Use Each Method

| Scenario | Method | Why |
|----------|--------|-----|
| Initial setup | `init()` | Start VIKS |
| Layout changed | `refresh()` | Recalculate positions |
| New elements added | `refreshHard()` | Re-scan DOM |
| Window resize | Automatic | Built-in listener |
| Route change (SPA) | `refreshHard()` | New page content |
| Accordion opened | `refresh()` | Position shift |

---

## 🚀 Advanced Features

### Mirror Mode (Bidirectional Animation)

Animate both when scrolling down AND scrolling up:

```html
<div data-viks="fade-up mirror-true">
  Fades in when scrolling down,
  fades out when scrolling up
</div>
```

**Note:** Requires `once-false` (default) to work.

### Once Mode (Single Animation)

Animate only once, never repeat:

```html
<div data-viks="fade-up once-true">
  Animates once and stays visible
</div>
```

**Good for:**
- Hero sections
- One-time reveals
- Performance optimization

### MutationObserver (Auto-Refresh)

VIKS automatically detects when elements with `data-viks` are added/removed:

```javascript
// Enabled by default
VIKS.init({
  disableMutationObserver: false // default
});

// Disable for static content
VIKS.init({
  disableMutationObserver: true // Better performance
});
```

**How it works:**
1. Watches for DOM changes
2. Detects new/removed elements with `data-viks`
3. Automatically calls `refreshHard()`

### Custom Class Names

Use animation names as CSS classes:

```javascript
VIKS.init({
  useClassNames: true
});
```

```html
<div data-viks="fade-up">
  <!-- Classes added: viks-init, fade-up -->
  <!-- When animated: viks-animate, fade-up -->
</div>
```

```css
/* Target animated elements */
.fade-up.viks-animate {
  /* Custom styles */
}
```

### Custom Initialization Timing

```javascript
// Wait for specific event
VIKS.init({
  startEvent: 'custom-event'
});

// Trigger manually
document.dispatchEvent(new Event('custom-event'));
```

### Throttle & Debounce Tuning

```javascript
VIKS.init({
  throttleDelay: 99,   // Scroll event throttle (default)
  debounceDelay: 50    // Resize event debounce (default)
});

// For better performance on slow devices
VIKS.init({
  throttleDelay: 150,  // Less frequent checks
  debounceDelay: 100
});
```

---

## ⚡ Performance

### Built-in Optimizations

VIKS is performance-optimized out of the box:

- ✅ **Throttled scroll events** (99ms default) - Reduces event frequency
- ✅ **Debounced resize events** (50ms default) - Prevents excessive recalculations
- ✅ **Cached element queries** - No repeated DOM lookups
- ✅ **CSS transforms** - GPU-accelerated animations
- ✅ **Efficient MutationObserver** - Smart DOM change detection
- ✅ **Batched calculations** - Minimizes reflows and repaints

### Performance Tips

#### 1. Use `once: true` for One-Time Animations

```javascript
VIKS.init({
  once: true // Animations don't repeat = better performance
});
```

#### 2. Disable MutationObserver for Static Content

```javascript
VIKS.init({
  disableMutationObserver: true // No dynamic content = save resources
});
```

#### 3. Increase Throttle/Debounce on Slower Devices

```javascript
VIKS.init({
  throttleDelay: 150,  // Less frequent scroll checks
  debounceDelay: 100   // Less frequent resize checks
});
```

#### 4. Disable on Low-End Devices

```javascript
VIKS.init({
  disable: function() {
    // Disable on weak CPUs
    return navigator.hardwareConcurrency < 4;
  }
});
```

#### 5. Limit Animated Elements

```html
<!-- ✅ Good: Animate containers -->
<section data-viks="fade-up">
  <h2>Title</h2>
  <p>Content...</p>
</section>

<!-- ❌ Avoid: Animating every child -->
<section>
  <h2 data-viks="fade-up">Title</h2>
  <p data-viks="fade-up">Para 1</p>
  <p data-viks="fade-up">Para 2</p>
  <span data-viks="fade-up">Text</span>
</section>
```

### Bundle Size

Approximate sizes (actual may vary based on build):

- **JavaScript:** ~25-30KB minified, ~10-12KB gzipped
- **CSS:** ~8-10KB minified, ~3-4KB gzipped
- **Total:** ~35-40KB minified, ~13-16KB gzipped

---

## 🐛 Troubleshooting

### Animations Not Working

**Problem:** Elements with `data-viks` aren't animating.

**Solutions:**

1. **Check CSS is loaded:**
```html
<!-- CSS MUST be loaded before JS -->
<link rel="stylesheet" href="viks.css">
<script src="viks.js"></script>
```

2. **Check initialization:**
```javascript
// Make sure you called init()
VIKS.init();
```

3. **Check for JavaScript errors:**
```javascript
// Open browser console (F12)
console.log('VIKS loaded:', typeof VIKS !== 'undefined');
```

4. **Check elements exist in DOM:**
```javascript
// Elements must exist when VIKS initializes
document.addEventListener('DOMContentLoaded', () => {
  VIKS.init();
});
```

5. **Try hard refresh:**
```javascript
VIKS.refreshHard();
```

---

### Dynamic Content Not Animating

**Problem:** Content added after page load doesn't animate.

**Solutions:**

**Method 1: MutationObserver (Automatic)**
```javascript
VIKS.init({
  disableMutationObserver: false // default - auto-detects new elements
});
```

**Method 2: Manual Refresh**
```javascript
function addContent() {
  container.innerHTML += '<div data-viks="fade-up">New content</div>';
  VIKS.refreshHard(); // Re-scan DOM after adding
}
```

---

### Animations Too Fast/Slow

**Problem:** Animation speed doesn't feel right.

**Solutions:**

```javascript
// Global duration
VIKS.init({
  duration: 1000 // milliseconds
});

// Per-element duration
<div data-viks="fade-up duration-2000">Slower</div>
<div data-viks="fade-up duration-500">Faster</div>
```

---

### Janky Animations on Mobile

**Problem:** Animations stutter or lag on mobile devices.

**Solutions:**

```javascript
// Solution 1: Increase throttle delays
VIKS.init({
  throttleDelay: 150,
  debounceDelay: 100
});

// Solution 2: Shorter durations on mobile
const isMobile = window.innerWidth < 768;
VIKS.init({
  duration: isMobile ? 400 : 800
});

// Solution 3: Disable on mobile entirely
VIKS.init({
  disable: 'mobile'
});
```

---

### Animation Triggers Too Early/Late

**Problem:** Animation fires at wrong scroll position.

**Solutions:**

```javascript
// Adjust global offset
VIKS.init({
  offset: 200 // pixels from viewport bottom
});

// Per-element offset
<div data-viks="fade-up offset-300">Later trigger</div>
<div data-viks="fade-up offset-50">Earlier trigger</div>

// Use anchor placement
<div data-viks="fade-up anchor-placement-center-center">
  Triggers when element center reaches viewport center
</div>
```

---

### Conflicts with Other Libraries

**Problem:** VIKS conflicts with other animation libraries.

**Solutions:**

```javascript
// Use custom class names
VIKS.init({
  animatedClassName: 'custom-animate',
  initClassName: 'custom-init'
});
```

---

## 🌐 Browser Support

### Modern Browsers

| Browser | Version | Status |
|---------|---------|--------|
| Chrome | Latest & last 2 | ✅ Full support |
| Firefox | Latest & last 2 | ✅ Full support |
| Safari | Latest & last 2 | ✅ Full support |
| Edge | Latest & last 2 | ✅ Full support |
| Opera | Latest & last 2 | ✅ Full support |

### Mobile Browsers

| Browser | Version | Status |
|---------|---------|--------|
| iOS Safari | 12+ | ✅ Full support |
| Chrome Android | Latest | ✅ Full support |
| Samsung Internet | Latest | ✅ Full support |
| UC Browser | Latest | ✅ Full support |

### Legacy Browsers

| Browser | Status | Notes |
|---------|--------|-------|
| IE 11 | ⚠️ Detected but not supported | Falls back gracefully |
| iOS Safari 11 | ⚠️ Partial support | Some features limited |

**Note:** VIKS will detect unsupported browsers and disable animations gracefully.

---

## 📚 Examples

### Hero Section

```html
<section class="hero">
  <h1 data-viks="fade-up duration-1200 delay-0">
    Welcome to VIKS Animation
  </h1>
  <p data-viks="fade-up duration-1000 delay-200">
    Beautiful scroll animations made simple
  </p>
  <button data-viks="zoom-in duration-800 delay-400 easing-ease-out-back">
    Get Started
  </button>
</section>
```

---

### Feature Cards with Stagger

```html
<div class="features">
  <div class="card" data-viks="fade-up delay-0">
    <h3>⚡ Fast</h3>
    <p>Optimized for performance</p>
  </div>
  <div class="card" data-viks="fade-up delay-100">
    <h3>🎨 Beautiful</h3>
    <p>30+ pre-built animations</p>
  </div>
  <div class="card" data-viks="fade-up delay-200">
    <h3>🔧 Easy</h3>
    <p>Simple inline configuration</p>
  </div>
  <div class="card" data-viks="fade-up delay-300">
    <h3>📦 Lightweight</h3>
    <p>Only ~15KB gzipped</p>
  </div>
</div>
```

---

### Image Gallery

```html
<div class="gallery">
  <img src="img1.jpg" data-viks="zoom-in duration-800 delay-0" alt="Image 1">
  <img src="img2.jpg" data-viks="zoom-in duration-800 delay-100" alt="Image 2">
  <img src="img3.jpg" data-viks="zoom-in duration-800 delay-200" alt="Image 3">
  <img src="img4.jpg" data-viks="zoom-in duration-800 delay-300" alt="Image 4">
</div>
```

---

### Video Section with Events

```html
<section data-viks="fade-up id-video-section">
  <video id="promo-video" src="video.mp4" muted loop></video>
  <h2>Watch Our Story</h2>
</section>

<script>
document.addEventListener('viks:in:video-section', (e) => {
  const video = e.detail.querySelector('#promo-video');
  video.play();
});

document.addEventListener('viks:out:video-section', (e) => {
  const video = e.detail.querySelector('#promo-video');
  video.pause();
});
</script>
```

---

### Pricing Cards

```html
<div class="pricing">
  <div class="plan" data-viks="flip-up delay-0">
    <h3>Basic</h3>
    <p class="price">$9/mo</p>
    <button>Choose Plan</button>
  </div>
  
  <div class="plan featured" data-viks="flip-up delay-100 duration-1000 easing-ease-out-back">
    <span class="badge">Popular</span>
    <h3>Pro</h3>
    <p class="price">$29/mo</p>
    <button>Choose Plan</button>
  </div>
  
  <div class="plan" data-viks="flip-up delay-200">
    <h3>Enterprise</h3>
    <p class="price">Custom</p>
    <button>Contact Sales</button>
  </div>
</div>
```

---

### Testimonials with Mirror

```html
<div class="testimonials">
  <blockquote data-viks="fade-left mirror-true">
    <p>"VIKS transformed our website's user experience!"</p>
    <cite>— Sarah Johnson, CEO</cite>
  </blockquote>
  
  <blockquote data-viks="fade-right mirror-true">
    <p>"The easiest animation library I've ever used."</p>
    <cite>— Mike Chen, Developer</cite>
  </blockquote>
</div>
```

---

### SPA Integration (React Example)

```jsx
import { useEffect } from 'react';
import VIKS from 'viks-animation';

function App() {
  useEffect(() => {
    // Initialize on mount
    VIKS.init({
      duration: 800,
      easing: 'ease-out-cubic'
    });
    
    // Cleanup on unmount
    return () => {
      // VIKS doesn't require cleanup
    };
  }, []);
  
  // Refresh when route changes
  useEffect(() => {
    VIKS.refreshHard();
  }, [location.pathname]);
  
  return (
    <div>
      <h1 data-viks="fade-up">React + VIKS</h1>
    </div>
  );
}
```

---

## 🎓 How VIKS Works

### Animation Lifecycle

```
1. Initialization
   ↓
   VIKS.init() scans DOM for [data-viks]
   
2. Element Preparation
   ↓
   Parse attributes → Calculate trigger positions → Add init classes
   
3. Scroll Detection
   ↓
   Throttled scroll events (99ms) → Compare position vs triggers
   
4. Animation Trigger
   ↓
   Add/remove classes → CSS handles animation → Fire events
```

### Architecture Diagram

```
┌─────────────────┐
│   User Scrolls  │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Throttle (99ms) │ ← Reduces event frequency
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ handleScroll()  │ ← Core scroll handler
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ applyClasses()  │ ← Check each element
└────────┬────────┘
         │
    ┌────┴────┐
    ▼         ▼
┌──────┐  ┌──────┐
│ Show │  │ Hide │ ← Add/remove classes
└──┬───┘  └───┬──┘
   │          │
   ▼          ▼
┌─────────────────┐
│  Fire Events    │ ← viks:in / viks:out
└─────────────────┘
```

### Class System

VIKS uses CSS classes to control animations:

**Default Classes:**
- `viks-init` - Added on initialization
- `viks-animate` - Added when animation triggers
- `{animation-name}` - Optional (if `useClassNames: true`)

**Example:**
```html
<!-- Before scroll -->
<div class="viks-init" data-viks="fade-up">
  
<!-- After scroll -->
<div class="viks-init viks-animate" data-viks="fade-up">
```

**CSS Transitions:**
```scss
[data-viks] {
  opacity: 0;
  transition-property: opacity, transform;
  
  &.viks-animate {
    opacity: 1;
    transform: none;
  }
}
```

---

## 🤝 Contributing

We welcome contributions! Here's how you can help:

### Ways to Contribute

- 🐛 **Report bugs** - Open an issue with details
- 💡 **Suggest features** - Share your ideas
- 📝 **Improve docs** - Fix typos, add examples
- 🔧 **Submit PRs** - Add features or fix bugs
- ⭐ **Star the repo** - Show your support

### Development Setup

```bash
# Clone repository
git clone https://github.com/MeViksry/viks-animation.git
cd viks-animation

# Install dependencies (if any)
npm install

# Build SASS to CSS
sass src/viks.scss dist/viks.css

# Minify for production
# (Use your preferred minification tool)
```

### Coding Guidelines

- Follow existing code style
- Add comments for complex logic
- Test on multiple browsers
- Keep bundle size small
- Update documentation for new features

### Submit a Pull Request

1. Fork the repository
2. Create feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📄 License

MIT License

Copyright (c) 2025 VIKRI AHPAD TANTOWI

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

---

## 🌐 Links & Resources

<div align="center">

[![Website](https://img.shields.io/badge/Website-Visit_Demo-4285F4?style=for-the-badge&logo=googlechrome&logoColor=white)](https://viksanimation.my.id)
[![GitHub](https://img.shields.io/badge/GitHub-Source_Code-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/MeViksry/viks-animation)

### Connect with Me

[![Gmail](https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:kingvikvik25@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/MeViksry)
[![Instagram](https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://www.instagram.com/meviksry)
[![TikTok](https://img.shields.io/badge/TikTok-000000?style=for-the-badge&logo=tiktok&logoColor=white)](https://www.tiktok.com/@viksry)
[![Threads](https://img.shields.io/badge/Threads-000000?style=for-the-badge&logo=threads&logoColor=white)](https://www.threads.net/@meviksry)
[![Facebook](https://img.shields.io/badge/Facebook-1877F2?style=for-the-badge&logo=facebook&logoColor=white)](https://www.facebook.com/share/19aKzAtBeZ/)

</div>

---

## 🙏 Acknowledgments

Special thanks to:
- The open-source community
- Everyone who contributed feedback
- All users of VIKS Animation

---

## 📝 Changelog

### Version 2.3.1 (Current)

**Features:**
- ✨ Inline configuration syntax
- 📱 Advanced device detection
- 🔄 MutationObserver auto-refresh
- 🎯 Custom event system
- ⚙️ Flexible configuration system

**Animations:**
- 9 Fade variants
- 10 Zoom variants
- 4 Slide directions
- 4 Flip directions
- 21 Easing functions

**Performance:**
- Throttled scroll events
- Debounced resize events
- Cached element queries
- GPU-accelerated animations

---

<div align="center">

**Made with ❤️ by [VIKRI AHPAD TANTOWI](https://github.com/MeViksry)**

⭐ Star this repo if you find it helpful!

</div>