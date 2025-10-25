[Bits-and-Bristles](https://bits-and-bristles.netlify.app) is built with Hugo.

## Development

### Prerequisites

- [Hugo](https://gohugo.io)
- Git

### Setup

Follow instructions to setup [Hugo](https://gohugo.io/getting-started/quick-start/)

#### Clone Repository with Submodules

```bash
git clone --recursive https://github.com/kranthilakum/bits-and-bristles.git
cd bits-and-bristles
```

If you already cloned without `--recursive`, initialize the submodule:

```bash
git submodule update --init --recursive
```

### Run

Start Hugo's development server to see your changes live.

```bash
hugo server -D
```

## Theme Management

This repository uses a **forked submodule** approach for the Hugo Paper theme to maintain custom modifications while keeping the ability to receive upstream updates.

### Theme Submodule Information

- **Original Theme**: [hugo-paper](https://github.com/nanxiaobei/hugo-paper) by nanxiaobei
- **Fork**: [kranthilakum/hugo-paper](https://github.com/kranthilakum/hugo-paper)
- **Local Path**: `themes/paper`

### Custom Modifications

The forked theme includes the following customizations:
- Custom archive layout (`layouts/archive/list.html`) with reduced spacing and no link underlines
- Any future custom modifications will be documented here

### Managing the Forked Submodule

#### Making Changes to the Theme

1. **Make changes in the submodule directory**:
   ```bash
   cd themes/paper
   # Make your changes to theme files
   ```

2. **Commit changes to your fork**:
   ```bash
   cd themes/paper
   git add .
   git commit -m "Description of your theme changes"
   git push origin main
   ```

3. **Update the main repository to reference the new commit**:
   ```bash
   cd ../..  # Back to main repository root
   git add themes/paper
   git commit -m "Update theme submodule with custom changes"
   git push origin main
   ```

#### Updating from Upstream (Original Theme)

To get updates from the original hugo-paper theme:

1. **Add upstream remote** (one-time setup):
   ```bash
   cd themes/paper
   git remote add upstream https://github.com/nanxiaobei/hugo-paper.git
   ```

2. **Fetch and merge upstream changes**:
   ```bash
   cd themes/paper
   git fetch upstream
   git checkout main
   git merge upstream/main
   # Resolve any conflicts if they occur
   git push origin main
   ```

3. **Update main repository**:
   ```bash
   cd ../..
   git add themes/paper
   git commit -m "Update theme submodule with upstream changes"
   git push origin main
   ```

#### Troubleshooting Submodules

**If submodule appears empty or outdated**:
```bash
git submodule update --init --recursive --force
```

**Reset submodule to match .gitmodules**:
```bash
git submodule sync
git submodule update --init --recursive
```

**Check submodule status**:
```bash
git submodule status
```

**View submodule configuration**:
```bash
cat .gitmodules
```

### Development Workflow

1. Clone repository with submodules
2. Make changes to content in `content/` directory
3. If theme changes are needed:
   - Modify files in `themes/paper/`
   - Commit and push theme changes to fork
   - Update main repository to reference new theme commit
4. Test with `hugo server -D`
5. Deploy changes

### Note on Theme Updates

Since we're using a fork, we maintain full control over theme modifications while still being able to pull updates from the original theme. This approach ensures:

- ✅ Custom modifications are preserved
- ✅ Version control for theme changes
- ✅ Ability to receive upstream updates
- ✅ Easy collaboration on theme customizations
- ✅ Rollback capability if issues arise
