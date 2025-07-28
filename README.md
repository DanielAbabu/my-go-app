# Go Clean Architecture Folder Structure

```
my-go-app/
├── cmd/
│   └── api/
│       └── main.go            # Application entry point
├── config/
│   └── config.go              # Configuration loader (e.g., viper)
├── delivery/
│   ├── http/
│   │   ├── user_handler.go    # HTTP handlers (e.g., gin)
│   │   └── order_handler.go   # Additional handlers
│   └── route/
│       └── routes.go          # HTTP route setup
├── domain/
│   ├── user.go                # Domain models
│   └── repository.go          # Repository interfaces
├── infrastructure/
│   ├── middleware/
│   │   ├── auth_middleware.go # Authentication middleware
│   │   └── logger_middleware.go # Logging middleware
│   ├── database.go            # DB setup (e.g., sqlx)
│   ├── logger.go              # Logger (e.g., zap)
│   └── twilio.go              # Twilio client setup (e.g., for SMS)
├── repository/
│   └── user_repository.go     # Repository implementation
├── usecase/
│   └── user_usecase.go        # Business logic
├── utils/
│   ├── utils.go               # Utility functions
│   ├── Dockerfile             # Docker setup
│   ├── .github/
│   │   └── workflows/
│   │       └── ci.yml         # GitHub Actions CI
│   └── openapi.yaml           # OpenAPI spec
├── tests/
│   └── user_usecase_test.go   # Unit tests (e.g., testify)
├── .gitignore                 # Git ignore file
├── go.mod                     # Go modules
├── go.sum                     # Go module checksums
├── render.yaml                # Render deployment config
└── README.md                  # Project docs
```

# Quick Guide
- **cmd/api/**: `main.go` starts the app (uses `github.com/gin-gonic/gin`).
- **config/**: `config.go` loads settings, including Twilio API key (uses `github.com/spf13/viper`).
- **delivery/**: HTTP handlers (`http/`) and routes (`route/`, uses `gin`).
  - `user_handler.go`, `order_handler.go`: Handle API endpoints.
- **domain/**: Business models and repository interfaces.
  - `user.go`: Defines User struct.
  - `repository.go`: Defines repository interfaces.
- **infrastructure/**: External services.
  - `database.go`: DB setup (uses `github.com/jmoiron/sqlx`).
  - `logger.go`: Logger setup (uses `go.uber.org/zap`).
  - `twilio.go`: Configures Twilio client for SMS (uses `github.com/twilio/twilio-go`).
- **repository/**: Data access implementations (e.g., `user_repository.go`).
- **usecase/**: Business logic (e.g., `user_usecase.go` for user operations).
- **utils/**: Helpers and third-party files (Docker, GitHub Actions CI, OpenAPI).
- **tests/**: Unit tests (uses `github.com/stretchr/testify`).
- **.gitignore**: Ignores build artifacts.
- **go.mod**, **go.sum**: Manages dependencies (`gin`, `sqlx`, `viper`, `zap`, `testify`, `twilio-go`).
- **render.yaml**: Render deployment config.
- **README.md**: Project setup and usage guide.
