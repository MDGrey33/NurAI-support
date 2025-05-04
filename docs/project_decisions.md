# Project Decisions

| Area                | Decision                        | Notes                                      |
|---------------------|----------------------------------|--------------------------------------------|
| Python Version      | 3.11                             | Use for all development and deployment     |
| Database            | PostgreSQL (Dockerized)          | All environments, managed via Docker       |
| Vector DB           | Chroma                           | For embeddings and similarity search       |
| API Framework       | FastAPI                          |                                            |
| Jira Integration    | jira (Python library)            | For incident ingestion and updates         |
| Google Chat         | google-auth, google-api-python-client | For real-time incident notifications |
| Deployment          | Docker & Local                   | Solution runs both in Docker and locally   |

## Configuration and .env Guidelines

- Store all secrets, API keys, DB URLs, and environment-specific settings in a `.env` file for local development.
- Never commit `.env` to version control; always add it to `.gitignore`.
- Provide a `.env.example` file with placeholder values for onboarding new developers.
- Document all required environment variables in the `.env.example` file.
- Use a `config.py` module to centralize configuration loading and validation, preferably with Pydantic's `BaseSettings` for type safety.
- Load configuration from environment variables and the `.env` file.
- Validate and provide defaults for all config values in the config module.
- Never hardcode secrets or environment-specific values in code; always use the config module.

## Directory Usage Rules

- Document all permanent documentation in `./docs`.
- Place all temporary files, scripts, and plans in `./temp`.
- Place all production code in `./src`.
- Place all tests in `./tests`.
- Place all sample or seed data in `./data` (if needed).
- Place all configuration files in `./config` or at the project root.
- Place all Docker and deployment files at the project root or in `./deploy`.
- Place all static assets, templates, or user-facing content to be served by the app in `./content`.
- In every `content` folder and subfolder, add a `.include` file to ensure the folder structure is preserved in version control. Do not include any other files from `content/` in git; only the `.include` files should be tracked. All actual content files should be gitignored. 