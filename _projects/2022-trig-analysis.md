---
layout: project
title: Cube Craze Autonomous Robot Competition
description: Design, fabrication, and competition execution of an Arduino-based autonomous cube-collecting robot
technologies: [Mechatronics, Robotics, Arduino, Embedded Systems, Mechanical Design, Prototyping]
image: /assets/images/crazycuberobot.png
---

<section class="section">
  <h2>Project Overview</h2>

  <p>
    This project was completed as part of the MAE 3780 mechatronics robot competition, known as
    <strong>Cube Craze</strong>. The objective was to design, build, and compete with an autonomous robot capable
    of collecting wooden cubes from a playing field during a timed match. Each team developed a robot within defined
    size, material, budget, and gameplay constraints, then competed against other student-built robots.
  </p>

  <p>
    Our team focused on a practical design strategy built around mechanical simplicity, predictable motion, and
    reduced competition-day risk. Rather than relying on a complex collection mechanism or a sensor-heavy control
    strategy, we emphasized a durable physical collection structure and a repeatable movement sequence.
  </p>

  <p>
    <a href="/assets/images/MAE3780-Competition-Final-Report.pdf">View Final Report</a>
  </p>
</section>

<section class="section">
  <h2>Competition Objective</h2>

  <p>
    The robot was required to begin each match within an 8-inch by 8-inch starting footprint and operate autonomously
    once the match began. The goal was to collect as many cubes as possible within the match period while remaining
    inside the playing field boundaries and complying with the competition rules.
  </p>

  <p>
    The competition environment required the robot to perform reliably under real match conditions, including battery
    variation, field-surface differences, repeated rounds, and potential sensor uncertainty caused by changing lighting.
  </p>
</section>

<section class="section">
  <h2>Design Strategy</h2>

  <p>
    Our design philosophy was to be effective at the fundamentals: move reliably, stay on the board, collect cubes
    consistently, and avoid unnecessary technical failure points. The robot used a simple outward-facing collection
    structure that guided cubes into the robot rather than relying on a powered intake or complex mechanical actuator.
  </p>

  <p>
    The final design used a C-shaped physical collection structure attached to the robot chassis. The inner surfaces
    were lined with duct tape to help retain cubes after contact. This approach allowed the robot to capture cubes
    while keeping the overall mechanical design lightweight, simple, and compliant with the competition’s dimensional
    constraints.
  </p>
</section>

<section class="section">
  <h2>My Role: Mechanical Structure Design and Iteration</h2>

  <p>
    My primary contribution was the design, fabrication, and refinement of the physical collection structures attached
    to the robot chassis. I developed the mechanical elements that allowed the robot to gather and retain cubes while
    remaining within the required starting dimensions.
  </p>

  <p>
    After initial testing, I evaluated how the structure interacted with the cubes, how well it held its shape during
    repeated runs, and whether the geometry supported reliable cube collection. Based on those trial results, I
    iterated the design to improve the robot’s collection path, simplify the attachment approach, and reduce mechanical
    complexity. I then produced the final physical design used for the competition.
  </p>

  <p>
    This role required balancing several engineering tradeoffs: structural stiffness, weight, dimensional compliance,
    ease of fabrication, cube retention, and reliability across multiple competition rounds. The final structure
    reflected a deliberate decision to prioritize a simple, repeatable, and competition-ready solution over a more
    complex mechanism with a higher risk of failure.
  </p>
</section>

<section class="section">
  <h2>Mechanical Design</h2>

  <p>
    The robot’s mechanical system centered on a lightweight C-shaped collector mounted to the chassis. The structure
    was designed to funnel cubes inward and hold them once collected. This allowed the robot to use its forward motion
    as the primary collection method, eliminating the need for powered arms, rotating intakes, or additional actuators.
  </p>

  <h3 style="font-size: 1.05rem; margin-top: 0.75rem;">Key Mechanical Features</h3>
  <ul>
    <li><strong>Chassis-mounted collection structure:</strong> provided a fixed physical interface for cube capture.</li>
    <li><strong>C-shaped collector geometry:</strong> guided cubes inward while maintaining a simple mechanical profile.</li>
    <li><strong>Duct tape retention surface:</strong> helped prevent cubes from immediately sliding out after contact.</li>
    <li><strong>Lightweight construction:</strong> reduced load on the robot while remaining easy to modify during testing.</li>
    <li><strong>Low-complexity fabrication:</strong> minimized failure points and supported rapid design iteration.</li>
  </ul>

  <p>
    An early concept involved a more snowplow-style front structure, but testing showed that a simpler C-shaped
    collector was more practical for the competition objective. The final design reduced unnecessary complexity while
    still supporting the team’s collection strategy.
  </p>
