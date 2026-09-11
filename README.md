# 🔬 Multi-Beam Interferometer Analyzer (OPD) ENG

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

# 🔬 Multi-Beam Interferometer Analyzer (OPD) Ru

> Программа с графическим интерфейсом для визуализации, фильтрации и спектрально-фазового анализа данных многолучевого интерферометра, расчета разности оптического хода (OPD) и поканального распределения фазовых сдвигов.

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg?logo=python&logoColor=white)](https://www.python.org/)
[![PyQt5](https://img.shields.io/badge/GUI-PyQt5-green.svg?logo=qt&logoColor=white)](https://riverbankcomputing.com/software/pyqt/)
[![PyQtGraph](https://img.shields.io/badge/Plots-PyQtGraph-orange.svg)](https://www.pyqtgraph.org/)
[![SciPy](https://img.shields.io/badge/DSP-SciPy%20%26%20NumPy-blueviolet.svg)](https://scipy.org/)
[![Platform](https://img.shields.io/badge/Platform-Windows-lightgrey.svg?logo=windows&logoColor=white)](https://github.com/Amizx2/Programme-for-the-intorferometer-OPD/releases)

---

## 📋 О проекте

**Multi-Beam Interferometer Analyzer** — специализированный аналитический комплекс для автоматизации обработки сигналов с оптических интерферометров. Программа разработана для исследователей, инженеров и студентов, работающих в области волоконной оптики, лазерной физики, интерферометрических сенсоров и спектроскопии.

Приложение позволяет загружать интерферограммы, пересчитывать оптические длины волн в частоты (THz), выполнять цифровую фильтрацию шумов, рассчитывать огибающую аналитического сигнала с помощью преобразования Гильберта, строить БПФ-спектры (FFT), а также определять разность фаз выбранных гармоник по пространственным/временным каналам для нахождения **разности оптического хода (Optical Path Difference, OPD)**.

---

## ✨ Ключевые возможности

### 📥 1. Импорт и организация данных
* **Поддержка популярных форматов:** загрузка матриц данных из файлов `.txt` (включая разделители пробелами и табуляцией), `.csv` и `.xlsx` (Excel).
* **Drag-and-Drop:** загрузка файлов простым перетаскиванием прямо в окно программы с анимированным оверлеем.
* **Автоматическое преобразование дБ $\to$ линейная шкала:** перевод логарифмических уровней мощности в амплитуду:
  $$A = 10^{\frac{\text{dB}}{20}}$$
* **Многоканальность:** быстрое переключение между каналами измерений и просмотр исходных массивов в виде таблицы (`Raw Data`).

### ⚙️ 2. Цифровая фильтрация и предобработка
* **Скользящее среднее (Moving Average)** — устранение высокочастотного шума с настраиваемым размером окна.
* **Гауссова фильтрация (Gaussian Filter 1D)** — сглаживание с сохранением контуров интерференционных полос.
* **Фильтр Савицкого — Голея (Savitzky-Golay)** — полиномиальное сглаживание без искажения амплитуды пиков.
* **Zero-Padding:** настраиваемое дополнение массива нулями для увеличения частотной дискретизации и плавности спектра.
* **Центрирование:** автоматическое удаление постоянной составляющей (DC-компоненты).

### 📊 3. Интерферометрический и спектральный анализ
* **Пересчет длины волны в частоту:** встроенный диапазон оптической калибровки $\lambda \in [1410, 1490]\text{ нм}$ с автоматическим преобразованием по формуле $\nu = \frac{c}{\lambda}$ и шкалой в терагерцах (THz).
* **Преобразование Гильберта:** расчет аналитического сигнала, выделение мгновенной амплитуды (огибающей) и мгновенной фазы:
  $$s_a(t) = s(t) + i\mathcal{H}\{s(t)\}$$
* **Быстрое преобразование Фурье (FFT):** расчет амплитудного спектра с автоматической отсечкой нулевой гармоники.
* **Детекция экстремумов (Peaks):** автоматический поиск пиков интерференционной картины по смене знака производной с маркировкой на графике.

### 📐 4. Фазовый анализ разности оптического хода (OPD)
* **Интерактивный маркер частот:** удобный визир с привязкой к бинам частот и точным отображением частоты и амплитуды.
* **Поканальное распределение фазы («Plot Phase»):** фиксация выбранной гармоники $f_0$ и расчет ее фазы $\Delta\phi(n)$ по всем каналам с устранением скачков $\pm\pi$ (`unwrap`). Это дает прямую картину разности оптического хода (OPD) и фазового фронта между лучами / каналами интерферометра.

### 💾 5. Публикационный экспорт графиков
* Экспорт в **растровый формат высокой четкости (PNG, до 1920px)**.
* Экспорт в **векторный формат (SVG)** для вставки в научные статьи (LaTeX, Word), презентации и дипломные работы без потери качества.
* Экспорт как отдельных графиков, так и всех активных графиков одним действием («Export All Plots»).

---

## 🚀 Быстрый старт

### Вариант 1. Запуск автономного EXE (Windows, без установки Python)

1. Перейдите в раздел [**Releases**](https://github.com/Amizx2/Programme-for-the-intorferometer-OPD/releases).
2. Скачайте файл **`InterferometerAnalyzer.exe`**.
3. Запустите двойным кликом — установка дополнительных библиотек или Python не требуется.

---

### Вариант 2. Запуск из исходного кода Python

#### 1. Клонирование репозитория
```bash
git clone https://github.com/Amizx2/Programme-for-the-intorferometer-OPD.git
cd Programme-for-the-intorferometer-OPD



