# RedRust Project Plan

This document outlines the development plan and roadmap for the RedRust project, aiming for feature parity with `rrmcpy` but implemented in Rust.

## Guiding Principles

- **Feature Parity with rrmcpy**: Implement all core functionalities and MCP tools present in `rrmcpy`.
- **Rust Idioms**: Leverage Rust's strengths for safety, performance, and concurrency.
- **Keep It Simple**: Adhere to a clear, modular, and maintainable architecture.
- **Utilize Official MCP Rust SDK**: Leverage `modelcontextprotocol/rust-sdk` ([https://github.com/modelcontextprotocol/rust-sdk](https://github.com/modelcontextprotocol/rust-sdk)) for core MCP functionality.
- **Testability**: Design components for easy unit and integration testing.
- **Comprehensive Documentation**: Provide clear setup, usage, and development guides.

## High-Level Roadmap

**Phase 1: Foundation & Core Connectivity (Target: v0.1.0)**

*   **Task 1.1**: Set up Rust project structure (`cargo new RedRust --lib`).
*   **Task 1.2 (Revised)**: Integrate `modelcontextprotocol/rust-sdk` and supporting crates:
    *   Add `rmcp` (with `server` feature) and `rmcp-macros` from the SDK to `Cargo.toml`.
    *   Confirm and add necessary dependencies like `tokio` and `serde` (as required by the SDK).
    *   Select and add a suitable logging crate (e.g., `tracing` or `env_logger`).
    *   Select and add an HTTP client (e.g., `reqwest`) for direct Redmine API calls (distinct from MCP communication).
    *   Ensure JSON parsing capabilities (e.g., via `serde`, `serde_json`) for Redmine API data.
    *   Review SDK examples for server setup and tool implementation patterns.
*   **Task 1.3**: Implement Redmine API client basics:
    *   Configuration management (environment variables for URL & API key).
    *   Basic GET request functionality to Redmine (using the chosen HTTP client).
    *   Error handling for API communication.
*   **Task 1.4 (Revised)**: Implement core MCP server using `modelcontextprotocol/rust-sdk`:
    *   Structure the RedRust server based on the SDK's server examples.
    *   Utilize the SDK's built-in mechanisms for request handling, tool registration, and dispatch.
*   **Task 1.5 (Revised)**: Implement first Redmine MCP tool: `redmine-health-check` (using `rmcp-macros`).
*   **Task 1.6**: Basic unit tests for API client and health check tool.
*   **Task 1.7 (Revised)**: Initial `README.md` with project goals, setup (including SDK usage), and basic usage.

**Phase 2: Project & Issue Management Tools (Target: v0.2.0)**

*   **Task 2.1**: Implement MCP tools for Project management:
    *   `redmine-create-project`
    *   `redmine-get-project` (by ID/identifier)
    *   `redmine-list-projects`
    *   `redmine-update-project`
    *   `redmine-delete-project`
*   **Task 2.2**: Implement MCP tools for Issue management:
    *   `redmine-create-issue`
    *   `redmine-get-issue`
    *   `redmine-list-issues` (with basic filters like project_id, status_id)
    *   `redmine-update-issue`
    *   `redmine-delete-issue`
*   **Task 2.3**: Expand unit and integration tests for new tools.
*   **Task 2.4**: Documentation for project and issue tools.

**Phase 3: User, Version & Other Entity Management (Target: v0.3.0)**

*   **Task 3.1**: Implement MCP tools for User management:
    *   `redmine-current-user`
    *   (Consider others based on `rrmcpy` if they exist, e.g., list users - might require admin rights)
*   **Task 3.2**: Implement MCP tools for Version (Roadmap) management:
    *   `redmine-create-version`
    *   `redmine-get-version`
    *   `redmine-list-versions` (for a project)
    *   `redmine-update-version`
    *   `redmine-delete-version`
    *   `redmine-get-issues-by-version`
*   **Task 3.3**: Implement tools for other relevant entities (e.g., Groups, Time Entries, if covered by `rrmcpy` and deemed essential).
*   **Task 3.4**: Comprehensive testing for all new tools.
*   **Task 3.5**: Update documentation.

**Phase 4: Advanced Features & Refinements (Target: v0.4.0 - v0.5.0)**

*   **Task 4.1**: Implement remaining MCP tools from `rrmcpy` for feature parity.
*   **Task 4.2**: Advanced filtering and querying for `list-*` tools.
*   **Task 4.3**: Investigate and implement file attachment handling if supported by `rrmcpy`.
*   **Task 4.4**: Concurrency and performance optimizations for the MCP server.
*   **Task 4.5**: Robust error reporting and diagnostics.
*   **Task 4.6**: Dockerization: Create `Dockerfile` for easy deployment.
*   **Task 4.7**: CI/CD pipeline setup (e.g., GitHub Actions).

**Phase 5: Beta & Release (Target: v1.0.0)**

*   **Task 5.1**: Extensive end-to-end testing.
*   **Task 5.2**: Beta testing phase with users.
*   **Task 5.3**: Address feedback and bugs from beta.
*   **Task 5.4**: Finalize documentation, including migration notes if applicable.
*   **Task 5.5**: Official v1.0.0 release.