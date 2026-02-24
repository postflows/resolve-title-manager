# Title Manager

> Part of [PostFlows](https://github.com/postflows) toolkit for DaVinci Resolve

Copy style and transform text across Text+ clips or Fusion Macros on the timeline via a single-window interface.

## What it does

- **Text+**: Copy full style or selected parameter groups (Font, Style, Color, Size, Spacing, Layout, Transform, Shading), apply text transforms (lowercase, uppercase, capitalize), remove punctuation.
- **Fusion Macros**: Copy all published Inspector parameters between clips with the same macro name, or **choose which parameters to copy** via the parameter selector. Same-structure check uses copyable inputs only (text-content inputs are excluded). Text transform applies to published Styled Text and inner Text+ nodes.
- **Target selection** (both modes): Filter by track and clip color. Source is the clip under the playhead.

## New in v04 (Fusion Macros — selective parameters)

- **Select Parameters…** (Fusion Macros mode): Opens a window with a tree of the source macro's published inputs. Labels and groups match the Inspector layout; text-content inputs are shown but not copyable. Click a row or group header to toggle selection; use Select All / Clear All / Invert. **Use Selection** saves your choice and closes. When you click **Apply Style**, only the selected parameters are copied to target clips. If you never open the selector (or clear all and use selection), all copyable parameters are copied.
- **Window layout**: Geometry is recalculated when switching between Title Type (Text+ / Fusion Macros) so the combo box stays usable and the parameter block does not overlap it.

## Requirements

- DaVinci Resolve Studio
- Open project and timeline before use
- **Optional:** UTF-8 module for full Unicode support (lowercase/uppercase/capitalize for non-ASCII text). The script works without it; ASCII-only transforms still work.

## Installation

### 1. Copy the script

Copy **`title-manager.lua`** to Resolve's Fusion Scripts folder:

- **macOS:** `~/Library/Application Support/Blackmagic Design/DaVinci Resolve/Fusion/Scripts/` (or a subfolder, e.g. `Utility/`)
- **Windows:** `C:\ProgramData\Blackmagic Design\DaVinci Resolve\Fusion\Scripts\`

### 2. Optional: UTF-8 module (recommended for non-ASCII text)

For correct case conversion (lower/upper/capitalize) with Unicode (e.g. Cyrillic, accented characters), copy **`utf8_module.lua`** from this repo into the **same folder** as the script. The script uses `require("utf8_module")`, so Lua must find `utf8_module.lua` in the same directory (or on `package.path`).

- If you place the script in a subfolder (e.g. `Fusion/Scripts/Utility/`), put `utf8_module.lua` in that same subfolder.
- If the module is missing, the script runs without it and falls back to built-in string functions (ASCII-only for case transforms).

## Usage

1. Position playhead on the source clip.
2. Click **Refresh** to load the timeline.
3. Choose **Title Type** (Text+ or Fusion Macros), **Track**, **Clip Color**.
4. **Text+:** Choose **Style Copy** (Full Style or Selected Parameters); if Selected Parameters, tick the parameter groups/subgroups to copy.
5. **Fusion Macros:** Optionally click **Select Parameters…** to choose which published parameters to copy (default: all copyable).
6. Set **Text transform** and punctuation options if needed.
7. Click **Apply Text Format Only** or **Apply Style**.

## License

MIT © PostFlows
