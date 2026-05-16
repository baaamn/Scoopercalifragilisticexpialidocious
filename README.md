# Scoopercalifragilisticexpialidocious 🎭

An extraordinarily wonderful and no nonsense super duper scoop bucket that is atoning for being educable through delicate beauty.

[![CI](https://github.com/baaamn/Scoopercalifragilisticexpialidocious/actions/workflows/ci.yml/badge.svg)](https://github.com/baaamn/Scoopercalifragilisticexpialidocious/actions/workflows/ci.yml) [![Excavator](https://github.com/baaamn/Scoopercalifragilisticexpialidocious/actions/workflows/excavator.yml/badge.svg)](https://github.com/baaamn/Scoopercalifragilisticexpialidocious/actions/workflows/excavator.yml)

**Status:** ✅ Indexed on scoop.sh | 🏷️ [scoop-bucket](https://scoop.sh) topic | 🔧 Auto-PR enabled

---

## 🚀 Quick Start

Add this bucket to your Scoop installation:

```pwsh
scoop bucket add Scooper https://github.com/baaamn/Scoopercalifragilisticexpialidocious

# View available packages
scoop search Scooper

# Install a package
scoop install Scooper/<package-name>

# Update all packages from this bucket
scoop update Scooper
```

---

## 📦 Available Packages

| Package | Description | License |
|---------|-------------|---------|
| **AnyTXT** | Local document search application | Freeware |
| **Directory Opus** | Advanced file manager (replacement for Explorer) | Proprietary |
| **Everything (Alpha)** | Instant file/folder search by name | MIT |
| **IDM** | Internet Download Manager - 5x faster downloads | Proprietary |
| **Notepad++** | Text and source code editor | GPL-2.0 |
| **Notepad++ Portable** | Portable version of Notepad++ | GPL-2.0 |
| **PromptExt** | Prompt extension utility | Open Source |

*Run `scoop search Scooper` to see full details of all available packages.*

---

## 📋 How to Install These Manifests

After this bucket is added, install packages using:

```pwsh
scoop install Scooper/<package-name>
```

**Example:**
```pwsh
scoop install Scooper/everything-alpha
scoop install Scooper/directory-opus
scoop install Scooper/notepadplusplus-np
```

---

## 🛠️ Maintenance & Quality

All packages in this bucket are:

- ✅ **Validated** - Manifests are auto-tested via GitHub Actions CI
- 🔄 **Auto-updated** - Excavator tool keeps manifests in sync with upstream releases
- 📝 **Well-documented** - Each manifest includes version detection and auto-update rules
- 🔍 **Verified** - Download URLs and checksums are validated on every commit

---

## 🤝 Contributing

Want to add a new package or fix an existing one? See [CONTRIBUTING.md](./CONTRIBUTING.md) for:

- Step-by-step guide to creating new manifests
- Manifest structure and required fields
- Testing and validation procedures
- Best practices for naming, versioning, and licensing
- Common patterns and examples

**Quick summary:**
1. Copy `bucket/app-name.json.template` to `bucket/<your-app-name>.json`
2. Fill in the manifest with app details
3. Test locally with `scoop install .\bucket\<your-app-name>.json`
4. Submit a pull request

---

## 📚 Resources

- **Scoop Documentation:** https://scoop.sh
- **App Manifest Guide:** https://github.com/ScoopInstaller/Scoop/wiki/App-Manifests
- **Scoop Contributing Guide:** https://github.com/ScoopInstaller/.github/blob/main/.github/CONTRIBUTING.md
- **SPDX License List:** https://spdx.org/licenses/

---

## 📝 License

This bucket is released under the [Unlicense](LICENSE) - do what you want with it.

Individual packages retain their respective licenses as specified in their manifests.

---

**Made with 🎭 dedication to education, delicate beauty, and no nonsense.**
