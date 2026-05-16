Biophysical Brain Simulation

A spiking neural network simulation built from scratch — not a machine learning project. This is a bottom-up reconstruction of how real brains work, built neuron by neuron, synapse by synapse, over 12 versions spanning several months.

What this is
Most AI projects start from mathematics and work toward biology. This goes the other direction. Every mechanism here is grounded in actual neuroscience — the physics of ion channels, the anatomy of cortical layers, the dynamics of sleep. The goal is not to build something that performs a task. The goal is to build something that works the way a brain works and see what emerges.

What's implemented

Leaky Integrate-and-Fire neurons with biologically calibrated membrane time constants and refractory periods

Conductance-based synapses with AMPA and GABA conductances and reversal potentials — inhibition strength depends on membrane voltage, not a fixed sign flip

Tsodyks-Markram short-term plasticity — synapses fatigue under sustained firing and recover between bursts, enabling working-memory-like dynamics

Spike-timing dependent plasticity (STDP) with asymmetric time constants and an 80ms causal window — the network learns from its own activity

Interneuron diversity — PV (fast somatic inhibition), SST (dendritic filtering), and VIP (disinhibition) with correct connectivity rules. VIP releases SST releases pyramidal 

cells — the attentional gating circuit found in real cortex

Layered cortical architecture — L4 input layer, L2/3 association layer, L5/6 output layer with laminar-specific connection probabilities

T-type calcium current in thalamic relay neurons enabling burst mode firing

Ornstein-Uhlenbeck correlated noise — temporally correlated membrane fluctuations instead of white noise

After-hyperpolarization adaptation — neurons become harder to fire the more they've recently fired

Homeostatic synaptic scaling — each neuron tracks its own firing rate and adjusts sensitivity to stay near a biological target

Fatigue system — accumulated spiking raises effective threshold, modeling neural fatigue

Sleep/wake state machine — sleep pressure builds with network activity, triggers sleep state, recovers during sleep

Hippocampal memory replay — during sleep, hippocampal input neurons receive periodic reactivation pulses modeling sharp wave ripple consolidation

Gamma-distributed axon delays — biologically realistic right-skewed conduction time distributions

Three brain regions — Thalamus (8 relay + 4 TRN), Layered Cortex (18E + 4I), Hippocampus (15E + 3I) with bidirectional feedforward and feedback projections


Where this is going

V13 — Pattern learning
Present distinct sensory patterns through the thalamus and measure whether the network learns to respond differently to each. This is the bridge from simulator to cognitive system.

V14 — Maze navigation
Closed action-perception loop. Sensory input encodes environment, output layer drives actions, dopamine-modulated STDP provides reward signal. Watch the network learn to navigate.

V15 — Disease modeling
Selectively impair specific mechanisms and observe network breakdown. Epilepsy from E/I imbalance. Alzheimer's from progressive hippocampal neuron loss. Schizophrenia from PV interneuron dysfunction. The network is biologically grounded enough to break in realistic ways.

V16 — Vectorized engine
Rewrite neuron and synapse operations as NumPy array operations. Target: 10,000–100,000 neurons on GPU hardware.

Why this approach?

Most neural network projects optimize for performance on a task. This project optimizes for biological fidelity. The hypothesis is that if you build the architecture correctly — the right neurons, the right connections, the right learning rules, the right dynamics — interesting behavior should emerge without being explicitly programmed.
The sleep replay wasn't added because it seemed cool. It emerged as a logical necessity from the fatigue system. The interneuron diversity wasn't added for complexity. It was added because without it the E/I balance was physically wrong.
Every mechanism is there because the biology demanded it.

Built by
A 14 year old who started with a single neuron and couldn't stop. pretty rad right?
