# Vite Lib Vue 3 PNPM Starter

## What is this library?

This is a minimal Vite + Vue 3 library starter template that uses pnpm workspace for dependency management. It provides a ready-to-use structure for creating Vue 3 component libraries with TypeScript support, designed to streamline the bootstrap process for library developers.

## What is it used for?

This starter template is designed to help developers quickly set up a Vue 3 component library with the following capabilities:

- Create a structured Vue 3 component library with TypeScript support
- Use Vite as the build tool for optimized development and production builds
- Implement a monorepo structure using pnpm workspace
- Generate TypeScript type declarations automatically
- Provide a playground environment for local testing and development
- Follow best practices for library development (e.g., externalizing Vue dependency)

## When to use this library

This starter is suitable for:

- **Creating a new Vue 3 component library** that needs TypeScript support
- **Developers preferring pnpm** as their package manager
- **Projects requiring a monorepo structure** for better dependency management
- **Teams needing a consistent library bootstrap process** with minimal configuration
- **Libraries that need a playground** for testing components during development
- **Projects targeting modern browsers** with ES modules support
- **Developers who want to avoid Vite's official initialization** and prefer direct file generation

## When NOT to use this library

This starter is NOT suitable for:

- **Projects using npm or yarn** as the package manager (pnpm only)
- **Vue 2 projects** (this is specifically designed for Vue 3)
- **Projects not requiring TypeScript** (TypeScript is integrated by default)
- **Applications that don't need a library structure** (use a regular Vue 3 app template instead)
- **Projects needing complex build configurations** (this uses a minimal configuration approach)
- **Libraries that need to bundle Vue** (Vue is configured as an external dependency)
- **Teams unfamiliar with pnpm workspaces** (requires knowledge of pnpm's workspace functionality)

## Core Features

- Direct file generation without manual intervention
- pnpm workspace for monorepo structure management
- Vue 3 + TypeScript support
- Minimal configuration approach
- Built-in playground for testing
- TypeScript declaration generation
- Optimized build process

## Project Structure

```
project-root/
├── .gitignore
├── index.ts
├── package.json
├── pnpm-workspace.yaml
├── tsconfig.json
├── tsconfig.app.json
├── tsconfig.node.json
├── vite.config.ts
├── src/
│   ├── index.ts
│   ├── components/
│   │   ├── index.ts
│   │   └── Counter.vue
│   └── style.css
├── playground/
│   ├── .gitignore
│   ├── index.html
│   ├── package.json
│   ├── tsconfig.json
│   ├── tsconfig.app.json
│   ├── tsconfig.node.json
│   ├── vite.config.ts
│   ├── public/
│   └── src/
│       ├── main.ts
│       ├── App.vue
│       ├── style.css
│       └── assets/
└── dist/ (generated after build)
```

## Getting Started

### 1. Install Dependencies

```bash
pnpm install
```

### 2. Build the Library

```bash
pnpm build
```

### 3. Run the Playground

```bash
cd playground && pnpm dev
```

## Key Configuration Details

- **Vue as External Dependency**: Vue is not bundled into the library to avoid version conflicts
- **TypeScript References**: Uses project references for faster compilation
- **pnpm Workspace**: Enables monorepo structure with local library reference
- **Minimal Configuration**: Focused settings for library development
- **Type Checking**: `vue-tsc` runs before build to ensure type safety

## Important Notes

- **pnpm Only**: This project is configured exclusively for pnpm
- **No Vite Official Commands**: Uses direct file generation instead
- **Workspace Dependency**: Playground uses `workspace:*` to reference the latest library code
- **External Vue**: Applications using this library must provide their own Vue instance

## Troubleshooting

### Why pnpm instead of npm?
Faster installation, stricter dependency management, and better monorepo support.

### Why separate package.json for playground?
Isolated environment with its own dependencies, referencing the main library via workspace.

### Why externalize Vue in build?
Avoids duplicate bundling and version conflicts, follows library best practices.

### Why use TypeScript References?
Enables independent compilation of subprojects for faster builds and more accurate type checking.