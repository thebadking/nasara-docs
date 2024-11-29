# Nasara Connect Technical Documentation

## System Architecture

### Frontend Architecture

- **Framework**: Next.js (React)
- **Deployment**: Vercel
- **Key Features**:
  - Server-side rendering
  - API routes
  - Dynamic routing
  - TypeScript support

### Backend Services

- **Database**: Supabase (PostgreSQL)
- **Authentication**: Supabase Auth
- **Vector Store**: pgvector for RAG implementation
- **Deployment**: Coolify with Docker containers for custom microservices that should not be serverless
- **Services**:
  - Golang microservices (planned)
  - Python microservices (planned)

## Core Components

### Dynamic Form Builder

- **Technology**: Custom implementation with Zod and React Hook Form
- **Features**:
  - Client-side validation
  - Server-side validation
  - Dynamic form generation
  - Custom field types
  - Conditional logic
  - Real-time validation

### Risk Assessment Table

- **Technology**: AG Grid Enterprise
- **Features**:
  - Custom cell renderers
  - Real-time data updates
  - Sorting and filtering
  - Data export
  - Custom editing interfaces
  - AI integration for summary generation (required by FCA)

### AI Integration

- **Components**:
  - OpenAI integration (subject to change)
  - LangChain for agent orchestration
  - RAG framework implementation
  - Vector embeddings in PostgreSQL with custom indexing for easy update

### Payment Processing

- **Current**: Stripe Integration
  - Subscription management
  - Payment processing
  - Webhook handling
- **Planned**: XRPL Integration
  - Cross-border payments
  - Real-time settlement

### Blockchain Integration

- **Wallet**: Rainbow Wallet Integration
  - Web3 authentication
  - Transaction signing
  - Account management
- **Future XRPL Features**:
  - Payment channels
  - Cross-border settlement
  - Compliance automation

## Infrastructure

# Database Overview

## Core Business Tables

### Organization Management

- Organizations and entities tracking
- Role-based access control for organizations
- Entity-specific permissions and roles
- Multi-level organizational structure support

### Risk Assessment System

- Risk group categorization
- Predefined risk scenarios
- Entity risk assessments and monitoring
- Control measures tracking
- Compliance status management

### Dynamic Form System

- Configurable form definitions
- Complex form structure support
- Multiple answer types and validations
- AI-assisted form completion
- Form submission tracking

### Remittance System

- Recipient contact management
- Transaction logging and tracking
- Multi-currency support
- Payment status monitoring

### AI and Document Management

- Document indexing system
- Vector embeddings storage
- RAG framework support
- AI processing status tracking

### Security and Authentication

- User profile management
- Granular permission system
- Two-factor authentication
- Session management
- Role-based access control

### Payment Processing

- Product and pricing management
- Subscription tracking
- Payment status monitoring
- Multi-tier pricing support

### API Architecture

```
/api
  /chat                    # AI and RAG endpoints
    /agents               # AI agent management
    /risk_plan_summary    # Risk assessment AI analysis
    /retrieval           # Document retrieval
    /indexer             # Document indexing

  /webhooks              # Payment webhook handlers

  /create-checkout-session  # Stripe payment integration
  /create-portal-link      # Stripe customer portal

  /ch-uk                 # Companies House UK integration
```

## Security Features

### Authentication

- Supabase JWT-based auth
- Custom granular permission control system that includes RBAC
- Multi-factor authentication for specific endpoints with OTP
- Session management

### Data Security

- End-to-end encryption
- Secure data storage
- Regular backups
- Audit logging

## Development Workflow

### CI/CD Pipeline

- **Platform**: Coolify
- **Features**:
  - Automated deployments
  - Container orchestration
  - Environment management
  - Rollback capabilities

## Monitoring and Analytics

- Possiblity of using PostHog for analytics and Feature Flags

### Infrastructure Monitoring

- Most of the infrastructure does not require monitoring because of its serverless architecture, but certain endpoints for external services should have monitoring

### System Monitoring (trough Vercel)

- Performance metrics
- Error tracking
- Usage analytics
- Security monitoring

### Business Intelligence

- Transaction analytics - 
- User behavior tracking  - Can be done by PostHog since it keeps user data private
- Compliance reporting - The platform itself is for complicance so it can leverage itself for compliance reports
- Risk assessment metrics (same as above)

## Future Enhancements

### Planned Technical Improvements

1. XRPL Integration

   - Payment channel implementation
   - Smart contract deployment
   - Cross-chain bridges

2. AI Capabilities

   - Multi knowledge bases for advanced RAG implementations
   - Custom AI models
   - Automated compliance checking

3. Security Upgrades
   - Advanced encryption
   - Enhanced audit trails
   - Automated security testing

### Production Environment

- Vercel (https://vercel.com/) Serverless Platform
- Supabase (https://supabase.com/) Database + Auth Service (Serverless)
