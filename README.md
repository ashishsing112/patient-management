# Patient Management

This repository contains a simple demo of a patient management system composed of two Spring Boot microservices. It also includes sample HTTP and gRPC request files that can be used with HTTP or gRPC clients during development.

## Services

### Patient Service

- Location: `patient-service`
- Exposes a REST API on port `4000`
- Provides CRUD operations for patients using Spring Data JPA
- See `api-request/patient-service/` for sample HTTP requests
- Docker image exposes port `4000`

### Billing Service

- Location: `billing-service`
- Provides a gRPC service on port `9001`
- The service exposes a single `CreateBillingAccount` RPC
- Sample gRPC request file: `grpc-request/billing-service/create-billing-account.http`
- Docker image exposes ports `4001` (HTTP) and `9001` (gRPC)

## Building and Running

Both services use Maven. From within each service directory you can run the application locally using:

```bash
mvn spring-boot:run
```

To build Docker images run:

```bash
docker build -t patient-service ./patient-service
docker build -t billing-service ./billing-service
```

Then run each container exposing the appropriate ports:

```bash
docker run -p 4000:4000 patient-service
docker run -p 4001:4001 -p 9001:9001 billing-service
```

## Repository Layout

```
api-request/          # HTTP request examples for the patient service
billing-service/      # Billing service source code and Dockerfile
grpc-request/         # gRPC request examples for the billing service
patient-service/      # Patient service source code and Dockerfile
```

The `api-request` and `grpc-request` directories contain files usable by tools such as IntelliJ HTTP Client or `grpcurl` for manual testing.

## Notes

These projects are intended for demonstration and learning purposes and do not include production configurations such as databases or security. Feel free to extend them to suit your needs.
