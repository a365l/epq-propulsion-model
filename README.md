# Quadcopter propulsion model validation

**How accurately can first-principles modelling predict quadcopter propulsion
performance from manufacturer versus measured component data?**

My Level 3 Extended Project Qualification (Pearson Edexcel), started October 2026.
The deliverable is two things: a Python simulation of quadcopter propulsion, and a
written report comparing what the model predicts against what I actually measure.

## The question, and why it is worth asking

Manufacturers publish thrust and current figures for motor and propeller
combinations. Those numbers are measured on their bench, under their conditions,
and builders size whole aircraft around them. This project asks how far a model
built from first principles can be trusted when it is fed those published numbers,
compared with when it is fed numbers I measure myself on a thrust stand.

The interesting result is not "the model works" or "the model fails". It is where
the two diverge, by how much, and which assumption is responsible.

## Scope

Three levels, each building on the last. The project is split this way on purpose:
if I fall behind, Level 1 is a complete and submittable piece of work on its own,
and anything above it is added depth rather than a dependency.

| Level | Model | Status |
|---|---|---|
| 1 | Momentum theory and the actuator disk. The simplest defensible first-principles model. | Planned |
| 2A | Lookup model driven by the UIUC propeller database, cross-checked against my own thrust stand runs. | Planned |
| 2B | Blade Element Momentum Theory, for a model that resolves the blade rather than the disk. | Planned |
| 3 | Stretch goal: whole-system model adding motor and battery behaviour to predict real endurance. | Stretch |

## Repository layout

```
src/propulsion/     the model itself, one module per level
thruststand/        logger and run data from my own measurements
data/               UIUC propeller database (fetched separately, not committed)
notebooks/          exploratory analysis and plots
report/             the written report
```

## Data

The UIUC Propeller Data Site is the validation reference for Level 2A. It is not
committed here: it is third-party data and roughly 90 MB. Download it from the
UIUC Applied Aerodynamics Group and unpack it to `data/UIUC-propDB/`.

Propeller selection for the experiments is constrained by that database. A
propeller only goes on the thrust stand if UIUC already holds data for it,
otherwise there is nothing to validate the measurements against.

## Running it

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
```

## A note on authorship

This is assessed coursework for a qualification, so the modelling, the analysis
and the report are my own work. Where I use a library, a published dataset or a
derivation from a textbook, it is cited in the report.

## Related

This is deliberately separate from my personal quadcopter build at
[a365l/quadcopter-project](https://github.com/a365l/quadcopter-project). The two
share a subject area and nothing else: the EPQ does not depend on that build, and
no work is counted twice. Portfolio: [alfred-leigh.co.uk](https://alfred-leigh.co.uk)
