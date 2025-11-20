# **STUDY OF DIFFRACTION PRODUCED BY CIRCULAR APERTURES OF DIFFERENT DIAMETERS**

## **AIM**

The objective of this experiment is to develop a Virtual Instrument (VI) using LabVIEW’s graphical programming environment to generate circular apertures of varying diameters and to compute their corresponding diffraction patterns. This is achieved by applying the Fourier Transform to the mathematical representation of the aperture. The goal is to observe how changes in aperture size influence the resulting diffraction pattern.

---

## **SOFTWARE REQUIRED**

**LabVIEW 2025**

---

## **THEORY**

LabVIEW (Laboratory Virtual Instrument Engineering Workbench) is an advanced graphical programming platform widely used in scientific research, instrumentation control, signal processing, and automation. Instead of traditional text-based coding, LabVIEW employs a graphical approach in which the programmer connects functional blocks using wires—this paradigm is known as *Graphical Programming*.

This visual method makes LabVIEW highly intuitive and accessible, particularly for engineering and experimental applications that require instrument simulation, data acquisition, or real-time visualization. LabVIEW programs are referred to as **Virtual Instruments (VIs)** because they closely resemble physical instruments in both layout and functionality.

A VI typically contains two key components:

1. **Front Panel** – User interface where indicators display results and controls allow user input.
2. **Block Diagram** – Graphical code composed of interconnected nodes, functions, and structures.

LabVIEW includes a comprehensive library of tools for mathematical computation, array manipulation, image processing, and signal analysis—making it ideal for simulating optical experiments such as diffraction.

In this experiment, several important nodes and tools are utilized, including:

---

### **Important Nodes Used in This Program**

#### **1. Eval Node**

The Eval Node, found under the Formula Evaluation palette, allows mathematical expressions to be entered as a *string*. The user can declare variables on the front panel and supply equations dynamically. This provides much more flexibility compared to the regular Formula Node because the formula itself can be modified during program execution.

It is mainly used to compute function values for arrays based on user-supplied expressions.

---

#### **2. Initialize Array**

This function creates an array of user-defined size, filling each element with a specified value. It is commonly used when generating coordinate matrices such as X- and Y-grids for image simulation.

---

#### **3. Transpose Array**

This function interchanges the rows and columns of an input matrix. It transforms an element located at position (i, j) into (j, i). It is essential when constructing 2-D coordinate grids for circular aperture generation.

---

#### **4. FFT.vi**

The FFT (Fast Fourier Transform) VI computes the Fourier Transform of a 1-D or 2-D array. The FFT is fundamental to optical diffraction simulation because **Fraunhofer diffraction patterns are equivalent to the Fourier Transform of the aperture function**.

---

#### **5. IMAQ Create**

This VI allocates memory for an image buffer. Since LabVIEW handles images through the NI Vision module, we must explicitly create image references using IMAQ Create before storing or displaying image data.

---

#### **6. IMAQ ArrayToImage**

This VI converts a standard numeric array (U8, I16, or floating point) into an IMAQ-compatible image reference. It allows raw matrix data to be displayed in LabVIEW’s image indicators.

---

## **PROCEDURE**

1. Launch **LabVIEW 2025** and create a **blank VI**. Two windows will appear—the *Front Panel* and the *Block Diagram*.
2. On the Block Diagram, place an **Eval Node** to generate linearly spaced numerical values.
3. Use numeric controls to define:

   * Start value = –1
   * Number of sample points = **N**
4. Insert an **Initialize Array** function. Set its dimensions using the numeric input and initialize all values to 1.
5. Create an **Outer Product** using the Initialize Array output and the Eval Node output to generate the **X-matrix**.
6. Apply **Transpose Array** to produce the **Y-matrix** from the X-matrix.
7. Use multiplication nodes to compute (X^2) and (Y^2).
8. Add these matrices and apply a **Square Root** node to calculate:
   [
   r = \sqrt{X^2 + Y^2}
   ]
   This gives the radial distance matrix.
9. Insert an **Expression Node** and implement a conditional expression such as:
   [
   x < 0.09 ? 1 : 0
   ]
   This generates a binary circular aperture.
10. Place **IMAQ Create** to allocate an image buffer.
11. Connect the aperture matrix to **IMAQ ArrayToImage** to convert it into a displayable image.
12. Add an image indicator on the Front Panel to visualize the circular aperture.
13. Insert an **FFT.vi**, and wire the aperture matrix into it to compute its diffraction pattern.
14. Set:

    * (m = 4N), (n = 4N) (to satisfy the Nyquist sampling criterion)
    * Enable **FFT Shift** to center the diffraction pattern.
15. Use **Complex to Polar** conversion to extract the magnitude of the FFT output.
16. Convert the FFT magnitude to an image using IMAQ functions and display it on the Front Panel.
17. Enclose the entire program inside a **While Loop** and add a Boolean STOP control.

---

## **DIFFRACTION PATTERNS OBSERVED**

### **Figure 1 – Circular Aperture (Diameter = 0.18)**

### **Figure 2 – Circular Aperture (Diameter = 0.4)**

### **Figure 3 – Circular Aperture (Diameter = 0.74)**

### **Figure 4 – Single Slit (Width = 0.018)**

---

## **OBSERVATIONS**

* Circular apertures produce diffraction patterns consisting of bright central spots surrounded by concentric rings. This is known as the **Airy Pattern** or **Airy Disk**.
* Mathematically, the intensity distribution of a circular aperture’s diffraction is proportional to the square of a first-order **Bessel function**.
* In Fraunhofer (far-field) diffraction, the pattern is directly obtained through a Fourier Transform.
* The central bright region (Airy disk) becomes **smaller** when the aperture diameter **increases**, consistent with:
  [
  \text{Width of Airy Disk} \propto \frac{\lambda}{D}
  ]
* A single rectangular (horizontal) slit produces a **vertical diffraction pattern**, resembling a sinc-squared intensity distribution.

---

## **RESULT**

A virtual instrument was successfully constructed in LabVIEW to generate circular apertures of various diameters and compute their diffraction patterns using Fourier Transform principles. The experiment validates the inverse relationship between aperture diameter and the width of the diffraction pattern. Additionally, diffraction from a single slit was simulated and analyzed.
