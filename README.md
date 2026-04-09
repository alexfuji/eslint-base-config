# @alexfuji/eslint-base-config

Base ESLint configuration for JavaScript/TypeScript projects using flat config (ESLint 9+).

## Installation

```bash
npm install @alexfuji/eslint-base-config
```

Or if using pnpm:

```bash
pnpm add @alexfuji/eslint-base-config
```

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