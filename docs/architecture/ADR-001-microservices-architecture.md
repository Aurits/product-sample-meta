#### `/docs/architecture/ADR-001-microservices-architecture.md`
```markdown
# ADR-001: Microservices Architecture

## Status
Accepted

## Context
The Product Sample platform needs to handle:
- Multiple data sources with different processing requirements
- Variable load patterns (batch vs. real-time)
- Independent scaling of components
- Different technology requirements per service

## Decision
We will adopt a microservices architecture with the following services:

### Core Services
1. **API Gateway Service**
   - Single entry point for all client requests
   - Request routing and load balancing
   - Rate limiting and authentication

2. **Data Service**
   - Handles multiple data source types
   - Data validation and transformation
   - Queue management for processing

3. **Processing Service**
   - Real-time and batch processing
   - Data aggregation and computation
   - Business logic execution

4. **Storage Service**
   - Data optimization
   - Data partitioning and archival
   - Query optimization

5. **UI Service**
   - Configuration storage
   - User preferences
   - Session management

### Communication
- **Synchronous**: REST APIs for client-facing operations
- **Asynchronous**: RabbitMQ for processing pipeline
- **Caching**: Redis for session and query caching

## Consequences
### Positive
- Independent scaling based on load
- Technology flexibility per service
- Fault isolation
- Easier team organization

### Negative
- Increased operational complexity
- Network latency between services
- Distributed transaction challenges
- More complex debugging