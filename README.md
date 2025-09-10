# FlyWeb

FlyWeb is a startup focused on revolutionizing last-mile delivery through autonomous drone technology. I are currently in the early prototype development phase.

## Project Progress

The foundation of a reliable delivery network is a robust drone capable of carrying a meaningful payload. My first major milestone was the design and construction of a large-scale, custom quadcopter (X-class UAV) with a 10-inch propeller diameter to explore the capabilities and challenges of this platform.

**First 10-inch Quadcopter Prototype:**
<p align="left">
  <img src="./images/10 inch build.jpg" width="500"/>
</p>

**Initial Flight Tests:**
<p align="left">
  <img src="./images/10 inch air.jpg" alt="Drone in flight" width="200"/>
  <img src="./images/10 inch building.jpg" alt="Drone flying near a building" width="200"/>
  <img src="./images/10 inch landing.jpg" alt="Drone landing" width="200"/>
</p>

### Custom High-Capacity Battery Development

To maximize flight time and range, I moved beyond standard LiPo batteries and engineered custom high-energy-density Li-ion packs.

**18650 6S2P Pack (5000mAh, 40A Continuous Discharge):**
<p align="left">
  <img src="./images/18650 raw no plug.jpg" alt="Raw 18650 cell assembly" height="200"/>
  <img src="./images/18650 kapton taped.jpg" alt="Taped cell assembly" height="200"/>
  <img src="./images/18650 weight.jpg" alt="Final pack weight" height="200"/>
  <img src="./images/10 inch with 18650 6s2p.jpg" alt="Drone with 18650 pack" height="200"/>
</p>

**21700 6S2P Pack (8000mAh, 80A Continuous Discharge):**
<p align="left">
  <img src="./images/21700 raw no jst.jpg" alt="Raw 21700 cell assembly" height="200"/>
  <img src="./images/21700 ready.jpg" alt="Finished 21700 pack" height="200"/>
  <img src="./images/21700 weight.jpg" alt="21700 pack weight" height="200"/>
  <img src="./images/10 inch with unfinished 21700 6s2p.jpg" alt="Drone with 21700 pack" height="200"/>
</p>

## Long-Range Endurance Test

I successfully validated the platform's range and efficiency with a **13km round-trip flight**. The mission was completed with a significant margin of remaining battery capacity, confirming the viability of that design for delivery routes.

**First-Person View (FPV) from the flight:**
<p align="left">
  <img src="./images/longrange tower dvr.png" alt="FPV view during flight" height="220"/>
  <img src="./images/longrange landing dvr.png" alt="FPV view on landing approach" height="220"/>
</p>

**Flight Path:**
<p align="left">
  <img src="./images/map.jpg" alt="GPS map of the 13km flight" height="600"/>
</p>

## Key Learnings

### 1. Critical Importance of PID Tuning
    A PID controller is a feedback loop algorithm that automatically corrects the drone's movement to keep it stable.

A well-tuned PID controller is not only essential for stable flight, but also for hardware longevity. An improperly tuned controller induces high-frequency oscillations, forcing motors to work inefficiently and overheat. I observed this firsthand when the motors became hot enough to damage their windings during a simple hover. Proper tuning allows even smaller motors to perform optimally, preventing thermal damage and maximizing efficiency without unnecessary weight increases.

### 2. Significant Amperage Headroom Requirement
While the drone cruises efficiently at 10-20A, its peak current demand can briefly exceed 100A during full-throttle maneuvers. This non-linear power requirement means a battery must be rated for these high bursts, not just for cruise performance plus some headroom. Our initial 40A-rated battery could not supply these bursts, causing severe voltage sag. This power instability directly disrupted the PID controller's operation, inducing dangerous oscillations that led to motor overheating and damage.

To avoid that problem, the maximum motor power can be software-limited, trading off top-end agility for compatibility.
(although I haven't rigorously tested this makeshift solution yet)

### 3. The Battery Trilemma: Capacity vs. Discharge vs. Longevity
    The C-Rating defines a battery's maximum safe continuous discharge current.
    It is a multiplier of the battery's capacity. For instance:
        A 3C 5000mAh battery can supply 15A
        A 20C 5000mAh battery can supply 100A

My research into Li-ion cells revealed a critical trade-off:
-   **High Discharge Rate (C-Rating):** Cells rated for 10-20C typically offer only 200-300 cycles before degrading to 60-80% of original capacity.
-   **Low Discharge Rate:** Cells rated for 2-3C can achieve 500-800 cycles while retaining 80-90% capacity.

This creates a key design challenge: optimizing for sufficient peak amperage (see Learning #2) while prioritizing long-term battery cycle life for economic viability.

**TL;DR: Key Learnings:**
Proper PID tuning can outperform hardware upgrades, using batteries with an inadequate discharge-rating risks motor damage, and higher-performance cells significantly sacrifice long-term lifespan.

## Next Steps

My next goal is to build upon these learnings by developing a **hexacopter frame** for the 10-inch drone class. This design will introduce motor redundancy and it will be using more cost effective motors. the frame also allows for more options to mount payload to for my first proof-of-concept delivery tests.

<p align="left">
  <img src="./images/10 inch hex.jpg" alt="10-inch hexacopter frame design" height="500"/>
</p>
