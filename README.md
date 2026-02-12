# Valentine's Day Proposal Webapp

A fun and interactive web application to propose to your special someone on Valentine's Day! This webapp features a playful "Will you be my Valentine?" question with a clever twist - the "No" button runs away when you try to click it (They can't say no to you)

## Usage

### Option 1: Direct Use
-Send the link: https://mervinsumboo.github.io/Will-You-Be-My-Valentine/
- Don't forget to remane the displayed name of the url

### Option 2: Download (GIF will not work unless you change the src to an https link for your gif)
1. Download the `valentine-proposal.html` file
2. Email the HTML file directly
3. Share via messaging apps
  
## Features

### 1. **Interactive Button Behavior**
- **Yes Button**: Slightly smaller, with a continuous pulsing animation that makes it irresistible to click
- **No Button**: Moves to a random position whenever the cursor hovers over it, making it impossible to click!

### 3. **Epic Celebration**
- When "Yes" is clicked, an explosive celebration begins:
  - animated confetti pieces
  - Mix of colorful confetti and emoji (hearts, flowers, stars)
  - Congratulations message with customizable GIF placeholder
  - Smooth fade-in animation

### 4. **Smart Positioning**
- The "No" button avoids both the cursor AND the "Yes" button
- Ensures minimum distance to prevent accidental overlap
- Uses a placeholder system to maintain layout stability
- The "Yes" button never moves, staying perfectly centered

### 5. **Smooth Loading**
- Page loads with blank background
- Content fades in elegantly once fully loaded

## How It Works

### Initial Layout
```
┌─────────────────────────────────┐
│                                 │
│           💝                    │
│   Will You Be My Valentine?     │
│                                 │
│   [Yes! 💕]     [No]            │
│                                 │
└─────────────────────────────────┘
```

### Button Layout Structure
The three elements are positioned as:
1. **Left**: Yes button (with pulsing animation)
2. **Middle**: Invisible placeholder (maintains space)
3. **Right**: No button (positioned absolutely on top of placeholder)


### Movement Algorithm
When the user hovers over the "No" button:
1. Calculates current cursor position
2. Generates random position within container bounds
3. Checks distance from cursor (must be > 100px away)
4. Checks distance from Yes button (must be > 150px away)
5. If valid, moves button to new position
6. If not valid, tries again (up to 50 attempts)

## Customization

### Change the GIF
Look for this line in the HTML (around line 185):
```html
<img src="placeholder.gif" alt="Celebration GIF">
```

Replace the `src` URL with your own romantic GIF.

### Adjust Colors
The color scheme uses CSS gradients. Main colors to customize:

**Background Gradient:**
```css
background: linear-gradient(135deg, #ff9a9e 0%, #fecfef 50%, #ffecd2 100%);
```

**Yes Button:**
```css
background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
```

**No Button:**
```css
background: linear-gradient(135deg, #a8edea 0%, #fed6e3 100%);
```

### Modify Text
Change the proposal text (around line 165):
```html
<h1>Will You Be My Valentine?</h1>
```

Change the celebration message (around line 180):
```html
<h2>Yay! 🎉💖</h2>
<p style="font-size: 1.5em; color: #555; margin-bottom: 20px;">You've made me the happiest!</p>
```

### Adjust Container Size
The container is currently 2x the original size. To change it, modify:
```css
.container {
    padding: 120px 80px;    /* Spacing inside */
    max-width: 1000px;      /* Maximum width */
}
```

### Animation Speed
**Yes Button Pulse:**
```css
animation: pulse 2s ease-in-out infinite;  /* Change 2s to desired speed */
```

**Confetti Speed:**
```javascript
confetti.style.animationDuration = (Math.random() * 2 + 2) + 's';  /* 2-4 seconds */
```

## Browser Compatibility

Works on all modern browsers:
- Chrome/Edge (recommended)
- Firefox
- Safari
- Mobile browsers (iOS Safari, Chrome Mobile)

## Technical Details

### Technologies Used
- **HTML5**: Semantic markup
- **CSS3**: Animations, gradients, flexbox
- **Vanilla JavaScript**: No dependencies, pure JS

### Key Animations
1. **Heartbeat**: CSS keyframe animation on the heart emoji
2. **Pulse**: Continuous scale animation on Yes button
3. **Confetti Fall**: Random falling animation for celebration
4. **Fade In**: Page load transition
5. **Bounce**: Celebration heading animation

### Performance
- **Lightweight**: Single HTML file (~10KB)
- **No external dependencies**: Everything is self-contained
- **Smooth animations**: Hardware-accelerated CSS transforms
- **Efficient**: Uses requestAnimationFrame for smooth rendering

## License

This is a personal project created for Valentine's Day proposals. Feel free to use, modify, and share!

## Credits

Created with love for an unforgettable Valentine's Day proposal!

---

## Advanced Customization

### Add More Confetti
Change this number in the JavaScript (around line 270):
```javascript
for (let i = 0; i < 300; i++) {  // Change 300 to desired amount
```

### Change Movement Distance
Adjust these values in the JavaScript (around line 250):
```javascript
if (distanceFromCursor > 100 && distanceFromYesBtn > 150) {
    // 100 = minimum distance from cursor
    // 150 = minimum distance from Yes button
}
```

### Disable No Button Movement (for testing)
Comment out these lines (around line 220):
```javascript
// noBtn.addEventListener('mouseenter', (e) => {
//     moveButton(e);
// });
```

## Final Notes

Remember: The best proposals come from the heart! This webapp is just a fun, creative way to express your feelings.

Good luck with your Valentine's Day proposal! 

---

**Made with ❤️ for Valentine's Day 2026**
