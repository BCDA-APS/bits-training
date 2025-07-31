# BITS-Starter Setup

## Overview

**This is the first step in creating your BITS instrument.** You'll fork and clone the BITS-Starter template repository to create your own customizable instrument package.

**Time**: ~10 minutes  
**Goal**: Create your own BITS instrument repository ready for customization

## Prerequisites

### Required Software
- **Git**: Version control system
- **GitHub Account**: For creating your repository
- **Python 3.11+**: Conda or system Python

### Optional but Recommended
- **GitHub CLI**: For command-line repository creation

## What is BITS-Starter?

BITS-Starter is a GitHub template repository that provides:
- Complete instrument package structure
- Working device configuration examples
- Integration with queue server
- Data management setup
- Testing framework
- Production-ready deployment patterns

## Step-by-Step Setup

### 1. Create Your GitHub Repository

**Option A: Using GitHub Web Interface (Recommended)**

1. Go to [BITS-Starter repository](https://github.com/BCDA-APS/BITS-Starter)
2. Click the green **"Use this template"** button
3. Select **"Create a new repository"**
4. Set repository settings:
   - **Repository name**: `my_beamline_bits` (replace with your actual beamline name)
   - **Description**: "BITS instrument for [your beamline] beamline"
   - **Visibility**: Public (recommended for learning)
   - **Include all branches**: Leave unchecked
5. Click **"Create repository from template"**

**Option B: Using GitHub CLI (Alternative)**

```bash
# Create repository from template
gh repo create my_beamline_bits --template BCDA-APS/BITS-Starter --public

# The repository is created but not cloned yet
```

### 2. Clone Your New Repository

```bash
# Navigate to your workspace
mkdir -p ~/ws
cd ~/ws

# Clone the training repository
git clone https://github.com/BCDA-APS/bits-training.git

# Clone your repository (replace YOUR_USERNAME with your GitHub username)
git clone https://github.com/YOUR_USERNAME/my_beamline_bits.git
cd my_beamline_bits

# Verify the structure
ls -la
```

**Expected structure:**
```
my_beamline_bits/
├── LICENSE
├── README.md
├── pyproject.toml
├── src/
│   └── (template instrument files)
├── scripts/
└── tests/
```

### 3. Set Up Python Environment

```bash
# Create BITS environment
conda create -y -n bits_env python=3.11 pyepics
conda activate bits_env

# Install BITS framework
pip install apsbits

# Verify BITS installation
python -c "import apsbits; print('✅ BITS installed:', apsbits.__version__)"
```

### 4. Create your First Instrument & Install It As A Package
```bash
# Use the below command to create your instrument
bits-create my_instrument

# Install your instrument in development mode
pip install -e .

# This allows you to edit the code and see changes immediately
```

### 4. Install Your Instrument Package

```bash
# Install your instrument in development mode
pip install -e .

# This allows you to edit the code and see changes immediately
```

### 5. Verify Installation

```bash
# Test that your instrument package can be imported
ipython
```
Inside the ipython environment run the below
```python
from my_instrument import * # Import your instrument
RE(sim_rel_scan()) # Run one of the pre-configured plans
```

## Understanding Your Repository Structure

Your new repository contains:

### Core Files
- **`pyproject.toml`**: Package configuration and dependencies
- **`README.md`**: Project documentation (customize for your beamline)
- **`LICENSE`**: Software license

### Source Code (`src/`)
- **Template instrument files**: Ready to customize for your beamline
- **Configuration examples**: Device and plan templates
- **Queue server setup**: For remote operation

### Development Tools
- **`scripts/`**: Utility scripts for development and deployment


**Expected output:**
- ✅ BITS framework installed and importable
- ✅ Repository cloned and customized
- ✅ Package installed in development mode
- ✅ Git repository ready for development

## Next Steps

With your BITS instrument repository created, you're ready to:

1. **Explore your IOCs** to understand available devices
2. **Configure devices** to match your hardware  
3. **Create custom plans** for your experiments
4. **Set up interactive operation** for data acquisition

**→ Next Step**: [IOC Exploration & Device Discovery](01_ioc_exploration.md)

## Support

If you encounter issues:
1. Check the [BITS-Starter repository](https://github.com/BCDA-APS/BITS-Starter) for updates
2. Review the [BITS documentation](https://github.com/BCDA-APS/BITS)
3. Ensure all prerequisites are properly installed

---

**You now have your own BITS instrument repository!** 🎉

**Next Step**: [IOC Exploration & Device Discovery](01_ioc_exploration.md)