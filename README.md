# ToPu_SurfaceReslicer

[![Blender](https://img.shields.io/badge/Blender-4.2%2B-F5792A?logo=blender&logoColor=white)](https://www.blender.org/)

選択した縦方向の辺を基準に、横方向の辺を編集可能な格子で再構築するBlenderアドオンです。

髪束などのメッシュに対して、スライスの間隔・密度・向きをプレビューしながら調整できます。全体の分割数に加えて、束の一部だけ密度を変えたり、元の縦辺の流れに沿ってスライスを配置したりできます。

## 対応環境

- Blender 4.2以降
- 対象：メッシュの編集モード・辺選択（複数オブジェクトの編集に対応）
- パネル・HUD：日本語表示／アドオン登録時の説明文：英語・日本語併記
- 配布形式：従来形式のアドオンZIP

## ダウンロード

配布用のアドオンZIPは [Releases](https://github.com/http4211/ToPu_SurfaceReslicer/releases) からダウンロードしてください。

## インストール

1. [Releases](https://github.com/http4211/ToPu_SurfaceReslicer/releases) からアドオンのZIPファイルをダウンロードします。
2. ZIPは解凍せずにBlenderのウィンドウへドラッグ＆ドロップし、表示される確認画面でインストールします。
3. メニューからインストールする場合は、`編集 > プリファレンス > エクステンション` の右上のメニューで `ディスクからインストール` を選び、ZIPを指定します。
4. `編集 > プリファレンス > アドオン` で **ToPu_SurfaceReslicer** が有効になっていることを確認します。

インストール済みのアドオンを入れ替えた場合は、Blenderを再起動してください。アドオンプリファレンスの説明文は英語・日本語の併記です。

## 場所

`3Dビュー > サイドバー（N）> ToPu > Surface Reslicer`

## 主な機能

### 格子で再スライス

残したい縦辺から操作用の格子を作成し、横方向のスライスを再配置します。格子は束の根元・先端・分岐や曲率に応じて構成されます。

- 格子頂点・横線のドラッグによる調整
- `G`／`R` による格子の移動・回転
- 矩形選択、選択の追加・解除
- 操作用格子の段数と、基本スライス数の独立調整

### 密度と追従スライス

- **個別スライス密度**：選択した格子の周辺を20〜800％の範囲で調整
- **追従スライス**：格子を基準にした配置から、元の縦辺の流れに沿う配置まで0〜100％で調整
- **全体格子追加**：対象全体へ調整位置を追加
- **局所格子追加**：クリックした格子区画に対応する束・分岐へ調整位置を追加

### プレビューと編集

- 画面下部のHUDから、数値のドラッグ・格子追加・Undo／Redo・確定／取消を操作
- 実行中の調整を戻せるUndo／Redo
- 確定時にメッシュを再構築し、キャンセル時は元メッシュを維持
- 複数オブジェクトの編集と、実行中の3Dマウスによる視点操作に対応

## 基本的な使い方

1. メッシュを選択し、**編集モード・辺選択**にします。
2. 髪の根元から先端へ伸びる、**残したい縦方向の辺**を選びます。
3. `N` キーでサイドバーを開き、**ToPu → Surface Reslicer** へ進みます。
4. 「基本スライス数」「格子の余白」を設定し、**再スライスを実行**を押します。
5. 格子を選択し、密度・追従量・位置・傾きを調整します。
6. HUDの**確定**、`Enter` または `Space` でメッシュを再構築します。

Nパネルの「リング選択」「ループ選択」はBlender標準の選択操作です。ハードエッジを使う場合も、残したい縦辺が選ばれていることを確認してください。「選択面内だけ」を有効にすると、面も選択されている場合に対象面を限定できます。

## 操作方法

| 操作 | 動作 |
| --- | --- |
| 格子頂点を左クリック／左ドラッグ | 選択／移動 |
| 格子の横線を左クリック／左ドラッグ | 横断格子をまとめて選択／移動 |
| 空白を左ドラッグ | 格子頂点を矩形選択 |
| `Shift` ＋選択 | 選択へ追加 |
| `Ctrl` ＋空白をドラッグ | 矩形内の格子頂点を選択解除 |
| `G`／`R` | ビューに沿った移動／ビュー方向の回転 |
| `Alt` ＋ホイール | 基本スライス数 |
| `Ctrl` ＋ `Shift` ＋ホイール | 格子数 |
| `Shift` ＋ホイール | 個別スライス密度 |
| `Ctrl` ＋ホイール | 追従スライス |
| `Ctrl` ＋格子線をクリック | 全体格子の追加／追加済み格子の削除 |
| `Ctrl` ＋ `Shift` ＋格子線をクリック | 局所格子の追加／追加済み局所格子の削除 |
| `Ctrl` ＋ `Z`／`Ctrl` ＋ `Shift` ＋ `Z` | Undo／Redo |
| `H`／`Shift` ＋ `H` | 格子の表示切り替え／HUDの詳細表示切り替え |
| HUDの「確定」／`Enter`／`Space` | メッシュを再構築して終了 |
| HUDの「取消」／`Esc`／右クリック | キャンセルして終了 |

`G`／`R` の操作中は、`Shift` で微調整、回転中の `Ctrl` で15°刻みになります。左クリック・`Enter`・`Space` は**移動・回転だけの確定**、`Esc`・右クリックは**移動・回転だけの取消**です。その後、再スライスの調整を続けられます。

### HUDと視点操作

数値欄は全体を左右にドラッグするか、欄上でホイールを回して調整できます。個別密度・追従量を変更するときは、先に対象の格子を選択してください。

HUDはウィンドウの解像度差を補正し、高解像度でも小さく見えないように描画します。フルHD相当を基準とし、4K相当では約2倍のピクセル寸法で表示します。BlenderのUIスケールも考慮します。同じウィンドウ内でのビュー分割・最大化では表示倍率を変えず、狭い領域では簡易表示に切り替えます。

この補正は画面内での見た目の比率をそろえるもので、寸法の異なるモニター間で物理サイズを完全に固定するものではありません。

通常のビュー操作と3Dマウスの視点操作（NDOF）は実行中も使用できます。HUD操作中や格子の移動・回転中も、3Dマウスの入力をBlenderへ通します。

## オプション

### 実行前の設定

Nパネルの `ToPu > Surface Reslicer` で設定します。

| 項目 | 内容 |
| --- | --- |
| 基本スライス数 | 全体の分割数の基準。初期値12、設定範囲2〜256。実行中も変更できます。 |
| 格子の余白 | 操作用格子を対象面の外側へ広げる量。確定後のメッシュを膨らませる設定ではありません。 |
| 選択面内だけ | 面も選択されている場合、その選択面の中だけを対象にします。 |
| ヘルプ | 選択方法と実行中の操作説明を表示します。 |

### 実行中の調整

HUDまたはショートカットで調整します。個別密度・追従量を変更するときは、先に対象の格子を選択してください。

| 項目 | 役割 |
| --- | --- |
| 基本スライス数 | 全体の分割数の基準。初期値12、設定範囲2〜256。束の長さや局所設定により実際のスライス本数は変わります。 |
| 格子数 | 操作用格子の段数。3段から開始し、端部・分岐に必要な格子も表示します。 |
| 個別スライス密度 | 選択格子の周辺の密度。100％が標準で、20〜800％まで調整できます。 |
| 追従スライス | 0％は格子の平面・曲面を基準に配置し、100％は元の縦辺の流れに沿って配置します。 |
| 全体格子追加 | 対象全体の調整位置を追加します。 |
| 局所格子追加 | クリックした格子区画に対応する束・分岐の調整位置を追加します。 |

追従100％では、格子の中心位置の移動を反映し、格子を傾けたことによる角度の変化はスライスの向きへ反映しません。密度と追従量は周囲の格子の間で補間します。

格子を追加するだけではスライスは増えません。追加後に個別密度などを調整してください。局所格子は束の断面全体へ反映しますが、一つの区画に複数の束が入っている場合は、その束も対象になります。

## 対応範囲・注意点

- 複雑な自己交差やNゴン、平面成分を含むスライスでの強い格子の傾きでは、意図しない交差が生じる場合があります。確定前にプレビューを確認してください。
- Basisを含めて複数のシェイプキーがあるメッシュは、トポロジー変更に未対応のため実行を停止します。
- マテリアル境界を保持して再構築します。トポロジー変更に伴い、カスタム属性などは変化する場合があります。
- 操作用格子はプレビューです。確定後に独立した格子オブジェクトとして残りません。

詳しい操作方法は、配布ZIPに同梱の操作マニュアルも参照してください。

## 作者・サポート

- 作者：[http4211](https://github.com/http4211)
- リポジトリ：[http4211/ToPu_SurfaceReslicer](https://github.com/http4211/ToPu_SurfaceReslicer)

不具合報告や要望は [Issues](https://github.com/http4211/ToPu_SurfaceReslicer/issues) へお願いします。

---

<details>
<summary><strong>English</strong></summary>

## Overview

**ToPu_SurfaceReslicer** is a Blender add-on that rebuilds cross edges from selected longitudinal edges using an editable lattice.

Adjust slice spacing, density, and orientation on hair strands and similar meshes while previewing the result. You can change the overall division count, refine density around selected lattice sections, and make slices follow the original longitudinal edge flow.

## Requirements

- Blender 4.2 or later
- Mesh Edit Mode with Edge Select; multi-object editing is supported
- Panel and HUD labels: Japanese; registered add-on description: English and Japanese
- Distributed as a legacy add-on ZIP

## Download and installation

Download the add-on ZIP from [Releases](https://github.com/http4211/ToPu_SurfaceReslicer/releases). Keep it compressed, then drag and drop it into Blender and confirm installation. Alternatively, open `Edit > Preferences > Extensions`, choose `Install from Disk` from the top-right menu, and select the ZIP.

Check that **ToPu_SurfaceReslicer** is enabled under `Edit > Preferences > Add-ons`. Restart Blender after replacing an installed copy.

Location: `3D View > Sidebar (N) > ToPu > Surface Reslicer`

## Main features

- Rebuild cross sections from the longitudinal edges you want to keep
- Move and rotate lattice points or entire cross-section rings
- Adjust the slice count independently of the number of lattice levels
- Set local slice density from 20% to 800%
- Blend between lattice-based slicing and original-edge following from 0% to 100%
- Add global or local lattice sections that inherit surrounding settings
- Build lattices around strand ends, branches, and curved shapes
- Edit values through the HUD, undo or redo adjustments, and confirm or cancel
- Use multi-object editing and 3D-mouse navigation during the operation

## Quick start

1. Select the mesh and enter **Edit Mode > Edge Select**.
2. Select the longitudinal edges you want to keep, such as edges running from the root to the tip of a hair strand.
3. Open `Sidebar (N) > ToPu > Surface Reslicer`.
4. Set the base slice count and lattice padding, then click **再スライスを実行** (Run Reslice).
5. Select lattice points or rings and adjust their density, follow amount, position, and orientation.
6. Click **確定** (Confirm) in the HUD, or press `Enter` or `Space`, to rebuild the mesh. Use **取消** (Cancel), `Esc`, or right-click to cancel.

The panel's **リング選択** (Ring Select) and **ループ選択** (Loop Select) buttons use Blender's built-in selection tools. When selecting sharp edges, check that the selection contains the longitudinal edges you want to keep. **選択面内だけ** (Selected Faces Only) restricts the target when faces are also selected.

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

## HUD and navigation

Drag a numeric field horizontally, or scroll over it, to adjust its value. Select the target lattice points before changing local density or follow amount.

The HUD compensates for window resolution and accounts for Blender's UI scale. At a 4K-sized window, its pixel dimensions are approximately twice those at Full HD. Splitting or maximizing a viewport within the same window keeps the display scale unchanged; narrow regions use a compact display. This maintains a similar visual proportion, rather than a guaranteed physical size across monitors of different dimensions.

View navigation and 3D-mouse input (NDOF) remain available while using the HUD or moving and rotating the lattice.

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

</details>
