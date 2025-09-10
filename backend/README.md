# BioMapper Backend - Advanced Biodiversity Analysis Server

The backend component of BioMapper Lite, providing comprehensive REST APIs for biodiversity analysis, AI/ML model inference, quantum computing integration, and real-time collaborative features.

## 🚀 Features

### Core Services
- **RESTful API**: Comprehensive endpoints for biodiversity analysis
- **Real-time Communication**: WebSocket support for collaborative sessions
- **Authentication & Security**: JWT-based auth with role-based access control
- **File Processing**: Multi-format file upload handling (FASTA, FASTQ, CSV)
- **Database Integration**: MongoDB with optimized schemas for large datasets

### Advanced Integrations
- **NVIDIA BioNeMo**: ESM2, Evo2, Geneformer, AlphaFold2 model integration
- **Quantum Computing**: Qiskit integration with IBM Quantum and local simulators
- **QIIME2 Workflows**: Microbiome analysis pipelines with conda environment management
- **Parabricks Genomics**: GPU-accelerated genomic analysis tools
- **Blockchain Services**: Immutable audit trails for research findings
- **Federated Learning**: Privacy-preserving distributed ML across institutions

## 🏗️ Architecture

### Technology Stack
- **Runtime**: Node.js 18+ with Express.js framework
- **Database**: MongoDB with Mongoose ODM
- **Authentication**: JWT with bcrypt password hashing
- **Security**: Helmet.js, CORS, rate limiting, input validation
- **Real-time**: Socket.IO for collaborative features
- **File Processing**: Multer for multi-format uploads
- **External APIs**: Axios for third-party service integration

### Project Structure
```
backend/
├── server.js                 # Main application entry point
├── package.json             # Dependencies and scripts
├── .env.example            # Environment configuration template
├── routes/                 # API route handlers
│   ├── analysis.js         # Core analysis endpoints
│   ├── auth.js            # Authentication routes
│   ├── collaboration.js    # Collaborative features
│   ├── federated_learning.js # FL endpoints
│   ├── bionemo.js         # NVIDIA BioNeMo integration
│   ├── quantum.js          # Quantum computing routes
│   ├── qiime2.js          # QIIME2 workflow management
│   ├── parabricks.js      # GPU genomics routes
│   ├── blockchain.js      # Blockchain audit services
│   ├── security.js        # Security monitoring
│   └── ...
├── services/              # Business logic services
│   ├── quantum_service.js  # Quantum computing integration
│   ├── bionemo_service.js # AI model management
│   ├── fl_service.js      # Federated learning orchestration
│   └── ...
├── models/               # Database models
│   ├── User.js           # User authentication model
│   ├── Analysis.js       # Analysis job tracking
│   ├── Session.js        # Collaborative session model
│   └── ...
├── middleware/           # Express middleware
│   ├── auth.js           # JWT authentication
│   ├── validation.js     # Input validation
│   ├── rateLimit.js      # Rate limiting
│   └── ...
├── data/                # Static data and configurations
├── scripts/             # Utility scripts
└── test_routes.js       # API testing utilities
```

## 🚀 Quick Start

### Prerequisites
- Node.js 18+
- MongoDB (local or Atlas)
- npm or yarn

### Installation

1. **Install Dependencies**
   ```bash
   cd backend
   npm install
   ```

2. **Environment Configuration**
   ```bash
   cp .env.example .env
   # Edit .env with your configuration
   ```

3. **Start the Server**
   ```bash
   npm start
   # Server runs on http://localhost:5000
   ```

### Environment Variables

#### Required
```env
MONGODB_URI=mongodb://localhost:27017/biomapper
JWT_SECRET=your_super_secret_jwt_key_here
PORT=5000
```

#### Optional API Keys
```env
# AI/ML Services
NVIDIA_API_KEY=your_nvidia_api_key
OPENAI_API_KEY=your_openai_key

# Quantum Computing
IBM_QUANTUM_TOKEN=your_ibm_token

# External Services
MAPBOX_TOKEN=your_mapbox_token
QIIME2_CONDA_ENV=qiime2-2023.5

# Security
ENCRYPTION_KEY=your_encryption_key
```

## 📊 API Endpoints

### Authentication
```
POST /api/auth/register     # User registration
POST /api/auth/login        # User login
POST /api/auth/refresh      # Token refresh
GET  /api/auth/profile      # Get user profile
```

### Core Analysis
```
POST /api/analysis/analyze           # Start biodiversity analysis
GET  /api/analysis/results/:id       # Get analysis results
POST /api/analysis/batch             # Batch processing
GET  /api/analysis/status/:jobId     # Job status tracking
```

