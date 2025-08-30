# Branch Protection Setup Guide

This document outlines the manual repository settings that need to be configured to protect the main branch.

## Required GitHub Repository Settings

To properly protect the main branch, the repository administrator needs to configure the following settings in the GitHub repository:

### 1. Branch Protection Rules for `main`

Navigate to: **Settings** > **Branches** > **Add rule**

Configure the following settings:

#### Required Settings:
- **Branch name pattern**: `main`
- **Require a pull request before merging**: ✅ Enabled
  - **Require approvals**: ✅ Enabled (minimum 1 approval)
  - **Dismiss stale PR approvals when new commits are pushed**: ✅ Enabled
  - **Require review from code owners**: ✅ Enabled
- **Restrict pushes that create files**: ✅ Enabled
- **Do not allow bypassing the above settings**: ✅ Enabled

#### Additional Recommended Settings:
- **Require branches to be up to date before merging**: ✅ Enabled
- **Include administrators**: ✅ Enabled (applies rules to repository admins too)

### 2. CODEOWNERS File

The `.github/CODEOWNERS` file has been created to ensure that:
- All changes require approval from `@MatejSkultety`
- Critical files (README.md, LICENSE, .github/) have explicit owner protection

### 3. Repository Access

Ensure that:
- Only trusted collaborators have write access to the repository
- All contributors use the fork-and-pull-request workflow for contributions

## Workflow Summary

With these settings in place:

1. **Direct pushes to main**: ❌ Blocked
2. **All changes via PR**: ✅ Required
3. **Code review required**: ✅ Required (minimum 1 approval)
4. **Owner approval**: ✅ Required (via CODEOWNERS)
5. **Stale approvals dismissed**: ✅ Automatic on new commits

## Verification

After configuring these settings:

1. Try to push directly to main (should fail)
2. Create a test PR and verify that it requires approval
3. Verify that the PR cannot be merged without review

## Implementation Status

- ✅ CODEOWNERS file created
- ⏳ Manual repository settings (requires admin access)
- ⏳ Testing and verification

---

**Note**: These repository protection settings can only be configured by users with admin access to the repository through the GitHub web interface.