---
layout: project
title: Linear Actuator Mechanism Optimization
description: Mechanics Optimization
technologies: [Python and 2D Modeling]
image: /assets/images/LinearActuatorProblemSketch.jpg

---

For a problem in out Statics and Mechanics of Solids class, we were given a design assignment in which we are given a 2D design space that’s 150 cm long and 50 cm tall. Within this space, we were asked to design a mechanism with a linear actuator that can lift the maximum possible weight to the maximmum possible height. The thing that we were allowed to use were:
    - A rigid bar of fixed length (we get to choose how long it is)
    - Three pin supports, where two must be mounted on the ground
    - A linear actuator chosen from this online catalog: https://www.tolomatic.com/wp-content/uploads/2022/05/2700-4000_29_IMA_cat.pdf

All supports, the actuator, and the bar are assumed to be rigid. The challenge in this was to arrange these elements into a frame or mechanism that acheives the goal specificed above. 

To start off, I made a sketch that defined the variables, an image of it follows:
![Sketch of Problem]({{ "/assets/images/LinearActuatorProblemSketch.jpg" | relative_url }}){: .inline-image-l}

Then, to determine the correct linear actuator, I tried to find one that would fit the height range. The resulted in the IMA actuator as it was the only one that could fit. From there I found that the force of this linear actuator was 36kN which was used in the calculations. An image of these calculations used for the python script is below:
![Calculations Image]({{ "/assets/images/LinearActuatorCalculationsSketch.jpg" | relative_url }}){: .inline-image-l}

Then I designed a python script that would run through 10 million combinations of the variables to maximize the result. The python script is as follows: 
```python
    import random
    import math
    Fa = 36
    wmax = 0
    iterations = 1000000
    bestp = 0
    bestL = 0
    bestx = 0
    for i in range(iterations):
        p = random. uniform(0, (math.pi) / 2 - 1e-12)
        Ly = 50 * math.sin (p)
        Lx = 150 * math. cos (p)
        L = math.sqrt(Lx ** 2 + Ly ** 2)
        X = L * random. random ()

        w = (Fa * math.sin(math.pi - p) * (L - x) * math.cos (p) - Fa * math.cos(math.pi - p) * (math.sin (math.pi - p) * 30)) / (L * math.cos (p) )

        if w > wmax:
            wmax = W
            bestp = p * (180 / math.pi)
            bestl = L
            bestx = X
    print(f"The optimal weight is {wmax:.2f}, angle (degrees) is {bestp:.2f}, L value is {bestL:.2f}, x value is {bestx:.2f}")
```

The result from the above I got was an optimal weight of 57.60 kg, optimal angle (degrees) of 89.80, and optimal L value of 50.00 cm. This then resulted in a final sketch below, in which I believe the max height was prioritized over the max weight. However, in designing there are many tradeoffs to be made and in this situation, the max height will always be reached in comparison to the max weight.
![Final Sketch]({{ "/assets/images/LinearActuatorFinalSketch.jpg" | relative_url }}){: .inline-image-l}
