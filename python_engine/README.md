# BioMapper Python Engine - Advanced AI/ML Analysis Platform

The Python Engine component of BioMapper Lite, providing cutting-edge AI/ML capabilities for biodiversity analysis, quantum computing integration, and advanced bioinformatics workflows.

## 🚀 Features

### Core AI/ML Capabilities
- **Multi-Model Hybrid Analysis**: Intelligent pipeline combining BLAST, local LLMs, and cloud AI
- **Quantum Computing Integration**: Qiskit-powered quantum algorithms for sequence analysis
- **Protein Structure Prediction**: ESM2, Evo2, Geneformer, and AlphaFold2 integration
- **GPU-Accelerated Genomics**: NVIDIA Parabricks integration for high-performance analysis
- **Microbiome Analysis**: QIIME2-compatible workflows with enhanced performance
- **Federated Learning**: Privacy-preserving distributed ML across research institutions

### Advanced Analysis Modules
- **Sequence Analysis Toolkit**: Comprehensive bioinformatics analysis suite
- **Phylogenetic Analysis**: Advanced tree construction and comparative genomics
- **Metagenomic Profiling**: Taxonomic and functional analysis of microbial communities
- **Machine Learning Models**: Custom models for species classification and novelty detection
- **Real-time Processing**: Asynchronous job processing with progress tracking

## 🏗️ Architecture

### Technology Stack
- **Core Framework**: Python 3.11+ with async/await support
- **ML Libraries**: PyTorch, TensorFlow, scikit-learn, transformers
- **Bioinformatics**: BioPython, QIIME2, scikit-bio, biom-format
- **Quantum Computing**: Qiskit with IBM Quantum and local simulator
- **Web Framework**: FastAPI for high-performance API serving
- **Data Processing**: pandas, NumPy, SciPy for advanced analytics
- **Visualization**: matplotlib, seaborn, plotly for interactive plots

### Project Structure
```
python_engine/
├── main_ensemble.py              # Main hybrid analysis orchestrator
├── api_server.py                # FastAPI server for external access
├── fastapi_server.py            # Alternative FastAPI implementation
├── app.py                        # Flask-based web interface
├── requirements.txt               # Python dependencies
├── setup.py                      # Package configuration
├── biomapper_lite/               # Main package
│   ├── core/                     # Core analysis modules
│   │   ├── abundance_estimator.py # Biodiversity abundance estimation
│   │   ├── classifier_fallback.py # Fallback classification
│   │   ├── classifier_real.py     # Primary classification
│   │   └── aligner.py             # Sequence alignment utilities
│   └── utils/                     # Utility functions
│       └── languages.py           # Language processing utilities
├── scripts/                      # Utility scripts
├── data/                         # Sample data and test files
├── db/                           # Local databases (BLAST, taxonomic)
├── federated_learning/           # FL implementation
├── notebooks/                    # Jupyter notebooks for analysis
└── quantum_jobs/                 # Quantum computing job management
```

### Analysis Scripts
- `run_sequence_analysis.py` - Comprehensive sequence analysis
- `run_quantum.py` - Quantum computing workflows
- `run_bionemo.py` - Protein structure prediction
- `run_parabricks.py` - GPU-accelerated genomics
- `run_qiime2.py` - Microbiome analysis pipelines
- `run_mamba_dna.py` - DNA sequence modeling
- `run_microbiome.py` - Advanced microbial analysis
- `run_xai.py` - Explainable AI analysis

## 🚀 Quick Start

### Prerequisites
- **Python 3.11+**
- **pip** package manager
- **Virtual environment** (recommended)
- **NVIDIA GPU** (optional, for GPU acceleration)

### Installation

1. **Create Virtual Environment**
   ```bash
   cd python_engine
   python -m venv biomapper_env
   source biomapper_env/bin/activate  # Linux/Mac
   # biomapper_env\Scripts\activate   # Windows
   ```

2. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Install Optional Heavy Dependencies**
   ```bash
   # QIIME2 (requires conda)
   conda install -c qiime2 -c conda-forge qiime2=2023.5

   # NVIDIA BioNeMo (if you have GPU)
   pip install nvidia-bionemo

   # Ollama for local LLM (optional)
   # Install from: https://ollama.ai/
   ollama pull llama3:8b-instruct-q4_K_M
   ```

