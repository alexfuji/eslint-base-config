# @alexfuji/eslint-base-config

Base ESLint configuration for JavaScript/TypeScript projects using flat config (ESLint 9+).

## Setup & Installation

> **Note**: This package is published to GitHub Packages. Authentication required.

### First Time Setup (Fresh Checkout)

Since the project needs dependencies from GitHub Packages, you need authentication to install:

**Option 1: Using env-cmd**
```bash
# Install env-cmd globally (required for the install script)
npm install -g env-cmd

# Run the install script
npm run install:auth
```

**Option 2: Direct environment variable**
```bash
# Set the token and install in one command
GITHUB_TOKEN=your_github_token npm install
```

### Configuration

Create `.env` file in project root:
```bash
GITHUB_TOKEN=your_github_token
```

Add to `.npmrc`:
```bash
@alexfuji:registry=https://npm.pkg.github.com/
//npm.pkg.github.com/:_authToken=${GITHUB_TOKEN}
```

### Generating a GitHub Token

1. Go to: https://github.com/settings/tokens
2. Click **Generate new token (classic)**
3. Give the token a descriptive name (e.g., "GitHub Packages Read")
4. Select the following **scope**:
   - `read:packages` - Read packages from GitHub Packages
5. Click **Generate token**
6. Copy the token and use it in the commands above

For CI/CD, add `GITHUB_TOKEN` as a secret environment variable in your CI platform.

## Usage

In your project's `eslint.config.js`:

```javascript
import baseConfig from '@alexfuji/eslint-base-config';
import tseslint from 'typescript-eslint';

export default tseslint.config(
  ...baseConfig,
  {
    // Your project-specific overrides
    rules: {
      // Custom rules for your project
    },
  },
);
```

## What's Included

- `eslint:recommended` - ESLint recommended rules
- `typescript-eslint/recommended` - TypeScript-specific recommended rules
- Common overrides for unused variables (set to warn)
- Console rules disabled
- Common ignores: `dist/`, `node_modules/`, `coverage/`

## Requirements

- ESLint 9+
- Node.js 18+