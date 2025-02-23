
# dt

**dt** is a lightweight, high-performance JavaScript framework inspired by NestJS, built on Bun and ElysiaJS. It combines a structured, developer-friendly experience with blazing-fast execution, making it ideal for building modern, scalable backend applications like task management systems, real-time SaaS platforms, and APIs.

## Why dt?

- **NestJS-Inspired DX**: Use familiar decorators (`@Controller`, `@Get`), dependency injection, and modular architecture to organize your code effortlessly.
- **Bun-Powered Speed**: Leverage Bun’s optimized runtime and ElysiaJS’s minimal overhead for top-tier performance (~100k+ req/s).
- **Real-Time Ready**: Built-in WebSocket support for dynamic, interactive applications.
- **TypeScript First**: Full TypeScript integration for type safety and modern development.

## Features

- **Modular Design**: Organize your app with modules (e.g., `AuthModule`, `TaskModule`).
- **Decorators**: Simplify routing with `@Get`, `@Post`, etc.
- **Dependency Injection**: Inject services seamlessly with `@Injectable` and `Container`.
- **CLI**: Generate boilerplate with `dt g controller <name>` (coming soon!).
- **WebSocket**: Real-time communication via Elysia’s native WS support.

## Getting Started

dt is under active development. Stay tuned for the initial release! To get a sneak peek:

1. **Clone the Repo**:
   ```bash
   git clone https://github.com/[your-username]/dt.git
   cd dt
   ```

2. **Install Dependencies** (once published):
   ```bash
   bun install
   ```

3. **Run the App** (once implemented):
   ```bash
   bun run start
   ```

## Contributing

