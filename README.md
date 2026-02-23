# CMOS_Design_Prasad_More_C25SCM015

## 1) Github codespaces for the CMOS circuit design on cloud with GUI and VNC
stepwise guidlines to use this platform are as follows:
### Step1:
- Start the codespace: open new directory where you want to create a cloud-based Ubuntu environment for you, github will make one performing the following stpes.
- Now click on 'code' in that 'codespaces' and in that 'Create codespace on main' <br/>

<img width="449" height="485" alt="image" src="https://github.com/user-attachments/assets/4d7b109b-2e67-47a5-9c8b-bb184289d074" />

- Github will make cloud based Ubuntu environment for you with all setup in it. Now we are ready to run ngspice in this environment.

### Step2:
- Starting ngspice: Now as we are in the environment check once by typing ngspice in the terminal for me I am using vscode, type ngspice in terminal If installation is proper you will get like this  <br/>
<img width="1124" height="518" alt="image" src="https://github.com/user-attachments/assets/fc3f8137-fe3f-4ac5-9935-f300cae98848" />


### Step3:
- Check PORTS tab the codespace creates graphical deskstop environment accessible through noVNC <br/>
<img width="1108" height="177" alt="image" src="https://github.com/user-attachments/assets/7043fc77-bb74-451d-b8fb-dcba70f0bbd8" />

- You will see this tab: <br/>
<img width="573" height="351" alt="image" src="https://github.com/user-attachments/assets/57a49f39-80b3-421e-a5f1-b74c69c67126" />

### Step4:
- Check working: use some commands like cd for changing directory and ls for listing the contents in present directory, to see the correct working of the environment we created <br/>
<img width="775" height="489" alt="image" src="https://github.com/user-attachments/assets/e4f309aa-edf0-489f-8c15-dba5f461319c" /> 

- So with this we are ready with Ubantu virtual environment and we can start creating designs and visualize the outputs in ngspice application.

## 2) Day1_Lec0: Why do we need Circuit Design and SPICE Simulations:
### Circuit Design:
- CMOS circuit design is the process of creating electronic circuits using complementary pairs of pMOS and nMOS transistors to implement logic functions.<br/>
<img width="296" height="298" alt="image" src="https://github.com/user-attachments/assets/0542c00a-1842-4c68-850a-7f4ce44917ce" /> <br/>

<img width="1205" height="553" alt="image" src="https://github.com/user-attachments/assets/d4acac53-e68a-4b9a-a506-d808545f4927" />
<img width="625" height="514" alt="image" src="https://github.com/user-attachments/assets/30bee086-56ab-45ac-9e8f-10341397e818" /> <br/>

- CMOS inverter Voltage Transfer Characteristic (Vout vs Vin) showing switching behavior and transistor operating regions (cutoff, linear, saturation).

- NMOS & PMOS Id–V characteristics, showing their intersection to determine Vout for different Vin.

- Together, they explain CMOS inverter switching operation and output voltage determination.

## Why do we need SPICE?
- SPICE is used to simulate and analyze electronic circuits before fabrication to verify functionality and performance.

- It helps predict voltage, current, timing, and power behavior, reducing design errors and manufacturing cost. <br/>
<img width="1793" height="1055" alt="image" src="https://github.com/user-attachments/assets/d0d3bcee-3da8-46de-9c0d-51227ca8e36e" />


- It shows how we design a clock tree (CTS) so the clock reaches all flip-flops at the same time with minimum power.

- Buffers are arranged in two balanced levels, each driving equal load to control delay and reduce clock skew.

- The delay tables explain how input slew and load capacitance affect buffer delay, helping choose the right buffer size for timing and power.

  ### i) Did you know where does the delay of a cell actually comes from?
- Ans: The delay of a CMOS cell mainly comes from the time required to charge and discharge the load     capacitance at its output through the transistor resistance.
  ### ii) We have learnt about delay models, but are the models accurate?
- Ans: They are reasonably accurate for design and timing closure, but final accuracy comes from SPICE-level simulations and detailed extraction after layout (parasitics included)
  ### iii) How do you verify if what you arre doing in static timing analysis, is correct?
