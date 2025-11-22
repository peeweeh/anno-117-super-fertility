# Contributing to Super Fertility

Thank you for your interest in contributing! This mod is open for community contributions.

## 🚀 Quick Start

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-farm-buff`)
3. Make your changes
4. Test in-game
5. Commit with clear messages (`git commit -m 'Add olive plantation buffs'`)
6. Push to your fork (`git push origin feature/new-farm-buff`)
7. Open a Pull Request

## 📋 Contribution Guidelines

### Modifying Farm Properties

Each farm modification requires:
- **Farm GUID** from the game's asset pool
- **XML ModOps** in `data/base/config/export/assets.xml`
- **Testing** to ensure changes work as expected

### Code Standards

- Use clear, descriptive comments
- Follow existing XML formatting
- Add XML comments for complex sections
- Test all changes in-game before submitting

### Farm GUID Management

Common farm asset pools:
- **100001** - Barley Fields
- **100002** - Wheat Fields
- **100003** - Lavender Fields
- **100004** - Plantations (general)

Individual farm GUIDs can be found by examining game files or using modding tools.

### Commit Messages

Use conventional commits format:

```
feat: add grape plantation buffs
fix: correct production multiplier calculation
docs: update farm list in README
refactor: reorganize assets.xml structure
```

### Testing Checklist

Before submitting a PR:

- [ ] Mod loads without errors
- [ ] Farms display correct production values
- [ ] Module limits work as expected
- [ ] Maintenance costs calculate correctly
- [ ] Compatible with existing saves
- [ ] No conflicts with base game mechanics

## 🐛 Reporting Issues

When reporting bugs, include:

- Anno 117 version
- Mod version
- Steps to reproduce
- Expected vs actual behavior
- Screenshots if applicable
- Other active mods

## 💡 Suggesting Features

Feature requests are welcome! Please:

- Check existing issues first
- Describe the feature clearly
- Explain the use case
- Consider balance implications

## 📚 Resources

- [Modding Guide](https://github.com/anno-mods/modding-guide)
- [Anno Discord](https://discord.anno-mods.dev)
- [DEVELOPMENT.md](DEVELOPMENT.md) - Technical documentation

## 🤔 Questions?

Open a [Discussion](https://github.com/peeweeh/anno-117-super-fertility/discussions) or ask in the Anno Discord.

---

By contributing, you agree that your contributions will be licensed under the MIT License.
