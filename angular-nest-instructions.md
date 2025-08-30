# Project Requirements

## Folder Structure
This repository utilizes Nx to manage a monorepo structure. The main folders include:
- `apps/`: Contains the main application code.
- `libs/`: Contains shared libraries and utilities.
- `tools/`: Contains custom scripts and tools for development and deployment.
- `docs/`: Contains documentation related to the project.

## Libraries and Frameworks
- Angular, Tailwind CSS, and PrimeNG for the frontend.
- Cypress for end-to-end and component testing.
- NestJS for the backend.
- TypeORM for database interactions.
- PostgreSQL for the database.
- Docker for containerization.
- Nx for monorepo management.
- GitHub Actions for CI/CD.
- Auth0 for authentication and authorization.

## Coding Standards
- All frontend code should follow Angular style guidelines.
- All frontend code should follow Tailwind CSS best practices.
- All frontend code should follow PrimeNG component usage guidelines.
- All frontend code should follow angular-eslint rules.
- All frontend components should be modular and reusable.
- All frontend components should contain no logic.
- All frontend components should have a self contained store utilizing angular signals.
- All frontend components should have Cypress component tests.
- All frontend business logic should be contained in services.
- All backend code should follow NestJS style guidelines.
- All backend code should follow TypeScript best practices.
- All backend code should follow eslint rules.
- All backend code should be modular and reusable.
- All backend business logic should be contained in services.
- All database interactions should be handled through TypeORM repositories.
- All code should include appropriate error handling and logging.
- All code should be well-documented with comments and README files where necessary.
- All code should include unit tests and integration tests where applicable.
- All code should be reviewed through pull requests before merging into the main branch.
- All code should follow the DRY (Don't Repeat Yourself) principle.
- All code should be optimized for performance and scalability.
- All frontend components should interact only with a dedicated facade service. This facade acts as an intermediary between the component, the store, and other services or states, encapsulating business logic and state management.
- Each facade service should expose only the necessary observables, signals, and methods required by the component, keeping the component logic minimal and focused on presentation.
- Facade services should be well-documented and covered by unit tests.
- All entities (for the backend) and API models (for the frontend) should have shared definitions in a `shared` library to ensure consistency across the application.
- All database interactions and creations should be functions on the repository classes. Services should call these repository functions to interact with the database, ensuring a clear separation of concerns and promoting code reusability.

## Frontend Store Standards
- All frontend stores should be implemented as plain Angular services utilizing signals for state management.
- Stores should expose signals and methods for state updates and queries.
- Stores should not need unit tests as they are simple services.
- Stores should never contain business logic. Business logic should be contained in dedicated services.

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
- Libraries should be placed in the `libs/` folder.
- Application-specific code should be placed in the `apps/` folder.
- Libraries should have the type of library in their name (e.g., `data-access-livestock-api` for the frontend and `feature-livestock-api` for the backend).
- Libraries should be organized by domain or feature.
- Each library should have a clear purpose and responsibility.
- Libraries should be reusable and shareable across different applications within the monorepo.
- Libraries should have their own README files documenting their usage and purpose.
- Libraries shared between frontend and backend should be placed in a `shared` library.
- Frontend libraries should be of four types: UI libraries (containing only presentational components), feature libraries (containing business logic, services, and state management), utility libraries (containing helper functions and utilities), and data-access libraries (containing services for API interactions and data fetching).
- Backend libraries should be organized by domain or feature, similar to frontend libraries.
- Backend libraries should be of three types: feature libraries (containing business logic, services, and controllers), utility libraries (containing helper functions and utilities), and data-access libraries (containing repositories and database interaction logic).

## MCP Usage
This project utilizes several MCPs (Microservice Control Points) to streamline development, documentation, and task management:

- **context7 MCP**: All documentation fetching should be attempted through the context7 MCP. This ensures that documentation is always up-to-date and accessible from a centralized source.
- **taskMaster MCP**: Task management, including assignment, tracking, and progress updates, should be handled through the taskMaster MCP. This provides a unified workflow for managing development tasks and team collaboration.
- **nx MCP**: Any operations related to Nx, such as workspace management, project generation, and build orchestration, should be performed using the nx MCP. This guarantees consistency and reliability in Nx-related processes.

Refer to each MCP's documentation for integration details and usage examples. Always prefer MCPs for their respective domains to maintain project standards and efficiency.

## Contribution Guidelines
- Use feature branches named as `feature/<short-description>` or bugfix branches as `bugfix/<short-description>`.
- Write clear, descriptive commit messages following the Conventional Commits format (e.g., `feat: add animal tracking`).
- All changes must be submitted via pull requests. PRs should include a summary and reference related issues.
- Code reviews are required before merging. Address all review comments before approval.

## Testing Requirements
- All code must include unit tests and integration tests where applicable.
- Frontend: Use Cypress for E2E and component tests. Backend: Use Jest for unit and integration tests.
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

## MCP Usage Examples
- **context7 MCP**: To fetch documentation, use the context7 MCP API endpoint, e.g., `GET /context7/docs/{topic}`.
- **taskMaster MCP**: For task management, interact with the taskMaster MCP, e.g., `POST /taskMaster/tasks` to create a new task.
- **nx MCP**: For Nx operations, use the nx MCP CLI or API, e.g., `nx generate @nx/angular:component <name>` via nx MCP.

## Important Notes
- Always refer to the latest project documentation for updates on standards and practices.
  - This document is subject to change as the project evolves.
  - This document lives in the 'docs/prd.md' file.
