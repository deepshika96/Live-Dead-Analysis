# Live-Dead-Analysis
# 🔬 Quantitative Analysis of DAPI+ Cells and Caspase-3 Activation

This repository contains two complementary scripts designed to analyze confocal microscopy data:

1. **Estimate the average size of DAPI+ cells** from randomly sampled patches. - Use Single Cell Area Calculation 
2. **Measure DAPI and Caspase-3 (clCASP3) stain coverage and intensity** across `.lif` image series. - Use Stain Area Coverage Analysis
3. **Normalize Caspase-3 intensity by DAPI cell size** to get per-cell apoptotic burden. 

---


---

## 🧪 1. Estimating Average DAPI+ Cell Area

**Script**: `Single Cell Area Calculation.py`

This script:
- Loads a `.lif` file with DAPI-stained nuclei.
- Extracts non-overlapping random patches from the DAPI channel.
- Segments each patch using the **CellSAM** deep-learning model.
- Counts objects (nuclei) and total DAPI+ area per patch.
- Saves masks and an Excel summary.

### 📤 Output:
- Labeled TIFF masks per patch
- Excel file with:
  - Number of DAPI+ cells per patch
  - Total DAPI+ intensity per patch

### ✅ Final Result:
Use this to compute the **average area per DAPI+ nucleus**:


---

## 🔍 2. DAPI & Caspase-3 Area Coverage

**Script**: `Stain Area Coverage Analysis.py`

This script:
- Loads a `.lif` file with DAPI and clCASP3 channels.
- Computes max-intensity projections (MIPs).
- Extracts 10 random non-overlapping patches per image series.
- Applies **Otsu thresholding** on each channel.
- Calculates area (µm²) and intensity of DAPI+ and Caspase-3+ pixels.
- Saves overlays and exports a detailed Excel report.

### 📤 Output:
- Binary masks for each patch
- RGB overlay images (R = Caspase-3, B = DAPI)
- Excel file with:
  - DAPI and Caspase-3 area and intensity per patch

---

## 📊 3. Final Step: Normalizing Caspase-3 Intensity

With both Excel files:

1. From `estimate_dapi_cell_area.py`: compute the **mean DAPI+ cell area**.
2. From `stain_area_coverage_analysis.py`: use Caspase-3 total intensity per patch.
3. Normalize clCASP3 intensity per cell:





