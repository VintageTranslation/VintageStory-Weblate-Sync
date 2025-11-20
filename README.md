# Polish Translations Pack for Vintage Story

Community-maintained Polish translations for Vintage Story mods.

## Requirements

- .NET 10.0 SDK (or higher) - for build scripts
- .NET 8.0 SDK - for TranslationReloader.dll compilation
- `VINTAGE_STORY` environment variable pointing to game installation

```powershell
$env:VINTAGE_STORY = "C:\Program Files\Vintagestory"
```

## Building

```bash
# Test build (no history)
dotnet scripts\mods.cs build test-$(Get-Date -Format "yyyyMMdd-HHmmss") --no-history

# Release build
dotnet scripts\mods.cs build <version>

# Examples
dotnet scripts\mods.cs build 1.0.0
dotnet scripts\mods.cs build 1.2.0-pre.16
```

## How It Works

The pack includes `TranslationReloader.dll` which:
1. Uses `ExecuteOrder() = double.MaxValue` to run last
2. Moves translation pack Origin to end of Origins list via reflection
3. Reloads all translations - our files load last and override older versions

## Commands

### Update mods from ModDB
```bash
dotnet scripts\mods.cs update
```
Downloads and updates mod translation files from Vintage Story ModDB.

### Check translation status
```bash
dotnet scripts\mods.cs check
```
Checks completeness of translations for all mods.

### Build package
```bash
dotnet scripts\mods.cs build <version> [--no-history]
```

**Parameters:**
- `<version>` - Version string (e.g., `1.0.0`, `test-20251106`)
- `--no-history` - Skip saving to build history (optional, recommended for test builds)

**Examples:**
```bash
# Test build
dotnet scripts\mods.cs build test-$(Get-Date -Format "yyyyMMdd-HHmmss") --no-history

# Release build
dotnet scripts\mods.cs build 1.0.0
```




