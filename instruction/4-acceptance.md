# Part 4 - Acceptance

This part computes acceptance $A(p_\mathrm{T},|y|)$. Acceptance contains only muon kinematic requirements in our analysis.

Why acceptance is needed:
- even a perfectly efficient detector cannot observe events outside the fiducial region,
- acceptance quantifies detector geometric coverage and kinematic visibility before converting yields into cross sections.
- without this correction, the extracted cross section would be biased by inaccessible regions of phase space rather than true production rates.

## Acceptance Definition
In each bin:

$A(p_\mathrm{T},|y|)=\frac{N^{\mathrm{fid}}_{\mathrm{gen}}(p_\mathrm{T},|y|)}{N^{\mathrm{all}}_{\mathrm{gen}}(p_\mathrm{T},|y|)}$.
- denominator: all generated $\Upsilon\to\mu^+\mu^-$ events in one bin,
- numerator: events where both generated muons satisfy fiducial cuts.

Acceptance cuts:
- $|\eta(\mu)|<2.0$
- $p_\mathrm{T}(\mu)>3.1$ GeV



## Acceptance Calculation
We used the `particle-GUN` tool to simulate a large number of $\Upsilon\to\mu^+\mu^-$ decay events. By applying acceptance criteria to these events and calculating the proportion of events that pass the filter relative to the total number of events, we can estimate the acceptance values.

This part uses `acceptance.C`. The core logic is:
```cpp
All[iY][iPt] += 1.0;
...
if (std::abs(gen_muonP_p4->Eta()) > kMuonAbsEtaMax) continue;
if (std::abs(gen_muonN_p4->Eta()) > kMuonAbsEtaMax) continue;
if (gen_muonP_p4->Pt() <= kMuonPtMin) continue;
if (gen_muonN_p4->Pt() <= kMuonPtMin) continue;
Passed[iY][iPt] += 1.0;
```

**Note: DO NOT MODIFY the `kInputRoot` path in `acceptance.C`. The existing path can be accessed.**
```bash
cd /path/to/CMSDAS_Upsilon/acceptance
root -l acceptance.C
```

Outputs are acceptance 2D maps in $(p_\mathrm{T},|y|)$:
- `/path/to/CMSDAS_Upsilon/acceptance/results/acceptance.csv`
- `/path/to/CMSDAS_Upsilon/acceptance/results/acceptance.pdf`


Statistical uncertainty is computed with Clopper-Pearson intervals:
```cpp
double low = TEfficiency::ClopperPearson((int)all, (int)passed, 0.682689492, false);
double up  = TEfficiency::ClopperPearson((int)all, (int)passed, 0.682689492, true);
acc_err = std::max(acc - low, up - acc);
```


> #### **Question**
> 1. In data you directly observe reconstructed muons, while acceptance here uses generated muons; can this introduce a bias?
> 2. If yes, what method can you design to estimate its size? We will continue this question in `Part 6`.
