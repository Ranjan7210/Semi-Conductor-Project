# Semi-Conductor Project: Hall Effect Virtual Laboratory

A high-fidelity, interactive, and physics-accurate 3D-style web simulation of the **Hall Effect Experiment**. It provides an engineering-grade environment to study carrier density, Hall coefficients, and magnetic field interactions across different semiconductor materials.

---

## 🔬 Core Physics & Mathematical Engine

The core math engine mimics real-world laboratory calibration parameters matching VLab reference structures, allowing students to extract $V_H$ safely using pure SI units natively mathematically rather than hardcoded magic offsets. 

### 1. Magnetic Field (B) Calibration
The Electromagnet outputs a B-field directly proportional to the applied current, strictly utilizing the empirical exact multiplier confirmed against reference systems:
- Let $I_{\text{em}}$ = Electromagnet Current (Amps)
- **$B \text{ (Tesla)} = 0.1482 \times I_{\text{em}}$**

### 2. The Hall Voltage ($V_H$) Calculation
The simulation utilizes the textbook Lorentz force derivation formula scaled safely via standard SI metrics:
- **$V_H = \frac{R_H \cdot I_H \cdot B}{t}$**
  - $R_H$: Hall Coefficient ($m^3 / C$)
  - $I_H$: Hall Current ($A$)
  - $B$: Magnetic Field Density ($T$)
  - $t$: Specimen Thickness ($m$)

### 3. Material Databases & Constants
Internally, the simulation accurately maintains the following polarity and property constraints:
* **Germanium (p-type)**: $R_H = +0.0194 \text{ m}^3\text{/C}$, $n = 3.227 \times 10^{17} \text{ m}^{-3}$, $\mu = 0.39$
* **Silicon (n-type)**: $n = 5.0 \times 10^{22} \text{ m}^{-3}$, $\mu = 0.15$
* **Gallium Arsenide (n-type)**: $n = 1.0 \times 10^{20} \text{ m}^{-3}$, $\mu = 0.85$

*(p-type materials trigger positive $V_H$ logic, while n-type carriers logically invert $V_H$ dynamically)*

---

## ✨ Features & Interactivity

The web app is engineered from the ground up to prevent "stodgy" legacy 2D designs. Instead, it offers a "Modern Laboratory" aesthetic.

* **3D Glassmorphic UI**: High-end styling overlay, shadows, glowing LEDs, and smooth variable manipulation components.
* **Realistic Digital Readouts**: "Digital-7 Mono" segmented LED fonts exactly mirroring lab hardware LCD setups. The Gauss meter realistically sits at `0.0000 T` when the probe is removed, and tracks beautifully up to 4 significant decimal places when active inside the magnetic field.
* **Animated Probe & Wires**: Dynamic SVG physics. Wires actually warp and flex as you insert the Hall Probe. The measurement connections utilize visually striking braided / twisted-pair cable (Red & Teal) graphics that dynamically bend with the UI.
* **Carrier Deflection Graphics**: A live Canvas API animation natively renders hole ($+$) and electron ($-$) trajectories inside the active specimen, visually modeling thermal wobble and the macroscopic deflection gradients introduced by the presence of a strong perpendicular $B$-field scalar.
* **Auto-Scaling Outputs**: The voltage output smartly drops from $V$ → $mV$ → $µV$ matching standard electrical laboratory multimeters via scaling parameters rather than static numerical readouts.

---

## 🛠️ Stack & Technologies

1. **HTML5 / CSS3**: Responsive, vanilla implementation. Advanced structural stylings leveraging `blur()` filters, CSS grid layouts, animated `stroke-dashoffset` for moving magnetic flux lines.
2. **Vanilla JavaScript (ES6)**: Real-time simulation state management. Direct DOM manipulation mapping formulas directly into the Canvas rendering loop. No bulky external frameworks involved (React/Vue/ThreeJS), minimizing payload overhead. 
3. **SVG & Canvas API Syncing**: Multi-mode visual displays balancing Vector Graphics (for sharp lab machinery/wires) with HTML5 Canvas (for particle physics inside the semiconductor specimen). 
4. **Chart.js**: Utilized to trace relationships dynamically like $V_H$ vs Magnetic Field directly.

---

## 🚀 Running Locally

Because the lab handles local module loading, you can preview the app via any basic web server to bypass CORS limitations:

```bash
# Clone the repository
git clone <repository_url>
cd Semi-Conductor-Project