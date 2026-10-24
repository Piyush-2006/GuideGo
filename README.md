# GuideGo 🌍

### AI-Powered Travel Planning & Local Guide Discovery

GuideGo is a travel-planning web application designed to help travelers explore destinations, discover local guide profiles, and plan personalized trips. The project aims to combine AI-assisted itinerary planning with a secure PayPal Sandbox booking workflow.

> **Project status:** Development in progress. Guide profiles are fictional demo data. PayPal checkout, authorization, capture, and guide confirmation must be tested before being described as a complete working booking flow.

## ✨ Features

- **Guide Discovery:** Browse fictional guide profiles by destination, specialty, and search query.
- **Destination Insights:** View guide catalog statistics and available destinations.
- **AI-Powered Travel Planning:** Planned integration for personalized itineraries based on travel preferences, budget, duration, and interests.
- **Booking Management:** Backend booking records with server-side price calculation and idempotency support.
- **PayPal Sandbox Integration:** Planned checkout using PayPal's sandbox environment for development and testing.
- **Secure Backend:** FastAPI endpoints, environment-based credentials, and protected PayPal health checks.
- **Responsive Interface:** React-based frontend for browsing guide profiles and exploring travel options.

## 🛠️ Technology Stack

| Component | Technologies |
|---|---|
| Frontend | React, TypeScript, Vite |
| Backend | Python, FastAPI |
| Database | SQLite |
| API Validation | Pydantic |
| Payments | PayPal Sandbox — integration in progress |
| AI | Planned AI-provider integration |
| Version Control | Git, GitHub |

## 🏗️ Project Structure

```text
GuideGo/
├── artifacts/
│   └── guidego/          # Frontend application
├── guidego/
│   ├── api.py            # FastAPI routes
│   ├── database.py       # Database and booking operations
│   ├── schemas.py        # Request and response schemas
│   └── seeds.py          # Fictional demo guide data
├── tests/                # Backend tests
├── main.py               # Application entry point
├── pyproject.toml        # Python dependencies
├── package.json          # JavaScript workspace scripts
├── pnpm-lock.yaml        # JavaScript dependency lockfile
├── .gitignore
├── LICENSE
└── README.md
```

*The structure above is illustrative; update it to match the files actually committed to the repository.*

## 🚀 Getting Started

### Prerequisites

- Python 3.13 or a compatible version supported by the project
- Node.js and pnpm
- Git
- A PayPal Developer account for Sandbox testing

### 1. Clone the repository

```bash
git clone https://github.com/Piyush-2006/GuideGo.git
cd GuideGo
```

### 2. Install JavaScript dependencies

```bash
pnpm install
```

### 3. Configure environment variables

Configure secrets through your development environment or hosting provider. Never commit credentials to GitHub.

Example variable names:

```env
PAYPAL_CLIENT_ID=your_sandbox_client_id
PAYPAL_CLIENT_SECRET=your_sandbox_client_secret
PAYPAL_HEALTH_TOKEN=your_private_health_check_token

# Optional AI provider configuration
LLM_BASE_URL=
LLM_API_KEY=
LLM_MODEL=
```

Replace placeholders using your own credentials. Do not publish real secrets.

### 4. Start the backend

Use the backend command configured by the project. For the existing workspace, the API Server workflow uses Uvicorn to run:

```bash
uvicorn guidego.api:app --host 0.0.0.0 --port 8080
```

If the project uses a workspace-specific launcher, follow its configured development command instead.

### 5. Start the frontend

Run the frontend development command defined in the root `package.json` or the frontend workspace's `package.json`. For example:

```bash
pnpm run guidego
```

The exact command depends on the scripts configured in the committed project.

## 💳 PayPal Sandbox

GuideGo is intended to use PayPal Sandbox for simulated payment testing.

The planned booking lifecycle is:

1. Traveler selects a fictional guide and travel dates.
2. Backend validates the request and calculates the booking amount.
3. Backend creates a PayPal order with authorization intent.
4. Traveler approves the order using a Sandbox buyer account.
5. Backend verifies the order and authorizes payment.
6. Guide confirmation triggers payment capture.
7. Cancellation and payment failures are handled according to the implemented payment state.

**Important:** Creating an order is not the same as authorizing or capturing payment. Do not consider a booking paid until the backend verifies the corresponding PayPal transaction.

## 🧪 Testing

Run the available backend tests using the test command configured in the project. For example, if `pytest` is installed:

```bash
pytest
```

Test guide discovery, invalid booking inputs, duplicate requests, PayPal Sandbox errors, and payment-state transitions before demonstrating the complete flow.

## 🔐 Security

- Never commit API keys, client secrets, passwords, or private tokens.
- Keep `.env` files and local secrets excluded through `.gitignore`.
- Use server-side price calculations rather than trusting client-submitted prices.
- Validate payment state through PayPal's server-side API.
- Use Sandbox accounts for development and testing.
- Do not store or expose PayPal access tokens in frontend code or API responses.

## 🗺️ Roadmap

- [ ] AI-generated personalized itineraries
- [ ] Improved guide matching
- [ ] Complete booking creation and checkout UI
- [ ] PayPal order approval and authorization
- [ ] Protected guide confirmation and payment capture
- [ ] Cancellation and refund handling
- [ ] Automated integration tests
- [ ] Public deployment and end-to-end demo

## 👨‍💻 Author

**Piyush Kumar**

GitHub: [@Piyush-2006](https://github.com/Piyush-2006)

## 📄 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

## ⚠️ Disclaimer

GuideGo is a development and demonstration project. Guide profiles are fictional, and any payment integration should be treated as a Sandbox demonstration until the complete workflow has been implemented and verified.
