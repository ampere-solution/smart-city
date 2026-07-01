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

<img width="2091" height="1094" alt="Screenshot 2026-04-14.png" src="Screenshot 2026-04-14.png" />

## Architectural Diagram
Below is the architectural diagram which visualize the smart city video intelligence in New York:

<img width="2091" height="1094" alt="image-20260608-232951.png" src="image-20260608-232951.png" />

## What This Demo Shows

The demo shows a live traffic operations dashboard for NYC.  On screen you see:
**On the dashboard** (the visible demo)
- Live NYC Dot camera feeds across 5 areas, with YOLO bounding boxes drawn on vehicles and pedestrians in real time
- Top 5 busiest cameras ranked live by traffic.
- Detected anomalies  - accidents, road constructions, and crowds 
- Traffic density per area (free flow, congested, etc) confirmed visually by the AI
- Per area situation reports (weather, AQ, density, anomalies)
- System health

What it is demonstrating 
- Real time multi camera AI vision for on CPU, no GPU required
- A mart pipeline beats brute force - a 3-tier funnel (heuristic → VLM → temporal tracking) gives both accuracy and throughput by only sending ~10% of frames to the expensive model.
- Human-in-the-loop operations - operators can Confirm?Decline anomalies, with smart per-object suppression.
- The same workload at a fraction of GPU/cloud cost, scaling linearly with cores rather than accelerators.

## Target Audience

This is fundamentally an Ampere Computing edge-compute showcase the underlying sell across every audience is that demanding vision-AI workloads run economically on Arm64 Ampere CPUs
- Technical leaders / Engineering decision-makers 
  - Want the how: the 3-tier pipeline, Qwen2.5-VL 3B running on Ampere’s optimized llama.cpp, area isolation, latency characteristics 
- Edge compute buyer / TCO-focused stakeholders
  - Want the cost story:  the performance vs cost
- Municipal / transit / government stakeholders 
  - Want the outcome:  real NYC cameras, real time accidents, crowd detections, operator review workflow, 