- Ans: We verify STA by correlating its timing results with SPICE simulations on critical paths to check delay and slew accuracy.

## Day1_Lec1: Introduction to basic element in Circuit design - NMOS

NMOS Structure: 
- Built on a p-type substrate (body/bulk).
- NMOS is a 4-terminal device: Gate (G), Drain (D), Source (S), and Body (B).
- Two heavily doped n⁺ regions form the source and drain.
- A gate electrode is placed over a thin SiO₂ oxide layer above the channel region.
- When Vgs > Vth, an n-type inversion channel forms between source and drain, allowing current flow. <br/>

<img width="391" height="355" alt="image" src="https://github.com/user-attachments/assets/722b89d9-695c-4297-be2e-4ec5ac6e93b6" />

### Threshold Voltage:<br/>

<img width="591" height="307" alt="image" src="https://github.com/user-attachments/assets/472620d4-1a3f-430d-a531-198c7acd9ab2" />

- It shows the condition at VGS = 0, where no inversion channel exists (device OFF).

- As positive VGS increases, electrons accumulate at the surface of the p-substrate.

- Threshold voltage (Vth) is the exact gate voltage at which a strong inversion layer forms, creating a conducting channel between source and drain.

## Day1_Lec2 : Strong Inversion and Threshold Voltage

### Strong Inversion:
- When Vgs exceeds the threshold voltage Vt, enough electrons are attached to the surface of the p substrate.
- The surface electron concentration becomes higher than the hole concentration, effectively turning the surface into n-type (inversion layer).

- A continuous conductive channel forms between source and drain, allowing current to flow.
- The Vgs voltage at which strong inversion occurs is called threshold voltage Vt. <br/>

<img width="578" height="309" alt="image" src="https://github.com/user-attachments/assets/d07e3fa0-b9ab-440f-80ea-f934cc88ddd7" /> <br/>

- There will be no change in depletion layer width but there will be increase in channel width.
- Electrons from heavily doped n+ source region are drawn in region under gate 'G'.
- So now due to continuous n-channel formation from S-D, whose conductivity is modulated by 'Vgs'. <br/>

### Body Terminal:
<img width="843" height="345" alt="image" src="https://github.com/user-attachments/assets/43bed69e-a448-4709-a232-eabb9bc02eb8" /> <br/>

- When Vsb>0 (NMOS), the source–body junction becomes more reverse biased.
- The depletion region widens, increasing depletion charge under the gate.
- THe Threshold voltage Vt increases (Body Effect).
- A higher Vgs is required to achieve strong inversion.
- Hence, channel formation is delayed and the NMOS becomes harder to turn ON.
  
## Day1_Lec3 : Threshold voltage with positive substrate potential

<img width="1894" height="949" alt="image" src="https://github.com/user-attachments/assets/8cd30beb-b5af-4e01-bb6d-230e18f09c6c" /> <br/>

* When **Vsb = 0**, strong inversion occurs at **Vgs = Vt0**, and the channel forms normally.
* When **Vsb > 0**, the source–bulk junction becomes more reverse biased, increasing the depletion width near the source.
* As a result, the threshold voltage increases (Vt = Vt0 + ΔV), so a higher **Vgs** is required to achieve strong inversion — this is called the body effect.
- When Vsb = 0, strong inversion occurs at Vgs = Vto (threshold voltage without body bias).
- When Vsb > 0 (positive source-to-bulk voltage), the source–body junction becomes more reverse biased, increasing the depletion region width near the source.
- Due to this body effect, a higher Vgs (Vgs = Vto + ΔV) is required to achieve strong inversion — meaning the threshold voltage increases with Vsb.

<img width="898" height="457" alt="image" src="https://github.com/user-attachments/assets/f0e1e6af-8e8d-4362-a5e8-7c8748709732" />