### Basic Usage

1. **Run Hybrid Analysis**
   ```bash
   python main_ensemble.py path/to/your/sequences.fasta
   ```

2. **Start API Server**
   ```bash
   python api_server.py
   # Server runs on http://localhost:8000
   ```

3. **Run Specific Analysis**
   ```bash
   # Sequence analysis
   python run_sequence_analysis.py input.fasta

   # Quantum analysis
   python run_quantum.py sequences.fasta

   # Protein structure prediction
   python run_bionemo.py protein_sequences.fasta
   ```

## 📊 Analysis Capabilities

### Multi-Model Hybrid Pipeline
The engine uses an intelligent multi-stage analysis approach:

1. **Local BLAST Search**: Fast database matching against curated sequences
2. **Local LLM Analysis**: Ollama-powered species identification
3. **Cloud AI Models**: Advanced ML models for complex cases
4. **Fallback Analysis**: Rule-based classification for edge cases

### Supported File Formats
- **FASTA/FASTQ**: Standard sequence formats
- **CSV/TSV**: Tabular data with metadata
- **BIOM**: Microbiome data format
- **Newick**: Phylogenetic tree format
- **PDB**: Protein structure format

### Output Formats
- **JSON**: Structured analysis results
- **CSV**: Spreadsheet-compatible data
- **HTML**: Interactive visualizations
- **PDF**: Publication-ready reports

## 🔧 Configuration

### Environment Variables
```bash
# API Configuration
BIOMAPPER_API_HOST=localhost
BIOMAPPER_API_PORT=8000

# External Services
OLLAMA_API_URL=http://localhost:11434/api/generate
OLLAMA_MODEL=llama3:8b-instruct-q4_K_M

# Database Paths
LOCAL_BLAST_DB_PATH=python_engine/db/BioMapperDB
TAXDUMP_PATH=python_engine/db/taxdump

# GPU Configuration
CUDA_VISIBLE_DEVICES=0
TF_FORCE_GPU_ALLOW_GROWTH=true

# Quantum Computing
IBM_QUANTUM_TOKEN=your_ibm_token
```

### Model Configuration
```python
# In your analysis script
from biomapper_lite.core.classifier_real import BioAnalyzer

analyzer = BioAnalyzer(
    model_path="path/to/model",
    confidence_threshold=0.8,
    use_gpu=True,
    batch_size=32
)
```

## 📈 Advanced Usage Examples

### Hybrid Analysis Pipeline
```python
from main_ensemble import analyze_with_hybrid_strategy
import pandas as pd

# Run complete analysis
results_df, biodiversity_metrics, abundance = analyze_with_hybrid_strategy("data/sequences.fasta")

# Access results
print("Species identified:", results_df['Predicted_Species'].unique())
print("Biodiversity metrics:", biodiversity_metrics)
print("Abundance estimates:", abundance)
```

### Quantum Sequence Analysis
```python
from run_quantum import QuantumSequenceAnalyzer

analyzer = QuantumSequenceAnalyzer()
results = analyzer.analyze_sequences("sequences.fasta")

# Results include quantum-enhanced alignments and classifications
for result in results:
    print(f"Sequence: {result['id']}")
    print(f"Quantum alignment score: {result['quantum_score']}")
    print(f"Predicted species: {result['species']}")
```

### Protein Structure Prediction
```python
from run_bionemo import ProteinStructurePredictor

predictor = ProteinStructurePredictor(model="esm2")
structures = predictor.predict_structures("protein_sequences.fasta")

# Generate 3D visualizations
for structure in structures:
    predictor.visualize_structure(structure, output_format="pdb")
```

### Microbiome Analysis
```python
from run_qiime2 import MicrobiomeAnalyzer

analyzer = MicrobiomeAnalyzer()
results = analyzer.run_analysis(
    input_files=["sequences.fastq", "metadata.tsv"],
    analysis_type="diversity",
    parameters={"sampling_depth": 1000}
)

# Access taxonomic profiles and diversity metrics
taxa_table = results['taxonomy']
diversity_metrics = results['diversity']
```

