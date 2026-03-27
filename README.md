# Warehouse Productivity Simulation 📦

A data-driven approach to measuring warehouse worker productivity fairly by accounting for different order types and handling complexities.

## Problem Statement

Traditional warehouse metrics like **Picks Per Hour (PPH)** unfairly penalize workers who handle larger items or bulk orders (totes). A worker picking 5 totes might move 750+ items but show only 5 picks, while another worker picking 200 small boxes shows 200 picks - despite moving fewer total items.

This creates:
- ❌ Demotivated high-productivity workers
- ❌ Inaccurate performance reviews  
- ❌ Suboptimal workforce allocation
- ❌ Bias against workers assigned to bulk items

## Solution

This notebook provides **two approaches** to fair productivity measurement:

### Approach 1: Weighted Scoring System
Calculates time-based weights for each container type:
- Small Box = 1.0 point (baseline)
- Medium Box = ~1.2 points
- Tote = ~25+ points (based on actual time investment)

### Approach 2: Machine Learning Model
Uses Linear Regression to automatically discover the true effort cost of each container type by learning from simulated work data.

**Output:** Efficiency Score where:
- **> 1.0** = Overperforming (excellent)
- **= 1.0** = Meeting expectations
- **< 1.0** = Underperforming (needs improvement)

## Quick Start

### Prerequisites
- Python 3.8+
- Jupyter Notebook or JupyterLab

### Installation

1. Clone this repository:
```bash
git clone <your-repo-url>
cd Effort
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Run the simulation:
```bash
jupyter notebook stimi.ipynb
```

Or run the Python script:
```bash
python stimi.py
```

## What's Included

- `stimi.ipynb` - Interactive Jupyter notebook with visualizations
- `stimi.py` - Standalone Python script version
- `requirements.txt` - Python dependencies
- `warehouse_simulation_data.csv` - Generated after running (output file)

## Configuration

You can customize the simulation parameters in the notebook:

```python
TARGET_PPH = 220  # Target picks per hour
ITEMS_PER_TOTE = 150  # Items in a bulk tote
TIME_PER_ITEM_SMALL = 15  # Seconds per item
TIME_PER_CONTAINER_TOTE = 60  # Seconds to process a tote
```

## Key Visualizations

The notebook generates several charts showing:
1. **System View vs Reality** - Exposes the measurement bias
2. **Fair Productivity Scores** - Corrected view using weighted approach
3. **Distribution Analysis** - Shows how bias affects different worker types
4. **ML Model Insights** - Discovered weights and accuracy metrics
5. **Worker Efficiency Rankings** - Fair leaderboard based on actual effort

## Example Output

After running, you'll see analysis like:

```
Comparison Table:
                   System_PPH  Total_Items_Actual  Fair_PPH
Worker_Type                                                
Box_Picker          145.2             145.2           145.2
Mixed               112.5             387.4           142.8
Tote_Picker           4.2             598.6           148.3
```

Notice how Tote_Pickers appear worst in System_PPH (4.2) but are actually the most productive when measured fairly (148.3 Fair_PPH)!

## Requirements

- pandas >= 2.0.0
- numpy >= 1.24.0
- matplotlib >= 3.7.0
- seaborn >= 0.12.0
- scikit-learn >= 1.2.0
- jupyter >= 1.0.0

## Use Cases

- ✅ Warehouse operations optimization
- ✅ HR performance management systems
- ✅ Logistics workforce planning
- ✅ Educational demos for ML/analytics
- ✅ Operations research case studies

## License

© 2026 All Rights Reserved. This software is provided for educational and informational purposes only. No license is granted for commercial use, modification, distribution, or creation of derivative works without explicit permission from the author.

For licensing inquiries, please contact the repository owner.

## Author

Created as a demonstration of fair productivity measurement using data science and machine learning techniques.

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests for improvements.

---

**Keywords:** warehouse optimization, productivity metrics, machine learning, fairness in analytics, operations research, workforce management, Python, data science