We welcome contributions! Check out our [CONTRIBUTING.md](#) (coming soon) for guidelines. Feel free to open issues or submit PRs to help shape dt.

## License

dt is licensed under the [MIT License](LICENSE). See the LICENSE file for details.

## Roadmap

Here’s our detailed plan to bring dt to life:

### [ ] Initial CLI Implementation
Lay the foundation for developer productivity with a command-line interface adapted from `dt-workspace/cli`.

- [ ] **Setup CLI Structure**: Configure `dt` as an npm package with a `bin` entry point (`dt` command).
- [ ] **Basic Commands**: Implement `dt g <type> <name>` for generating:
  - `controller`: Create a controller with `@Controller`, `@Get`, etc.
  - `service`: Generate an `@Injectable` service class.
  - `module`: Scaffold a module with controllers and providers.
- [ ] **Template Files**: Adapt `dt-workspace/cli` templates for dt syntax (e.g., Elysia routing, Bun compatibility).
- [ ] **File Structure**: Ensure generated files follow a modular layout (e.g., `src/modules/auth/auth.controller.ts`).
- [ ] **Test CLI**: Verify CLI works with `bun dt g controller auth` and `npx dt g module task`.

### [ ] Full NestJS Feature Parity
Achieve feature parity with NestJS to provide a familiar, robust DX while leveraging Bun’s speed.

- [ ] **Core Architecture**:
  - Enhance `@Module` to support `imports`, `controllers`, `providers`, and `exports`.
  - Implement dynamic module registration (e.g., `forRoot` pattern).
- [ ] **Dependency Injection**:
  - Add constructor injection (e.g., `constructor(private service: Service)`).
  - Support provider scopes (singleton, request-scoped, transient).
- [ ] **Routing**:
  - Add `@Put`, `@Delete`, `@Param`, `@Query`, `@Body` decorators for full HTTP support.
  - Integrate Elysia’s route validation (e.g., `t.Object`) into `@Body`.
- [ ] **Middleware**:
  - Implement `@Use` decorator for route-specific middleware.
  - Add global middleware support (e.g., authentication).
- [ ] **Exception Handling**:
  - Create `@Catch` decorator and exception filters (e.g., `HttpException`).
- [ ] **Pipes**:
  - Add `@Pipe` decorator with validation/transform pipes (e.g., `ValidationPipe` using Zod).
- [ ] **Guards**:
  - Implement `@Guard` decorator for route protection (e.g., JWT auth).
- [ ] **Interceptors**:
  - Add `@Interceptor` for request/response transformations (e.g., logging).
- [ ] **WebSocket**:
  - Implement `@WsGateway` and `@WsSubscribe` for real-time features (e.g., task updates).

### [ ] Comprehensive Documentation
Build detailed, accessible documentation to onboard users and contributors.

- [ ] **Getting Started Guide**: Cover installation (`bun add dt`), CLI usage, and a "Hello World" example.
- [ ] **API Reference**: Document all decorators (`@Controller`, `@Get`), DI (`Container`, `@Inject`), and factory (`dtFactory`).
- [ ] **Examples**: Provide sample apps (e.g., task management API with WebSocket).
- [ ] **Contributing Guide**: Create `CONTRIBUTING.md` with setup, PR process, and coding standards.
- [ ] **Website**: Optional mini-site (e.g., using Bun’s static file serving) with docs hosted on GitHub Pages.

### [ ] Official npm Release
Prepare and publish dt to npm for widespread adoption.

- [ ] **Package Setup**: Finalize `package.json` with `main`, `types`, `bin`, and dependencies (`elysia`, `reflect-metadata`).
- [ ] **Build Process**: Ensure `bun build` produces a distributable `dist/` folder with TypeScript declarations.
- [ ] **Versioning**: Start at `0.1.0` for alpha, increment with features (e.g., `1.0.0` for full parity).
- [ ] **Test Suite**: Add basic unit tests (e.g., Bun’s `bun test`) for core features (routing, DI).
- [ ] **CI/CD**: Set up GitHub Actions to build, test, and publish on tag push (e.g., `v0.1.0`).
- [ ] **Release**: Publish with `npm publish` after CLI and core features are stable.

### Detailed Roadmap Explanation

#### Initial CLI Implementation
- **Why**: A CLI is critical for DX, automating boilerplate creation like NestJS’s `nest g`. Adapting `dt-workspace/cli` saves time.
- **Tasks**:
  - **Setup**: Configure the npm package with a `bin` entry (`dt`), ensuring it works with `bun`, `npx`, and `npm`.
  - **Commands**: Basic `generate` command for controllers, services, and modules—core building blocks.
  - **Templates**: Modify your existing CLI templates to use dt decorators (`@Controller`) and Elysia syntax.
  - **Structure**: Mirror NestJS’s `src/modules/<name>` layout for consistency.
  - **Testing**: Manual verification with `bun dt g` commands.

#### Full NestJS Feature Parity
- **Why**: Matching NestJS features ensures dt meets developer expectations for structure and extensibility.
- **Tasks**:
  - **Core**: Expand `@Module` to handle imports and dynamic configs (e.g., database settings).
  - **DI**: Upgrade DI to constructor-based (more ergonomic) with scope support for flexibility.
  - **Routing**: Complete HTTP method support and add parameter extraction for full REST API coverage.
  - **Middleware/Guards/Pipes/Interceptors**: Add NestJS-style request lifecycle hooks for auth, validation, and logging.
  - **WebSocket**: Wrap Elysia’s WS in decorators for real-time features (e.g., `@WsSubscribe('taskAssigned')`).

#### Comprehensive Documentation
- **Why**: Clear docs reduce onboarding friction and encourage adoption.
- **Tasks**:
  - **Guides**: Step-by-step setup and basic app creation.
  - **API**: Exhaustive list of dt exports and usage.
  - **Examples**: Task app demo with WebSocket and MongoDB.
  - **Contributing**: Instructions for PRs and issues.
  - **Website**: Optional stretch goal for polished presentation.

#### Official npm Release
- **Why**: Public release makes dt accessible to the community.
- **Tasks**:
  - **Package**: Finalize metadata and build process for distribution.
  - **Versioning**: Start with an alpha release (e.g., `0.1.0`) to iterate publicly.
  - **Tests**: Basic sanity checks for stability.
  - **CI/CD**: Automate publishing to npm via GitHub Actions.
  - **Release**: Push to npm once CLI and core are functional.



