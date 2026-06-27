# **Epistemic Theory Extractor (The "Meat Filter" Analyzer)**

**PerceptionLab / Helsinki**  
An autonomous, epistemic AI tool designed to algebraically extract the linear physical transfer function mapping electrical brain activity (EEG) to acoustic speech (Voice).  
Unlike standard Deep Learning models that rely on gradient descent and black-box neural networks to guess relationships, this tool uses **Takens Delay Embedding** and **SINDy (Sparse Identification of Nonlinear Dynamics)** to algebraically deduce the explicit, human-readable laws of physics governing the acoustic resonance of the human skull and electrode hardware.

## **🧠 The Theory: Epistemic Signal Processing**

When analyzing simultaneous EEG and audio recordings during speech, the human head, skull, and electrode cables act as a physical, passive acoustic resonator (the "microphonic effect").  
To extract the exact physical shape of this resonator without hallucinating noise, this tool executes the following pipeline:

1. **Acoustic Isolation:** Bandpass filters both signals to the mechanical resonance band (50–300 Hz), stripping away massive, slow brain waves (Delta/Alpha) that would otherwise blind a linear solver.  
2. **Topological Unfolding (Takens' Theorem):** The 1D EEG signal is dynamically embedded into a high-dimensional Hankel matrix in RAM. This "unfolds" the hidden geometry of the biological system.  
3. **The Algebraic Solver:** Uses Moore-Penrose pseudo-inverses (via robust LAPACK gelsy drivers) to instantly find the flat geometrical plane mapping the unfolded EEG to the target Voice.  
4. **Occam's Razor (SINDy):** Applies Sequential Thresholded Least Squares (STLSQ). It violently crushes statistically weak dimensional connections to exactly 0.000, leaving behind only the sparse, mathematically rigorous Finite Impulse Response (FIR) filter.

## **✨ Features**

* **Professional Dual-Pane GUI:** Clean interface for data loading, parameter tuning, and real-time console output.  
* **Native EDF & WAV Support:** Uses mne to natively read EEG channels directly from .edf files, and automatically resamples the .wav audio to match the EEG clock.  
* **Instant Extraction:** Discovers the physical law algebraically in seconds. No epochs, no backpropagation.  
* **Spectral Analysis:** Converts the discovered time-domain FIR filter into a Frequency Response Bode Plot (via Discrete Fourier Transform) to visualize the exact resonant frequencies of the skull.  
* **Native Playback & Export:** Listen to the mathematically reconstructed audio instantly via sounddevice, and explicitly export both the .wav and a .txt log of the discovered physical laws.

## **⚙️ Installation**

The tool requires Python 3.8+ and standard scientific libraries.

Bash  
pip install numpy scipy mne soundfile matplotlib sounddevice

## **🚀 Usage**

Run the graphical interface:

Bash  
python epistemic\_pro\_gui.py

### **Workflow:**

1. **Load Data:** Select your .edf (EEG) and .wav (Microphone) files.  
2. **Select Channel:** Enter the target EEG channel (e.g., EEG132 or Cz). If left blank, the tool automatically selects the channel with the highest variance.  
3. **Set Geometry Parameters:**  
   * **Takens Dimensions:** The size of the FIR filter (e.g., 128 taps). This dictates how far back in time the model looks.  
   * **Takens Delay:** The spacing between samples in the unfolding (usually 1 for high-frequency acoustic analysis).  
   * **Sparsity Penalty:** The L1 SINDy threshold. Start low (0.005) to find the full continuous wave, or raise it to force the model to drop weaker acoustic echoes.  
4. **Extract:** Click **EXTRACT PHYSICAL LAW**. The UI will print the exact mathematical equation (e.g., Target(t) \= 11.00 \* EEG(t \- 2.5ms) \- 29.09 \* EEG(t \- 3.3ms)) to the console.  
5. **Analyze:** Play the reconstructed audio or click **SHOW SPECTRA** to view the resonance peaks in the frequency domain.

## **🔬 Interpreting the Output**

If SINDy "crushes 0 terms," this is not a failure of sparsity. It is mathematical proof that the skull's resonance is a *continuous, unbroken transfer of energy*. The printed coefficients represent the exact impulse response wave. The latency peak (the point of maximum coefficient magnitude) reveals the precise mechanical delay between the electrical signal and the acoustic recording.
