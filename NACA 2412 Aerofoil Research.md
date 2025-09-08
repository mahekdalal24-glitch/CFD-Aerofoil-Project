# NACA 2412 Aerofoil (NACA 2412-IL)

The **NACA 2412** aerofoil belongs to the **NACA 4-digit series**, created in the 1930s–40s to provide designers with a systematic way of defining and using aerofoil shapes.  

- **NACA 4-digit series**: Used mainly for tails of subsonic aircraft.  
- **NACA 5-digit series**: Developed to shift max camber forward for higher lift. (First digit × 0.25 gives lift coefficient).  
- **NACA 6-digit series**: Designed to maximize laminar flow region. Still used in high-speed aircraft (e.g., F-15, principal USAF air superiority fighter during the late Cold War).  

---

## Decoding NACA 2412

- **2** → Maximum camber is **2%** of chord length.  
- **4** → Maximum camber located at **40% chord** (0.4c) from leading edge.  
- **12** → Maximum thickness is **12%** of chord length.  

### Summary:
- **Camber**: 2% at 40% chord  
- **Thickness**: 12% of chord  

---

## General Characteristics

- **Shape**: Moderately cambered with a relatively thin profile.  
- **Lift**: Produces lift at zero angle of attack (due to camber).  
- **Stall behaviour**: Gentle and predictable.  
  - **Progressive Lift Loss** → Gradual decrease in lift at stall.  
  - **Good Warning Signs** → Buffeting before full stall.  
  - **Nose-Down Tendency** → Negative pitching moment helps recovery.  
  - **Predictability** → Consistent stall behaviour across conditions.  
- **Drag**: Reasonably low at moderate angles of attack (though less efficient than modern aerofoils).  
- **Pitching moment**: Negative (nose-down tendency).  

---

## Typical Performance Data  
(Approximate, varies with Reynolds number)

- **Lift curve slope (Cl/α)**: ~0.11 per degree of AoA  
- **Cl max**: ~1.5 (at Reynolds number ~9 million)  
- **Cd (drag coefficient)**: ~0.006 at moderate AoA  
- **Zero-lift AoA**: ~ –2°  
- **Moment coefficient (Cm)**: ~ –0.05 (about quarter chord)  

---

## Applications

The **NACA 2412** has been used widely in **general aviation aircraft**.  

- **Cessna 172** (wings use NACA 2412)  
- Other light aircraft & UAVs (good balance of lift, drag, stall behaviour).  

---

## Reynolds Number

Formula:  

\[
Re = \frac{\rho V c}{\mu}
\]

Where:  
- ρ = air density (kg/m³)  
- V = flow velocity (m/s)  
- c = chord length (m)  
- μ = dynamic viscosity (Pa·s)  

### Ways to Change Reynolds Number (Re) for Same Aerofoil:
- **Change Flow Velocity (V)** → Faster speed = higher Re.  
- **Change Chord Length (c)** → Larger chord = higher Re. (Model scale tests → lower Re).  
- **Change Air Density (ρ)** → Sea level (higher Re) vs. high altitude (lower Re).  
- **Change Air Viscosity (μ)** → Warmer air = higher μ = lower Re. Colder air = lower μ = higher Re.  

At **cruise**, Re is in the **millions** (turbulent flow).  
At **model scale** (e.g., chord = 0.15 m, speed = 20 m/s), Re is much lower, affecting stall/lift/drag behaviour.  

The geometry of the aerofoil **does not change** — only the flow conditions do.  

---

## Why NACA 2412?

I chose the **NACA 2412** profile because:  
- It is one of the **most widely used and documented** 4-digit aerofoils.  
- Its combination of **moderate camber** and **thickness** makes it ideal for **general aviation aircraft**.  
- Abundant **experimental & published data** exists.  
- I plan to compare my **CFD results** against the **Cl vs. AoA curves from Abbott & von Doenhoff’s _Theory of Wing Sections_**, ensuring benchmarking against trusted reference data.  

---