- The threshold voltage with body bias is given by Vt = Vto + γ(√(2ϕF + Vsb) − √(2ϕF)), which shows that Vt increases when Vsb increases due to the body effect.
- When Vsb > 0, the source–body PN junction becomes more reverse biased, increasing the depletion region width near the source.
- The increased depletion width results in more depletion charge, so a higher gate voltage is required to achieve strong inversion.
- The body-effect coefficient γ = √(2qεsiNA) / Cox indicates that higher substrate doping or lower oxide capacitance increases the sensitivity of Vt to Vsb.
- Therefore, inversion occurs at Vgs = Vto + ΔV instead of Vto, and the increase in threshold voltage follows a square-root dependence on Vsb.

## NMOS resistive region and saturation region of operation
## Day1_Lec4 : Resistive region of operation with small drain-source voltage
- Earlier, we studied the cut-off region where no channel is formed. Now, by applying a small drain-to-source voltage (Vds) and setting Vgs greater than Vt, the MOSFET operates in the resistive (linear) region. In this condition, a continuous inversion channel is formed between source and drain, allowing current to flow. As the gate-to-source voltage (Vgs) is increased further, the inversion charge increases and the channel becomes stronger (effectively wider), reducing channel resistance.
  
<img width="899" height="358" alt="image" src="https://github.com/user-attachments/assets/b5b3899a-6b98-4f87-abe5-c92455f3af85" />

- The net induced inversion charge in the channel is proportional to (Vgs − Vt). Initially, a very small drain-to-source voltage (Vds) is applied so that the device operates in the linear (resistive) region. Let the threshold voltage be Vt = 0.45 V, and assume Vgs is only slightly greater than Vt at the beginning. Under these conditions, a thin but continuous inversion channel forms, allowing a small drain current to flow due to the applied Vds.

<img width="901" height="374" alt="image" src="https://github.com/user-attachments/assets/2558c4e7-2235-4a32-90cb-4ba0e304ba61" />

- Since the source is grounded and the drain is at a positive potential, a voltage gradient is established along the channel from source to drain. This causes the channel potential V(x) to gradually increase from 0 at the source to Vds at the drain, slightly reducing the inversion charge toward the drain end. As a result, the effective channel length becomes slightly shorter than the original physical channel length due to the lateral electric field influence.

<img width="559" height="404" alt="image" src="https://github.com/user-attachments/assets/fe6d2d6c-4d87-4a35-851c-01bba94e4e53" />

- In this representation, the y-axis corresponds to the transistor width, while the x-axis represents the position along the channel from source to drain. When Vds is applied, the channel voltage varies along the x-direction, so each point experiences a different local potential V(x). Therefore, the effective gate-to-channel voltage at any point becomes Vgs − V(x), and this variation along the channel determines the drain current equation.

<img width="556" height="403" alt="image" src="https://github.com/user-attachments/assets/36157ff2-d2b1-47fb-b498-d8814dad2de9" />

## Day1_Lec5 : Drift current theory
- We know that the effective gate-to-channel voltage varies along the channel with respect to x. For example, at x = 0 (source end), V(x) = 0, so Vgs − V(x) = 1 V. At the drain end, where V(x) = Vds = 0.05 V, the effective voltage becomes Vgs − V(x) = 0.95 V. Since the induced inversion charge is proportional to the effective gate-to-channel voltage, it gradually decreases from the source toward the drain.

<img width="328" height="115" alt="image" src="https://github.com/user-attachments/assets/c9e28253-a6a6-4404-83e0-87fc1aba80f4" />

<img width="343" height="298" alt="image" src="https://github.com/user-attachments/assets/f1c53af1-935f-4309-937f-8b59851b3460" />

<img width="889" height="437" alt="image" src="https://github.com/user-attachments/assets/6b6b2986-5252-4775-9fe3-67e47fe6a95d" />

- There are two types of current in a MOSFET: drift current and diffusion current. In this case, since there is a potential difference across the channel due to Vds, the dominant component is drift current. To derive the drain current expression, we consider the top view of the transistor and analyze the channel along its length.

<img width="881" height="490" alt="image" src="https://github.com/user-attachments/assets/7d29e8c5-dc17-4d3f-b00d-eda9dc65ad07" />

