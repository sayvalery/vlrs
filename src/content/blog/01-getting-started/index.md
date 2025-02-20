---
title: "Creating a Word Learning Device on ESP32"
description: "How I Decided to Build My First Arduino Project Without Tutorials."
date: "Feb 22 2025"
---

## How I Decided to Build My First Arduino Project Without Tutorials

I had wanted to try building a device on Arduino or ESP32 for a long time, but I kept putting it off. Usually, when working with new hardware, the first instinct is to look up tutorials. However, this time I decided to take a different approach: grab the components, come up with an idea, and implement it from scratch.

## Project Idea

I had an ESP32, a small `128x64` screen, a few buttons, and the desire to make something useful. This led to the idea of a simple word-learning device. The core functionality would be to display a word and three possible translations, with the user selecting the correct one.

### Key Requirements for Version 1

- **Minimal controls** – nothing unnecessary, just what is required.
- **Clean interface** – focus on content, no visual clutter.
- **Invisible UI elements** – everything should look as natural as possible.
- **Endless process** – words should continuously cycle without extra screens.
- **No statistics** – no tracking of errors or progress in the first version.
- **Local storage** – no cloud services or synchronization at the start.

## Designing the Interface

Since the screen was only `128x64` pixels, careful layout planning was crucial. The final structure consisted of:

- **Main word** – displayed prominently for easy reading.
- **Three translation options** – optimal in terms of both size and meaning.

### Initial Sketches

I first drafted a basic layout, determining row heights and element placement.

```plaintext
![files/frame-1321319749.png]
```

I then tested how the words would fit inside the blocks to ensure they didn’t look cluttered.

```plaintext
![files/frame-1321319750.png]
```

Next, I experimented with fonts. I chose a serif style for the main word to make it stand out.

```plaintext
![files/frame-1321319751.png]
```

I also tested the text appearance with screen colors.

```plaintext
![files/frame-1321319752.png]
```

Added a subtle glow effect to highlight the active element.

```plaintext
![files/frame-1321319818.png]
```

Everything looked good enough for a prototype, so I moved on to the next step.

## Implementing the Interface

Next, I needed to find suitable libraries for rendering the interface. I explored multiple options and found that `U8g2lib` was the best for handling fonts.

### Font Selection

Fonts in `U8g2lib` are categorized by height. After visually testing several options, I settled on `Lucida`:

```plaintext
[https://github.com/olikraus/u8g2/wiki/fntgrplucida](https://github.com/olikraus/u8g2/wiki/fntgrplucida)
```

```plaintext
![files/image.png]
```

- **Main text** – `14px` height worked best. `18px` was too large, causing long words to overflow.
- **Translation options** – Cyrillic font at `8px` height.

```plaintext
![files/u8g2_font_unifont_t_cyrillic.png]
```

## Conclusion

After all the testing, it became clear that the interface could be implemented with the necessary fonts and grid structure. The next step is working on the code and device logic.

This project turned out to be an exciting challenge because I completely avoided tutorials and figured things out myself. If the first version is successful, I’ll consider adding synchronization, statistics, and other useful features in future iterations.

