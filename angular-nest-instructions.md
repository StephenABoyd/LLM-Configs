# Project Requirements

## Folder Structure
This repository utilizes Nx to manage a monorepo structure. The main folders include:
- `apps/`: Contains the main application code.
- `libs/`: Contains shared libraries and utilities.
- `tools/`: Contains custom scripts and tools for development and deployment.
- `docs/`: Contains documentation related to the project.

## Libraries and Frameworks
- Angular, Tailwind CSS, and PrimeNG for the frontend.
- Jest for unit tests
- Cypress for end-to-end and component testing.
- NestJS for the backend.
- TypeORM for database interactions.
- PostgreSQL for the database.
- Docker for containerization.
- Nx for monorepo management.
- GitHub Actions for CI/CD.
- Auth0 for authentication and authorization.
- OpenAPI for API specifications and type generation

## Frontend Coding Standards
### General Practices
- All frontend code should follow Angular style guidelines.
- All frontend code should follow Tailwind CSS best practices.
- All frontend code should follow PrimeNG component usage guidelines.
- All frontend code should follow angular-eslint rules.

### Testing
- All facades should have Jest unit tests
- All frontend components should have Cypress component tests.
- All frontend workflows should have Cypress integration (e2e) tests that are fully mocked out

### Component Standards
- All frontend components should be modular and reusable.
- All frontend components should contain no logic outside of control flow in the template
- All control flow usages should utilize the latest in Angulars control flow
- Pipes should be created and utilized where data is needing to be changed only for viewing
- All frontend components should interact only with a dedicated facade service. This facade acts as an intermediary between the component, the store, and other services or states, encapsulating business logic and state management.
- Components should not need unit tests as they contain no business logic.
- All components should have Cypress component tests

### Facade Standards
- Each facade service should expose only the necessary observables, signals, and methods required by the component, keeping the component logic minimal and focused on presentation.
- Facade services should contain no "business logic" but should handle data changes for the view, and events from the view (such as button clicks)
- Instances of facades should not be passed around ever
- All facades should have Jest unit tests

### Service Standards
- All business logic should exist within services
- Services should only be provided at 'root' when absolutely required
- Instances of services should not be passed around ever
- Should majorly only contain pure functions, exceptions made for services that are combining data from other services. Business logic itself should exist in pure functions.
- All services should have Jest unit tests

### Store Standards
- Each component or workflow store should only be injected in one place. The only store that can be provided in 'root' would be a global application store.
- Stores should be pure Angular services utilizing signals. Stores should only expose setter functions for the signals and readonly signals to read the state.
- Instances of stores should not be passed around ever
- Should contain no logic at all. The only functions that should exist are setters for the signals.
- Stores should not need unit tests as they are simple services.

## Backend Coding Standards

### General Best Practices
- All backend code should follow NestJS style guidelines.
- All backend code should follow TypeScript best practices.
- All backend code should follow eslint rules.
- All backend code should be modular and reusable.

### Controller Standards
- Controller functions should not contain business logic
- Controllers should only inject services, never repository files
- All endpoints that either accept or return data should have respective DTOs
  - All DTOs should utilize the `class-validator` package
  - All POST/PUT/PATCH endpoints should validate that the request body is validated against the DTO
- Controllers should have Jest integration tests
- Controllers should not require unit tests

### Service Standards
- All backend business logic should be contained in services.
- Services that are not repository services should never interact with the database.
- Services should have Jest unit tests

### Repository Standards
- Repository files should be standards NestJS services that contain a getter for the DataSource
- All database interactions should be handled through services that utilize TypeORMs latest standards
- All database interactions and creations should be functions on the repository classes. Services should call these repository functions to interact with the database, ensuring a clear separation of concerns and promoting code reusability.
- Repositories should not contain actual logic and should not require unit tests
- Repositories should be tested through integration tests on the controller

## Shared Coding Standards
- All entities (for the backend) and API models (for the frontend) should have shared definitions in a `shared` Nx library to ensure consistency across the application.
  - The definitions should be generated from OpenAPI specs that exist in the Nx library
