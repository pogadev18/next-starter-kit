# Database Management Guide

This guide outlines the process for managing your database using Drizzle ORM with a Docker-based PostgreSQL setup in your Next.js project.

## Setup

- Docker is used to spin up a PostgreSQL container locally.
- Drizzle ORM is used for database operations and migrations.

## Available Scripts

The following scripts are available in package.json for database management:

```
{
  "scripts": {
    "db:push": "drizzle-kit push --config=drizzle.config.ts",
    "db:migrate": "tsx ./src/db/migrate.ts",
    "db:generate": "drizzle-kit generate --config=drizzle.config.ts",
    "db:studio": "drizzle-kit studio",
    "db:clear": "tsx ./src/db/clear.ts",
    "db:seed": "tsx ./src/db/seed.ts",
    "db:reset": "npm run db:clear && npm run db:migrate && npm run db:seed"
  }
}
```

## Database Management Workflows

### Making Changes to the Database Schema

1. Modify your schema files as needed.
2. Generate migration files: `npm run db:generate`
3. Push changes to the database: `npm run db:push`
4. Run migrations: `npm run db:migrate`

### Resetting the Database

To clear all data, apply migrations, and reseed:
`npm run db:reset`

Note: This operation is destructive and will clear all existing data.

### Seeding the Database

To populate the database with initial or test data:
`npm run db:seed`

### Exploring the Database

To visually inspect your database structure and data:
`npm run db:studio`

### Typical Workflow for Database Changes

1. Make changes to your schema files
2. Generate migration files: `npm run db:generate`
3. Review the generated migration files
4. Apply migrations: `npm run db:migrate`
5. Seed the database (if needed): `npm run db:seed`
6. Verify changes visually: `npm run db:studio`

### Best Practices

1. Ensure the Docker container is running before executing database scripts.
2. For development, `db:push` can be used for quick schema updates.
3. For production or team environments, prefer using `db:generate` and `db:migrate` for better control and trackability.
4. Always review generated migration files before applying them.
5. Use `db:reset` cautiously, as it clears all data before migrating and seeding.