## 🔧 Development & Testing

### Running Tests
```bash
# Install test dependencies
pip install pytest pytest-asyncio pytest-cov

# Run all tests
pytest

# Run with coverage
pytest --cov=biomapper_lite --cov-report=html
```

### Code Quality
```bash
# Install development tools
pip install black flake8 mypy

# Format code
black .

# Lint code
flake8 biomapper_lite/

# Type checking
mypy biomapper_lite/
```

### Adding New Analysis Modules
```python
# Create new analyzer in biomapper_lite/core/
class NewAnalyzer:
    def __init__(self, config=None):
        self.config = config or {}

    def analyze(self, input_data):
        # Your analysis logic here
        return results

    def validate_input(self, data):
        # Input validation
        return True

# Create corresponding run script
# python run_new_analysis.py input_file
```

## 🚀 API Server

### FastAPI Server
```bash
# Start the FastAPI server
python fastapi_server.py

# Access API documentation
# http://localhost:8000/docs
```

### Available Endpoints
```
GET  /health              # Health check
POST /analyze/sequences   # Sequence analysis
POST /analyze/proteins    # Protein analysis
POST /analyze/microbiome  # Microbiome analysis
POST /analyze/quantum      # Quantum analysis
GET  /jobs/{job_id}       # Job status
GET  /results/{job_id}    # Analysis results
```

### API Usage Example
```python
import requests

# Submit analysis job
response = requests.post(
    "http://localhost:8000/analyze/sequences",
    files={"file": open("sequences.fasta", "rb")},
    data={"analysis_type": "comprehensive"}
)

job_id = response.json()["job_id"]

# Check status
status = requests.get(f"http://localhost:8000/jobs/{job_id}")

# Get results when complete
results = requests.get(f"http://localhost:8000/results/{job_id}")
```

## 📊 Performance Optimization

### GPU Acceleration
```bash
# Enable GPU for PyTorch
export CUDA_VISIBLE_DEVICES=0
python run_bionemo.py --gpu

# Enable GPU for TensorFlow
export TF_FORCE_GPU_ALLOW_GROWTH=true
python your_script.py
```

### Memory Optimization
```python
# Use memory-efficient data structures
import pandas as pd

# Read large files in chunks
for chunk in pd.read_csv("large_file.csv", chunksize=10000):
    process_chunk(chunk)

# Use generators for large datasets
def sequence_generator(fasta_file):
    for record in SeqIO.parse(fasta_file, "fasta"):
        yield record
```

### Parallel Processing
```python
from concurrent.futures import ProcessPoolExecutor
import multiprocessing as mp

def analyze_sequence(sequence):
    # Your analysis logic
    return result

# Parallel processing
with ProcessPoolExecutor(max_workers=mp.cpu_count()) as executor:
    results = list(executor.map(analyze_sequence, sequences))
```

## 🐛 Troubleshooting

### Common Issues

**Import Errors**
```bash
# Reinstall dependencies
pip uninstall -r requirements.txt
pip install -r requirements.txt
```

**GPU Issues**
```bash
# Check GPU availability
nvidia-smi

# Install CUDA toolkit if needed
# Follow NVIDIA instructions for your system
```

**Memory Errors**
```bash
# Increase virtual memory
# Linux: sudo sysctl -w vm.max_map_count=262144
# Or process large files in batches
```

**Quantum Backend Issues**
```bash
# Check IBM Quantum account
# Verify token in environment variables
# Use local simulator as fallback
export QISKIT_IBMQ_PROVIDER=local
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-analysis`)
3. Add tests for new functionality
4. Ensure all tests pass
5. Update documentation
6. Submit a pull request

### Development Guidelines
- Follow PEP 8 style guidelines
- Add type hints for new functions
- Write comprehensive docstrings
- Include unit tests for all new features
- Update requirements.txt for new dependencies

## 📝 License

This project is licensed under the MIT License.

---

**BioMapper Python Engine** - Advanced AI/ML platform for biodiversity analysis and bioinformatics research.