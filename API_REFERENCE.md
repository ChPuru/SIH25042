# BioMapper Lite API Reference

Complete API documentation for the BioMapper Lite biodiversity analysis platform.

## 📋 Table of Contents

- [Authentication](#authentication)
- [Core Analysis APIs](#core-analysis-apis)
- [Advanced AI/ML APIs](#advanced-aiml-apis)
- [Collaboration APIs](#collaboration-apis)
- [Federated Learning APIs](#federated-learning-apis)
- [Specialized Analysis APIs](#specialized-analysis-apis)
- [Security & Blockchain APIs](#security--blockchain-apis)
- [Real-time WebSocket APIs](#real-time-websocket-apis)
- [Error Handling](#error-handling)
- [Rate Limiting](#rate-limiting)

## 🔐 Authentication

All API endpoints require JWT authentication except for authentication endpoints themselves.

### Headers
```
Authorization: Bearer <your_jwt_token>
Content-Type: application/json
```

### Authentication Endpoints

#### POST /api/auth/register
Register a new user account.

**Request Body:**
```json
{
  "username": "researcher123",
  "email": "researcher@university.edu",
  "password": "secure_password_123",
  "organization": "University of Biodiversity",
  "role": "Researcher"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "user": {
      "id": "user_123",
      "username": "researcher123",
      "email": "researcher@university.edu",
      "role": "Researcher",
      "organization": "University of Biodiversity"
    },
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
  },
  "message": "User registered successfully"
}
```

#### POST /api/auth/login
Authenticate user and receive JWT token.

**Request Body:**
```json
{
  "email": "researcher@university.edu",
  "password": "secure_password_123"
}
```

#### POST /api/auth/refresh
Refresh JWT token before expiration.

#### GET /api/auth/profile
Get current user profile information.

---

## 🔬 Core Analysis APIs

### POST /api/analysis/analyze
Upload and analyze FASTA/FASTQ sequence files.

**Request:**
- **Method:** POST
- **Content-Type:** multipart/form-data
- **File:** `sequenceFile` (FASTA/FASTQ format)
- **Parameters:**
  ```json
  {
    "analysisType": "comprehensive",
    "metadata": {
      "sampleLocation": "Amazon Rainforest",
      "collectionDate": "2024-01-15",
      "researcher": "Dr. Jane Smith"
    }
  }
  ```

**Response:**
```json
{
  "success": true,
  "data": {
    "jobId": "analysis_123456",
    "status": "processing",
    "estimatedTime": 300,
    "filesProcessed": 1,
    "sequencesFound": 150
  },
  "message": "Analysis job started successfully"
}
```

### GET /api/analysis/results/:jobId
Retrieve analysis results.

**Response:**
```json
{
  "success": true,
  "data": {
    "jobId": "analysis_123456",
    "status": "completed",
    "results": {
      "species_identified": 45,
      "novel_sequences": 12,
      "biodiversity_index": 3.24,
      "dominant_species": "Panthera onca",
      "analysis_metadata": { ... }
    },
    "visualizations": {
      "phylogenetic_tree": "url_to_svg",
      "abundance_chart": "url_to_png",
      "diversity_plot": "url_to_json"
    },
    "download_links": {
      "csv_report": "url_to_csv",
      "pdf_report": "url_to_pdf",
      "fasta_processed": "url_to_fasta"
    }
  }
}
```

### POST /api/analysis/batch
Process multiple sequence files simultaneously.

**Request:**
- **Files:** Multiple FASTA/FASTQ files
- **Parameters:**
  ```json
  {
    "parallelProcessing": true,
    "priority": "high",
    "notificationEmail": "researcher@university.edu"
  }
  ```

### GET /api/analysis/status/:jobId
Get real-time job status and progress.

**Response:**
```json
{
  "success": true,
  "data": {
    "jobId": "analysis_123456",
    "status": "processing",
    "progress": 75,
    "stage": "AI Model Inference",
    "estimatedTimeRemaining": 45,
    "currentStep": "Running BioNeMo analysis",
    "totalSteps": 8
  }
}
```

---

## 🤖 Advanced AI/ML APIs

### POST /api/bionemo/analyze
NVIDIA BioNeMo model inference for protein analysis.

**Request:**
```json
{
  "model": "esm2_t33_650M_UR50D",
  "sequences": [
    {
      "id": "protein_1",
      "sequence": "MKLVLSVFAVLLVLHFVQGS"
    }
  ],
  "tasks": ["folding", "function_prediction", "structure_analysis"]
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "jobId": "bionemo_789",
    "results": [
      {
        "sequence_id": "protein_1",
        "folding_confidence": 0.89,
        "predicted_structure": "pdb_data_here",
        "function_prediction": "Enzyme inhibitor",
        "domains_identified": ["alpha_helix", "beta_sheet"]
      }
    ]
  }
}
```

### POST /api/bionemo/protein-fold
Protein structure prediction using AlphaFold2.

### POST /api/quantum/analysis
Quantum-enhanced sequence analysis.

**Request:**
```json
{
  "algorithm": "quantum_alignment",
  "sequences": ["ATCGATCG", "ATCGTTCG"],
  "optimization": "sequence_similarity",
  "backend": "ibm_quantum" // or "local_simulator"
}
```

### POST /api/qiime2/start-analysis
QIIME2 microbiome analysis workflows.

**Request:**
```json
{
  "inputFiles": ["sequences.fastq", "metadata.tsv"],
  "workflow": "diversity_analysis",
  "parameters": {
    "trunc_len": 250,
    "sample_depth": 1000,
    "metadata_column": "sample_type"
  }
}
```

### POST /api/parabricks/start-job
GPU-accelerated genomics pipelines.

---

## 🤝 Collaboration APIs

### POST /api/collaboration/sessions
Create a new collaborative analysis session.

**Request:**
```json
{
  "name": "Amazon Biodiversity Study 2024",
  "description": "Multi-institutional analysis of Amazon rainforest samples",
  "maxParticipants": 10,
  "dataAccess": "shared",
  "permissions": {
    "canEdit": true,
    "canDelete": false,
    "canInvite": true
  }
}
```

### GET /api/collaboration/sessions
List active collaborative sessions.

### POST /api/collaboration/join/:sessionId
Join an existing collaborative session.

### POST /api/collaboration/annotations
Add sequence annotations in collaborative sessions.

**Request:**
```json
{
  "sessionId": "session_123",
  "sequenceId": "seq_456",
  "annotation": {
    "type": "species_identification",
    "species": "Panthera onca",
    "confidence": 0.95,
    "notes": "Confirmed by expert review",
    "references": ["doi:10.1234/example"]
  }
}
```

---

## 🔄 Federated Learning APIs

### POST /api/federated-learning/start
Initialize a federated learning session.

**Request:**
```json
{
  "name": "Global Biodiversity ML Model",
  "modelType": "species_classifier",
  "datasetType": "genomic_sequences",
  "privacyLevel": "high",
  "maxRounds": 50,
  "minClients": 5,
  "aggregationMethod": "fedavg"
}
```

### GET /api/federated-learning/status
Get federated learning session status.

### POST /api/federated-learning/contribute
Submit local model updates.

**Request:**
```json
{
  "sessionId": "fl_session_123",
  "modelUpdate": {
    "weights": "encrypted_model_weights",
    "metadata": {
      "localEpochs": 10,
      "localBatchSize": 32,
      "dataSize": 1000
    }
  },
  "clientSignature": "digital_signature"
}
```

---

## 🎯 Specialized Analysis APIs

### POST /api/case-studies/search
Search real-world biodiversity case studies.

**Request:**
```json
{
  "query": "Amazon rainforest conservation",
  "filters": {
    "region": "South America",
    "species": "Panthera onca",
    "timeRange": "2020-2024",
    "outcome": "successful"
  },
  "limit": 20
}
```

### POST /api/cost-analysis/estimate
Generate project cost estimates.

**Request:**
```json
{
  "project": {
    "name": "Amazon Monitoring Network",
    "duration": 24, // months
    "region": "Amazon Basin"
  },
  "resources": {
    "sequencing": {
      "platform": "illumina",
      "samples": 1000,
      "readLength": 150
    },
    "compute": {
      "gpuHours": 500,
      "cpuHours": 2000,
      "storage": "10TB"
    },
    "personnel": {
      "researchers": 5,
      "technicians": 3,
      "bioinformaticians": 2
    }
  }
}
```

### POST /api/benchmarking/start
Compare against established bioinformatics pipelines.

### POST /api/policy-simulation/run
Environmental policy impact modeling.

### POST /api/economic-modeling/forecast
Economic forecasting for conservation projects.

### POST /api/climate-integration/analyze
Climate change impact analysis on biodiversity.

---

## 🔒 Security & Blockchain APIs

### POST /api/blockchain/record
Record findings with blockchain audit trail.

**Request:**
```json
{
  "finding": {
    "type": "species_discovery",
    "species": "Unknown species X",
    "location": {
      "lat": -3.4653,
      "lng": -62.2159,
      "accuracy": 10
    },
    "evidence": {
      "genetic_sequence": "ATCG...",
      "photographic_evidence": "image_url",
      "collection_method": "eDNA sampling"
    },
    "researcher": "Dr. Jane Smith",
    "institution": "University of Biodiversity"
  },
  "metadata": {
    "conservation_status": "potentially_endangered",
    "policy_implications": "protected_area_designation"
  }
}
```

### GET /api/blockchain/audit/:sessionId
Retrieve immutable audit logs.

### GET /api/security/threat-level
Get current security threat assessment.

### POST /api/security/scan-file
Scan uploaded files for security threats.

---

## 🌐 Real-time WebSocket APIs

### WebSocket: /socket.io/
Real-time collaborative updates.

**Events:**
```javascript
// Join session
socket.emit('join_session', { sessionId: 'session_123' });

// Receive updates
socket.on('session_update', (data) => {
  console.log('Session updated:', data);
});

// Send annotation
socket.emit('add_annotation', {
  sessionId: 'session_123',
  annotation: { ... }
});
```

### WebSocket: /fl-updates
Federated learning progress updates.

### WebSocket: /analysis-updates
Live analysis progress tracking.

**Example:**
```javascript
const socket = io('ws://localhost:5000');

socket.on('analysis_progress', (data) => {
  console.log(`Job ${data.jobId}: ${data.progress}% complete`);
  console.log(`Current stage: ${data.stage}`);
});
```

---

## ❌ Error Handling

### Standard Error Response Format
```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid file format. Only FASTA and FASTQ are supported.",
    "details": {
      "field": "sequenceFile",
      "expected": ["fasta", "fastq"],
      "received": "pdf"
    },
    "timestamp": "2024-01-15T10:30:00Z",
    "requestId": "req_123456"
  }
}
```

### Common Error Codes

| Code | Description | HTTP Status |
|------|-------------|-------------|
| `VALIDATION_ERROR` | Invalid request data | 400 |
| `AUTHENTICATION_ERROR` | Invalid or missing JWT | 401 |
| `AUTHORIZATION_ERROR` | Insufficient permissions | 403 |
| `NOT_FOUND` | Resource not found | 404 |
| `RATE_LIMIT_EXCEEDED` | Too many requests | 429 |
| `INTERNAL_ERROR` | Server error | 500 |
| `SERVICE_UNAVAILABLE` | External service down | 503 |

### Error Recovery
```javascript
// Example error handling
try {
  const response = await fetch('/api/analysis/analyze', {
    method: 'POST',
    body: formData,
    headers: {
      'Authorization': `Bearer ${token}`
    }
  });

  if (!response.ok) {
    const error = await response.json();
    switch (error.error.code) {
      case 'RATE_LIMIT_EXCEEDED':
        // Wait and retry
        await new Promise(resolve => setTimeout(resolve, 60000));
        return retryRequest();
      case 'AUTHENTICATION_ERROR':
        // Refresh token
        await refreshToken();
        return retryRequest();
      default:
        throw new Error(error.error.message);
    }
  }

  return await response.json();
} catch (error) {
  console.error('API Error:', error);
  // Handle network errors, timeouts, etc.
}
```

---

## 📊 Rate Limiting

### Limits by Endpoint Category

| Category | Limit | Window |
|----------|-------|--------|
| Authentication | 10 requests | 15 minutes |
| Core Analysis | 100 requests | 1 hour |
| File Upload | 50 requests | 1 hour |
| AI/ML Services | 50 requests | 1 hour |
| Collaboration | 500 requests | 1 hour |
| Federated Learning | 200 requests | 1 hour |
| Specialized Analysis | 100 requests | 1 hour |
| Security & Blockchain | 200 requests | 1 hour |

### Rate Limit Headers
```http
X-RateLimit-Limit: 100
X-RateLimit-Remaining: 95
X-RateLimit-Reset: 1640995200
X-RateLimit-Retry-After: 3600
```

### Handling Rate Limits
```javascript
// Check rate limit headers
const response = await fetch('/api/analysis/analyze', {
  method: 'POST',
  body: formData
});

if (response.status === 429) {
  const retryAfter = response.headers.get('X-RateLimit-Retry-After');
  console.log(`Rate limited. Retry after ${retryAfter} seconds`);

  // Wait and retry
  setTimeout(() => {
    retryRequest();
  }, retryAfter * 1000);
}
```

---

## 📝 API Versioning

### Version Header
```
Accept: application/vnd.biomapper.v1+json
```

### Version Support
- **v1** (Current): Full feature set
- **Legacy**: Deprecated endpoints (supported until 2025)

### Breaking Changes
Breaking changes will be communicated 90 days in advance with:
- Email notifications to registered users
- Documentation updates
- Migration guides

---

## 🔧 SDKs and Libraries

### JavaScript/TypeScript SDK
```bash
npm install @biomapper/sdk
```

```javascript
import { BioMapperClient } from '@biomapper/sdk';

const client = new BioMapperClient({
  apiKey: 'your_jwt_token',
  baseURL: 'https://api.biomapper-lite.org'
});

// Upload and analyze sequences
const result = await client.analysis.analyze(file, {
  analysisType: 'comprehensive'
});

console.log('Analysis complete:', result);
```

### Python SDK
```bash
pip install biomapper-lite-sdk
```

```python
from biomapper import BioMapperClient

client = BioMapperClient(api_key='your_jwt_token')

# Analyze sequences
result = client.analysis.analyze('sequences.fasta')
print(f"Identified {result.species_count} species")
```

---

## 📞 Support

### Getting Help
- **API Status**: https://status.biomapper-lite.org
- **Developer Forum**: https://community.biomapper-lite.org
- **GitHub Issues**: https://github.com/biocloud/biomappler-lite/issues
- **Email Support**: api-support@biomapper-lite.org

### Service Level Agreement
- **Uptime**: 99.9% guaranteed
- **Response Time**: <200ms for API calls
- **Support**: 24/7 for critical issues
- **Updates**: Monthly feature releases

---

**Last Updated**: January 2025
**API Version**: v1.0
**Contact**: api-support@biomapper-lite.org