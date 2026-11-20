# Student Learning Model — A System Dynamics Simulation

A 3-stock system dynamics model of student academic performance over a 30-week semester, built in [Stella Online](https://www.iseesystems.com/) for the *System Modelling* course, M.Tech Industrial Engineering & Management, IIT Kharagpur (April 2026).

## What it models

Three stocks interact through reinforcing and balancing feedback loops:

| Stock | Start | Meaning |
|---|---|---|
| **Motivation** | 50 | Drive to keep studying |
| **Knowledge** | – | Accumulated subject mastery |
| **Career Readiness** | 20 | Employability built from knowledge |

Six flows (Motivation Gain/Loss, Learning/Forgetting Rate, Career Gain/Loss) and nine auxiliary variables (Discipline, Sleep Quality, Social Support, Exam Pressure, Procrastination, Stress Proxy, Burnout, Study Time, Study Efficiency) drive them. Stress is computed as an auxiliary (`Stress Proxy`) rather than a stock, and all inflows use a saturation term `MAX(0,(100 − Stock)/100)` to keep stocks within 0–100.

**Feedback loops**
- **R1** – Motivation self-amplification
- **R2** – Learning–Career spiral (Motivation → Study Time → Learning → Knowledge → Career → Motivation)
- **B1** – Knowledge → Stress Proxy → Study Efficiency → Learning Rate (the stabilising loop)

## Base-case findings

- Motivation peaks at ~73 (week 14) then falls to ~52 as stress builds.
- Career Readiness peaks at ~56 (week 18), ending near 48.
- Forgetting overtakes learning around week 29.
- Burnout appears only in the final weeks.

The report also tests four improvement scenarios: better sleep, discipline, social support, and a gentler exam-pressure ramp.

## Repository contents

```
model/student-learning-model.stmx   Stella / XMILE model file
report/SMDA_Project_Report.pdf      Full project report (diagram, formulas, results, scenarios)
```

## Running the model

1. Open [Stella Online](https://stella.iseesystems.com/) (or Stella Architect / Professional).
2. Import `model/student-learning-model.stmx` (the file is standard [XMILE](http://docs.oasis-open.org/xmile/xmile/v1.0/xmile-v1.0.html)).
3. Simulation settings: 0–30 weeks, dt = 0.25, Euler integration.

## Author

Ritik Raj — M.Tech, Industrial & Systems Engineering, IIT Kharagpur
