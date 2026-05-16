
# ✈️ GreenWing Analytics

**Aviation Fuel Efficiency & Emission Intelligence Platform**

Data-driven fuel optimization and CORSIA-compliant emission monitoring for airlines.

---

## 🎯 What It Does

GreenWing Analytics helps airlines **save fuel, reduce CO₂ emissions, and prepare for CORSIA compliance** through advanced data analytics.

### Core Capabilities

| Feature | Description |
|---------|-------------|
| **Fuel Efficiency Analysis** | Route-by-route fuel consumption tracking and benchmarking |
| **Altitude Optimization** | Optimal cruise altitude calculation with buffet, RVSM, and directional constraints |
| **Step Climb Planning** | Weight-based step climb recommendations with dispatcher instructions |
| **Cost Index Optimization** | Route-specific CI/Mach optimization balancing fuel vs. time cost |
| **Tankering Analysis** | Fuel price differential optimization with MTOW safety checks |
| **CORSIA Reporting** | MRV-compliant (Monitoring, Reporting, Verification) emission reports |
| **SAF Impact Analysis** | Sustainable Aviation Fuel lifecycle emission and cost-benefit analysis |
| **Interactive Dashboard** | Real-time fleet performance visualization |
| **Professional Reports** | Automated HTML/PDF reports with KPIs, benchmarks, and recommendations |
| **Sensitivity Analysis** | Input uncertainty propagation and confidence intervals |
| **Uncertainty Tracking** | Results in “value ± error” format for transparency |

---

## 🛠 Technology Stack

| Component | Technology |
|-----------|-----------|
| Core Engine | Python 3.9+ |
| Physics Models | ISA Atmosphere, BADA-based performance, ICAO emission methodology |
| Optimization | Altitude, step climb, cost index, tankering |
| Visualization | Plotly, Matplotlib |
| Dashboard | Dash + Dash Bootstrap Components |
| Data Source | OpenSky Network (ADS-B), customer Excel/CSV |
| Advanced Analysis | MATLAB |
| Reporting | Jinja2-style HTML → PDF |

---

## 📁 Project Structure

