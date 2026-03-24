## Welcome to the CMSDAS Upsilon Cross-Section Long-exercise Repository

This repository contains materials for measurements of the cross sections of $\Upsilon(1\mathrm{S})$, $\Upsilon(2\mathrm{S})$, and $\Upsilon(3\mathrm{S})$ with 2025 CMS data.

## Folder Structure
```text
CMSDAS_Upsilon/
├── README.md                                # This file
├── instruction/                             # Instructions
│   ├── 0-remarks.md
│   ├── 1-introduction.md
│   ├── 2-data.md
│   ├── 3-yield.md
│   ├── 4-acceptance.md
│   ├── 5-efficiency.md
│   ├── 6-systematics.md
│   ├── 7-results.md
│   ├── 8-display.md
│   ├── 9-polarization.md
│   └── figures/                             # Figures in instructions
│       ├── access.png
│       ├── event_display_web.png
│       └── HX_frame.png
├── data/
│   └── plot.C                               # Plot data distributions
├── yield/
│   └── yield.C                              # Fit data and extract yields
├── acceptance/
│   └── acceptance.C                         # Calculate acceptance from generation-level MC
├── efficiency/
│   └── mc_efficiency/
│       └── mc_efficiency.C                  # Calculate efficiency from full-chain MC
├── luminosity/
│   ├── Cert_Collisions2025_391658_398903_Muon.json  # Lumi mask for data
│   └── luminosity.py                        # Calculate integrated luminosity
├── cross_section/
│   ├── cross_section.py                     # Calculate cross-section results
│   ├── plot.py                              # Plot differential cross-section
│   └── plot_comprison_13p6TeV.py            # Plot comparison of new results with the previous analysis
└── event_display/
    └── event_display.py                     # Select events for display
```


First, connect to `lxplus8` using a terminal or VS Code and clone the repository:
```bash
ssh <cern_username>@lxplus8.cern.ch # or connect with VS Code

cd YourWorkSpace
git clone git@github.com:yiyangzha/CMSDAS_Upsilon.git
```


Then follow the tutorials in the `instruction` folder:
- [Part 0 - Remarks](instruction/0-remarks.md)
- [Part 1 - Introduction](instruction/1-introduction.md)
- [Part 2 - Data](instruction/2-data.md)
- [Part 3 - Yield](instruction/3-yield.md)
- [Part 4 - Acceptance](instruction/4-acceptance.md)
- [Part 5 - Efficiency](instruction/5-efficiency.md)
- [Part 6 - Systematics](instruction/6-systematics.md)
- [Part 7 - Results](instruction/7-results.md)
- [Part 8 - Event Display (Optional)](instruction/8-display.md)
- [Part 9 - Polarization Effects on Acceptance (Optional)](instruction/9-polarization.md)