## Day1_Lec6 : Drain current model for linear region of operation

- Since the voltage varies along the channel length, the electric field also changes from source to drain. This variation in electric field causes the carrier velocity to change along the channel, as velocity is proportional to mobility and the local electric field.

<img width="328" height="485" alt="image" src="https://github.com/user-attachments/assets/d2cb0b49-0750-497b-a78c-cd01bf28b22a" />

<img width="329" height="241" alt="image" src="https://github.com/user-attachments/assets/045c6695-da7b-4798-b596-9eb0e698e3d9" />

- We integrate the equation along the channel, taking the limits of dV from 0 to Vds and the limits of dx from 0 to L.
- Here, Cox, W/L, Vgs, μn, and Vt are technology parameters of the device. We can simulate the circuit using SPICE to obtain the I–V characteristics. However, from the drain current expression, we observe that Id is a quadratic function of Vds, so we cannot simply conclude that the device behaves purely linearly. Using the given parameter values, we can substitute them into the equation to calculate the drain current Id.

<img width="317" height="216" alt="image" src="https://github.com/user-attachments/assets/a0b22ab1-ab89-44cf-9f49-0dea5cad5ba9" />

<img width="895" height="499" alt="image" src="https://github.com/user-attachments/assets/c4a9ca62-3861-45c3-b91f-8b7f63ae1eac" />

- When (Vgs − Vt) ≥ Vds, the MOSFET operates in the linear (ohmic/triode) region.

<img width="883" height="505" alt="image" src="https://github.com/user-attachments/assets/14a7d909-7f4a-4230-a1ae-450023c74953" />

## Day1_Lec7 : SPICE conclusion to resistive operation:

<img width="897" height="506" alt="image" src="https://github.com/user-attachments/assets/3496a35a-2bfa-4b52-8fad-4016a3867746" />

- We need to analyze how Vgs and Vds affect the drain current equation by considering different values of both parameters. If we vary Vgs, the device will remain in the linear region only when (Vgs − Vt) is greater than Vds. The key question is how to calculate Id for different values of Vgs, and for each selected Vgs, sweep Vds up to (Vgs − Vt) using the linear region current equation. To accurately study this behavior and obtain the I–V characteristics, we perform SPICE simulations.

## Day1_Lec8 : Pinch-off region condition
- There is another region of operation called the saturation region, which occurs when the drain-to-source voltage exceeds (Vgs − Vt). As Vds increases, the channel voltage near the drain reduces since the local effective voltage becomes (Vgs − V(x)). When Vds reaches (Vgs − Vt), pinch-off begins at the drain end, and the device enters the saturation region.

<img width="873" height="456" alt="image" src="https://github.com/user-attachments/assets/c7b76467-853f-45b6-90cf-f22da7cde225" />

<img width="505" height="384" alt="image" src="https://github.com/user-attachments/assets/806ad9cb-b7a2-4064-be57-228976fcba56" />

<img width="329" height="369" alt="image" src="https://github.com/user-attachments/assets/bd699cd1-d9d4-4b38-85be-e17a3d846818" />

- When the channel near the drain end starts to shrink and eventually disappears due to a high Vds, this condition is termed the pinch-off region. This occurs when Vds reaches (Vgs − Vt), causing the inversion charge at the drain end to become zero and the device to enter saturation.

<img width="512" height="425" alt="image" src="https://github.com/user-attachments/assets/b5ed8800-1b64-407a-90d5-4141a847ebf5" />

- When (Vgs − Vds) < Vt, the effective gate-to-channel voltage at the drain end becomes less than the threshold voltage, so no inversion channel is present near the drain. As a result, the channel is pinched off at the drain side.
- This condition is termed the saturation region, where the MOSFET becomes saturated because the channel is pinched off at the drain end. Beyond this point, increasing Vds does not significantly increase the drain current, as it is mainly controlled by Vgs.

<img width="866" height="441" alt="image" src="https://github.com/user-attachments/assets/0b8fbac1-2351-4e25-9dbb-6bfa69ffa83c" />

