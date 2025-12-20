# Super Fertility - Anno 117: Pax Romana

[![Anno 117](https://img.shields.io/badge/Anno%20117-Pax%20Romana-red)](https://www.anno-union.com/games/anno-117-pax-romana/)
[![Version](https://img.shields.io/badge/version-1.0.0-blue)](https://github.com/peeweeh/anno-117-super-fertility/releases)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Ko-fi](https://img.shields.io/badge/Ko--fi-Support%20Me-FF5E5B?logo=ko-fi&logoColor=white)](https://ko-fi.com/mrfixit027)

Simple quality-of-life mod for Anno 117: Pax Romana that increases farm module limits to 60, allowing for better organization and more aesthetic farm layouts.

## 📋 Table of Contents
- [Features](#-features)
- [Installation](#-installation)
- [What Gets Changed](#-what-gets-changed)
- [Technical Details](#-technical-details)
- [Contributing](#-contributing)
- [Development](#-development)
- [License](#-license)

## ✨ Features

- **72 Module Limit** - Build massive, organized farm layouts (7+2=9!)
- **14 Farm Types** - Covers all major farms and plantations
- **Save Compatible** - Works with existing saves
- **Mod Compatible** - Clean ModOps, no conflicts
- **Lightweight** - Only modifies module limits, nothing else

## 📦 Installation

### For Players

1. Download the latest release from [mod.io](https://mod.io/g/anno-117-pax-romana) or [GitHub Releases](https://github.com/peeweeh/anno-117-super-fertility/releases)
2. Extract to your Anno 117 mods folder (typically `Documents/Anno 117 Pax Romana/mods/`)
3. Launch Anno 117 and enable the mod in-game
4. Start building your agricultural empire!

### For Developers

```bash
git clone https://github.com/peeweeh/anno-117-super-fertility.git
cd anno-117-super-fertility
```

## 🌾 What Gets Changed

All farm types get their module limit increased to 72:

| GUID | Farm Type | Module Limit |
|------|-----------|-------------|
| **2799** | Barley Field (Latium) | 72 |
| **2698** | Wheat Field (Latium) | 72 |
| **2693** | Lavender Field (Latium) | 72 |
| **2699** | Flax Plantation (Latium) | 72 |
| **5972** | Olive Plantation (Latium) | 72 |
| **2669** | Grape Plantation (Latium) | 72 |
| **5971** | Date Plantation (Albion) | 72 |
| **31762** | Farm (Albion) | 72 |
| **31750** | Farm (Albion) | 72 |
| **2200** | Farm | 72 |
| **2800** | Farm (General) | 72 |
| **23723** | Plantation (General) | 72 |
| **2694** | Additional Farm | 72 |
| **5849** | Additional Farm | 72 |

### Why This Change?

- **Better Layouts**: Create symmetrical, organized farm complexes
- **More Flexibility**: Maximize use of fertile land
- **Quality of Life**: No more arbitrary module restrictions
- **Lucky Number**: 72 (7+2=9) for good fortune! 🍀

## 🎮 Usage

1. **Enable the Mod** - Activate in game mod manager
2. **Build or Upgrade Farms** - All farms can now have up to 72 modules
3. **Enjoy** - Create massive, organized farm layouts

### Balance Notes

- Only affects module limits - production and costs unchanged
- Quality of life improvement, not a cheat mod
- Compatible with base game and other mods

## 🛠️ Technical Details

### How It Works

The mod uses ModOps in `assets.xml` to modify farm properties:

```xml
<ModOp Type="merge" GUID="[FARM_GUID]" Path="/Values/Standard">
  <ProductionMultiplier>2</ProductionMultiplier>
  <MaintenanceMultiplier>0.5</MaintenanceMultiplier>
  <ModuleLimit>60</ModuleLimit>
</ModOp>
```

### Affected Asset Pools

- **100001** - Barley Fields
- **100002** - Wheat Fields  
- **100003** - Lavender Fields
- **100004** - Plantations (Flax, Olive, Grape, Date)
- Plus individual farm GUIDs for specific tweaks

### Why Merge Operations?

We use `Type="merge"` instead of `Type="replace"` to:
- Keep original asset structure intact
- Avoid conflicts with other mods
- Reduce mod file size
- Make updates easier

## 🤝 Contributing

Contributions welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details.

### Quick Start for Modders

See [DEVELOPMENT.md](DEVELOPMENT.md) for comprehensive documentation:

- Step-by-step guide to modifying farms
- GUID structure and asset pools
- Testing checklist and debugging tips
- Packaging for mod.io

## 📂 Development

### Project Structure

```
anno-117-super-fertility/
├── data/
│   └── base/
│       └── config/
│           └── export/
│               └── assets.xml           # Farm modifications
├── modinfo.json                         # Mod metadata
├── README.md                            # This file
├── CONTRIBUTING.md                      # Contribution guide
├── DEVELOPMENT.md                       # Technical docs
└── LICENSE                              # MIT License
```

### Building for Release

See [DEVELOPMENT.md](DEVELOPMENT.md#modio-packaging) for complete packaging instructions.

```bash
# Quick package command (auto-detects version from modinfo.json)
zip -r super-fertility-v$(jq -r '.Version' modinfo.json).zip \
  modinfo.json data/ README.md LICENSE \
  -x "*.git*" "*.vscode*" "*plans/*" "*references/*"
```

### Versioning

Follow [Semantic Versioning](https://semver.org/):

- **MAJOR.x.x** - Breaking changes, incompatible with saves
- **x.MINOR.x** - New farm types/features, backward compatible
- **x.x.PATCH** - Bug fixes, balance tweaks

Before releasing:
1. Update `Version` in `modinfo.json`
2. Add entry to changelog below
3. Test in-game
4. Create release package
5. Upload to mod.io and GitHub

## 📝 Changelog

### [1.0.1] - 2025-12-20
- Updated release workflow for better mod.io compatibility
- Improved GitHub release automation

### [1.0.0] - 2024-11-22
- Initial release
- Increases module limit to 72 for all farm types (7+2=9!)
- Affects 14 different farm buildings across Latium, and Albion

## 📜 License

This project is licensed under the MIT License - see [LICENSE](LICENSE) for details.

## 🙏 Credits

- **Modding Framework** - Anno modding community
- **Inspiration** - Players wanting more agricultural productivity
- **Support** - ☕ [Buy me a coffee on Ko-fi](https://ko-fi.com/mrfixit027)

## 🔗 Links

- [mod.io Page](https://mod.io/g/anno-117-pax-romana)
- [Anno Discord](https://discord.anno-mods.dev)
- [Modding Guide](https://github.com/anno-mods/modding-guide)

---

## 📝 mod.io Submission Guide

When uploading to mod.io, use these details:

**Name:** Super Fertility

**Summary:** Quality of life mod - increases farm module limits to 72 for better layouts and organization

**Description:**
```html
<p style="text-align: center;"><a href="https://ko-fi.com/mrfixit027"><img src="https://storage.ko-fi.com/cdn/brandasset/kofi_button_red.png" alt="Ko-fi" width="200" /></a></p>
<p style="text-align: center;">⚠️ Found a bug? Report it on <a href="https://github.com/peeweeh/anno-117-super-fertility/issues">GitHub Issues</a> ⚠️</p>

<hr />

<p>Quality of life mod that increases farm module limits to 72, allowing for better organization and more aesthetic farm layouts. Perfect for players who want symmetrical, massive farm complexes.</p>

<h3>🌾 WHAT YOU GET</h3>

<ul>
<li><strong>72 Module Limit</strong> - Build massive, organized farm layouts (7+2=9 for good luck!)</li>
<li><strong>14 Farm Types</strong> - Works across Latium, and Albion regions</li>
<li><strong>No Cheats</strong> - Only changes module limits, production and costs unchanged</li>
</ul>

<h3>🎯 AFFECTED FARMS</h3>

<ul>
<li>Barley Fields</li>
<li>Wheat Fields</li>
<li>Lavender Fields</li>
<li>Flax Plantations</li>
<li>Olive Plantations</li>
<li>Grape Plantations</li>
<li>Date Plantations</li>
<li>All other farm types</li>
</ul>

<h3>✨ WHY THIS MOD ROCKS</h3>

<ul>
<li>Create symmetrical, organized farm complexes</li>
<li>Maximize use of fertile land areas</li>
<li>Perfect for players who love planning efficient layouts</li>
<li>Save Compatible - Drop it in anytime</li>
<li>Mod Compatible - Clean ModOps, no conflicts</li>
<li>Not a cheat - just removes arbitrary module restrictions</li>
</ul>

<p>Just enable the mod and start building beautiful farm layouts 🌾</p>

```

**Tags:** farms, modules, quality-of-life, layout, organization, agriculture

**Maturity Rating:** Everyone

**File to Upload:** `super-fertility-v1.0.1.zip` (from GitHub Releases)

**Changelog:**
```
## [1.0.1] - 2025-12-20
- Updated release workflow for better mod.io compatibility
- Improved GitHub release automation

## [1.0.0] - 2024-11-22
- Initial release
- Increases module limit to 72 for all farm types (7+2=9!)
- Affects 14 different farm buildings across Latium and Albion
```

---

Made with ⚡ for the Anno community
