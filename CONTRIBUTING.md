# Contributing to Scoopercalifragilisticexpialidocious

Thank you for your interest in contributing to this Scoop bucket! This guide explains how to set up the repository, create new package manifests, and contribute updates.

---

## 🔧 Maintainer Setup

If you're setting up this bucket on a new machine or as a collaborator, follow these steps:

### 1. Enable GitHub Actions

Navigate to your repository settings:

- **Settings** → **Actions** → **General** → **Actions permissions**
  - Select: `Allow all actions and reusable workflows`
  - Click: **Save**

- **Settings** → **Actions** → **General** → **Workflow permissions**
  - Select: `Read and write permissions`
  - Click: **Save**

### 2. Update auto-pr.ps1

The `bin/auto-pr.ps1` script contains the repository reference for auto-pull-request generation:

```powershell
param(
    # overwrite upstream param
    [String]$upstream = "baaamn/Scoopercalifragilisticexpialidocious:master"
)
```

Ensure `$upstream` matches your repository's owner, name, and default branch.

### 3. Verify Workflows

Check that these workflows are present and enabled:

- `.github/workflows/ci.yml` - Manifest validation
- `.github/workflows/excavator.yml` - Auto-PR for upstream updates
- `.github/workflows/issues.yml` - Issue labeling
- `.github/workflows/issue_comment.yml` - Comment automation
- `.github/workflows/pull_request.yml` - PR automation

---

## 📦 Creating New Package Manifests

### Quick Start

1. **Copy the template:**
   ```powershell
   Copy-Item bucket/app-name.json.template bucket/<your-app-name>.json
   ```

2. **Edit the manifest:**
   - Replace placeholder values with actual app information
   - See the [Manifest Structure](#manifest-structure) section below

3. **Validate locally** (if you have Scoop installed):
   ```powershell
   scoop search .\bucket\<your-app-name>.json
   ```

4. **Commit and push:**
   ```powershell
   git add bucket/<your-app-name>.json
   git commit -m "Add <app-name> manifest"
   git push
   ```

---

## 📋 Manifest Structure

All manifests should follow the Scoop App Manifest format. Key fields:

```json
{
    "version": "1.0.0",                          // Application version
    "description": "App description",            // Short description
    "homepage": "https://example.com",          // Official website
    "license": "MIT",                           // License type
    "url": "https://download.url/app.exe",      // Download URL
    "hash": "sha256:...",                       // File checksum
    "installer": { ... },                       // Custom installer config (if needed)
    "uninstaller": { ... },                     // Custom uninstaller config (if needed)
    "bin": "app.exe",                           // Binary/executable name(s)
    "shortcuts": [["app.exe", "App Name"]],     // Desktop shortcuts
    "checkver": { ... },                        // Version detection rules
    "autoupdate": { ... }                       // Auto-update URL patterns
}
```

### Important Fields

- **`version`**: Must match the actual application version
- **`hash`**: Use SHA-256 (SHA-1 is deprecated). Calculate with:
  ```powershell
  # PowerShell
  Get-FileHash -Path "app.exe" -Algorithm SHA256 | Select-Object Hash
  ```
- **`checkver`**: Tells Scoop how to find the latest version (regex, GitHub releases, etc.)
- **`autoupdate`**: Rules for automatically updating `url` and `hash` during version bumps

---

## 🧪 Validation & Testing

### Automated CI/CD

Every pull request runs automatic validation:

1. **Manifest Syntax** - JSON parsing
2. **Schema Validation** - Required fields and types
3. **URL Health Check** - Downloads are accessible
4. **Hash Verification** - Checksums are correct

### Manual Testing

Before submitting a PR, test locally:

```powershell
# Install from your local manifest
scoop install .\bucket\<app-name>.json

# Test the installed app
<app-name>

# Verify shortcuts work
# Uninstall to clean up
scoop uninstall <app-name>
```

---

## 📝 Best Practices

### Manifest Naming

- Use lowercase with hyphens: `app-name.json` (not `AppName.json`)
- Keep names short and recognizable
- Avoid generic names; include version suffix if needed (e.g., `python39.json`)

### Version Format

- Follow the app's actual versioning scheme (e.g., `8.9.5`, `642build63`)
- Don't invent or modify versions
- Include pre-release tags if the app uses them (e.g., `1.5.0.1237a`)

### Descriptions

- One-line description only (fits in `scoop search` output)
- Avoid marketing hype; be factual
- Example: ✅ "Local document search application" vs ❌ "The BEST document searcher ever!"

### Downloads

- Prefer official sources (project GitHub, vendor homepage)
- Use direct download links (avoid redirects when possible)
- Always verify URLs are stable and long-term accessible
- Test downloads before committing

### Licensing

- Accurate license field (see [SPDX identifiers](https://spdx.org/licenses/))
- Include `"notes"` field if there are licensing caveats
- Example: `"license": "Proprietary"` with a note for commercial software

---

## 🔍 Common Manifest Patterns

### Portable ZIP Archives

```json
{
    "url": "https://example.com/app-1.0.zip",
    "hash": "sha256:...",
    "bin": "app.exe"
}
```

### Installer EXE with Arguments

```json
{
    "url": "https://example.com/app-setup.exe",
    "hash": "sha256:...",
    "installer": {
        "args": ["/S", "/D=$dir"]
    },
    "uninstaller": {
        "file": "uninstall.exe",
        "args": "/S"
    }
}
```

### Multiple Architectures

```json
{
    "architecture": {
        "64bit": {
            "url": "https://example.com/app-x64.zip",
            "hash": "sha256:..."
        },
        "32bit": {
            "url": "https://example.com/app-x86.zip",
            "hash": "sha256:..."
        }
    }
}
```

### Auto-Update from GitHub Releases

```json
{
    "checkver": {
        "github": "https://github.com/user/project"
    },
    "autoupdate": {
        "url": "https://github.com/user/project/releases/download/v$version/app-$version.zip"
    }
}
```

---

## 🚀 Submitting Your Contribution

1. **Fork and clone** this repository
2. **Create a feature branch:** `git checkout -b add-app-name`
3. **Add your manifest(s)** to `bucket/`
4. **Test locally** (see Validation & Testing)
5. **Commit with clear message:**
   ```powershell
   git commit -m "Add app-name manifest - v1.0.0"
   ```
6. **Push and open a PR** with a description of the package(s)

### PR Template

Please include in your PR description:

- **App Name:** What is the application?
- **Why:** Why should it be in this bucket?
- **Testing:** Confirm you tested installation/uninstall
- **Links:** Homepage, download page, documentation

---

## ❓ Questions or Issues?

- **Ask questions:** Open a GitHub Discussion
- **Report bugs:** Use GitHub Issues with a clear description
- **Check existing:** Search issues/discussions to avoid duplicates

---

## 📚 Additional Resources

- **Scoop Bucket Documentation:** https://scoop.sh
- **App Manifest Guide:** https://github.com/ScoopInstaller/Scoop/wiki/App-Manifests
- **Scoop Contributing Guide:** https://github.com/ScoopInstaller/.github/blob/main/.github/CONTRIBUTING.md
- **Excavator Tool:** https://github.com/ScoopInstaller/Excavator (for auto-updating manifests)

---

**Thank you for contributing to Scoopercalifragilisticexpialidocious! 🎭**