- Pinch off region --> no channel near drain region
- Pinch off cndition --> Vgs-Vds <= Vt

## Day1_Lec9 : Drain current model for saturation region of operation
- In the saturation region, the channel voltage at the pinch-off point remains fixed at (Vgs − Vt), and the drain current ideally becomes independent of Vds. To derive the drain current equation in saturation, we substitute Vds = (Vgs − Vt) into the linear region current expression.

 <img width="891" height="446" alt="image" src="https://github.com/user-attachments/assets/0aaa2c20-d6ff-47eb-9868-f04783c69cb4" />

 <img width="851" height="437" alt="image" src="https://github.com/user-attachments/assets/999b028e-aa3e-41ad-9fb3-65e2ab791249" />

 <img width="629" height="123" alt="image" src="https://github.com/user-attachments/assets/c59560f6-2cf0-4789-92ae-6e0869c70752" />

 
 - From the ideal saturation current equation, the MOSFET appears to behave like a perfect current source, with Id independent of Vds. However, in practice, as Vds increases further, the depletion region at the drain widens, effectively reducing the channel length. Because of this channel length reduction, Id slightly increases with Vds even in saturation. This effect is known as channel length modulation.

 ## Introduction to SPICE
 ## Day1_Lec10 : Basic SPICE setup
 
<img width="869" height="449" alt="image" src="https://github.com/user-attachments/assets/3ee06dcc-7ad8-4f37-99f9-d93c912cff13" />

Some parameters are constants that are directly provided by the foundry in the technology model files, so we do not need to derive them manually. These fixed technology parameters are the ones highlighted in yellow.

<img width="866" height="448" alt="image" src="https://github.com/user-attachments/assets/2849e2eb-9ef1-4253-ae1c-b6aafc15228c" />

<img width="867" height="463" alt="image" src="https://github.com/user-attachments/assets/32cffd00-8a97-45f6-87ac-fa8f5f0cc75a" />

- When we provide the SPICE model parameters along with the SPICE netlist to the simulator, it generates the device characteristics such as Id vs Vds for different values of Vgs.

- In the SPICE netlist, the MOSFET must be defined in a specific format so that the SPICE engine can interpret it correctly. The circuit equivalent of the given MOSFET is represented as shown below.

<img width="833" height="418" alt="image" src="https://github.com/user-attachments/assets/ac65b036-c43c-4694-b868-1c972a0ab9e5" />

 ## Day1_Lec11 : Circuit description in SPICE syntax
- Steps to write SPICE netlist syntax for particular circuit:
- Nodes:

<img width="408" height="303" alt="image" src="https://github.com/user-attachments/assets/cdd35bf9-fea9-4d43-a331-f42457237ab3" />

- Give names to node
- Write netlist code for specific device i.e. mosfet or resistor
- mosfet --> 4 terminals, resistor --> 2 terminals
- mosfet:
<img width="821" height="254" alt="image" src="https://github.com/user-attachments/assets/c08c488e-035b-4c70-8105-914ceafd145b" />
-drain:
<img width="809" height="254" alt="image" src="https://github.com/user-attachments/assets/35c3a789-11e6-45c3-92e8-9e623ce1c01a" />
-gate:
<img width="818" height="250" alt="image" src="https://github.com/user-attachments/assets/4a986fcb-40f9-452d-91bf-bab52d74fbc7" />
-source:  
<img width="808" height="250" alt="image" src="https://github.com/user-attachments/assets/3b665984-3e2a-49f7-b5d8-bf76aaea467e" />
-substrate:
<img width="815" height="251" alt="image" src="https://github.com/user-attachments/assets/87442ef6-2371-4905-b8ce-22b5fd69d9f9" />
- name of mosfet:
<img width="818" height="258" alt="image" src="https://github.com/user-attachments/assets/164eea59-b51e-4fe6-a5c9-4b19d96464e8" />
- width:
<img width="815" height="250" alt="image" src="https://github.com/user-attachments/assets/b887cade-24a9-41af-ab78-1e96ce22af68" />
-length:
<img width="817" height="251" alt="image" src="https://github.com/user-attachments/assets/3433ce9a-0282-4a79-a386-03fb2c88c238" />