```text
GreenWing_Analytics/
├── config/                          # Configuration
│   ├── settings.py                  # Physical constants, system settings
│   ├── aircraft_database.yaml       # Aircraft parameters (11 types)
│   └── assumptions.py               # Operational assumptions (overrideable)
│
├── src/
│   ├── units.py                     # Unit conversion & standardization
│   ├── utils.py                     # Shared helpers
│   ├── logging_config.py            # Analysis traceability
│   │
│   ├── validation/                  # 3-layer validation
│   │   ├── data_validator.py
│   │   ├── physics_validator.py
│   │   └── business_validator.py
│   │
│   ├── models/                      # Physics engines
│   │   ├── atmosphere.py
│   │   ├── aircraft_performance.py
│   │   ├── fuel_model.py
│   │   └── emission_model.py
│   │
│   ├── data_collection/             # Data collection
│   │   ├── opensky_collector.py
│   │   └── airport_database.py
│   │
│   ├── analysis/                    # Analysis engines
│   │   ├── phase_segmentation.py
│   │   ├── flight_analyzer.py
│   │   ├── fleet_analyzer.py
│   │   ├── benchmark.py
│   │   ├── sensitivity.py
│   │   └── uncertainty.py
│   │
│   ├── optimization/                # Optimization engines
│   │   ├── altitude_optimizer.py
│   │   ├── cost_index_optimizer.py
│   │   ├── tankering_optimizer.py
│   │   └── model_calibrator.py
│   │
│   └── reporting/                   # Reporting
│       └── report_generator.py
│
├── dashboard/
│   └── app.py                       # Interactive web dashboard
│
├── matlab/
│   ├── cruise_optimization.m
│   └── step_climb_analysis.m
│
├── scripts/
│   ├── 01_collect_data.py
│   ├── 02_analyze_and_optimize.py
│   └── 03_generate_outputs.py
│
├── tests/                           # Test suite
├── data/                            # Local data (not tracked in git)
├── reports/                         # Generated reports (not tracked in git)
├── notebooks/                       # Jupyter notebooks
└── docs/                            # Docs and exported charts
________________________________________
📊 Supported Aircraft
ICAO	Name	Engine
B738	Boeing 737-800	CFM56-7B26
B38M	Boeing 737 MAX 8	LEAP-1B
A320	Airbus A320-200	CFM56-5B4/3
A20N	Airbus A320neo	LEAP-1A
A321	Airbus A321-200	V2533-A5
A21N	Airbus A321neo	LEAP-1A-33
B77W	Boeing 777-300ER	GE90-115B
B788	Boeing 787-8	GEnx-1B70
B789	Boeing 787-9	GEnx-1B76
A350	Airbus A350-900	Trent XWB-84
A380	Airbus A380-800	Trent 970
________________________________________
🚀 Quick Start
Installation
Bash
git clone https://github.com/YOUR_USERNAME/greenWing-analytics.git
cd greenWing-analytics

python -m venv greenWing_env
greenWing_env\Scripts\activate

pip install -r requirements.txt
Environment Variables
Bash
copy .env.example .env
Then edit .env if you have OpenSky credentials:
env
OPENSKY_USERNAME=your_username
OPENSKY_PASSWORD=your_password
Run Core Module Tests
Bash
python -m config.settings
python -m config.assumptions
python -m src.units
python -m src.models.atmosphere
python -m src.models.fuel_model
python -m src.models.emission_model
python -m src.analysis.phase_segmentation
python -m src.analysis.fleet_analyzer
python -m src.optimization.altitude_optimizer
python -m src.reporting.report_generator
Run Full Test Suite
Bash
python tests/test_atmosphere.py
python tests/test_performance.py
python tests/test_fuel_model.py
python tests/test_emission.py
python tests/test_optimization.py
python tests/test_validation.py
python tests/test_units.py
python tests/test_uncertainty.py
python tests/test_utils.py
python tests/test_logging.py
Run Dashboard
Bash
python dashboard/app.py
Open in browser:
text
http://localhost:8050
Real Data Workflow
Bash
python scripts/01_collect_data.py
python scripts/02_analyze_and_optimize.py
python scripts/03_generate_outputs.py
________________________________________
📋 CORSIA Compliance
GreenWing Analytics supports the 3 components of CORSIA MRV:
Component	Status	Description
M — Monitoring	✅	Fuel-based monitoring (Method B — Block Fuel)
R — Reporting	✅	ICAO Annex 16 Vol IV compatible reporting
V — Verification	✅	Self-assessment checklist included
SAF Support
SAF Type	Lifecycle CO₂ Reduction
HEFA	72%
FT-SPK	90%
ATJ	62%
PTL	92%
SIP	65%
________________________________________
🔬 Methodology
Fuel Calculation
text
CD = CD0 + K × CL²
FF = SFC × Drag
SAR = TAS / FF
Total Fuel = Numerical integration over distance
Optimization Constraints
•	FAR 25.251 buffet margin
•	RVSM altitude levels
•	Directional flight level rules
•	Maximum operating altitude
•	MTOW checks
•	Fuel tank capacity checks
•	Step climb count and spacing limits
Emissions
•	CO₂ = Fuel × 3.16
•	H₂O = Fuel × 1.24
•	NOx = BFFM2 + ICAO Engine Emission Databank
•	Contrail = Schmidt-Appleman criterion
________________________________________
📈 Typical Insights
Based on real ADS-B and model-based analysis:
•	Altitude optimization potential: 1-3%
•	Step climb benefit on long routes: 100-300 kg per flight
•	Cost Index optimization: 0.5-2% total cost reduction
•	Tankering savings on fuel price differential routes: $50-300 per flight
•	Single-route annual saving potential: $100K-500K
________________________________________
🧪 Testing Philosophy
This project includes:
•	Module self-tests (python -m module)
•	Standalone test scripts (python tests/...)
•	Validation layers
•	Data validation
•	Physics validation
•	Business validation
•	Benchmark checks
•	Sensitivity analysis
•	Uncertainty propagation
The goal is not just to produce numbers, but to ensure those numbers are:
•	physically valid
•	operationally realistic
•	commercially explainable
________________________________________
🔒 Data & Privacy
•	ADS-B data used from public OpenSky Network feeds
•	Customer data is assumed to remain local
•	Generated reports are local files
•	No mandatory cloud dependency
•	.env files and raw data are excluded from git
________________________________________
📧 Contact
•	Email: greenwingsanalytics@gmail.com
•	LinkedIn: https://linkedin.com/in/emrecorakci
•	LinkedIn:  
________________________________________
📄 License
Proprietary — All rights reserved.
________________________________________
🙏 Acknowledgments
•	OpenSky Network
•	ICAO
•	Eurocontrol
•	IATA
•	EASA
________________________________________
Built with aerospace engineering logic and commercialization focus.
