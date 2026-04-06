# 🌊 GeoAI Flood Digital Twin

**Real-time GeoAI digital twin for urban flood simulation targeting South Mumbai**

A cutting-edge geospatial AI application that simulates coastal flooding impacts on urban infrastructure using network analysis and U-Net deep learning models.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Technologies](#technologies)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Data Files](#data-files)
- [How It Works](#how-it-works)

---

## 🎯 Overview

This project creates an interactive digital twin of South Mumbai's (BKC - Bandra Kurla Complex) road infrastructure to simulate the impact of coastal flooding and sea level rise. The application uses pre-calculated network graphs at different water levels to provide real-time visualization and impact analysis.

**Target Area:** South Mumbai (BKC Region)  
**Edge AI Model:** U-Net  
**Simulation Levels:** 0m, 2m, 4m, 6m, 8m, 10m sea level rise

---

## ✨ Features

- 🗺️ **Interactive Map Visualization** - Real-time visualization of road networks using OpenStreetMap data
- 📊 **Dynamic Flood Simulation** - 5 different sea level rise scenarios (2m to 10m)
- 📈 **Live Infrastructure Metrics** - Track navigable roads and blocked/flooded routes
- 🎨 **Dark Theme UI** - Modern, responsive Gradio interface
- ⚠️ **Alert System** - Automatic status alerts for flooding conditions
- 🚀 **Fast Processing** - Pre-calculated graphs for instant scenario visualization
- 🌐 **Web-Based** - Easy-to-deploy Gradio application

---

## 🛠️ Technologies

| Technology | Purpose |
|-----------|---------|
| **Gradio** | Interactive web UI framework |
| **OSMnx** | OpenStreetMap network data retrieval and analysis |
| **Matplotlib** | Network visualization and plotting |
| **NetworkX** | Network analysis and graph operations |
| **Python 3.8+** | Core programming language |

---

## 📦 Installation

### Prerequisites
- Python 3.8 or higher
- pip (Python package manager)

### Setup Instructions

1. **Clone the repository**  
   ```bash
   git clone https://github.com/pg-gosavi/GeoAI-Flood-Digital-Twin.git
   cd GeoAI-Flood-Digital-Twin
   ```

2. **Create a virtual environment (optional but recommended)**  
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**  
   ```bash
   pip install -r requirements.txt
   ```

4. **Verify all GraphML files are present**  
   - `mumbai_bkc_graph_baseline.graphml`
   - `mumbai_flood_2m.graphml`
   - `mumbai_flood_4m.graphml`
   - `mumbai_flood_6m.graphml`
   - `mumbai_flood_8m.graphml`
   - `mumbai_flood_10m.graphml`

---

## 🚀 Usage

### Running the Application

```bash
python app,py
```

The application will start a local Gradio server (typically at `http://127.0.0.1:7860`)

### Using the Dashboard

1. **Adjust the Water Level Slider** - Ranges from 0m (baseline) to 10m
2. **View the Map** - Roads turn red as they become flooded
3. **Monitor Metrics**:
   - Total Navigable Roads: Count of accessible routes
   - Flooded/Blocked Roads: Count of impassable routes
   - System Status: Real-time alert messages

### Interpretation

- **White Roads**: Safe, navigable infrastructure
- **Red Roads**: Flooded or blocked by water
- **Status Messages**: 
  - "Mumbai Infrastructure operating at 100% capacity." (0m)
  - "ALERT: Coastal flooding detected. Sea level rise: Xm." (2m-10m)

---

## 📂 Project Structure

```
GeoAI-Flood-Digital-Twin/
├── app,py                              # Main application
├── requirements.txt                    # Python dependencies
├── mumbai_bkc_graph_baseline.graphml  # Baseline network (2.1 MB)
├── mumbai_flood_2m.graphml            # 2m flood scenario (1.2 MB)
├── mumbai_flood_4m.graphml            # 4m flood scenario (2.1 MB)
├── mumbai_flood_6m.graphml            # 6m flood scenario (1.8 MB)
├── mumbai_flood_8m.graphml            # 8m flood scenario (1.5 MB)
├── mumbai_flood_10m.graphml           # 10m flood scenario (1.2 MB)
└── README.md                           # This file
```

---

## 📊 Data Files

All graph files are in **GraphML format** (XML-based network representation):

| File | Size | Description |
|------|------|-------------|
| `mumbai_bkc_graph_baseline.graphml` | 2.1 MB | Baseline road network without flooding |
| `mumbai_flood_2m.graphml` | 1.2 MB | Roads accessible at 2m sea level rise |
| `mumbai_flood_4m.graphml` | 2.1 MB | Roads accessible at 4m sea level rise |
| `mumbai_flood_6m.graphml` | 1.8 MB | Roads accessible at 6m sea level rise |
| `mumbai_flood_8m.graphml` | 1.5 MB | Roads accessible at 8m sea level rise |
| `mumbai_flood_10m.graphml` | 1.2 MB | Roads accessible at 10m sea level rise |

The graphs represent the road network with nodes (intersections) and edges (roads).

---

## 🧠 How It Works

### Architecture

```
User Input (Water Level Slider)
         ↓
Snap to Pre-calculated Tier (0, 2, 4, 6, 8, 10m)
         ↓
Load Corresponding GraphML File
         ↓
Calculate Differences (Baseline vs Current)
         ↓
Generate Visualization (Safe: White, Flooded: Red)
         ↓
Update Metrics (Navigable & Blocked Roads)
         ↓
Display on Dashboard
```

### Algorithm Steps

1. **Load all pre-calculated graphs** at startup
2. **Snap slider input** to nearest available level
3. **Compare baseline edges** with flood-level edges
4. **Identify lost roads** (edges in baseline but not in flood graph)
5. **Color-code visualization**: 
   - White for roads in both baseline and current graph
   - Red for roads only in baseline (now flooded)
6. **Calculate metrics**: Count remaining vs blocked roads
7. **Update status message** with current water level

### Why Pre-calculated Graphs?

- ⚡ **Real-time performance** - No computation delay
- 🎯 **Accuracy** - Each level has been carefully simulated
- 📊 **Scalability** - Handles large networks efficiently

---

## 🔍 Example Output

When you adjust the slider:

**At 0m (Baseline):**
- Status: "Mumbai Infrastructure operating at 100% capacity."
- All roads displayed in white
- 100% navigable roads

**At 6m (Flood Scenario):**
- Status: "ALERT: Coastal flooding detected. Sea level rise: 6m."
- Some roads turn red (flooded)
- Reduced navigable road count
- Increased blocked road count

---

## 🎓 Use Cases

- 🏙️ **Urban Planning** - Assess flood vulnerability of city infrastructure
- 📈 **Climate Risk Analysis** - Evaluate impact of sea level rise
- 🚦 **Emergency Response** - Plan evacuation and rescue routes
- 🔬 **Research** - Study urban resilience and climate adaptation
- 📊 **Policy Making** - Data-driven decisions for coastal protection

---

## 🔄 Customization

### Changing Water Levels

Edit the slider range in `app,py` (lines 82-88):
```python
water_slider = gr.Slider(
    minimum=0, 
    maximum=10,  # Change max level
    step=2,       # Change step size
    value=0, 
    label="Simulated Water Level (Meters)"
)
```

### Changing Visual Theme

Modify color definitions in `update_dashboard()` function (lines 33-35):
```python
BG_COLOR = '#111827'    # Dark background
SAFE_COLOR = '#FFFFFF'  # White for safe roads
FLOOD_COLOR = '#EF4444' # Red for flooded roads
```

---

## 📝 Requirements

See `requirements.txt`:
- `gradio` - UI framework
- `osmnx` - OpenStreetMap network tools
- `matplotlib` - Visualization library
- `networkx` - Network analysis library

---

## 🌍 Geographic Scope

- **Region:** South Mumbai (BKC - Bandra Kurla Complex)
- **Network Type:** Road infrastructure
- **Data Source:** OpenStreetMap

---

## 📚 References

- [Gradio Documentation](https://gradio.app/)
- [OSMnx Documentation](https://osmnx.readthedocs.io/)
- [NetworkX Documentation](https://networkx.org/)
- [GraphML Format](http://graphml.graphdrawing.org/)

---

## 🤝 Support

For issues, questions, or suggestions, please open an issue on the GitHub repository.

---

**Last Updated:** 2026-04-06 03:38:35  
**Repository:** [pg-gosavi/GeoAI-Flood-Digital-Twin](https://github.com/pg-gosavi/GeoAI-Flood-Digital-Twin)