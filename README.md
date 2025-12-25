# Smart-Power-Extension-Box
An automatic overload cutoff system using pure hardware logic – no microcontroller needed.
What does it do?

This project protects your appliances from electrical overloads by automatically cutting power when too much current flows through. The system stays OFF until you manually reset it, preventing any accidental restarts and keeping things safe.
How it works

The circuit uses an ACS712 current sensor to monitor the load continuously. When the current crosses your set threshold, the LM393 comparator sends a signal to a NAND gate latch (74HC00), which immediately trips the relay and cuts power to the load.

A transistor controls the relay switching, and once tripped, the system won't turn back on until you press the reset button. Simple, reliable, and fast.

Logic behind it:

text
Relay = NAND(RESET, SET)

Where SET comes from the comparator (goes LOW on overload) and RESET is your manual pushbutton.
Components you'll need

    IC LM393 – Dual Comparator

    IC 74HC00 – Quad 2-input NAND Gate

    ACS712 – 5A Current Sensor Module

    2N2222 / BC547 – NPN Transistor

    5V DC SPDT Relay (5A rating)

    10kΩ Potentiometer

    Resistors: 10kΩ (×4), 330Ω (×2)

    1N4007 Diode (flyback protection)

    LEDs – Red & Green for status indication

    Capacitors: 100µF (×2), 0.1µF (×1)

    7805 Voltage Regulator

    SPST Switch, Pushbutton (for reset)

    12V 1A DC Power Adapter

    Breadboard and jumper wires

    Load for testing: We used a 12V DC geared motor (100 RPM)

Truth Table
Condition	LM393 OUT (SET)	RESET	NAND OUT (Q)	Relay/Motor
Normal	1	1	1	ON
Overload	0	1	0	OFF
Cleared (latched)	1	1	0	OFF
Manual Reset	1	0	1	ON
Where can you use this?

    DIY overload-protected power strips

    Lab equipment protection for DC circuits

    Home/office appliance safety systems

    Anywhere you need automatic current limiting without complex programming

Why hardware logic?

Unlike microcontroller-based designs, this is purely analog and digital logic. That means faster response times, lower cost, and one less thing to program. Perfect for learning digital logic design or building a quick protective circuit.
