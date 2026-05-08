# Element Templates

Copy-paste JSON templates for each Excalidraw element type. The `strokeColor` and `backgroundColor` values are placeholders — always pull actual colors from `color-palette.md` based on the element's semantic purpose.

## Free-Floating Text (no container)
```json
{
  "type": "text",
  "id": "label1",
  "x": 100, "y": 100,
  "width": 200, "height": 25,
  "text": "Section Title",
  "originalText": "Section Title",
  "fontSize": 20,
  "fontFamily": 3,
  "textAlign": "left",
  "verticalAlign": "top",
  "strokeColor": "<title color from palette>",
  "backgroundColor": "transparent",
  "fillStyle": "solid",
  "strokeWidth": 1,
  "strokeStyle": "solid",
  "roughness": 0,
  "opacity": 100,
  "angle": 0,
  "seed": 11111,
  "version": 1,
  "versionNonce": 22222,
  "isDeleted": false,
  "groupIds": [],
  "boundElements": null,
  "link": null,
  "locked": false,
  "containerId": null,
  "lineHeight": 1.25
}
```

## Line (structural, not arrow)
```json
{
  "type": "line",
  "id": "line1",
  "x": 100, "y": 100,
  "width": 0, "height": 200,
  "strokeColor": "<structural line color from palette>",
  "backgroundColor": "transparent",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 0,
  "opacity": 100,
  "angle": 0,
  "seed": 44444,
  "version": 1,
  "versionNonce": 55555,
  "isDeleted": false,
  "groupIds": [],
  "boundElements": null,
  "link": null,
  "locked": false,
  "points": [[0, 0], [0, 200]]
}
```

## Small Marker Dot
```json
{
  "type": "ellipse",
  "id": "dot1",
  "x": 94, "y": 94,
  "width": 12, "height": 12,
  "strokeColor": "<marker dot color from palette>",
  "backgroundColor": "<marker dot color from palette>",
  "fillStyle": "solid",
  "strokeWidth": 1,
  "strokeStyle": "solid",
  "roughness": 0,
  "opacity": 100,
  "angle": 0,
  "seed": 66666,
  "version": 1,
  "versionNonce": 77777,
  "isDeleted": false,
  "groupIds": [],
  "boundElements": null,
  "link": null,
  "locked": false
}
```

## Rectangle
```json
{
  "type": "rectangle",
  "id": "elem1",
  "x": 100, "y": 100, "width": 180, "height": 90,
  "strokeColor": "<stroke from palette based on semantic purpose>",
  "backgroundColor": "<fill from palette based on semantic purpose>",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 0,
  "opacity": 100,
  "angle": 0,
  "seed": 12345,
  "version": 1,
  "versionNonce": 67890,
  "isDeleted": false,
  "groupIds": [],
  "boundElements": [{"id": "text1", "type": "text"}],
  "link": null,
  "locked": false,
  "roundness": {"type": 3}
}
```

## Text (centered in shape)
```json
{
  "type": "text",
  "id": "text1",
  "x": 130, "y": 132,
  "width": 120, "height": 25,
  "text": "Process",
  "originalText": "Process",
  "fontSize": 16,
  "fontFamily": 3,
  "textAlign": "center",
  "verticalAlign": "middle",
  "strokeColor": "<text color — match parent shape's stroke or use 'on light/dark fills' from palette>",
  "backgroundColor": "transparent",
  "fillStyle": "solid",
  "strokeWidth": 1,
  "strokeStyle": "solid",
  "roughness": 0,
  "opacity": 100,
  "angle": 0,
  "seed": 11111,
  "version": 1,
  "versionNonce": 22222,
  "isDeleted": false,
  "groupIds": [],
  "boundElements": null,
  "link": null,
  "locked": false,
  "containerId": "elem1",
  "lineHeight": 1.25
}
```

