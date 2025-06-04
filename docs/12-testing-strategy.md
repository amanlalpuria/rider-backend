# 🧪 Testing Strategy

To ensure RiderX is reliable and bug-free, we adopt a multi-layered testing approach covering backend, frontend, and infrastructure.

---

## ✅ Unit Testing

- **Tools**: JUnit + Mockito (Spring Boot)
- Test service methods, mappers, validators
- Example: fare calculation, distance logic, OTP generator

---

## 🧩 Integration Testing

- REST API contract tests using Spring’s `@WebMvcTest`
- H2 in-memory DB for test isolation
- Payment and notification mock services

---

## 🧪 End-to-End (E2E) Testing

- **Tool**: Postman Collection Runner / Playwright (future)
- Simulate signup → book ride → pay → rate ride
- Daily test suite for staging environment

---

## 🔁 CI/CD Pipeline Testing

- Linting + test coverage check in GitHub Actions
- Docker container boot test with health endpoint check

---

## 📲 Mobile Testing

- Flutter integration tests using `integration_test` package
- Simulated device taps and input

---

## 🔬 Load & Stress Testing

- Tool: k6 or JMeter
- Simulate 10k+ ride requests under surge

---

## 📈 Coverage & Quality

- Goal: 80%+ coverage on services/controllers
- Tools: Jacoco, SonarQube (optional)
- Code review checklist enforced via PR templates
