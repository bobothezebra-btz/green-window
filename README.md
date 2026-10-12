# GreenWindow

GreenWindow will help teams run flexible computing jobs when electricity is expected to be cleaner. It is intended for AI training and inference, backups, batch processing, rendering, software builds, and other jobs that can start within a time window.

## How it will work

1. Read recent grid carbon intensity data from the [UK Carbon Intensity API](https://api.carbonintensity.org.uk/).
2. Forecast the next 48 hours with [`amazon/chronos-bolt-small`](https://huggingface.co/amazon/chronos-bolt-small).
3. For each job, find the lowest-carbon start time that lets the job finish by its deadline.
4. Estimate the CO₂ saved compared with running the job immediately.

The plan includes a plain-English assistant built with Hugging Face smolagents, a FastAPI REST API for company systems, and a Gradio demo for Hugging Face Spaces.

This repository is currently a project scaffold. The forecasting, scheduling, agent, API, and demo have not been implemented yet.

## Project folders

| Folder | Planned purpose |
| --- | --- |
| `data/` | Fetch and prepare carbon intensity data. |
| `model/` | Load the Chronos model and produce forecasts. |
| `scheduler/` | Compare feasible job start times and estimate CO₂ savings. |
| `agent/` | Turn plain-English requests into scheduling actions. |
| `api/` | Provide a REST API for company systems. |
| `app/` | Provide the Gradio demo. |
| `tests/` | Test each feature as it is built. |

## Set up a development environment

Use Python 3.10 or newer. In a terminal opened at the repository root, run:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
```

Once application code and tests are added, run the tests with:

```bash
python -m pytest
```
