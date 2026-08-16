# DaVinci Resolve Studio Inspector UI Design Specification (V2)

Official Blackmagic Design DaVinci Resolve Inspector UI design metrics, color values, typography, and geometry standards for Version 2 of **AI Cinematic Haze Studio**.

---

## 1. Color Palette & Design Tokens

| Element | Color Preview | Hex Code | Description / Usage |
| :--- | :--- | :--- | :--- |
| **Panel Background** | <span style="display:inline-block;width:16px;height:16px;background:#222226;border:1px solid #444;border-radius:2px;vertical-align:middle;"></span> `#222226` | `#222226` | Main dark background for the Inspector panel. |
| **Input Box Fill** | <span style="display:inline-block;width:16px;height:16px;background:#141416;border:1px solid #444;border-radius:2px;vertical-align:middle;"></span> `#141416` | `#141416` | Background fill for numeric fields, input boxes, & dropdowns. |
| **Input Box Border** | <span style="display:inline-block;width:16px;height:16px;background:#08080A;border:1px solid #444;border-radius:2px;vertical-align:middle;"></span> `#08080A` | `#08080A` | 1px dark subtle stroke surrounding input boxes. |
| **Category Divider** | <span style="display:inline-block;width:16px;height:16px;background:#18181B;border:1px solid #444;border-radius:2px;vertical-align:middle;"></span> `#18181B` | `#18181B` | 1px horizontal separating line between collapsible categories. |
| **Active Highlight Line** | <span style="display:inline-block;width:16px;height:16px;background:#E55545;border:1px solid #444;border-radius:2px;vertical-align:middle;"></span> `#E55545` | `#E55545` | Coral/Red accent bar under active top tab ("Video", "Effects"). |
| **Toggle Switch (ON)** | <span style="display:inline-block;width:16px;height:16px;background:#D84836;border:1px solid #444;border-radius:2px;vertical-align:middle;"></span> `#D84836` | `#D84836` | Coral/Red circular status toggle for enabled effects. |
| **Toggle Switch (OFF)** | <span style="display:inline-block;width:16px;height:16px;background:#4A4A50;border:1px solid #444;border-radius:2px;vertical-align:middle;"></span> `#4A4A50` | `#4A4A50` | Muted dark grey circular indicator for disabled features. |
| **Slider Track (Background)** | <span style="display:inline-block;width:16px;height:16px;background:#111113;border:1px solid #444;border-radius:2px;vertical-align:middle;"></span> `#111113` | `#111113` | Recessed dark track color for slider bars. |
| **Slider Handle (Thumb)** | <span style="display:inline-block;width:16px;height:16px;background:#7E7E84;border:1px solid #444;border-radius:2px;vertical-align:middle;"></span> `#7E7E84` | `#7E7E84` | Neutral grey circular slider thumb handle. |
| **Disabled Keyframe Icon** | <span style="display:inline-block;width:16px;height:16px;background:#65656B;border:1px solid #444;border-radius:2px;vertical-align:middle;"></span> `#65656B` | `#65656B` | Unset diamond keyframe & reset curve icons. |
| **Icon Text Highlight** | <span style="display:inline-block;width:16px;height:16px;background:#FFFFFF;border:1px solid #444;border-radius:2px;vertical-align:middle;"></span> `#FFFFFF` | `#FFFFFF` | Active tab text/icon color ("Video", "Effects"). |
| **Inactive Tab Text** | <span style="display:inline-block;width:16px;height:16px;background:#808086;border:1px solid #444;border-radius:2px;vertical-align:middle;"></span> `#808086` | `#808086` | Dimmed text/icon color ("Audio", "Transition", etc.). |

---

## 2. Typography & Font Family

- **Primary System Font**: `Open Sans` (`Open Sans Regular` 400, `Open Sans SemiBold` 600). Blackmagic Design uses Open Sans natively across standard desktop platforms for its UI panel layout.
- **Fallbacks**: `-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif`.
- **Monospaced Numerics**: `JetBrains Mono` or tabular `Open Sans` for numeric entry boxes, coordinates, timecodes, and telemetry values.

### Font Specifications:
1. **Header / Category Labels** (*"AI Depth & Auto-Focus"*, *"Atmospheric Scattering"*):
   - Font Size: `13px` / `14px`
   - Font Weight: `600` (SemiBold / Medium)
   - Font Color: `#E1E1E5` (Light Neutral)
2. **Property Labels** (*"Far Limit"*, *"Airlight"*, *"Density"*):
   - Font Size: `12px`
   - Font Weight: `400` (Regular)
   - Font Color: `#9E9EA4` (Medium Muted Gray)
3. **Numeric Input Text** (*"1.000"*, *"0.000"*, *"-1.500"*):
   - Font Size: `12px`
   - Font Weight: `400` (Regular / Monospaced)
   - Font Color: `#FFFFFF` (Bright White)

---

## 3. UI Structure & Geometry

- **Panel Margins & Padding**:
  - Top tab spacing: `12px`
  - Element row heights: Fixed at `28px`–`32px` per parameter control
  - Category header height: `32px`
- **Border Radius**:
  - Input boxes & dropdown containers: `3px` corner radius
  - Category toggle buttons & link icons: `4px` or circular caps
  - Slider thumb handle: `50%` (Fully circular)
- **Component Dimensions**:
  - **Numeric Entry Boxes**: Width `~75px`, Height `~24px`, right-aligned/centered numeric text
  - **Slider Track**: Height `4px`, Background `#111113`, recessed 1px border `#08080A`
  - **Slider Thumbs**: Width `10px`, Height `10px`, Background `#7E7E84`, rounded `50%`

---

## 4. CSS Token Mapping Implementation

```css
:root {
    --dr-bg-panel: #222226;
    --dr-bg-input: #141416;
    --dr-border-input: #08080A;
    --dr-border-divider: #18181B;
    --dr-tab-active-line: #E55545;
    --dr-toggle-on: #D84836;
    --dr-toggle-off: #4A4A50;
    --dr-track-bg: #111113;
    --dr-thumb-bg: #7E7E84;
    --dr-keyframe-dim: #65656B;
    --dr-text-active: #FFFFFF;
    --dr-text-inactive: #808086;
    --dr-text-header: #E1E1E5;
    --dr-text-label: #9E9EA4;
    --dr-font-main: 'Open Sans', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
    --dr-font-mono: 'JetBrains Mono', monospace;
}
```
