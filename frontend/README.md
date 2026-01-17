# Eerie Tea - Frontend

Next.js 16.1.1 frontend application for the Eerie Tea e-commerce platform.

## Project Structure

This frontend uses **Next.js App Router**:

- `app/`: Next.js App Router pages and layouts
- `components/`: React components organized by feature
- `lib/`: Utilities, API client functions, hooks, and stores
- `types/`: TypeScript type definitions
- `public/`: Static assets

## Prerequisites

- Node.js 20.9+ 
- pnpm (recommended) or npm

## Getting Started

See the main [README.md](../README.md) for setup instructions.

## Configuration

- `.env.local`: Local environment variables (gitignored)
- `.env.example`: Example environment variables

## API Client

The frontend communicates with the .NET backend API via API client functions in `lib/api/`.

## Development

Run the development server:

```bash
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000) to see the application.