### Advanced AI/ML Services
```
POST /api/bionemo/analyze            # BioNeMo model inference
POST /api/bionemo/protein-fold       # Protein structure prediction
POST /api/quantum/analysis           # Quantum-enhanced analysis
POST /api/qiime2/start-analysis      # QIIME2 microbiome workflows
POST /api/parabricks/start-job       # GPU genomics pipelines
```

### Collaboration Features
```
POST /api/collaboration/sessions     # Create collaborative session
GET  /api/collaboration/sessions     # List active sessions
POST /api/collaboration/join/:id     # Join session
WebSocket /socket.io/               # Real-time collaboration
```

### Specialized Services
```
POST /api/case-studies/search        # Search biodiversity case studies
POST /api/cost-analysis/estimate     # Project cost estimation
POST /api/benchmarking/start         # Performance benchmarking
POST /api/policy-simulation/run      # Policy impact modeling
```

### Security & Blockchain
```
POST /api/blockchain/record          # Record with audit trail
GET  /api/blockchain/audit/:id       # Retrieve audit logs
GET  /api/security/threat-level      # Security assessment
POST /api/security/scan-file         # File security scanning
```

## 🔧 Development

### Available Scripts
```bash
npm start          # Start production server
npm run dev        # Start with nodemon (development)
npm test          # Run test suite
npm run lint      # Code linting
```

### Code Quality
- **ESLint**: JavaScript code linting and formatting
- **Prettier**: Automated code formatting
- **Jest**: Unit and integration testing
- **Supertest**: API endpoint testing

### Database Models

#### User Model
```javascript
{
  _id: ObjectId,
  username: String,
  email: String,
  password: String (hashed),
  role: String (Researcher/Scientist/Admin),
  organization: String,
  createdAt: Date,
  lastLogin: Date
}
```

#### Analysis Job Model
```javascript
{
  _id: ObjectId,
  userId: ObjectId,
  type: String (biodiversity/quantum/protein),
  status: String (pending/running/completed/failed),
  inputFiles: [String],
  results: Object,
  createdAt: Date,
  completedAt: Date
}
```

## 🔒 Security Features

### Authentication & Authorization
- JWT-based authentication with refresh tokens
- Role-based access control (RBAC)
- Password hashing with bcrypt
- Session management and timeout

### Data Protection
- Input validation and sanitization
- Rate limiting to prevent abuse
- CORS configuration for cross-origin requests
- Helmet.js security headers

### API Security
- Request/response encryption
- File upload security scanning
- Audit logging for all operations
- GDPR compliance for user data

## 📈 Performance Optimization

### Caching Strategies
- Redis integration for session caching
- Database query optimization
- API response caching
- Static file caching

### Scalability Features
- Horizontal scaling support
- Load balancing configuration
- Database connection pooling
- Asynchronous job processing

## 🧪 Testing

### Unit Tests
```bash
npm test
```

### API Testing
```bash
# Test authentication
curl -X POST http://localhost:5000/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"test@example.com","password":"password"}'

# Test analysis endpoint
curl -X POST http://localhost:5000/api/analysis/analyze \
  -H "Authorization: Bearer YOUR_JWT_TOKEN" \
  -F "file=@sequence.fasta"
```

## 🚀 Deployment

### Docker Deployment
```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY . .
EXPOSE 5000
CMD ["npm", "start"]
```

### Production Configuration
```bash
# Environment variables for production
NODE_ENV=production
MONGODB_URI=mongodb+srv://prod-cluster
JWT_SECRET=production_secret_key
API_RATE_LIMIT=1000
```

## 📞 API Documentation

### Swagger/OpenAPI
Access interactive API documentation at:
```
http://localhost:5000/api-docs
```

### Response Format
```json
{
  "success": true,
  "data": { ... },
  "message": "Operation completed successfully",
  "timestamp": "2024-01-15T10:30:00Z",
  "requestId": "req_123456"
}
```

## 🐛 Troubleshooting

### Common Issues

**Database Connection Failed**
```bash
# Check MongoDB status
sudo systemctl status mongod

# Test connection
mongosh "mongodb://localhost:27017/biomapper"
```

**Port Already in Use**
```bash
# Kill process on port 5000
npx kill-port 5000

# Find process
lsof -ti:5000 | xargs kill
```

**Environment Variables**
```bash
# Validate .env file
node -e "console.log(require('dotenv').config())"
```

## 🤝 Contributing

1. Follow the existing code style
2. Add tests for new features
3. Update API documentation
4. Ensure all tests pass
5. Create detailed commit messages

## 📝 License

This project is licensed under the MIT License.

---

**BioMapper Backend** - Enterprise-grade biodiversity analysis platform backend services.