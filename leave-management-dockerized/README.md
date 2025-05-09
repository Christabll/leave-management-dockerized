# Leave Management System — Docker Compose Orchestration

## Prerequisites

- Docker & Docker Compose installed

## Setup

```bash
git clone <your-leave-management-dockerized-repo-url>
cd leave-management-dockerized

# Initialize submodules
git submodule update --init --recursive

# Build and run all services
docker-compose up --build
```

## Submodule Repositories

- Auth Service: https://github.com/Christabll/IST-auth-service
- Leave Service: https://github.com/Christabll/IST_LeaveManagementService
- Frontend: https://github.com/Christabll/leave-management-frontend

## Environment Variables

- All required environment variables are set in the `.env` file inside each service folder (`auth-service/.env`, `leave-service/.env`, `frontend/.env`).
- No manual typing is required in the app directories.

## Multi-Platform Support

- Dockerfiles use multi-arch base images for compatibility with Apple Silicon (M1/M2/M3) and Intel/AMD CPUs.
- When building images for Docker Hub, use:
  ```bash
  docker buildx build --platform linux/amd64,linux/arm64 -t yourdockerhub/servicename:tag --push .
  ```

## Stopping the Services

```bash
docker-compose down
```

## Troubleshooting

- If you update any microservice, run:
  ```bash
  git submodule update --remote --merge
  docker-compose up --build
  ```

- Ensure all `.env` files are present in each service directory.
- If you encounter platform issues, check that your Dockerfiles use multi-arch compatible base images.

---

For any issues, please refer to the documentation or contact the maintainer. 