# Smart City Video Intelligence
## User Interface
This is a Smart City traffic monitoring demo built as an edge computing showcasing live traffic cameras across 5 areas in New York City - real time accidents, obstruction, and crowd detection plus traffic density - all running on Arm64 Ampere processor, zero GPUs, no cloud inference.
The dashboard includes three tabs:

**Overview - the main view:**

- Stat cards shows anomalies, latency, pedestrians, vehicles, and no GPU
- Top 5 busiest cameras at live feeds with YOLO bounding boxes ranked by traffic.
- Camera grid in 5 areas that toggles every 30s between a camera list and an animated rolling summary report with weather, air quality, etc.
- Charts of vehicle flow by area, traffic density
- NYC weather, air quality 
- System health gauges 
- Recent anomalies table

**Performance** - summary cards, a 3-tier pipeline visualization, and a full events table with “Clear All”

**Camera modal** (click any camera) - live feed with synced YOLO boxes plus a side panel showing camera detail, weather, air quality mini chart, VLM-confirmed density/flow, and per-anomaly confirm/decline operator-review buttons.
