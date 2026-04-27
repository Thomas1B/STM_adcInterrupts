# STM ADC Interrupts 

Readings 2 pots and the internal die temperature using interrupts with scan conversion mode enabled.

In STM32MX, under Pinout & Configuration:

**Timers Settings**
1. Select a timer
2. Under Mode: Set the "Clock Source" as Internal Clock.
3. Under Configuration > Parameters Settings: Set Prescaller and Counter Period.
4. Under Configuration > Parameters Settings: Set Trigger Event Selection to "Update Event"


**ADC Settings**
1. Pick what ADC pins you want. 
2. Set "Number Of Conversion", this is number of ADC you are reading.
3. Set Clock Prescaler (optional, normally left as default)
4. (optional set Resolution)
5. Set "Scan Conversion Mode" to Enabled.
6. In each "Rank" set the channel and sampling time (use the excel program to determine the max number of cyles).

<hr>

## Sampling Time Equations

$𝑇_{conv}=(\text{Sampling time + 12 Cycles})⋅𝑇_{𝐴𝐷𝐶}$

$𝑓_{ADC}=\frac{PCLK}{M}, \quad$ $𝑀$ is clock Prescaler in ADC Settings (Check what PCLK your timer is on, either PCLK1 or PCLK2).

$\rightarrow 𝑇_{𝐴𝐷𝐶}=\frac{1}{𝑓_{ADC}}$

$f_{sample} = \frac{ABP\\#(MHz)}{PSC \cdot ARR}, \quad$ ARR is the AutoReload Register (Check what ABP# your timer is on, either ABP1 or ABP2).

$\rightarrow T_{sample} = \frac{1}{T_{sample}}$

<br>
Pick largest number of cycles that satisfies:

$N \cdot T_{conv} \le T_{sample}$
