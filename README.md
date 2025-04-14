# NestJS Overview

## Table of Contents

- [Introduction](#introduction)
- [Architecture](#architecture)
- [Client-Server Architecture](#client-server-architecture)
- [Nest CLI](#nest-cli)
- [Project Structure](#project-structure)
- [Key Files and Directories](#key-files-and-directories)
- [main.ts](#maints)
- [Using Fastify with NestJS](#using-fastify-with-nestjs)

## Introduction

NestJS is a robust Node.js framework designed for building scalable and efficient server-side applications. Built on Express.js, it offers a rich feature set out of the box and leverages TypeScript for enhanced developer experience. Its architecture, inspired by Angular, emphasizes modularity and clean code.

- **TypeScript-based**: Provides type safety and modern JavaScript capabilities.
- **Modular design**: Organizes code into reusable, feature-specific modules.
- **Express.js core**: Combines NestJS structure with Express flexibility.
- **Angular-inspired**: Uses familiar dependency injection and modular patterns.

## Architecture

NestJS adopts a modular architecture, enabling scalable and maintainable applications through well-defined components.

- **Modules**: Group related functionality into self-contained units.
- **Controllers**: Handle incoming HTTP requests and define routes.
- **Services**: Encapsulate business logic for reusability.
- **Providers**: Manage database operations and other dependencies.

## Client-Server Architecture

NestJS follows a classic client-server model for seamless communication.

- **Client**: Sends HTTP requests from the user interface.
- **Server**: Processes requests and responds with data, powered by Express.js.

## Nest CLI

The Nest CLI is a powerful command-line tool that streamlines project setup and development.

- **Installation**: Run `npm i -g @nestjs/cli` to install globally.
- **Features**: Generates projects, controllers, services, and more with ease.

## Project Structure

Create a new NestJS project with a single command:

```bash
nest new project-name
```

## Key Files and Directories

- **tsconfig.json**: Configures TypeScript settings for the project.
- **tsconfig.build.json**: Specifies TypeScript configurations for building the application.
- **nest-cli.json**: Contains settings for the Nest CLI tool.
- **package.json**: Manages npm dependencies and project scripts.
- **src/**: Houses the application’s source code.
- **.eslintrc.js**: Defines ESLint rules for code linting.
- **.prettierrc**: Sets up Prettier for consistent code formatting.
- **.gitignore**: Lists files and directories ignored by Git.
- **test/**: Stores test cases for the application.
- **dist/**: Contains compiled application code.

## main.ts

The `main.ts` file serves as the entry point for a NestJS application, executed first when the application starts. It bootstraps the application and configures global settings.

- **Bootstrapping**: Initializes the app by importing the root `AppModule` and starting the server.
- **Environment Setup**: Configures environment variables for the application.
- **Global Configurations**:
  - Applies middleware, exception filters, and pipes for request handling.
  - Sets up logging, metrics, caching, security, authentication, and authorization.
- **Flexibility**: Allows customization of app-wide behavior and integrations.

```bash
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  await app.listen(3000);
}
bootstrap();
```

## Using Fastify with NestJS

By default, NestJS uses Express.js as its HTTP server. To use **Fastify** for improved performance and lower overhead, follow these steps:

- **Install Fastify Adapter**: Install the required Fastify dependencies.
  ```bash
  npm install @nestjs/platform-fastify
  ```
- **Configure NestJS to use Fastify**: Update the `main.ts` file

```bash
import { NestFactory } from '@nestjs/core';
import { FastifyAdapter, NestFastifyApplication } from '@nestjs/platform-fastify';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create<NestFastifyApplication>(
    AppModule,
    new FastifyAdapter()
  );
  await app.listen(3000);
}
bootstrap();
```
