# SSB-SC-WaveGenerator-MATLAB
Generates a SSB-SC Wave, with customizable carrier and message signal frequencies and amplitudes. 
# Single Sideband Suppressed Carrier (SSB-SC) Modulation in MATLAB

A MATLAB implementation demonstrating **Single Sideband Suppressed Carrier (SSB-SC)** modulation using the **Hilbert Transform phasing method**. This program accepts user parameters via an interactive GUI dialog to generate time-domain signals and their single-sided frequency spectra using Fast Fourier Transform (FFT).

---

## 📌 Features

* **Interactive Parameters GUI**: Simple dialog prompts to set carrier amplitude, carrier frequency, message frequency vector, and sampling frequency.
* **Hilbert Transform Modulation**: Generates SSB signals via phasing techniques for either Upper Sideband (USB) or Lower Sideband (LSB).
* **Nyquist Criterion Validation**: Includes built-in safety checks that trigger an error dialog if the sampling rate violates the Nyquist condition ($f_s \le 2(f_c + f_{m,\text{max}})$).
* **Frequency Spectrum Analysis**: Computes single-sided amplitude spectra for the message, carrier, and modulated signals.
* **Multi-Plot Visualization**: Real-time display of 6 subplots comparing time-domain waveforms alongside their frequency spectra.

---

## 🛠️ Code Structure

### 1. Main Execution Loop

Continuously launches the prompt dialog, computes signal components, and renders a 2x3 grid of subplots.

### 2. Core Functions

* `ssbscwvgn(Ac, fc, fmVec, dur, fs, useUSB)`: Key modular function executing the signal processing:
* Checks sampling parameters against the Nyquist frequency.
* Generates a normalized multi-tone message signal and carrier signal.
* Applies the Hilbert Transform (`hilbert`) to achieve phase shifting for SSB generation.
* Computes single-sided FFT spectra ($0$ to $f_s/2$).


* `examplewav()`: Displays user input dialogs (`inputdlg`) and routes variables to `ssbscwvgn`.

---

## 📊 Plot Layout Output

The code formats output displays across a 2-row, 3-column figure:

| Column 1 (Modulated) | Column 2 (Message) | Column 3 (Carrier) |
| --- | --- | --- |
| **Row 1 (Time Domain)**: SSB-SC Waveform | **Row 1 (Time Domain)**: Message Signal | **Row 1 (Time Domain)**: Carrier Signal |
| **Row 2 (Frequency)**: SSB-SC Spectrum | **Row 2 (Frequency)**: Message Spectrum | **Row 2 (Frequency)**: Carrier Spectrum |

---

## 🚀 How to Run

1. Open MATLAB.
2. Download or copy the code content into a `.m` file (e.g., `SSBSC_manual.m`).
3. Run the script from the MATLAB Command Window or Editor tab.
4. When prompted by the dialog box, enter your signal parameters:
* **Message Frequency**: Frequency of the input message (Hz)
* **Carrier Amplitude**: Peak voltage level of the carrier wave
* **Carrier Frequency**: High-frequency carrier wave frequency (Hz)
* **Sample Frequency**: Sampling rate $f_s$ in Hz (must satisfy $f_s > 2(f_c + f_m)$)
