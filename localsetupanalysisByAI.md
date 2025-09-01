● shadcn/ui Local Development Setup Guide

  Based on my exploration of this repository, here's a
  comprehensive guide to run the shadcn/ui project
  locally:

  Prerequisites

  - Node.js: Version 18+ recommended
  - pnpm: Version 9.0.6+ (specified as package manager)       
  - Git: For version control

  Repository Structure

  This is a monorepo with the following key components:       

  - apps/v4/ - Main documentation site (Next.js, runs on      
  port 4000)
  - apps/www/ - Legacy documentation site (runs on port       
  3333)
  - packages/shadcn/ - CLI tool for adding components
  - packages/tests/ - Test utilities

  Quick Start

  1. Clone and Install

  git clone <your-repo-url>
  cd shadcn-ui
  pnpm install

  2. Run Development Servers

  Option A: Run all development servers (recommended)
  pnpm dev

  Option B: Run specific components

  For the main v4 site:
  pnpm v4:dev
  # Runs on http://localhost:4000

  For the legacy www site:
  pnpm www:dev
  # Runs on http://localhost:3333

  For the CLI development:
  pnpm shadcn:dev

  3. Environment Setup (Optional)

  Copy environment files if needed:
  # For v4 app
  cp apps/v4/.env.example apps/v4/.env.local

  # For www app
  cp apps/www/.env.example apps/www/.env.local

  Development Workflows

  Working with Components

  1. Start the registry server:
  pnpm v4:dev
  2. Build registry (after component changes):
  pnpm build:registry

  CLI Development

  1. Start registry:
  pnpm v4:dev
  2. Run CLI in development:
  pnpm shadcn:dev
  3. Test CLI locally:
  pnpm shadcn
  # Or test in a specific directory:
  pnpm shadcn init -c ~/path/to/your-app

  Testing

  # Run all tests
  pnpm test

  # Run CLI tests specifically
  pnpm --filter=shadcn test

  # Run tests in development mode
  pnpm test:dev

  Build Commands

  # Build everything
  pnpm build

  # Build specific apps
  pnpm v4:build
  pnpm www:build
  pnpm shadcn:build

  # Build and check code quality
  pnpm check  # Runs lint, typecheck, and format:check        

  Code Quality

  # Linting
  pnpm lint
  pnpm lint:fix

  # Type checking
  pnpm typecheck

  # Formatting
  pnpm format:check
  pnpm format:write

  Key URLs

  - Main v4 site: http://localhost:4000
  - Legacy www site: http://localhost:3333
  - Official documentation: https://ui.shadcn.com/docs        

  Common Issues & Notes

  1. pnpm workspaces: This project uses pnpm workspaces,      
  so always use pnpm instead of npm
  2. Turborepo: Build system uses Turbo for caching and       
  parallel execution
  3. Registry system: Components are managed through a        
  registry system in apps/*/registry/
  4. No node_modules found: Project appears to be a fresh     
   clone - run pnpm install first

  The repository is well-structured with clear separation     
   of concerns and comprehensive development tooling. The     
   main development workflow involves running the v4
  development server for the documentation site and using     
   the CLI development mode for testing component
  additions.