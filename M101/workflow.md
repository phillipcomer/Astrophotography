# M101 – PixInsight Workflow (JPEG Processing)

## 📁 File Used
**1753941759557.jpg** – captured with Seestar S50, stacked and exported as JPEG

## 🧪 Step-by-Step PixInsight Workflow (For Stretched JPEG)

---

### 1. Load & Duplicate
- Open image in PixInsight
- Clone the image: `Image > Duplicate` (for backup)

---

### 2. Background Cleanup (Optional)
- **Tool**: `DynamicBackgroundExtraction`
- Place background samples away from galaxy/starfield
- Correction: Subtraction

---

### 3. Color & Contrast Tuning
- **Tool**: `CurvesTransformation`
  - Apply gentle S-curve to RGB/K channels
  - Boost saturation slightly (careful not to overdo)

- **Optional**: `SCNR` to remove green noise

---

### 4. Star Reduction
- **Step 1**: `StarMask`
  - Scale: 5–6, Truncation: 0.35, Midtones: 0.6
- **Step 2**: `MorphologicalTransformation`
  - Operation: Erosion, Amount: 0.20, Iterations: 1
  - Apply to star mask only

---

### 5. Structure Enhancement
- **Option 1**: `LocalHistogramEqualization`
  - Kernel radius: 64, Contrast limit: 1.5
- **Option 2**: `HDRMultiscaleTransform`
  - Layers: 6, Lightness mask if needed

---

### 6. Final Touches
- Additional `CurvesTransformation` for fine contrast
- Export as `.tif` (16-bit) or `.png` for final use

---

## 📝 Notes
- JPEG format limits dynamic range and deep calibration.
- For full astrophotography workflows, raw `.fits` or `.tif` exports from Seestar are preferred.
- This workflow is ideal for test shots, fast feedback, and backyard sessions.
