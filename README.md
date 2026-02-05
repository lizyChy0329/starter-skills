# vite-lib-vue-pnpm-starter-skill

Quickly scaffold a Vite + Vue 3 component library starter template (pnpm workspace + TypeScript).

## Purpose

Initialize a Vue 3 component library project with:

- Vue 3 + TypeScript support
- Vite build tool
- pnpm workspace for monorepo management
- Built-in playground for local testing
- Automatic TypeScript declaration generation

## Usage

```bash
npx skills add git@github.com:lizyChy0329/starter-skills.git --skill vite-lib-vue-pnpm-starter-skill
```

## Generated Project Structure

```
project-root/
├── package.json          # Main library config with workspace and build scripts
├── pnpm-workspace.yaml   # pnpm workspace configuration
├── vite.config.ts        # Library build config (Vue as external)
├── tsconfig.json         # TypeScript project references config
├── index.ts              # Library entry point
├── src/
│   ├── index.ts          # Component exports
│   ├── components/
│   │   ├── index.ts      # Unified component exports
│   │   └── Counter.vue   # Example component
│   └── style.css
├── playground/           # Local testing environment
│   ├── package.json      # Uses workspace:* to reference main library
│   ├── vite.config.ts
│   └── src/
│       ├── main.ts
│       └── App.vue
└── dist/                 # Build output (ES/UMD/type declarations)
```

## Workflow

### 1. Install Dependencies

```bash
pnpm install
```

### 2. Build Library

```bash
pnpm build
```

Output:
- `dist/index.es.js` - ES module
- `dist/index.umd.js` - UMD module
- `dist/index.d.ts` - Type declarations

### 3. Start Playground for Testing

```bash
cd playground && pnpm dev
```

## Key Configurations

### vite.config.ts

```typescript
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'
import dts from 'vite-plugin-dts'

export default defineConfig({
  plugins: [vue(), dts()],
  build: {
    lib: {
      entry: './index.ts',
      formats: ['es', 'umd'],
      name: 'MyLib',
      fileName: 'index',
    },
    rollupOptions: {
      external: ['vue'], // Vue not bundled into library
      output: {
        globals: { vue: 'Vue' },
      },
    },
  },
})
```

### package.json

```json
{
  "type": "module",
  "main": "./dist/index.umd.js",
  "module": "./dist/index.es.js",
  "types": "./dist/index.d.ts",
  "files": ["dist"]
}
```

### Playground References Main Library

```json
{
  "dependencies": {
    "my-lib": "workspace:*"
  }
}
```

## When to Use

- Creating a Vue 3 component library
- Using pnpm for dependency management
- Need monorepo structure for library and testing environment
- Require TypeScript type support

## Limitations

- **pnpm only** (no npm/yarn support)
- **Vue 3 only** (no Vue 2 support)
- **Vue as external dependency** (consuming projects must install Vue separately)
- **Direct file generation** (does not use Vite official init commands)