## Arrow
```json
{
  "type": "arrow",
  "id": "arrow1",
  "x": 282, "y": 145, "width": 118, "height": 0,
  "strokeColor": "<arrow color — typically matches source element's stroke from palette>",
  "backgroundColor": "transparent",
  "fillStyle": "solid",
  "strokeWidth": 2,
  "strokeStyle": "solid",
  "roughness": 0,
  "opacity": 100,
  "angle": 0,
  "seed": 33333,
  "version": 1,
  "versionNonce": 44444,
  "isDeleted": false,
  "groupIds": [],
  "boundElements": null,
  "link": null,
  "locked": false,
  "points": [[0, 0], [118, 0]],
  "startBinding": {"elementId": "elem1", "focus": 0, "gap": 2},
  "endBinding": {"elementId": "elem2", "focus": 0, "gap": 2},
  "startArrowhead": null,
  "endArrowhead": "arrow"
}
```

For curves: use 3+ points in `points` array.

## Bound Arrow — Complete 3-Element Wiring

Arrow connections must be **bidirectional**: the arrow holds `startBinding`/`endBinding`, AND each connected shape must list the arrow in its own `boundElements`. Without this wiring, arrows float and drift when shapes are moved in Excalidraw.

```json
[
  {
    "type": "rectangle",
    "id": "source_rect",
    "x": 100, "y": 120, "width": 180, "height": 60,
    "strokeColor": "#1a1a2e", "backgroundColor": "#e8f4f8",
    "fillStyle": "solid", "strokeWidth": 2, "strokeStyle": "solid",
    "roughness": 0, "opacity": 100, "angle": 0,
    "seed": 10001, "version": 1, "versionNonce": 10002,
    "isDeleted": false, "groupIds": [], "link": null, "locked": false,
    "roundness": {"type": 3},
    "boundElements": [
      {"id": "text_source", "type": "text"},
      {"id": "conn_arrow",  "type": "arrow"}
    ]
  },
  {
    "type": "text",
    "id": "text_source",
    "x": 145, "y": 143, "width": 90, "height": 20,
    "text": "Source", "originalText": "Source",
    "fontSize": 16, "fontFamily": 3,
    "textAlign": "center", "verticalAlign": "middle",
    "strokeColor": "#1a1a2e", "backgroundColor": "transparent",
    "fillStyle": "solid", "strokeWidth": 1, "strokeStyle": "solid",
    "roughness": 0, "opacity": 100, "angle": 0,
    "seed": 10003, "version": 1, "versionNonce": 10004,
    "isDeleted": false, "groupIds": [], "link": null, "locked": false,
    "containerId": "source_rect", "lineHeight": 1.25, "boundElements": null
  },
  {
    "type": "arrow",
    "id": "conn_arrow",
    "x": 282, "y": 150, "width": 118, "height": 0,
    "strokeColor": "#1a1a2e", "backgroundColor": "transparent",
    "fillStyle": "solid", "strokeWidth": 2, "strokeStyle": "solid",
    "roughness": 0, "opacity": 100, "angle": 0,
    "seed": 10005, "version": 1, "versionNonce": 10006,
    "isDeleted": false, "groupIds": [], "boundElements": null, "link": null, "locked": false,
    "points": [[0, 0], [118, 0]],
    "startBinding": {"elementId": "source_rect", "focus": 0.0, "gap": 2},
    "endBinding":   {"elementId": "target_rect", "focus": 0.0, "gap": 2},
    "startArrowhead": null,
    "endArrowhead": "arrow"
  },
  {
    "type": "rectangle",
    "id": "target_rect",
    "x": 400, "y": 120, "width": 180, "height": 60,
    "strokeColor": "#1a1a2e", "backgroundColor": "#e8f4f8",
    "fillStyle": "solid", "strokeWidth": 2, "strokeStyle": "solid",
    "roughness": 0, "opacity": 100, "angle": 0,
    "seed": 10007, "version": 1, "versionNonce": 10008,
    "isDeleted": false, "groupIds": [], "link": null, "locked": false,
    "roundness": {"type": 3},
    "boundElements": [
      {"id": "text_target", "type": "text"},
      {"id": "conn_arrow",  "type": "arrow"}
    ]
  },
  {
    "type": "text",
    "id": "text_target",
    "x": 445, "y": 143, "width": 90, "height": 20,
    "text": "Target", "originalText": "Target",
    "fontSize": 16, "fontFamily": 3,
    "textAlign": "center", "verticalAlign": "middle",
    "strokeColor": "#1a1a2e", "backgroundColor": "transparent",
    "fillStyle": "solid", "strokeWidth": 1, "strokeStyle": "solid",
    "roughness": 0, "opacity": 100, "angle": 0,
    "seed": 10009, "version": 1, "versionNonce": 10010,
    "isDeleted": false, "groupIds": [], "link": null, "locked": false,
    "containerId": "target_rect", "lineHeight": 1.25, "boundElements": null
  }
]
```

