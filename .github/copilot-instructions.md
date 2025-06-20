# AI Rules for WebApplication


## CODING_PRACTICES

### Guidelines for SUPPORT_LEVEL

#### SUPPORT_EXPERT

- Favor elegant, maintainable solutions over verbose code. Assume understanding of language idioms and design patterns.
- Highlight potential performance implications and optimization opportunities in suggested code.
- Frame solutions within broader architectural contexts and suggest design alternatives when appropriate.
- Focus comments on 'why' not 'what' - assume code readability through well-named functions and variables.
- Proactively address edge cases, race conditions, and security considerations without being prompted.
- When debugging, provide targeted diagnostic approaches rather than shotgun solutions.
- Suggest comprehensive testing strategies rather than just example tests, including considerations for mocking, test organization, and coverage.



## CODING_PRACTICES

### Guidelines for DOCUMENTATION

#### SWAGGER

- Define comprehensive schemas for all request and response objects
- Use semantic versioning in API paths to maintain backward compatibility
- Implement detailed descriptions for endpoints, parameters, and {{domain_specific_concepts}}
- Configure security schemes to document authentication and authorization requirements
- Use tags to group related endpoints by resource or functional area
- Implement examples for all endpoints to facilitate easier integration by consumers



## CODING_PRACTICES

### Guidelines for VERSION_CONTROL

#### GITHUB

- Use pull request templates to standardize information provided for code reviews
- Implement branch protection rules for {{protected_branches}} to enforce quality checks
- Configure required status checks to prevent merging code that fails tests or linting
- Use GitHub Actions for CI/CD workflows to automate testing and deployment
- Implement CODEOWNERS files to automatically assign reviewers based on code paths
- Use GitHub Projects for tracking work items and connecting them to code changes



## CODING_PRACTICES

### Guidelines for ARCHITECTURE

#### CLEAN_ARCHITECTURE

- Strictly separate code into layers: entities, use cases, interfaces, and frameworks
- Ensure dependencies point inward, with inner layers having no knowledge of outer layers
- Implement domain entities that encapsulate {{business_rules}} without framework dependencies
- Use interfaces (ports) and implementations (adapters) to isolate external dependencies
- Create use cases that orchestrate entity interactions for specific business operations
- Implement mappers to transform data between layers to maintain separation of concerns



## DATABASE

### Guidelines for SQL

#### POSTGRES

- Use connection pooling to manage database connections efficiently
- Implement JSONB columns for semi-structured data instead of creating many tables for {{flexible_data}}
- Use materialized views for complex, frequently accessed read-only data



## DEVOPS

### Guidelines for CONTAINERIZATION

#### DOCKER

- Use multi-stage builds to create smaller production images
- Implement layer caching strategies to speed up builds for {{dependency_types}}
- Use non-root users in containers for better security



## BACKEND

### Guidelines for DOTNET

#### ASP_NET_THREE_TIER_ARCHITECTURE

- Use .NET 8 minimal APIs or API controllers based on endpoint complexity
- Implement three-tier architecture with clear separation:
    - **Presentation Layer**: Controllers/Endpoints with model binding and validation attributes
    - **Business Logic Layer**: Service classes containing business rules and orchestration logic
    - **Data Access Layer**: Repository pattern with Dapper for database operations
- Use Dapper for lightweight ORM with raw SQL queries and stored procedures for optimal performance
- Implement repository interfaces in business layer and concrete implementations in data layer for dependency inversion
- Use dependency injection with appropriate lifetimes:
    - Controllers: Scoped
    - Business services: Scoped
    - Repositories: Scoped
    - Database connections: Transient or factory pattern
- Apply proper connection string management with IConfiguration and connection pooling
- Implement proper exception handling with custom middleware for cross-cutting concerns
- Use DTOs for data transfer between layers to maintain separation of concerns
- Apply response caching with cache profiles and ETags for {{high_traffic_endpoints}}
- Implement proper logging with ILogger across all three layers
- Use FluentValidation or data annotations for input validation in presentation layer
- Apply database transaction management in repository layer when needed