- All code should include appropriate error handling and logging.
- All code should be well-documented with comments and README files where necessary.
- All code should include unit tests and integration tests where applicable.
- All code should follow the DRY (Don't Repeat Yourself) principle.
- All code should be optimized for performance and scalability.

## UX Guidelines
- The application should be responsive and work well on both desktop and mobile devices.
- The user interface should be intuitive and easy to navigate.
- Consistent use of colors, fonts, and styles throughout the application.
- Clear and concise error messages and notifications.
- Accessibility considerations should be taken into account to ensure the application is usable by all users.
- Regular user feedback should be collected to improve the user experience.
- The application should follow best practices for web design and usability.
- The application should provide a seamless and efficient workflow for users.
- The application should prioritize important information and actions to enhance user productivity.

## Nx Library Standards
- All Nx generators should be ran as a dry run first to ensure no unintended changes are made.
- Nx Libraries should be placed in the `libs/` folder, then nested under their scope (api or client), then their domain. (e.g., 'libs/client/livestock/feature-livestock-list' and 'libs/api/livestock/feature-livestock-api')
- Nx Application-specific code should be placed in the `apps/` folder.
- Nx Libraries should have the type of library in their name (e.g., `data-access-livestock-api` for the frontend and `feature-livestock-api` for the backend).
- Each Nx library should have a clear purpose and responsibility.
- Nx Libraries should be reusable and shareable across different applications within the monorepo.
- Nx Libraries should have their own README files documenting their usage and purpose.
- Nx Libraries shared between frontend and backend should be placed in the `libs/shared` folder then under their domain (e.g., 'libs/shared/livestock/util-livestock-contract)
- Frontend Nx libraries should be of four types: UI libraries (containing only presentational components), feature libraries (containing business logic, services, and state management), utility libraries (containing helper functions and utilities), and data-access libraries (containing services for API interactions and data fetching).
- Backend Nx libraries should be of three types: feature libraries (containing business logic, services, and controllers), utility libraries (containing helper functions and utilities), and data-access libraries (containing repositories and database interaction logic).

## MCP Usage
This project utilizes several MCPs (Microservice Control Points) to streamline development, documentation, and task management:

- **context7 MCP**: All documentation fetching should be attempted through the context7 MCP. This ensures that documentation is always up-to-date and accessible from a centralized source.
- **taskMaster MCP**: Task management, including assignment, tracking, and progress updates, should be handled through the taskMaster MCP. This provides a unified workflow for managing development tasks and team collaboration.
- **nx MCP**: Any operations related to Nx, such as workspace management, project generation, and build orchestration, should be performed using the nx MCP. This guarantees consistency and reliability in Nx-related processes.
- **sequential-thinking MCP**: Dynamic and reflective problem-solving through a structured thinking process.
- **desktop-commander MCP**: Search, update, manage files and run terminal commands

### MCP Usage Examples
- **context7 MCP**: To fetch documentation, use the context7 MCP API endpoint, e.g., `GET /context7/docs/{topic}`.
- **taskMaster MCP**: For task management, interact with the taskMaster MCP, e.g., `POST /taskMaster/tasks` to create a new task.
- **nx MCP**: For Nx operations, use the nx MCP CLI or API, e.g., `nx generate @nx/angular:component <name>` via nx MCP.
- **sequential-thinking MCP**: For critical thinking breaking it down step by step. Including as a precursor to taskMaster to help break steps even further
- **desktop-commander MCP**: Search, update, manage files and run terminal commands

Refer to each MCP's documentation for integration details and usage examples. Always prefer MCPs for their respective domains to maintain project standards and efficiency.

## Contribution Guidelines
- Use feature branches named as `feature/<short-description>` or bugfix branches as `bugfix/<short-description>`.
- Write clear, descriptive commit messages following the Conventional Commits format (e.g., `feat: add animal tracking`).
- All changes must be submitted via pull requests. PRs should include a summary and reference related issues.
- Code reviews are required before merging. Address all review comments before approval.

## Testing Requirements
- Aim for at least 80% code coverage. Coverage reports should be generated and reviewed for each PR.

## Documentation Standards
- Use Markdown for documentation in the `docs/` folder and JSDoc for inline code documentation.
- All public APIs, services, and components must be documented.
- README files should be updated with any major changes.

## Accessibility Standards
- Follow WCAG 2.1 guidelines for accessibility.
- Use tools like axe or Lighthouse to test accessibility compliance.

## Error Handling and Logging
- Use centralized logging for backend (e.g., Winston or similar).
- Log at appropriate levels (info, warn, error) and include context for errors.
- Handle errors gracefully and provide user-friendly messages in the UI.

## Security Practices
- Never commit secrets or sensitive information. Use environment variables and secret management tools.
- Validate all user input on both frontend and backend.
- Keep dependencies up-to-date and monitor for vulnerabilities.

## Important Notes
- Always refer to the latest project documentation for updates on standards and practices.
  - This document is subject to change as the project evolves.
  - This document lives in the 'docs/prd.md' file.