**Key rules:**
- Both the source AND target shape must have `{"id": "<arrow_id>", "type": "arrow"}` in their `boundElements` array.
- `focus: 0.0` centres the connection on the edge midpoint. `gap: 5` adds a small visual clearance.
- Never leave bindings as `null` if the arrow visually connects two shapes — null bindings cause drift.

## Frame (Swimlane Container)

Frames create labelled visual sections. Child elements must set `"frameId"` to the frame's id.
Use for swimlane diagrams comparing parallel processes (e.g., Frontend vs Backend, Before vs After).

```json
{
  "type": "frame",
  "id": "frame1",
  "x": 0, "y": 0,
  "width": 400, "height": 500,
  "name": "Frontend",
  "isCollapsed": false,
  "strokeColor": "#e2e2e2",
  "backgroundColor": "transparent",
  "fillStyle": "solid",
  "strokeWidth": 1,
  "strokeStyle": "solid",
  "roughness": 0,
  "opacity": 100,
  "angle": 0,
  "seed": 20001,
  "version": 1,
  "versionNonce": 20002,
  "isDeleted": false,
  "groupIds": [],
  "boundElements": null,
  "link": null,
  "locked": false
}
```

**Swimlane layout recipe** (two frames side by side, 60px gap):
- Frame 1: `x: 0,   width: 400`
- Frame 2: `x: 460, width: 400`
- Child elements inside each frame: set `"frameId": "<frame_id>"`
- Elements that live inside a frame do NOT need to overlap the frame border — place them inside the frame's bounds.

## Container Sizing Guide

Excalidraw does not auto-size containers. Use these formulas to size boxes so text fits without clipping.

**Formula (fontSize 16, lineHeight 1.25, fontFamily 3 / Cascadia):**

```
char_px  = 9         # approximate glyph width in px at fontSize 16
line_h   = 20        # fontSize 16 × lineHeight 1.25 = 20px per line
pad_h    = 40        # horizontal padding total (20px each side)
pad_v    = 24        # vertical padding total (12px each side)

width  = max_chars_per_line × char_px + pad_h
height = line_count           × line_h  + pad_v
```

**Quick reference:**

| Text | Chars | Width | Lines | Height |
|------|-------|-------|-------|--------|
| "Start" | 5 | 85px | 1 | 44px → use 60 |
| "Process step" | 12 | 148px | 1 | 44px → use 60 |
| "Authentication\nService" | 14 | 166px | 2 | 64px → use 80 |
| "Load Balancer\n(Round Robin)" | 13 | 157px | 2 | 64px → use 80 |

**Minimum safe sizes:** width ≥ 120px, height ≥ 60px for single-line labels.

**For fontSize 20:** multiply char_px by 1.25 → `char_px = 11`. Add ~8px to padding.

When in doubt, size generously — a slightly larger box looks better than clipped text.
