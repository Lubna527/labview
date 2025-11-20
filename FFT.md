Below is a **fully rewritten, expanded, and polished version** of your second experiment write-up, similar in style and detail to the first expanded version I produced.
Everything is rephrased in clearer, more descriptive language and made significantly longer for academic/record-book use.

---

# **GENERATION OF SINE AND COSINE WAVES AND ANALYSIS OF THEIR FFT USING LABVIEW**

## **AIM**

The purpose of this experiment is to design a Virtual Instrument (VI) using LabVIEW’s graphical programming environment that can generate sine and cosine waveforms and compute their corresponding frequency spectra. This is achieved by applying the Fast Fourier Transform (FFT) to the time-domain signals. The experiment helps illustrate how sinusoidal signals behave in both the time domain and frequency domain.

---

## **SOFTWARE REQUIRED**

**LabVIEW 2025**

---

## **THEORY**

LabVIEW, or **Laboratory Virtual Instrument Engineering Workbench**, is a comprehensive system-design platform based on graphical programming. Instead of writing textual code, users construct programs by interconnecting functional blocks, making it especially suitable for signal processing, measurement, instrumentation, and educational simulation.

Graphical programming makes LabVIEW accessible to beginners while still providing powerful computational capabilities required for advanced science and engineering tasks. A LabVIEW program is known as a **Virtual Instrument (VI)** because its design and behavior resemble that of physical laboratory instruments.

A VI consists of:

1. **Front Panel** – The user interface, containing controls, knobs, and graphical displays such as waveforms and indicators.
2. **Block Diagram** – The code workspace, where nodes, functions, and structures are wired together to form the program.

LabVIEW includes an extensive library of built-in functions for signal generation, analysis, filtering, and transformation. In this experiment, the following tools are essential:

---

### **Important Nodes and Functions Used**

#### **1. Sine Wave.vi**

The Sine Wave VI simulates a function generator that produces discrete samples of a sine wave.

* If the input *Reset Phase* is set to **FALSE**, the VI continues generating samples from where it left off in the previous iteration, mimicking a continuous waveform.
* Parameters such as amplitude, frequency, number of samples, and phase shift can be controlled by the user.

A cosine wave can also be generated using the same VI by simply setting the phase shift to **90 degrees (π/2 radians)**.

---

#### **2. FFT.vi**

The Fast Fourier Transform VI computes the discrete Fourier Transform of the input signal.

* The FFT reveals the signal’s frequency content.
* For a pure sinusoid, the FFT output contains frequency spikes at the positive and negative frequencies corresponding to the sinusoidal oscillation.

The VI automatically detects the data type and format when wired, or the user can manually select the desired polymorphic instance.

---

#### **3. Waveform Graph**

A waveform graph is used to display signals that are evenly sampled in time.

* It plots amplitude (y-axis) versus time (x-axis).
* Multiple waveforms can be displayed simultaneously.
  These graphs are ideal for visualizing real-time signals such as sine waves and their FFT outputs.

---

## **PROCEDURE**

1. Launch **LabVIEW 2025** and open a new blank VI.
   The *Front Panel* and *Block Diagram* appear.

2. On the **Front Panel**, place a **Sine Wave VI** to generate the first sinusoidal waveform.

3. Create controls for:

   * **Amplitude**
   * **Frequency**
   * Optional inputs such as number of samples

4. Place a **Waveform Graph** on the Front Panel and connect the output of the Sine Wave VI to the graph in the Block Diagram so that the time-domain sine wave can be visualized.

5. To generate a cosine wave, insert **another Sine Wave VI**.

   * Right-click on the *Phase* input and create a **constant**.
   * Set the phase constant to **90 degrees**, producing a cosine wave.

6. Add another waveform graph to display the cosine signal.

7. Place two **FFT.vi** nodes—one for the sine wave and one for the cosine wave.

8. Wire the output of each sinusoidal generator into its corresponding FFT node.

9. Connect the FFT outputs to two additional waveform graphs to display the frequency spectra of both signals.

10. Adjust graph properties such as axis labels (e.g., changing x-axis to **Frequency (Hz)**).

11. Replace the frequency and amplitude numeric controls with **knobs** for real-time adjustment during execution.

12. Enclose all components in a **While Loop** for continuous, live signal generation and update.

13. Create a **Stop** Boolean control to terminate the loop.

---

## **CIRCUIT / BLOCK DIAGRAM**

*(Shown in the experiment images. Consists of sine wave generators, FFT modules, waveform graphs, and a while loop.)*

---

## **OUTPUTS**

### **Figure (a)**

Low-frequency sine and cosine waves along with their FFT spectrum show narrow peaks at the corresponding low frequency.

### **Figure (b)**

High-frequency sinusoidal signals display FFT spikes shifted to higher positions on the frequency axis.

---

## **OBSERVATIONS**

1. The FFT of both sine and cosine waves displays **two significant spikes**—one at positive frequency and one at negative frequency—corresponding to the frequency of the input signal.

2. **Variation of amplitude:**
   When the amplitude of the sinusoidal signal is changed, the height of the FFT spikes increases or decreases proportionally, but their frequency position remains unchanged.

3. **Variation of frequency:**
   Increasing the frequency of the sine or cosine wave shifts the FFT spikes to a higher frequency value.
   Thus, the FFT correctly identifies the frequency components of the time-domain signal.

4. **Spectral Interpretation:**
   The Fourier Transform enables extraction and analysis of hidden frequency information from time-domain signals. Complex signals that may appear irregular in the time domain become easier to interpret when converted into the frequency domain.

5. This demonstrates the fundamental principle that many real-world signals, no matter how complicated, can be decomposed into sinusoidal components using Fourier analysis.

---

## **RESULTS**

Sine and cosine waves of adjustable amplitude and frequency were successfully generated using LabVIEW. Their corresponding frequency spectra were obtained using the Fast Fourier Transform (FFT). The experiment confirms that the FFT accurately represents both amplitude and frequency characteristics of time-varying signals, demonstrating the effectiveness of LabVIEW for real-time signal processing and spectral analysis.

---

If you'd like, I can also:

✅ Convert this into a clean **PDF**
✅ Add diagrams, labeled block diagrams, or flowcharts
✅ Make a shorter or more technical version

Just tell me!
