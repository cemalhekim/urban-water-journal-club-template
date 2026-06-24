# Presentation notes and timing

Target duration: **11:30**, leaving roughly 30 seconds of safety against the
12-minute limit. Slides 15-19 are backup slides and are not part of the timed
talk.

## Presenter allocation

- **Cemal - slides 1-4: 3:50**
- **Jan - slides 5-9: 3:50**
- **Moyang - slides 10-14: 3:50**

Rehearse with one shared timer. Do not explain every bullet; state the claim,
point to the evidence, and move on.

## Full-score rehearsal gate

Before presenting, complete one uninterrupted rehearsal and verify all of the
following:

- finish between 11:00 and 12:00, with a target of 11:30;
- each presenter finishes their section in 3:50, including the handover;
- state when a claim is reported by the authors and when it is the presenters'
  interpretation;
- point to the evidence on each results slide instead of reading bullets;
- open backup slides only for Q&A;
- answer Q&A in the order: direct answer, evidence, uncertainty, resolving
  experiment.

For Q&A, the presenter whose section is closest to the question answers first.
Another presenter may add one short point only if it adds evidence or a
limitation. This keeps participation balanced and answers concise.

## Slide-by-slide speaking cues

### 1. Title - 0:20 - Cemal

Opening: “This paper asks whether normal hydraulic behavior can be learned as
an image translation problem and whether deviations from that learned behavior
can reveal leaks.”

### 2. Research challenges - 1:00 - Cemal

State the two challenges as questions: can weak leak signals be separated from
noise, and can detection plus localization work without labeled leaks?
Emphasize that these are the problems to solve, not a description of the
authors' method.

Transition: “The paper therefore needs a method that learns normal behavior
without requiring a library of labeled leaks.”

### 3. Paper goal and research question - 1:15 - Cemal

Read the research question once. Then state the paper's goal in plain language:
develop accurate, robust, near-real-time leak detection and localization from
pressure data despite uncertainty and scarce labels. Explicitly say that using
a GAN is the proposed method, not the research goal.

Transition: “To pursue that goal, the authors propose a four-stage pipeline.”

### 4. Core pipeline - 1:15 - Cemal

Follow the diagram from simulation to SSIM. Define the novelty as the
combination of normal-data simulation, a fast surrogate, and a spatial anomaly
score.

Handover: “Jan will now explain how this pipeline turns an image mismatch into
an alarm and how the authors tested it.”

### 5. What are GAN and CDCGAN? - 0:45 - Jan

Define the terms before discussing the leak detector. A GAN has a generator
that creates synthetic images and a discriminator that tries to identify them.
They improve through competition. CDCGAN adds two ideas: the output is
conditioned on a specific demand image, and convolutional layers learn spatial
pressure patterns. End with: “Here, demand is translated into the expected
leak-free pressure image.”

### 6. Decision logic - 0:45 - Jan

Separate training from deployment. During training, U-Net, PatchGAN, and L1
loss learn normal demand-pressure behavior. During deployment, the generator
predicts normal pressure; global SSIM detects and local SSIM localizes. State
the delay/false-alarm tradeoff.

### 7. Evaluation design - 0:50 - Jan

Separate the two evidence levels:

1. controlled hypothetical leaks;
2. the smaller, time-varying BattLeDIM leaks.

This distinction prepares the audience for the critical evaluation.

### 8. Magnitude drives detection - 0:50 - Jan

Use the large/medium/small comparison. The key sentence is:
“The model responds when the pressure-image disturbance becomes strong enough,
not necessarily when the leak begins.”

### 9. Averages hide failures - 0:40 - Jan

Do not present 0.90 accuracy as universally strong. Point out that high TNR can
coexist with poor small-leak TPR. Make the distinction between a reported
result and your interpretation explicit.

Handover: “Moyang will now examine the more realistic year-long test and what
the evidence does and does not justify.”

### 10. Year-long stress test - 0:50 - Moyang

Lead with “five of six detected,” then qualify it: detection near peak rate,
70% accuracy, 160-185 m localization. Conclude that this supports feasibility,
not field readiness.

### 11. Critical evaluation - 0:55 - Moyang

Keep the two columns distinct. The left side is supported by evidence; the
right side lists claims that require further experiments. The strongest
criticism is the missing deterministic U-Net or residual baseline.

### 12. Assumptions - 0:45 - Moyang

Say explicitly: “The first column is reported by the authors; the second is our
deployment interpretation.” Use one example: a valve change may look like a
leak because it shifts the learned normal mapping.

### 13. Conclusion and next tests - 0:50 - Moyang

Answer the research question directly: yes for sufficiently strong isolated
leaks; not yet for general early field detection. State the practical role as
screening and inspection prioritization.

### 14. Take-home verdict - 0:30 - All

Each presenter delivers one column in about 8 seconds. Moyang closes with:
“Our verdict is a promising proof of concept whose practical claims now need
comparative baselines and field robustness tests.”

## Q&A response pattern

Use this order:

1. answer the question directly in one sentence;
2. cite the relevant evidence or limitation;
3. acknowledge uncertainty;
4. state what experiment would resolve it.

### Likely question: Why use a GAN instead of a U-Net?

“Adversarial training may preserve spatial structure that helps SSIM-based
localization, but the paper provides no U-Net ablation, so the incremental
benefit of the GAN is not established.”

### Likely question: How can 33 sensors perform like 780 points?

“Both cases are converted to interpolated images, and aggregate accuracy is
dominated by easier conditions. Repeated sensor-placement experiments with
uncertainty intervals are needed before claiming sensor-count invariance.”

### Likely question: Is 70% accuracy operationally useful?

“It shows partial feasibility, but accuracy alone is insufficient for an
imbalanced time series. A utility would need event-level precision and recall,
false alarms per month, detection delay, and localization confidence.”

### Likely question: What is the most important limitation?

“External validity: one simulated network, fixed operating assumptions, no
simultaneous leaks, and no comparison against simpler baselines.”

### Likely question: What would you test next?

“A multi-network benchmark comparing CDCGAN with U-Net and hydraulic residual
baselines under sensor faults, topology changes, drift, and simultaneous leaks,
with cost-sensitive threshold evaluation.”
