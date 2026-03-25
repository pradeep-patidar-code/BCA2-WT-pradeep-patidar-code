# Day 25 — CSS Transitions, Animations & Transforms

📖 **Type:** Theory Session
🕐 **Duration:** 2 Hours
📚 **Unit:** 4 — CSS

---

## Learning Objectives

By the end of this session, students will be able to:
- Apply CSS transitions for smooth property changes
- Create keyframe animations
- Use 2D and 3D transforms (rotate, scale, translate, skew)
- Combine transitions, transforms, and animations for interactive effects

---

## 1. CSS Transitions

> **Analogy:** Without transitions, changing a property is like flipping a **light switch** — instant. With transitions, it's like a **dimmer switch** — smooth and gradual.

### Basic Syntax

```css
.box {
    background: #1565C0;
    width: 200px;
    height: 60px;
    transition: all 0.3s ease;
}

.box:hover {
    background: #E91E63;
    width: 300px;
    transform: scale(1.05);
}
```

### Transition Properties

| Property | Values | Description |
|----------|--------|-------------|
| `transition-property` | `all`, `background`, `width`, etc. | What to animate |
| `transition-duration` | `0.3s`, `500ms` | How long |
| `transition-timing-function` | `ease`, `linear`, `ease-in`, `ease-out`, `ease-in-out` | Speed curve |
| `transition-delay` | `0.2s` | Wait before starting |

```css
/* Shorthand */
.box {
    transition: background 0.3s ease, width 0.5s ease-in-out;
}
```

---

## 2. CSS Transforms

### 2D Transforms

```css
.translate { transform: translate(50px, 20px); }    /* Move */
.rotate    { transform: rotate(45deg); }              /* Rotate */
.scale     { transform: scale(1.5); }                 /* Resize */
.scale-xy  { transform: scale(2, 0.5); }              /* Stretch */
.skew      { transform: skew(10deg, 5deg); }          /* Slant */

/* Combine multiple transforms */
.combo {
    transform: translate(20px, 0) rotate(10deg) scale(1.1);
}
```

| Function | Effect | Example |
|----------|--------|---------|
| `translate(x, y)` | Move element | `translate(50px, 20px)` |
| `rotate(angle)` | Rotate | `rotate(45deg)` |
| `scale(x, y)` | Resize | `scale(1.5)` |
| `skew(x, y)` | Slant | `skew(10deg)` |

### 3D Transforms

```css
.rotate-x { transform: rotateX(45deg); }   /* Flip forward */
.rotate-y { transform: rotateY(45deg); }   /* Turn sideways */
.rotate-z { transform: rotateZ(45deg); }   /* Same as rotate() */

/* For 3D effect, parent needs perspective */
.parent {
    perspective: 800px;
}
```

---

## 3. CSS Animations (Keyframes)

> **Analogy:** Transitions are like a **single camera shot** from A to B. Animations are like a **full movie** — you define every scene (keyframe), and the browser plays through them.

### Basic Animation

```css
@keyframes slideIn {
    from {
        transform: translateX(-100%);
        opacity: 0;
    }
    to {
        transform: translateX(0);
        opacity: 1;
    }
}

.animated {
    animation: slideIn 0.5s ease forwards;
}
```

### Multi-Step Animation

```css
@keyframes rainbow {
    0%   { background: #FF0000; }
    16%  { background: #FF9900; }
    33%  { background: #FFFF00; }
    50%  { background: #00FF00; }
    66%  { background: #0000FF; }
    83%  { background: #9900FF; }
    100% { background: #FF0000; }
}

.rainbow-box {
    animation: rainbow 4s linear infinite;
}
```

### Animation Properties

| Property | Values |
|----------|--------|
| `animation-name` | Name of `@keyframes` |
| `animation-duration` | `1s`, `500ms` |
| `animation-timing-function` | `ease`, `linear`, `ease-in-out` |
| `animation-delay` | `0.5s` |
| `animation-iteration-count` | `1`, `3`, `infinite` |
| `animation-direction` | `normal`, `reverse`, `alternate` |
| `animation-fill-mode` | `none`, `forwards`, `backwards`, `both` |

```css
/* Shorthand */
.box {
    animation: bounce 1s ease-in-out 0.2s infinite alternate;
    /* name | duration | timing | delay | count | direction */
}
```

---

