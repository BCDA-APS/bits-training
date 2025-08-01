## Validation and Testing

### 1. Test Device Responsiveness
```bash
# Test motor motion
python scripts/explore_iocs.py --test-device gp:m1 --move-relative 0.1

# Test scaler counting
python scripts/explore_iocs.py --test-device gp:scaler1 --count 1.0

# Test area detector
python scripts/explore_iocs.py --test-device adsim: --acquire 1
```

### 2. Check Data Rates
```bash
# Monitor update rates
python scripts/explore_iocs.py --monitor-rates gp:m1.RBV gp:scaler1.S1

# Typical rates:
# - Motors: ~10 Hz position updates
# - Scalers: Variable (depends on counting)
# - Area detectors: Frame-rate dependent
```

### 3. Identify Connection Issues
```bash
# Check for disconnected PVs
python scripts/explore_iocs.py --check-connections

# Any PVs that don't connect may indicate:
# - IOC not running
# - Network issues  
# - Incorrect PV names
```

## Troubleshooting Setup

### Repository Creation Issues

**"Use this template" button not visible:**
- Make sure you're logged into GitHub
- Ensure you have permission to create repositories
- Try using Option B (GitHub CLI) instead

**Git clone fails:**
```bash
# Check if Git is installed
git --version

# Verify repository URL
# Make sure to replace YOUR_USERNAME with your actual GitHub username
```

### Python Environment Issues

**Conda command not found:**
```bash
# Source conda initialization
source ~/miniconda3/etc/profile.d/conda.sh
# or
source ~/anaconda3/etc/profile.d/conda.sh
```

**Import errors after installation:**
```bash
# Reinstall in development mode
pip install -e .

# Check if package is installed
pip list | grep my-beamline
```

### Permission Issues

**Can't push to repository:**
```bash
# Check remote URL
git remote -v

# If using HTTPS, you may need to configure Git credentials
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```
