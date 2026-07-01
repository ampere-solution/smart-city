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

## Key Message - What are we trying to convince of?

**Core message** 
demanding, real-time computer vision AI - at municipal scale - runs economically on commodity Arm64 processors.  You don’t need GPUs or the cloud.  
- It’s real - not a canned demo:  Live NYC DOT feeds, live weather, live AQ - every number on screen comes from a real source, refreshing in real time.
- It’s CPU-only: Five vision language models running in parallel on a single Arm64 server.  No GPU, no cloud inference
- It’s a pipeline, not a model:  it is feasible and affordable.  A 3 tier funnel (heuristics → VLM → temporal tracking) throws away ~90% of frames before the expensive model, giving accuracy and throughput plus a human intervention review step.  The architecture scales linearly with CPU cores, not accelerators - more cameras means more cores, not more GPUs.  The same workload at a fraction of the GPU cost.  
- So we’re convincing that edge AI economics favor Arm64 processors, and the live NYC traffic systems is the evidence.

## Proof Points - How does It Show This?

The Overview tab is a proof point - live DOT camera running in 5 different areas, 3 anomaly types, traffic density, weather Air Quality, and system health - all live, simultaneously on a Arm64 server.  
- It’s CPU only - no GPU
  - 8 live containers, all CPU pinned: Performance tab → pipeline diagram with live per-container CPU bars updating every 3s (5 VLM, detector, runner, and dashboard)
  - The cost consequence : Performance tab with cost comparison
 
- It’s real - live
  - Live camera feeds: Top 5 busiest strip - watch YOLO bounding boxes refresh in real time
  - Live weather + AQ: NYC weather strip and AQ section - pulled from Open-Metro per area
  - Live aggregation: Area summary reports 

- It’s a pipeline, not model
  - The 3 tiers are visible : 3 tier confidence breakdown per event
  - The funnel works: frame processed vs. anomalies detected - the gap proves ~90% of frames get filtered before the VLM.
  - VLM actually see: Density is dual confirmed.  PCE 40% + VLM 60%, shown as a confirmed density level per camera
  - Temporal lifecycle: incidents must persist across frames, not fire on one frame.
 
- Human intervention / Production Ready Ops
  - Operator review: Click any camera to Confirm/Decline buttons on anomalies
  - Resilience: If VLM drops, the other keep running.
 
The audience can watch what happened live - the CPU bars (not GPU), the refreshing feeds (real time), the expandable tier breakdown (pipeline), and the spatial decline (ops).  The presenter isn’t asserting any claims, the dashboard demonstrates each one in real time.

## Running the Demo

**Recommended Resources**

- Minimum: 64 cores. Recommended: 64+ cores
- Minimum: 64GB RAM. Recommended: 64+ GB RAM
- Minimum: 20GB disk space. Recommended: 100+ GB (multiple models, large models)







