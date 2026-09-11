# ToPu_SurfaceReslicer

[日本語](README.md) | **English**

[![Blender](https://img.shields.io/badge/Blender-4.2%2B-F5792A?logo=blender&logoColor=white)](https://www.blender.org/)

**ToPu_SurfaceReslicer** is a Blender add-on that rebuilds cross edges from selected longitudinal edges using an editable lattice.

Adjust slice spacing, density, and orientation on hair strands and similar meshes while previewing the result. You can change the overall division count, refine density around selected lattice sections, and make slices follow the original longitudinal edge flow.

## Requirements

- Blender 4.2 or later
- Mesh Edit Mode with Edge Select; multi-object editing is supported
- UI: English / Japanese, following Blender's language and translation settings

## Download and installation

Download the add-on ZIP from [Releases](https://github.com/http4211/ToPu_SurfaceReslicer/releases). Keep it compressed, then drag and drop it into Blender and confirm installation. Alternatively, open `Edit > Preferences > Extensions`, choose `Install from Disk` from the top-right menu, and select the ZIP.

Check that **ToPu_SurfaceReslicer** is enabled under `Edit > Preferences > Add-ons`. Restart Blender after replacing an installed copy.

Location: `3D View > Sidebar (N) > ToPu > Surface Reslicer`

The Japanese panel name is **サーフェス再スライス**. The panel, HUD, and help follow Blender's language and interface translation settings. Tooltips and reports follow their respective translation settings.

## Main features

- Rebuild cross sections from the longitudinal edges you want to keep
- Move and rotate lattice points or entire cross-section rings
- Adjust the slice count independently of the number of lattice levels
- Set local slice density from 20% to 800%
- Blend between lattice-based slicing and original-edge following from 0% to 100%
- Add global or local lattice sections that inherit surrounding settings
- Build lattices around strand ends, branches, and curved shapes
- Edit values through the HUD, undo or redo adjustments, and confirm or cancel
- Use multi-object editing

## Quick start

1. Select the mesh and enter **Edit Mode > Edge Select**.
2. Select the longitudinal edges you want to keep, such as edges running from the root to the tip of a hair strand.
3. Open `Sidebar (N) > ToPu > Surface Reslicer`.
4. Set the base slice count and lattice padding, then click **Run Reslice**.
5. Select lattice points or rings and adjust their density, follow amount, position, and orientation.
6. Click **Confirm** in the HUD, or press `Enter` or `Space`, to rebuild the mesh. Use **Cancel**, `Esc`, or right-click to cancel.

The panel's **Ring Select** and **Loop Select** buttons use Blender's built-in selection tools. When selecting sharp edges, check that the selection contains the longitudinal edges you want to keep. **Selected Faces Only** restricts the target when faces are also selected.

## Controls

| Input | Action |
| --- | --- |
| Click / drag a lattice point | Select / move the point |
| Click / drag a lattice cross-section line | Select / move the entire ring |
| Drag empty space | Box-select lattice points |
| `Shift` + select | Add to the selection |
| `Ctrl` + drag empty space | Deselect points inside the box |
| `G` / `R` | Move in the view plane / rotate around the view direction |
| `Alt` + wheel | Base slice count |
| `Ctrl` + `Shift` + wheel | Number of lattice levels |
| `Shift` + wheel | Local slice density |
| `Ctrl` + wheel | Follow amount |
| `Ctrl` + click a lattice line | Add / remove an added global lattice section |
| `Ctrl` + `Shift` + click a lattice line | Add / remove an added local lattice section |
| `Ctrl` + `Z` / `Ctrl` + `Shift` + `Z` | Undo / redo |
| `H` / `Shift` + `H` | Toggle the lattice / toggle HUD details |
| HUD Confirm / `Enter` / `Space` | Rebuild the mesh and finish |
| HUD Cancel / `Esc` / right-click | Cancel and finish |

During a `G` or `R` transform, hold `Shift` for precision; hold `Ctrl` while rotating for 15° snapping. Left-click, `Enter`, or `Space` confirms **only that transform**, and `Esc` or right-click cancels **only that transform**. The reslice session then continues.

## Options

The N-panel contains the initial settings. The HUD and shortcuts control adjustments during the operation.

| Setting | Description |
| --- | --- |
| Base slice count | Overall division target; default 12, range 2–256. Actual slice counts depend on strand length and local settings. |
| Lattice padding | Expands the editing lattice around the target surface without inflating the output mesh. |
| Selected Faces Only | Restricts the target to selected faces when faces are also selected. |
| Help | Shows selection instructions and operation shortcuts in the panel. |
| Lattice levels | Starts from three levels, with additional controls for ends and branches. |
| Local slice density | Density around selected lattice sections; 100% is standard, range 20–800%. |
| Follow amount | 0% uses the lattice planes or curved sections; 100% follows the original longitudinal edges. |
| Add global / local lattice | Adds a control position across the target or for strands and branches associated with the clicked lattice cell. |

At 100% follow, moving a lattice section's center affects placement, while tilting the lattice does not change slice orientation. Density and follow values are interpolated between surrounding controls.

Adding a lattice section alone does not add slices; adjust its density afterward. Local controls affect the entire strand cross section. If multiple strands share a lattice cell, they are also included in that control's scope.

## HUD controls

Drag a numeric field horizontally, or scroll over it, to adjust its value. Select the target lattice points before changing local density or follow amount.

## Notes

- Complex self-intersections, n-gons, or strong lattice tilts with a planar slicing component can produce unwanted intersections. Check the preview before confirming.
- Meshes with multiple shape keys, including Basis, are rejected because topology changes are not supported for those meshes.
- Material boundaries are preserved during reconstruction. Custom attributes may change with the topology.
- The editing lattice is a preview and does not remain as a separate object after confirmation.

The ZIP also includes a detailed Japanese operation manual.

## Author and support

- Author: [http4211](https://github.com/http4211)
- Repository: [http4211/ToPu_SurfaceReslicer](https://github.com/http4211/ToPu_SurfaceReslicer)

Please report bugs and feature requests through [Issues](https://github.com/http4211/ToPu_SurfaceReslicer/issues).
