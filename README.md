# FlyWeb: Autonomous Drone Delivery Prototype

This project documents the ongoing development of FlyWeb, a startup aimed at revolutionizing last-mile delivery through autonomous drone technology. The current focus is on iterating a robust, long-range drone platform capable of carrying a meaningful payload.

## Project Progress

The current prototype features a hexacopter frame with lightweight 15-inch carbon fiber propellers on 5010 motors.
While the lifting performance and efficiency are not yet optimal, this upgrade was a crucial step in solving the challenge of building a frame that is both stiff and light enough, supporting a motor-post to motor-post distance of 1 meter.

**Finished 15-Inch Hexacopter Prototype:**
<p align="left">
  <img src="./media/15 inch hex finished.jpeg" height = "300"/>
</p>

### Custom High-Capacity Battery Development

With the added motors a higher capacity Li-ion battery is better suited.

**18650 6S4P Pack (16000mAh, 160A Continuous Discharge):**
<p align="left">
  <img src="./media/6s4p spotwelds top.jpeg" height="300"/>
  <img src="./media/6s4p soldered top.jpeg" height="300"/>
  <img src="./media/6s4p finished.jpeg" height="300"/>
</p>

### Frame Design Iterations

I initially planned to keep the original carbon fiber tube diameter at 16mm, increase the tube length from 25cm to 50cm, and add braces for stiffness.

**Initial Design**
<p align="left">
  <img src="./media/hex with bracers.jpeg" height="300"/>
</p>

Unfortunately, this proved to be the wrong approach. Although it greatly increased stiffness in the x and y axes, the z-axis had too much flex. This would lead to unwanted oscillations and uncontrollable flight behavior.

I then tested carbon fiber tubes with a larger diameter and noticed they required significantly more force to bendeven, even with the same 1mm wall thickness (30mm outer diameter/28mm inner diameter instead of 16mm/14mm).

This led me to remodel the entire centerpiece and motor mount to accommodate the larger 30mm diameter tubing.

**Center Piece In Fusion360**
<p align="left">
  <img src="./media/middle piece cad top image.jpeg" height="300"/>
  <img src="./media/middle piece cad bottom image.jpeg" height="300"/>
</p>

**Motor Mount In Fusion360**
<p align="left">
  <img src="./media/motor attachment cad image.jpeg" height="300"/>
  <img src="./media/motor attachment cad with sketch image.jpeg" height="300"/>
</p>

The larger diameter improved stiffness significantly. Because the arms no longer required braces, the overall weight was also reduced.

**Final Design**
<p align="left">
  <img src="./media/15 inch hex wip.jpeg" height="300"/>
</p>

### first test flight

Now that the design was complete, I performed some test flights and tuned the filters and PIDs.

**Test Flight To Get The Tune Right**
<p align="left">
  <img src="./media/flying 15 inch hex cut.gif" height="500"/>
</p>

## Long Range Test

The upgraded platform showed only marginal improvements, if any, in range and payload capability.
On the 16Ah battery without any payload, it managed to reach ~10km, draining ~50% of the battery.
Although this test is not considered highly accurate, it suggests that a range of ~20km without payload may be achievable.

**First-Person View (FPV) from the flight:**
<p align="left">
  <img src="./media/FPV feed 15 inch hex.png" height="350"/>
</p>

## Key Learnings

### 1. Tube diameter beats arms supports

I was mistakenly convinced that braces alone would stiffen a motor arm. Even though the supportive arms used more material, they did not constrain the z-axis sufficiently. While adding supports in the z-direction was theoretically possible, it would overcomplicate the design. The simpler and better approach was to increase the tubing diameter, as a cylinder with a larger diameter naturally resists forces in all directions equally.

### 2. larger props aren't always more efficient

I ordered 17-inch carbon fiber propellers for the 5010 motors, expecting massive efficiency gains over the 10-inch props on 2812 motors. When they arrived, I was pleasantly surprised that they weighed only 33g.
However, thrust stand testing revealed poor performance with thrust stalling at 1kg. My theory is the motor could not supply enough torque, the coils heated up, and due to the decase in resistance with higher temperatures, less current flowed, resulting in less output power.

Testing with 13-inch propellers revealed better overall efficiency and more thrust in theory but this did not hold up to real world tests.


**Thrust stand data from my own tests**
<p align="left">
  <img src="./media/thrust stand data 17 inch.jpeg" height="250"/>
  <img src="./media/thrust stand data 13 inch.jpeg" height="250"/>
</p>

> **Note on Data:** The key data points are max thrust and efficiency at hover weight. With an all-up weight of ~4kg, each motor needs to generate ~650g-700g to hover. A lift-to-weight ratio of 1.5-2 is recommended, so motors need at least 1200g of thrust. Efficiency at ~650-700g determines hovering efficiency.

> **Note on Throttle Data:** 1000 = 0% throttle, 2000 = 100% throttle.

### 3. Take Testing Data and Specifications with a Grain of Salt.

Despite generating only 1kg of thrust on the stand (vs. 1.33kg for the 13-inch), the drone lifted itself with the 17-inch props but not with the 13-inch props. The most probable cause is that the motors received significantly more cooling during outdoor flight, allowing more current to flow and generate more thrust. Seeing that 15-inch props drew slightly less current to hover, I decided to use them instead.

I also found the motor did not match its specifications. A "5010" motor should have a 50mm stator diameter and 10mm height, but the measured stator was 40x7mm (a 4007). Confusingly, some motors have accurate names while others do not, regardless of price or quality.

Furthermore, the manufacturer's thrust stand data suggested significantly better performance. They may have used more efficient airfoils or motors with thicker windings allowing more current and torque.

**Thrust stand data according to the manufacturer**
<p align="left">
  <img src="./media/manufacturer thrust stand test.png" width="300"/>
</p>

### TL;DR: Key Learnings

* 1. Increasing the motor arm tube’s diameter is a simpler and more effective way to add stiffness than adding supportive braces.

* 2. A larger propeller doesn’t guarantee better flight efficiency if the motor lacks the torque to spin it properly.

* 3. Motor specifications and static test data can be misleading, as real-world characteristics and manufacturing variances greatly impact actual performance.

## Next Steps

In the mean time I have ordered 6010 motors with 21 inch propellers that operate on 12s and the thrust stand data seems very promising. If those result translate to real life performance, The drone could carry up to 5kg for tens of kilometers instead of struggling to reach 20km without payload.

The goal is to modify the current frame for this motor-prop combo, upgrade the flight controller and ESCs to support 12S, and build a second 16Ah 6S battery to connect the two in series.
<p align="left">
  <img src="./media/thrust stand data 21 inch.png" width="500"/>
</p>
<p align="left">
  <img src="./media/6010 motor with 2170 prop.jpeg" width="500"/>
</p>



