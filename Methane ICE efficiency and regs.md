# Summary: Methane ICEs for Stationary Generators vs SCGT, with EPA Standards

---

## Key Conclusions
- **Methane (CH₄) ICEs for generators are practical and deploy rapidly**, especially using automotive-scale engines (~2.3–3.3L displacement).
- They are "**efficient enough**" for applications like data center clusters where **low cost, modularity, and scalability** are more important than maximizing thermodynamic efficiency.
- **Waste heat recovery (e.g., via turbo-expanders)** is theoretically feasible but **not economically justified** for these small engines due to:
  - Lower exhaust temperatures (300–500°F vs SCGT's 400–600°F)
  - Narrow and less stable temperature profiles
  - Complexity and cost of integrating heat recovery systems

---

## Emissions & EPA Regulations

- **Natural Gas ICE Emissions:**
  - Primary emissions: **CO₂, H₂O**, and small amounts of **NOx**, CO, and unburned hydrocarbons (UHC).
  - Methane combustion is inherently cleaner than gasoline or diesel, reducing or eliminating the need for **catalytic converters** and other "smog" controls.

- **EPA NSPS (New Source Performance Standards):**
  - For **stationary ICEs**, standards typically require:
    - **NOx:** ≤1.0 g/hp-hr for rich-burn engines (lean-burn can be lower)
    - **CO:** ≤2.0 g/hp-hr
    - **VOCs:** ≤0.7 g/hp-hr
  - For **SCGTs (Simple Cycle Gas Turbines)** under **40 CFR Part 60 Subpart KKKK**:
    - **NOx:** ~15 ppm @15% O₂ for units ≥10 MW
    - CO and other limits apply, specific to turbine size and output.

- **Key Distinction:**
  - ICEs and SCGTs fall under different NSPS subparts, reflecting operational and emissions differences.
  - ICE emissions are measured in **g/hp-hr**, SCGTs in **ppm at a standardized oxygen content (15% O₂)**.

---

## Design Considerations
- **Constant RPM and Temperature Operation:** Reduces thermal cycling, extending engine life.
- **Modular System:** Designed for 1-year continuous duty with **5-minute modular swaps** for overhaul cycles.
- **Load Adaptability:** Achieved via **fuel/air throttling** while keeping RPM constant.
- **Cooling and Power Stability:**
  - Dynamic coolant flow scaled with load
  - Electrical capacitance (with optional supercapacitors or batteries) for **peak shaving** and smoothing voltage/current delivery.

---

## Regulatory Implications for OEMs
Repurposing automotive natural gas ICEs for stationary use is **expected to comply with U.S. EPA stationary source emissions standards** without extensive hardware changes due to methane's clean burn profile.

However, OEMs must:
- Implement or modify **engine control systems** to guarantee continuous emissions compliance under stationary operating conditions.
- Conduct **certification testing** against applicable **NSPS standards for stationary ICEs** (especially for NOx, CO, VOCs).
- Account for **state-specific regulations** like those from **CARB**, which may impose tighter emissions caps or monitoring requirements.

While the regulatory path is achievable, **OEM diligence in calibration, control tuning, and documentation** is necessary to ensure compliance across operating scenarios.

---

## Summary Statement
Methane ICEs are a **practical, cost-effective, and scalable** solution for stationary generation, particularly for modular deployments like data centers. While thermodynamic efficiency is modest, the economics and simplicity of deployment outweigh the marginal gains of heat recovery systems. Regulatory compliance is achievable with proper engine management, making this approach viable within current U.S. EPA and state emissions frameworks.
