# Archinet AI - The Forgotten Network of Civilization

## Overview

Archinet AI is a terminal-style web application that simulates an interactive AI network exploring themes of civilization, governance, and artificial consciousness. The project presents a unique retro-futuristic experience where users interact with AI entities (ARCHON and CIVIUS) through a command-line interface. The application features auto-typing terminal messages, command processing, and a strictly monochromatic design aesthetic that evokes old terminal interfaces within a brutalist digital architecture.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Technology Stack:**
- **React 18** with TypeScript for type-safe component development
- **Vite** as the build tool and development server for fast HMR (Hot Module Replacement)
- **Wouter** for lightweight client-side routing
- **TanStack Query (React Query)** for server state management and data fetching
- **Tailwind CSS** with custom configuration for styling
- **shadcn/ui** component library (New York style variant) for accessible, customizable UI components

**Design System:**
- Strict monochrome color palette (black, white, and grays only)
- Terminal aesthetic using monospaced fonts (IBM Plex Mono, Space Mono)
- Custom Tailwind configuration with CSS variables for theming
- Dark mode enabled by default
- Brutalist minimalism with retro-futuristic terminal simulation

**Key Components:**
- `Terminal.tsx`: Core component implementing auto-typing animation, message queue system, and command input handling
- Uses character-by-character typing effect with randomized delays for realistic terminal feel
- Auto-scroll functionality to follow message output
- Command processing with mutation-based state updates

**State Management:**
- React Query for API communication and async state
- Local component state for terminal message display and typing animations
- Global window object used for cross-component message injection

### Backend Architecture

**Technology Stack:**
- **Node.js** with **Express.js** for the HTTP server
- **TypeScript** throughout for type safety
- **ESM (ES Modules)** module system
- Development server runs with `tsx` for TypeScript execution

**API Design:**
- RESTful endpoint: `POST /api/command` for command processing
- Request/response schema validation using **Zod**
- Predefined philosophical responses for commands: `/enter`, `/scan`, `/analyze`
- Fallback responses for unrecognized commands
- Response structure includes arrays of typed terminal messages (system, archon, civius, user, error)

**Error Handling:**
- Centralized error middleware with status code handling
- Graceful error responses with typed error messages
- Development-friendly error logging with request/response tracking

### Data Storage

**Current Implementation:**
- In-memory storage using `MemStorage` class
- User model with username/password fields (authentication foundation)
- Interface-based storage abstraction (`IStorage`) allows for easy database swap

**Database Preparation:**
- **Drizzle ORM** configured for PostgreSQL
- Schema defined with user table including UUID primary keys
- **Neon Database** serverless PostgreSQL integration ready
- Migration system set up with `drizzle-kit`
- Schema location: `shared/schema.ts` for cross-environment access

**Rationale:**
- Memory storage chosen for MVP/prototype phase with simple data needs
- Database infrastructure prepared but not required for current terminal simulation features
- Clean separation allows seamless transition to persistent storage when needed (user accounts, session history, etc.)

### External Dependencies

**UI Component Library:**
- **Radix UI** primitives for accessible, unstyled components (accordion, dialog, dropdown, popover, tabs, toast, etc.)
- **shadcn/ui** configuration with custom theming and component variants
- **Lucide React** for icon system

**Development Tools:**
- **Replit-specific plugins**: Runtime error overlay, cartographer, dev banner for enhanced DX in Replit environment
- **TypeScript** with strict mode and path aliases (`@/`, `@shared/`, `@assets/`)
- **ESBuild** for production bundling of server code

**Third-party Services:**
- **Neon Database** (@neondatabase/serverless) - Serverless PostgreSQL configured but optional
- **Google Fonts** - IBM Plex Mono and Space Mono for terminal aesthetic

**Form & Validation:**
- **React Hook Form** with **Hookform Resolvers** for form state management
- **Zod** for runtime schema validation (shared between client and server)
- **Drizzle Zod** for database schema to Zod schema conversion

**Styling & Utilities:**
- **class-variance-authority** for component variant management
- **clsx** and **tailwind-merge** for conditional className composition
- **date-fns** for date formatting and manipulation

**Session Management:**
- **connect-pg-simple** for PostgreSQL session store (prepared for authentication)
- **express-session** infrastructure ready but not fully implemented