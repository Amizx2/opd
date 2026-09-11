# 🔬 Multi-Beam Interferometer Analyzer (OPD)

> A high-performance GUI desktop application for visualization, digital filtering, and spectral-phase analysis of interferometric data, calculation of Optical Path Difference (OPD), and inter-channel phase distribution.

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg?logo=python&logoColor=white)](https://www.python.org/)
[![PyQt5](https://img.shields.io/badge/GUI-PyQt5-green.svg?logo=qt&logoColor=white)](https://riverbankcomputing.com/software/pyqt/)
[![PyQtGraph](https://img.shields.io/badge/Plots-PyQtGraph-orange.svg)](https://www.pyqtgraph.org/)
[![SciPy](https://img.shields.io/badge/DSP-SciPy%20%26%20NumPy-blueviolet.svg)](https://scipy.org/)
[![Platform](https://img.shields.io/badge/Platform-Windows-lightgrey.svg?logo=windows&logoColor=white)](https://github.com/Amizx2/Programme-for-the-intorferometer-OPD/releases)

---

## 📋 Overview

**Multi-Beam Interferometer Analyzer** is a specialized scientific tool engineered to automate the processing and analysis of signals acquired from multi-beam optical interferometers. It is tailored for researchers, engineers, and students working in fiber optics, laser physics, interferometric sensing, and spectroscopy.

The application allows users to import multi-channel interferograms, convert optical wavelengths into frequencies (THz), apply digital noise filters, extract analytic signal envelopes using the Hilbert transform, compute FFT spectra, and track harmonic phase shifts across spatial or temporal channels to evaluate the **Optical Path Difference (OPD)**.

---

## ✨ Key Features

### 📥 1. Data Import & Management
* **Multi-Format Support:** Seamlessly read data matrices from `.txt` (whitespace- and tab-delimited), `.csv`, and `.xlsx` (Excel) files.
* **Drag-and-Drop Interface:** Load files by dragging them directly onto the application window with a smooth animated drop overlay.
* **Automatic dB-to-Linear Amplitude Conversion:** Converts logarithmic power measurements (dB) into linear amplitudes:
  $$A = 10^{\frac{\text{dB}}{20}}$$
* **Multi-Channel Navigation:** Instantly switch between measurement channels and inspect raw numeric datasets in the built-in **Raw Data** table view (`QTableView`).

### ⚙️ 2. Digital Signal Processing (DSP) & Filtering
* **Moving Average Filter:** Suppress high-frequency noise using a customizable sliding window.
* **Gaussian Filter (1D):** Weighted smoothing that preserves interference fringe contours.
* **Savitzky–Golay Filter:** Polynomial smoothing that maintains peak heights and widths without distorting extrema.
* **Zero-Padding:** Adjustable zero-padding to enhance frequency interpolation and spectral resolution.
* **DC-Offset Removal:** Automatic mean subtraction for baseline correction.

### 📊 3. Interferogram & Spectral Analysis
* **Wavelength-to-Frequency Conversion:** Built-in optical calibration over $\lambda \in [1410, 1490]\text{ nm}$ automatically mapped to optical frequency via $\nu = \frac{c}{\lambda}$ in Terahertz (THz).
* **Hilbert Transform:** Computes the analytic signal to extract both the instantaneous amplitude (envelope) and instantaneous unwrapped phase:
  $$s_a(t) = s(t) + i\mathcal{H}\{s(t)\}$$
* **Fast Fourier Transform (FFT):** Computes amplitude spectra with automatic suppression of the zero-frequency (DC) component.
* **Automated Peak Detection:** Locates interference fringe extrema based on first-derivative sign changes, marking them directly on the plot.

### 📐 4. Phase Analysis & Optical Path Difference (OPD)
* **Interactive Frequency Marker (Crosshair):** Visual crosshair with automatic frequency-bin snapping and live readout of frequency and amplitude values.
* **Inter-Channel Phase Tracking ("Plot Phase"):** Locks onto a selected spectral harmonic $f_0$ and evaluates its phase $\Delta\phi(n)$ across all channels with automatic phase unwrapping (`unwrap`). This directly characterizes the Optical Path Difference (OPD) profile and phase wavefront across interferometer channels.

### 💾 5. Publication-Ready Plot Export
* Export to **high-resolution raster images (PNG, up to 1920px)**.
* Export to **Scalable Vector Graphics (SVG)** for lossless integration into scientific papers (LaTeX, Word), theses, and conference slides.
* Single-plot export or batch export of all active figures ("Export All Plots").

---

## 🚀 Quick Start

### Option 1. Standalone Windows Executable (No Python required)

1. Go to the [**Releases**](https://github.com/Amizx2/Programme-for-the-intorferometer-OPD/releases) page.
2. Download **`InterferometerAnalyzer.exe`**.
3. Double-click to launch — no installation of Python or dependencies required.

---

### Option 2. Running from Python Source Code

#### 1. Clone the Repository
```bash
git clone https://github.com/Amizx2/Programme-for-the-intorferometer-OPD.git
cd Programme-for-the-intorferometer-OPD
```

#### 2. Set Up a Virtual Environment (Recommended)
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# Linux / macOS
python3 -m venv venv
source venv/bin/activate
```

#### 3. Install Dependencies
```bash
pip install -r requirements.txt
```
*(Or manually: `pip install PyQt5 pyqtgraph numpy scipy pandas openpyxl`)*

#### 4. Launch the Application
```bash
python interfe.py
```

---

## 📦 Requirements

| Package | Purpose |
|---|---|
| **Python** $\ge$ 3.8 | Core runtime environment |
| **PyQt5** | Modern graphical user interface (GUI) |
| **pyqtgraph** | High-performance hardware-accelerated 2D plotting |
| **NumPy** | Vectorized mathematical operations |
| **SciPy** | Signal processing (FFT, Hilbert transform, digital filters) |
| **Pandas** | Tabular data loading and processing (.csv, .xlsx, .txt) |
| **OpenPyXL** | Engine for reading Microsoft Excel spreadsheets |

---

## 📖 User Workflow

1. **Load Data:**
   * Click **`Load Data File`** or drag and drop a data file (`.txt`, `.csv`, `.xlsx`) into the window.
   * Select the channel to analyze from the **`Select Channel`** dropdown.
2. **Apply Filtering:**
   * In the **`Signal Processing`** panel, choose a filter (*Moving Average*, *Gaussian*, or *Savitzky-Golay*).
   * Specify the window parameter and click **`Apply Filter`**.
3. **Analyze Spectrum:**
   * Configure zero-padding in **`Number of Zeros`** and click **`Update Spectrum`**.
   * Click on the header label **`Spectrum of mained Signal`**, enter your sampling frequency, and inspect the dedicated spectrum tab.
4. **Evaluate Phase & OPD:**
   * In the spectrum tab, toggle **`Marker: On`** and position the vertical line over your harmonic of interest.
   * Click **`Plot Phase`** to generate the phase-versus-channel curve representing the Optical Path Difference.
5. **Export Figures:**
   * Click **`Export`** beneath any graph, choose your target folder, file name, and format (PNG or SVG).

---

## 🛠️ Building the Standalone Executable

To compile the application into a standalone `.exe` using [PyInstaller](https://pyinstaller.org/):

```bash
pip install pyinstaller
pyinstaller --noconsole --onefile --name "InterferometerAnalyzer" interfe.py
```
The compiled binary will be generated inside the `dist/` directory.

---

## 👤 Author

* **Amizx2** — [GitHub Profile](https://github.com/Amizx2)
* Repository: [Programme-for-the-intorferometer-OPD](https://github.com/Amizx2/Programme-for-the-intorferometer-OPD)

---

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
