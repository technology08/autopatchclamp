# 🧬 Auto-Patching Suspended Cells to Determine Optimal Electroporation Parameters  

**Automated Optical and Electrophysiology of Suspended Cells In Vitro**  
This system integrates real-time optical and electrophysiological techniques to optimize electroporation parameters for suspended cells. By automating patch-clamping, fluorescence measurement, and precise electrical stimulation, the platform improves the reproducibility and efficiency of cellular electrophysiology experiments.  

Developed during my research internship at Columbia Bioelectronics System Lab in Summer 2024.  

This project is built on the **[ACQ4](https://github.com/acq4/acq4)** open-source framework for electrophysiology and optical imaging experiments, expanding its capabilities for automated suspended cell patch-clamping and electroporation testing. 

| Cell Capture | Robotic Movement & Cleaning | Real-Time User Interface with Cell Detection & Microscope Camera |
|------------|------------|------------|
| ![Cell Capture](demo_media/cell_capture.gif) | ![Vertical Demo](demo_media/micromanipulator_movement.gif) | ![Horizontal Demo](demo_media/ui_demo.gif) | 

The left GIF shows the platform properly capturing a cell and moving around the bath, integrating micromanipulator robots, microscope cameras, and suction.
The middle animation shows the micromanipulators undergoing the cleaning procedure with precise robotic movements.
The right animation shows a demo of the user interface, integrating all devices for experiment preparation and performance.

See below for a more detailed description of these animations.

Special thanks to William Stoy, my mentor for this summer's project.

## Features  

✅ **Automated Pipette Positioning** – High-precision micromanipulator integration.  
✅ **Integration of 10 Hardware Devices** – Micromanipulators, DAQ, pressure control (suction), microscope's stage and camera all controllable and viewable through one platform.  
✅ **Continuous Voltage Application** – Patch clamping enables steady-state voltage control.  
✅ **Fluorescence Measurement** – Captures voltage-sensitive fluorescence at different membrane potentials.  
✅ **State Machine Workflow** – Automates cell patching and resistance monitoring.  
✅ **Live Data Analysis & Visualization** – Displays patch pipette resistance, current, voltage, and fluorescence in real-time.  
✅ **Electroporation Control** – Applies brief electric pulses to lyse the cell membrane. (undergoing testing)  

## Tech Stack & Tools  

- **Programming:** Python, PySerial  
- **Hardware:** Micropipette manipulators, Patch-clamp amplifier, NI DAQ digitizer, Microscope camera  
- **Electrophysiology:** Patch clamping, Fluorescence-based voltage measurement  
- **Automation:** Microcontroller integration (Arduino/Raspberry Pi)  
- **Software Dependencies:** NumPy, SciPy, Matplotlib

## Detailed Demo Animation Description
The left GIF shows the platform properly capturing a cell, moving around the bath, returning to its precise position, before expelling the cell and beginning the cycle again.
The middle animation shows the micromanipulators undergoing the cleaning procedure: lifting out of the cell bath, moving back 2cm, lowering before intaking and expeling cleaning solution, and finally returning to the cell bath. This entire process cannot hit any of the walls, which would break the micropipette and terminate the experiment.
The right animation shows a demo of the user interface. The left third of the UI contains three graphs: from top to bottom, the voltage, current, and resistance curves by time. The resistance curve is red when the resistance indicates the micropipette is not attached to a cell, and green when the micropipette is attached to a cell. The camera in the middle third is static for this demo, but updates in real time like the leftmost figure. Finally, the graph on the right third is a histogram for brightness, and is used for adjusting the microscope's light in real-time to provide the appropriate brightness for the image. In this way, the UI works both during preparation and during the experiment itself.

## Setup & Installation  

### 1. Clone the Repository  
```bash
git clone https://github.com/technology08/autopatcher-suspended-cell.git
cd autopatcher-suspended-cell
```

### 2. Install Dependencies  
```bash
pip install -r requirements.txt
```

### 3. Connect Hardware  
- Ensure the **micropipette manipulator, amplifier, and microscope** are connected via serial ports.  
- Configure **NI-DAQ settings** for data acquisition and electroporation control.  
- Default configuration includes 2 Scientifica PatchStar manipulators.  

### 4. Run the Auto-Patcher  
```bash
python autopatcher.py
```
- This launches the automated patching and fluorescence measurement system.  

## System Overview  

| Step | Description |
|------|------------|
| **1. Pipette Positioning** | Moves pipette into place using micromanipulator-controlled motors. |
| **2. Resistance-Based Cell Detection** | Detects cell contact using electrical resistance measurements. |
| **3. Electroporation** | Applies brief electric pulses to lyse the cell membrane. |
| **4. Patch Clamping** | Forms a GΩ seal between the micropipette and cell by applying suction through custom-built pressure controller. |
| **5. Continuous Voltage Control** | Applies voltage protocols to measure fluorescence. |
| **6. Data Collection & Analysis** | Displays live resistance, current, voltage, and fluorescence response. |

## Research & References  

- **Electroporation Theory** – [Springer Article on Electroporation](https://link.springer.com/article/10.1007/s42452-019-1646-2)  
- **Patch Clamping Techniques** – [JoVE Patch-Clamp Guide](https://app.jove.com/t/54024/whole-cell-patch-clamp-recordings-in-brain-slices)  
- **Automated Patch-Clamp Systems** – [IEEE Research Paper](https://ieeexplore.ieee.org/document/XXXXX)  
- **Fluorescence-Based Voltage Imaging** – [Voltage-Sensitive Fluorescent Proteins](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6708467/)  
- **ACQ4 Framework** – [ACQ4 GitHub Repository](https://github.com/acq4/acq4). All ACQ4 files are governed under its own MIT License, and this project as an extension is also governed by the same MIT License. From their README: "ACQ4 is developed with support from the [Allen Institute for Brain Science](alleninstitute.org), [Sensapex Oy](sensapex.com), the [University of North Carolina at Chapel Hill](unc.edu), and many other users around the world." Please support the ACQ4 platform and developers!  

## License  

This project is licensed under the **MIT License**. See `LICENSE` for details.  

## Author  

**Connor Espenshade**  
- [LinkedIn](https://linkedin.com/in/cespenshade)  
- [GitHub](https://github.com/technology08)