- So this was long channel mosfet.

-netlist code for Resistor:
- naming resistor:
<img width="824" height="240" alt="image" src="https://github.com/user-attachments/assets/c891480a-8f41-47c7-bc2c-b181ab5e2c11" />
- Vdd :
<img width="827" height="255" alt="image" src="https://github.com/user-attachments/assets/6e5650cb-bc8a-482a-bc94-1356b53dce98" />
- Vin:
<img width="816" height="246" alt="image" src="https://github.com/user-attachments/assets/f3c3cf86-da1b-4a6d-b9c6-df914718ac18" />

Total netlist code for the 2 components is:
<img width="399" height="139" alt="image" src="https://github.com/user-attachments/assets/f4de55e6-63bf-4ebf-b69d-3e63f1ad1f9d" />

 ## Day1_Lec12 : Define technology parameters
 - Now, we need to identify the model for this specific NMOS device. The required model parameters are provided by the foundry in the technology file, which simplifies accurate device modeling. The NMOS model can be found in the technology library under its corresponding model name, and this file is included in the SPICE netlist using the .include statement so the simulator can access all process parameters.

<img width="427" height="410" alt="image" src="https://github.com/user-attachments/assets/1f863f79-6acc-44a5-9c1f-e884b3ce0244" />

- Inside the model definition brackets, all the technology parameters are specified, and a similar structure exists for the PMOS model as well. We then place this packaged model file in a .mod file and reference it in the top-level SPICE netlist so the simulator can use the defined device models.

 <img width="884" height="492" alt="image" src="https://github.com/user-attachments/assets/183c3ed2-bb79-48e5-ab6a-5a7cc798025d" />

- call this file into netlist code:
<img width="455" height="176" alt="image" src="https://github.com/user-attachments/assets/b3add566-1062-40da-b00c-92e62d3b6afe" />

- complete netlist code:

<img width="514" height="465" alt="image" src="https://github.com/user-attachments/assets/c4c0ea97-9444-44ce-91e3-a82ca42ae5a5" />

- Now, we need to perform a sweep of Vgs and Vds in the SPICE simulation to analyze the device characteristics.

 ## Day1_Lec13 : First SPICE simulation:
- open cloud lab using vs code.
- type:
  cd /workspaces/vsd-cmos
  ls -ltr
  cd /workspaces/vsd-cmos/sky130CircuitDesignWorkshop/design
  ngspice day1_nfet_idvds_L2_W5.spice

- Inside the sky130_fd_pr directory, we can find subfolders such as cells, models, and tech files. Within the cells folder, nfet and pfet device cells are available, which we will use for simulation.

- Inside the nfet directory, SPICE libraries for different process corners are provided. We typically select one corner file (for example, the typical corner) that contains all the required model parameters for that process.

- The library also specifies predefined W and L values. For simulation purposes, we choose any valid W and L combination available in the library.

- Next, we navigate to models → lib.spice, where the corner library files for nfet and pfet are defined, including typical, slow-fast (SF), and fast-fast (FF) corners.

- In the design folder (for example, day1 file), the voltage sources are defined such that Vdd is swept from 0 to 1.8 V with a step of 0.1 V, and Vgs is swept from 0 to 1.8 V with a step of 0.2 V.

- After running the SPICE simulation, we obtain the Id vs Vds characteristics for different values of Vgs. To check the exact value of Id at a particular Vds and Vgs point, we can simply left-click on the waveform plot.
  
 <img width="1027" height="680" alt="image" src="https://github.com/user-attachments/assets/05a57b9d-27e0-49ca-b046-1f443100b3df" />

 <img width="1029" height="681" alt="image" src="https://github.com/user-attachments/assets/608326e3-3299-4789-a7ef-792bc8ac3209" />

 <img width="876" height="674" alt="image" src="https://github.com/user-attachments/assets/c446d0aa-f8b4-4445-8255-5eca865dce9b" />





