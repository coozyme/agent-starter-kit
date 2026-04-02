---
description: Workflow for managing software releases
---

# Release Workflow

Steps for versioning, tagging, and publishing releases.

## Steps

### 1. Determine Version
Follow [Semantic Versioning](https://semver.org/): `MAJOR.MINOR.PATCH`

| Change Type | Version Bump | Example |
|-------------|-------------|---------|
| Breaking change | MAJOR | 1.0.0 → 2.0.0 |
| New feature (backward-compatible) | MINOR | 1.0.0 → 1.1.0 |
| Bug fix | PATCH | 1.0.0 → 1.0.1 |

### 2. Update Changelog
- Add all changes since the last release
- Categorize: Added, Changed, Deprecated, Removed, Fixed, Security
- Reference PRs/issues where applicable

### 3. Create Release Branch
```bash
git checkout -b release/v1.2.0
```

### 4. Final Verification
- Run full test suite
- Perform smoke tests on staging
- Review all changes included in the release
- Verify documentation is up-to-date

### 5. Bump Version
```bash
# Update version in package.json, setup.py, etc.
npm version 1.2.0  # Node.js
```

### 6. Tag and Merge
```bash
git tag -a v1.2.0 -m "Release v1.2.0"
git push origin v1.2.0
```

### 7. Deploy
- Follow the deployment workflow in `workflows/deployment.md`
- Deploy to production from the tagged release

### 8. Publish Release Notes
- Create a GitHub/GitLab release from the tag
- Include changelog content
- Highlight breaking changes prominently
- Thank contributors

### 9. Post-Release
- Monitor production for issues
- Announce the release to stakeholders
- Merge release branch back to develop
- Close the release milestone