</section>

<section class="section">
  <h2>Electrical and Control Approach</h2>

  <p>
    The robot used Arduino-based motor control through an H-bridge. The team intentionally avoided over-reliance on
    additional sensors because sensor calibration and changing light conditions introduced additional execution risk.
    This decision helped keep the robot’s behavior more predictable during competition.
  </p>

  <p>
    The final operating strategy used a timed movement sequence. The robot drove forward, executed a left turn, moved
    forward again, and then stopped. This approach allowed the robot to follow a repeatable path without depending on
    complex real-time sensing.
  </p>
</section>

<section class="section">
  <h2>Software Implementation</h2>

  <p>
    The software used direct port manipulation to control motor behavior. The program executed a simple movement
    routine designed to move through the field, collect cubes, and avoid driving outside the board boundaries.
  </p>

```c
int main(void){ // setup code that only runs once
    DDRB = 0b00000111; // PB0, PB1, PB2 outputs
    DDRD = 0b10000000; // PD7 output

    while(1){ // code that loops forever
        PORTB = 0b00000110; // forward (PB1+PB2)
        PORTD = 0b00000000; // both directions forward
        _delay_ms(3000);

        PORTB = 0b00000110; // turn left
        PORTD = 0b00000000;
        PORTB |= 0b00000001; // left motor reverse
        _delay_ms(2750);

        PORTB = 0b00000110; // forward
        PORTD = 0b00000000;
        _delay_ms(2000);

        PORTB = 0b00000000; // end driving
        PORTD = 0b00000000;
        _delay_ms(100000);
    }
}
```

</section>

<section class="section">
  <h2>Competition Performance</h2>

  <p>
    During the competition, the robot collected approximately one to five cubes per match. The team won several
    rounds, tied others, and lost some depending on match conditions and mechanical performance. The robot’s strongest
    attribute was its simple and reliable movement logic, which helped it remain on the board when other robots were
    affected by sensor or lighting issues.
  </p>

  <p>
    The main limitation was the long-term durability of the cardboard collection structure. As the competition
    progressed, the arms became less rigid, which reduced collection performance in later rounds. However, the overall
    design still demonstrated that a simple and repeatable robot can remain competitive when the core mechanics and
    control logic are aligned with the gameplay objective.
  </p>
</section>

<section class="section">
  <h2>Lessons Learned</h2>

  <p>
    This project reinforced the importance of engineering tradeoff analysis in a live competition environment. A more
    complex design is not automatically a better design if it increases the likelihood of failure. Our team’s robot
    performed best when the design stayed focused on reliable execution, straightforward movement, and mechanical
    simplicity.
  </p>

  <ul>
    <li><strong>Reliability matters:</strong> a simple design that works consistently can outperform a complex design that fails under match conditions.</li>
    <li><strong>Mechanical durability is critical:</strong> materials must survive repeated testing and competition rounds.</li>
    <li><strong>Sensor dependence creates risk:</strong> lighting and calibration issues can reduce performance if not carefully controlled.</li>
    <li><strong>Rapid iteration improves outcomes:</strong> trial results should directly inform design changes before final competition.</li>
    <li><strong>Core functionality should come first:</strong> movement, collection, and field control were more important than unnecessary features.</li>
  </ul>
</section>

<section class="section">
  <h2>Future Improvements</h2>

  <p>
    A future version of the robot would retain the same basic collection concept but use a stronger and more repeatable
    mechanical structure. Replacing the cardboard collector with a lightweight 3D-printed or laser-cut mechanism would
    improve stiffness, consistency, and durability while preserving the simple collection strategy.
  </p>

  <ul>
    <li>Replace cardboard collection arms with a stronger lightweight structure.</li>
    <li>Improve chassis attachment points to reduce flex during repeated matches.</li>
    <li>Perform more structured battery testing before competition day.</li>
    <li>Calibrate turning motion through additional timed trials.</li>
    <li>Use sensors only where they provide proven reliability under competition lighting conditions.</li>
  </ul>
</section>

<section class="section">
  <h2>Final Reflection</h2>

  <p>
    The Cube Craze project provided practical experience in mechatronics, embedded control, rapid prototyping, and
    competition-based engineering. My work on the robot’s physical collection structure helped translate the team’s
    overall strategy into a functional mechanical design that could be tested, refined, and used during competition.
  </p>

  <p>
    The most important takeaway was that strong engineering execution often comes from simplifying the problem,
    validating the design through trials, and improving the final product based on observed performance. In this case,
    the team’s success came from prioritizing reliable movement and a practical collection structure over unnecessary
    mechanical complexity.
  </p>
</section>
