# Development Guide - Super Fertility

> **📚 Developer Documentation:** This is the comprehensive development guide. For user-facing information, see [README.md](README.md).

Complete technical documentation for modders and contributors who want to understand, modify, or extend this mod.

## Table of Contents
- [Quick Reference](#quick-reference)
- [Mod.io Packaging](#modio-packaging)
- [How It Works](#how-it-works)
- [Creating New Farm Buffs](#creating-new-farm-buffs)
- [Technical Reference](#technical-reference)

---

## Quick Reference

### Current Changes
- **Module Limit**: 72 modules per farm (only change this mod makes)

### File Structure
```
super-fertility/
├── data/
│   └── base/
│       └── config/
│           └── export/
│               └── assets.xml      # Farm modifications
├── modinfo.json                    # Mod metadata
├── README.md                       # User documentation
├── CONTRIBUTING.md                 # Contribution guide
├── DEVELOPMENT.md                  # This file
└── LICENSE                         # MIT License
```

## Installation
1. Locate your Anno 117 mods folder (typically `Documents/Anno 117 Pax Romana/mods/`)
2. Copy the entire `super-fertility` folder into the mods directory
3. Launch Anno 117: Pax Romana
4. Enable the mod in the in-game Mod Manager
5. Existing and new farms will automatically receive buffs

## Mod.io Packaging

### Quick Command
When ready to package for mod.io upload, run:
```bash
cd /path/to/super-fertility && zip -r super-fertility-v$(jq -r '.Version' modinfo.json).zip modinfo.json data/ README.md LICENSE -x "*.git*" "*.vscode*" "*plans/*" "*references/*" "*.txt" "*.md" "farms/*"
```

### Versioning Structure
Follow semantic versioning (MAJOR.MINOR.PATCH):

- **MAJOR** (1.x.x): Breaking changes, incompatible with saves, major rework
- **MINOR** (x.1.x): New farm types, new features, backward compatible
- **PATCH** (x.x.1): Bug fixes, balance tweaks, value corrections

**Examples:**
- `1.0.0` → `1.1.0`: Added new plantation types
- `1.1.0` → `1.1.1`: Fixed incorrect production value
- `1.1.1` → `2.0.0`: Completely reworked all farm mechanics (breaking)

**Before packaging:**
1. Update `Version` in `modinfo.json`
2. Add entry to "Changelog" section in README.md
3. Test in-game with updated version
4. Run packaging command
5. Upload to mod.io and GitHub

**What gets packaged:**
- ✅ `modinfo.json` (mod metadata)
- ✅ `data/` (all mod files)
- ✅ `README.md` (documentation)
- ✅ `LICENSE` (MIT license)

**What gets excluded:**
- ❌ `.git/`, `.github/`, `.vscode/` (dev files)
- ❌ `plans/`, `references/` (internal docs)
- ❌ `*.txt` files (old info files)
- ❌ `farms/` (reference XMLs)
- ❌ `*.zip` files (previous builds)

## How It Works

### ModOps Approach

This mod uses `Type="merge"` ModOps to cleanly modify farm module limits without replacing entire structures:

```xml
<ModOp GUID="2799" Type="merge" Path="/Values/ModuleOwner/ModuleLimits/Main">
  <Limit>72</Limit>
</ModOp>
```

### Why Merge Operations?

**Advantages:**
- ✅ Preserves original asset structure
- ✅ Reduces mod file size
- ✅ Better compatibility with other mods
- ✅ Easier to maintain and update
- ✅ Changes only what's needed

**Compared to Replace:**
- ❌ Replace requires copying entire asset XML
- ❌ Replace can conflict with other mods easily
- ❌ Replace makes updates harder

### Affected Farm GUIDs

This mod targets 14 individual farm buildings by GUID:

| GUID | Farm Type | Region |
|------|-----------|--------|
| **2799** | Barley Field | Latium |
| **2698** | Wheat Field | Latium |
| **2693** | Lavender Field | Latium |
| **2699** | Flax Plantation | Latium |
| **5972** | Olive Plantation | Latium |
| **2669** | Grape Plantation | Latium |
| **5971** | Date Plantation | Albion |
| **31762** | Farm | Albion |
| **31750** | Farm | Albion |
| **2200** | Farm | Arabia |
| **2800** | Farm | General |
| **23723** | Plantation | General |
| **2694** | Additional Farm | Various |
| **5849** | Additional Farm | Various |

## Creating New Farm Buffs

### Step-by-Step Guide

#### Step 1: Identify Target Farm

Find the farm's GUID or asset pool:
- Check game's `assets.xml` file
- Use modding tools like Anno Mod Manager
- Reference existing mod XMLs

#### Step 2: Add ModOp to assets.xml

Template for modifying module limits:

```xml
<ModOp GUID="YOUR_FARM_GUID" Type="merge" Path="/Values/ModuleOwner/ModuleLimits/Main">
  <Limit>72</Limit>
</ModOp>
```

#### Step 3: Test In-Game

1. Load Anno 117 with mod enabled
2. Build or view existing farms
3. Verify production/maintenance/module changes
4. Check for errors in mod loader

#### Step 4: Document Changes

Update README.md with:
- Farm type added
- Buff values applied
- Any special notes

### Module Limit Property

```xml
<!-- Module Limits -->
<ModOp GUID="FARM_GUID" Type="merge" Path="/Values/ModuleOwner/ModuleLimits/Main">
  <Limit>72</Limit>                                      <!-- Max modules -->
</ModOp>
```

**Note:** This mod only modifies module limits. To change production, costs, or other properties, you would need to target different paths in the asset structure.

### Example: Adding Another Farm Type

```xml
<ModOps>
  <!-- Another Farm: 72 module limit -->
  <ModOp GUID="12345" Type="merge" Path="/Values/ModuleOwner/ModuleLimits/Main">
    <Limit>72</Limit>
  </ModOp>
</ModOps>
```

## Technical Reference

### ModOp Types

| Type | Use Case | Example |
|------|----------|---------|
| **merge** | Add/update properties | Buff production without changing structure |
| **add** | Insert new elements | Add new farm types |
| **remove** | Delete elements | Remove restrictions |
| **replace** | Overwrite entirely | Complete asset rebuild |

### XML Path Reference

Common paths for farm modifications:

```xml
/Values/Standard                    <!-- Basic properties -->
/Values/Standard/ProductionMultiplier
/Values/Standard/MaintenanceMultiplier
/Values/Standard/ModuleLimit

/Values/Production                  <!-- Production-specific -->
/Values/Production/OutputRate
/Values/Production/CycleTime

/Values/Cost                        <!-- Cost-related -->
/Values/Cost/Construction
/Values/Cost/Maintenance
```

### Testing Best Practices

1. **Start Simple**: Test one farm type first
2. **Incremental Changes**: Add buffs one at a time
3. **Verify Each Change**: Check in-game after each edit
4. **Check Logs**: Review Anno 117 mod loader logs
5. **Test Compatibility**: Try with other popular mods

### Common Issues & Solutions

| Issue | Cause | Solution |
|-------|-------|----------|
| Buffs not applying | Wrong GUID | Verify GUID in game files |
| Mod not loading | XML syntax error | Check XML formatting |
| Conflicts with other mods | Same GUID modified | Use merge instead of replace |
| Game crashes | Invalid property value | Check property types/ranges |

### Debugging Tips

1. **Enable Mod Logs**: Check Anno 117 mod loader output
2. **Test Vanilla First**: Disable other mods to isolate issues
3. **Validate XML**: Use XML validator to check syntax
4. **Compare Working Mods**: Reference successful farm mods

## Advanced Topics

### Conditional Buffs

Add buffs based on conditions:

```xml
<ModOp Type="merge" GUID="FARM_GUID" Path="/Values/Standard">
  <ProductionMultiplier>
    <BaseValue>2</BaseValue>
    <Conditions>
      <Condition>
        <Type>Season</Type>
        <Value>Summer</Value>
        <Multiplier>1.5</Multiplier>
      </Condition>
    </Conditions>
  </ProductionMultiplier>
</ModOp>
```

### Farm Module Modifications

Modify individual modules:

```xml
<ModOp Type="merge" GUID="MODULE_GUID" Path="/Values/Module">
  <EffectRadius>15</EffectRadius>
  <ProductionBonus>50</ProductionBonus>
</ModOp>
```

### Multiple Farm Types

Target multiple farms with one ModOp:

```xml
<ModOps>
  <!-- Apply same buffs to multiple farms -->
  <ModOp Type="merge" GUID="100001,100002,100003" Path="/Values/Standard">
    <ProductionMultiplier>2</ProductionMultiplier>
    <MaintenanceMultiplier>0.5</MaintenanceMultiplier>
    <ModuleLimit>60</ModuleLimit>
  </ModOp>
</ModOps>
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for full guidelines.

### Quick Contribution Checklist

- [ ] Fork repository
- [ ] Create feature branch
- [ ] Make changes to `assets.xml`
- [ ] Test in-game
- [ ] Update documentation
- [ ] Commit with clear message
- [ ] Open Pull Request

## Resources

- **Anno Modding Guide**: [GitHub](https://github.com/anno-mods/modding-guide)
- **Anno Discord**: [discord.anno-mods.dev](https://discord.anno-mods.dev)
- **Mod.io**: [Anno 117 Mods](https://mod.io/g/anno-117-pax-romana)

## Version History

### [1.0.0] - 2024-11-22
- Initial release
- Increases module limit to 72 for 14 farm types (7+2=9!)
- Supports: Latium, Albion, and Arabia regions

---

## Lessons Learned from Development

### Path Traversal is Critical

The most important lesson: **correct XPath-like paths are essential** for ModOps to work.

**Example of correct path:**
```xml
<ModOp Type="merge" GUID="100001" Path="/Values/Standard">
```

**Common mistakes:**
- ❌ Wrong path: `/Values/Production` (when property is in `/Values/Standard`)
- ❌ Missing slash: `Values/Standard` (must start with `/`)
- ❌ Wrong GUID: Asset doesn't exist or is different type

**How to verify paths:**
1. Open game's `assets.xml`
2. Find your target asset by GUID
3. Trace the exact XML path to the property
4. Copy path structure exactly

### Merge vs Replace Philosophy

We chose `merge` over `replace` because:
- Keeps original asset intact
- Only changes what we need
- Better mod compatibility
- Easier to understand and maintain
- Reduces risk of breaking changes

### Testing Workflow

1. Make one change at a time
2. Load game and verify
3. Check mod logs for errors
4. Document what works
5. Iterate based on results

This iterative approach prevented hours of debugging from making too many changes at once.

---

Made with ⚡ for the Anno modding community
