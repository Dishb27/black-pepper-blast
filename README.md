# 🧬 Black Pepper BLAST Tool

[![Node.js](https://img.shields.io/badge/Node.js-14.0%2B-green.svg)](https://nodejs.org/)
[![Next.js](https://img.shields.io/badge/Next.js-Latest-black.svg)](https://nextjs.org/)
[![BLAST+](https://img.shields.io/badge/BLAST%2B-Required-blue.svg)](https://blast.ncbi.nlm.nih.gov/Blast.cgi?CMD=Web&PAGE_TYPE=BlastDocs&DOC_TYPE=Download)

> A modern web-based BLAST (Basic Local Alignment Search Tool) interface for searching Black Pepper (*Piper nigrum*) genomic sequences.

## ✨ Features

- **BLASTN**: Search nucleotide sequences against genome and CDS databases
- **BLASTP**: Search protein sequences against protein databases
- **File Upload**: Support for FASTA file uploads (`.fasta`, `.fa`, `.fna`)
- **Advanced Options**: Customizable E-value, number of descriptions, and alignments
- **Sequence Validation**: Automatic detection of sequence type and compatibility checking
- **Interactive Results**: Detailed alignment visualization with statistics

## 📋 Prerequisites

Before setting up this tool, ensure you have:

| Requirement | Version | Purpose |
|-------------|---------|---------|
| **Node.js** | 14.0+ | Runtime environment |
| **BLAST+** | Latest | Command-line tools |
| **Git** | Any | Repository cloning |

## 🛠️ Installation Guide

### 1️⃣ Install Node.js

<details>
<summary><b>Windows</b></summary>

1. Download Node.js from [https://nodejs.org/](https://nodejs.org/)
2. Run the installer and follow the setup wizard
3. Verify installation:
   ```cmd
   node --version
   npm --version
   ```
</details>

<details>
<summary><b>macOS</b></summary>

```bash
# Using Homebrew (recommended)
brew install node

# Verify installation
node --version
npm --version
```
</details>

<details>
<summary><b>Linux (Ubuntu/Debian)</b></summary>

```bash
# Update package index
sudo apt update

# Install Node.js
sudo apt install nodejs npm

# Verify installation
node --version
npm --version
```
</details>

### 2️⃣ Install BLAST+ Tools

<details>
<summary><b>Windows</b></summary>

1. Download BLAST+ from [NCBI FTP](https://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/)
2. Extract to `C:\blast`
3. Add `C:\blast\bin` to your system PATH
4. Verify installation:
   ```cmd
   blastn -version
   ```
</details>

<details>
<summary><b>macOS</b></summary>

```bash
# Using Homebrew
brew install blast

# Verify installation
blastn -version
```
</details>

<details>
<summary><b>Linux (Ubuntu/Debian)</b></summary>

```bash
# Install BLAST+
sudo apt update
sudo apt install ncbi-blast+

# Verify installation
blastn -version
```
</details>

### 3️⃣ Download Black Pepper Sequence Data

> 📁 **All files available**: [Black Pepper Data Files](https://drive.google.com/drive/folders/15MhkCYZEA-K7YQxVyShig14zGQqyC5Jl?usp=drive_link)

| Database | File | Description |
|----------|------|-------------|
| **Genome** | `Piper_nigrum.genome.fa` | Complete genome sequence |
| **CDS** | `Piper_nigrum.cds` | Coding sequences |
| **Protein** | `Piper_nigrum_proteome.pep` | Protein sequences |

### 4️⃣ Create BLAST Databases

After downloading the FASTA files, create BLAST databases:

```bash
# Create Genome Database (for BLASTN)
makeblastdb -in Piper_nigrum.genome.fa -dbtype nucl -out Piper_nigrum_genome_db

# Create CDS Database (for BLASTN)
makeblastdb -in Piper_nigrum.cds -dbtype nucl -out Piper_nigrum_cds_db

# Create Protein Database (for BLASTP)
makeblastdb -in Piper_nigrum_proteome.pep -dbtype prot -out Piper_nigrum_prot_db
```

### 5️⃣ Setup the Web Application

```bash
# Clone the repository
git clone https://github.com/yourusername/black-pepper-blast-tool.git
cd black-pepper-blast-tool

# Install dependencies
npm install

# Create database directory
mkdir Blast_DB

# Move BLAST databases to the directory
mv Piper_nigrum_*_db.* Blast_DB/
```

## 🟢 Running the Application

### Development Mode
```bash
npm run dev
```
🌐 **Access at**: `http://localhost:3000`

### Production Mode
```bash
npm run build
npm start
```

## 📁 Project Structure

```
black-pepper-blast-tool/
├── 📁 pages/
│   ├── 📁 api/
│   │   └── blast.js          # BLAST API endpoint
│   ├── blast.js              # Main BLAST interface
│   └── resultblast.js        # Results display page
├── 📁 styles/
│   ├── blast.module.css
│   └── resultblast.module.css
├── 📁 Blast_DB/              # Your BLAST databases
│   ├── Piper_nigrum_genome_db.*
│   ├── Piper_nigrum_cds_db.*
│   └── Piper_nigrum_prot_db.*
├── 📁 temp/                  # Temporary files (auto-created)
├── package.json
└── README.md
```

## 👨‍💻 Usage

1. **🌐 Access the Tool**: Navigate to `http://localhost:3000/blast`

2. **🔧 Select Program**:
   - **BLASTN**: For nucleotide sequences (DNA/RNA)
   - **BLASTP**: For protein sequences

3. **🗄️ Choose Database**:
   - **Genome Database**: Complete genome sequences
   - **CDS Database**: Coding sequences only
   - **Protein Database**: Protein sequences

4. **📝 Input Sequence**:
   - Paste FASTA sequences directly
   - Upload a FASTA file (`.fasta`, `.fa`, `.fna`)
   - Maximum 5 sequences per submission

5. **⚙️ Advanced Options** (Optional):
   - Adjust E-value threshold
   - Set number of descriptions and alignments

6. **📤 Submit and View Results**:
   - Click "BLAST" to run the search
   - View detailed alignment results with statistics
