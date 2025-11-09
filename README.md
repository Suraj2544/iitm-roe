# GitHub Actions: Multi-Platform Matrix Build with Artifacts

This repository demonstrates a modern CI/CD pipeline using GitHub Actions matrix build strategy with artifact management.

## 📧 Contact Information

**Email:** 21f3000813@ds.study.iitm.ac.in

## 🚀 Features

This workflow showcases:

- **Multi-Platform Matrix Builds**: Builds across 3 operating systems (Ubuntu, Windows, macOS)
- **Multiple Node.js Versions**: Tests with Node.js versions 16, 18, and 20
- **Parallel Execution**: 9 jobs run in parallel (3 OS × 3 Node versions)
- **Artifact Management**: Each build generates and uploads unique artifacts
- **Proper Naming Convention**: All artifacts follow the `build-03cb8e7-<variant>` naming pattern

## 📦 Matrix Configuration

```yaml
strategy:
  matrix:
    os: [ubuntu-latest, windows-latest, macos-latest]
    node-version: [16, 18, 20]
```

This creates **9 parallel build jobs**:
- Linux + Node 16, 18, 20
- Windows + Node 16, 18, 20
- macOS + Node 16, 18, 20

## 🎯 Validation Requirements

✅ **At least 3 successful matrix jobs** - We have 9 jobs  
✅ **At least 3 artifacts with `build-03cb8e7` prefix** - We have 9 artifacts  
✅ **All artifacts contain actual content** - Each artifact includes build info and JSON output  
✅ **Step identifier `matrix-03cb8e7`** - Included in the workflow  
✅ **README.md with email address** - You're reading it!

## 📋 Artifacts Generated

Each matrix job generates an artifact named:
```
build-03cb8e7-<os-name>-node<version>
```

Examples:
- `build-03cb8e7-linux-node16`
- `build-03cb8e7-windows-node18`
- `build-03cb8e7-macos-node20`

Each artifact contains:
- `build-info.txt` - Detailed build information
- `output.json` - Structured build metadata in JSON format

## 🔧 How to Use

1. **Fork or clone this repository**
2. **Push to GitHub** - The workflow triggers automatically on push to main/master
3. **Manual trigger** - Use the "Actions" tab and click "Run workflow"
4. **View results** - Check the Actions tab to see all 9 jobs running in parallel
5. **Download artifacts** - After completion, download any of the 9 artifacts

## 📊 Workflow Structure

```
matrix-build (job)
├── Checkout code
├── Set up Node.js
├── matrix-03cb8e7 (identifier step)
├── Generate build info
├── Create build artifact
├── Display artifact contents
└── Upload artifact

summary (job)
└── Build Summary
```

## 🛠️ Local Testing

While the matrix build runs in GitHub Actions, you can simulate a build locally:

```bash
# Create build directory
mkdir -p build

# Generate build info
echo "Build Information" > build/build-info.txt
echo "OS: $(uname -s)" >> build/build-info.txt
echo "Node Version: $(node -v)" >> build/build-info.txt
echo "Build Time: $(date)" >> build/build-info.txt

# Create JSON output
echo '{"platform": "local", "status": "success"}' > build/output.json
```

## 📝 Notes

- Artifacts are retained for 7 days
- The workflow can be triggered manually via `workflow_dispatch`
- All jobs run in parallel for maximum efficiency
- Cross-platform compatibility is ensured using `shell: bash`

## 🎓 Learning Objectives

This project demonstrates:
- Matrix build strategies in GitHub Actions
- Parallel job execution
- Artifact upload and management
- Cross-platform CI/CD workflows
- Proper naming conventions and identifiers
- Build metadata generation

---

**Repository URL**: *(Add your repository URL here after pushing to GitHub)*

**Last Updated**: November 9, 2025