## 4. Practical: Interactive Button & Card Effects

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Animations & Transitions</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body {
            font-family: 'Segoe UI', sans-serif;
            background: #f0f0f0;
            padding: 30px;
        }
        h1 { text-align: center; color: #1565C0; margin-bottom: 30px; }
        h2 { color: #333; margin: 30px 0 15px; text-align: center; }

        /* ===== BUTTON EFFECTS ===== */
        .btn-row {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
        }
        .btn {
            padding: 12px 30px;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
            color: white;
            transition: all 0.3s ease;
        }
        .btn-grow:hover {
            transform: scale(1.1);
        }
        .btn-shadow:hover {
            box-shadow: 0 8px 25px rgba(0,0,0,0.3);
            transform: translateY(-3px);
        }
        .btn-slide {
            position: relative;
            overflow: hidden;
            z-index: 1;
        }
        .btn-slide::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: rgba(255,255,255,0.2);
            transition: left 0.3s ease;
            z-index: -1;
        }
        .btn-slide:hover::before {
            left: 0;
        }
        .btn-1 { background: #1565C0; }
        .btn-2 { background: #E91E63; }
        .btn-3 { background: #4CAF50; }

        /* ===== CARD HOVER EFFECTS ===== */
        .card-row {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
        }
        .card {
            width: 250px;
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .card:hover {
            transform: translateY(-10px);
            box-shadow: 0 12px 30px rgba(0,0,0,0.15);
        }
        .card-header {
            height: 120px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2.5em;
            color: white;
        }
        .card-body {
            padding: 20px;
        }
        .card-body h3 { margin-bottom: 5px; }
        .card-body p { color: #777; font-size: 14px; }

        /* ===== LOADING SPINNER ===== */
        @keyframes spin {
            0%   { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        .spinner {
            width: 50px;
            height: 50px;
            border: 5px solid #e0e0e0;
            border-top: 5px solid #1565C0;
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin: 0 auto;
        }

        /* ===== PULSE EFFECT ===== */
        @keyframes pulse {
            0%   { transform: scale(1); opacity: 1; }
            50%  { transform: scale(1.05); opacity: 0.7; }
            100% { transform: scale(1); opacity: 1; }
        }
        .pulse {
            animation: pulse 2s ease-in-out infinite;
        }

        /* ===== FADE IN ON LOAD ===== */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        .fade-in {
            animation: fadeInUp 0.8s ease forwards;
        }
        .delay-1 { animation-delay: 0.1s; opacity: 0; }
        .delay-2 { animation-delay: 0.3s; opacity: 0; }
        .delay-3 { animation-delay: 0.5s; opacity: 0; }
    </style>
</head>
<body>

    <h1 class="fade-in">CSS Transitions & Animations</h1>

    <h2>Button Effects</h2>
    <div class="btn-row">
        <button class="btn btn-1 btn-grow">Grow</button>
        <button class="btn btn-2 btn-shadow">Shadow Lift</button>
        <button class="btn btn-3 btn-slide">Slide Shine</button>
    </div>

    <h2>Card Hover Effects</h2>
    <div class="card-row">
        <div class="card fade-in delay-1">
            <div class="card-header" style="background: linear-gradient(135deg, #667eea, #764ba2);">🌐</div>
            <div class="card-body">
                <h3>HTML5</h3>
                <p>Structure and semantics</p>
            </div>
        </div>
        <div class="card fade-in delay-2">
            <div class="card-header" style="background: linear-gradient(135deg, #11998e, #38ef7d);">🎨</div>
            <div class="card-body">
                <h3>CSS3</h3>
                <p>Styling and animations</p>
            </div>
        </div>
        <div class="card fade-in delay-3">
            <div class="card-header" style="background: linear-gradient(135deg, #ee0979, #ff6a00);">⚡</div>
            <div class="card-body">
                <h3>JavaScript</h3>
                <p>Interactivity and logic</p>
            </div>
        </div>
    </div>

    <h2>Loading Spinner</h2>
    <div class="spinner"></div>

    <h2>Pulse Effect</h2>
    <p style="text-align:center;">
        <span class="pulse" style="display:inline-block; background:#E91E63; color:white; padding:15px 30px; border-radius:50px; font-size:18px;">
            🔴 LIVE
        </span>
    </p>

</body>
</html>
```

---

## Summary

| Concept | Key Property | Purpose |
|---------|-------------|---------|
| Transitions | `transition: all 0.3s ease` | Smooth property changes |
| Transforms | `transform: rotate(45deg)` | Move, rotate, scale, skew |
| Animations | `@keyframes` + `animation` | Multi-step sequences |
| 3D | `perspective`, `rotateX/Y` | Depth effects |

**🎉 Unit 4 Complete!** Starting Day 26, we begin **Unit 5: JavaScript** — adding interactivity and dynamic behavior to our styled web pages.

---

*Day 25 of 55 | Unit 4 — CSS | Web Technology (25BCA060)*
