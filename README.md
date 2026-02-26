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
  
<img width="821" height="254" alt="image" src="https://github.com/user-attachments/assets/c08c488e-035b-4c70-8105-914ceafd145b" />br/>

-drain:

<img width="809" height="254" alt="image" src="https://github.com/user-attachments/assets/35c3a789-11e6-45c3-92e8-9e623ce1c01a" /><br/>

-gate:

<img width="818" height="250" alt="image" src="https://github.com/user-attachments/assets/4a986fcb-40f9-452d-91bf-bab52d74fbc7" /><br/>

-source:  

<img width="808" height="250" alt="image" src="https://github.com/user-attachments/assets/3b665984-3e2a-49f7-b5d8-bf76aaea467e" /><br/>

-substrate:

<img width="815" height="251" alt="image" src="https://github.com/user-attachments/assets/87442ef6-2371-4905-b8ce-22b5fd69d9f9" /><br/>

- name of mosfet:
  
<img width="818" height="258" alt="image" src="https://github.com/user-attachments/assets/164eea59-b51e-4fe6-a5c9-4b19d96464e8" /><br/>

- width:
  
<img width="815" height="250" alt="image" src="https://github.com/user-attachments/assets/b887cade-24a9-41af-ab78-1e96ce22af68" /><br/>

-length:

<img width="817" height="251" alt="image" src="https://github.com/user-attachments/assets/3433ce9a-0282-4a79-a386-03fb2c88c238" /><br/>

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

 ## Day1_Lec14 : SPICE lab with Sky130 models:
 - If we navigate to the models folder, we will find the all.spice file. When we open this file, it specifies the scaling information for device width and length. From this, we can observe that the W and L values are defined in microns.
   
all.spice file:

<img width="1596" height="930" alt="image" src="https://github.com/user-attachments/assets/7c37814f-1804-49d6-b17e-ad75a05f671e" /><br/>

sky130 file:

<img width="1588" height="937" alt="image" src="https://github.com/user-attachments/assets/d1306f0c-5c58-4862-a40f-0f3e0bc6a1ab" /><br/>

Note: From now on, I will be using a Virtual Machine for the simulations, as it is more convenient and easier to work with.

## Day2: Velocity saturation and basics of CMOS inverter VTC
## SPICE simulation for lower nodes and velocity saturation effect
## Day2_lec15 : SPICE simulation for lower nodes:

<img width="798" height="497" alt="image" src="https://github.com/user-attachments/assets/542b336c-8333-49f4-9935-8f0a95d4c9b7" />

- The Id vs Vds plots for multiple Vgs values show three distinct regions of operation. For Vds < (Vgs − Vt), the device operates in the linear region where current rises almost linearly with Vds. When Vds exceeds (Vgs − Vt), the MOSFET enters saturation, where the current ideally becomes constant but exhibits a slight upward slope due to channel length modulation and velocity saturation effects. The bottom portion of the graph represents the cutoff region, where no channel is formed. This behavior corresponds to a long-channel MOSFET.

- Next, we vary W and L while maintaining the same W/L ratio as before. From the ideal current equation, Id should remain the same because it depends on the ratio W/L. However, practically, especially in scaled devices, short-channel and second-order effects cause the current to deviate from the ideal expectation. The SPICE deck shown below reflects this case, where only W and L are changed and all other parameters remain unchanged.

## Day2_lec16 : Drain current vs gate voltage for long and short channel device
- Observation 1: 

<img width="910" height="510" alt="image" src="https://github.com/user-attachments/assets/31e70cfa-0b3f-4043-8319-10ddd2cd55cf" />

- If we examine the Id values at Vds = 2.5 V for different Vgs values, we observe a quadratic dependence of Id on Vgs in a long-channel device, as predicted by the square-law model. However, in a short-channel device, at the same Vds = 2.5 V, the drain current increases almost linearly with Vgs due to velocity saturation dominating the behavior.

<img width="556" height="443" alt="image" src="https://github.com/user-attachments/assets/ea6ba614-e2a9-4196-9219-696b2aac61e0" />

- Next, we plot Id versus Vgs by either sweeping Vds or by keeping Vds fixed at 2.5 V. In the SPICE syntax, the quantity written on the left-hand side is swept for every value specified on the right-hand side. For instance, for each value of Vdd, Vin is swept accordingly. The resulting plot shows a quadratic trend when Vds = 2.5 V for a long-channel device. Now, we repeat the same analysis for a short-channel device with L = 0.25 µm to observe the deviation from ideal quadratic behavior.

<img width="912" height="515" alt="image" src="https://github.com/user-attachments/assets/9fbdc130-96fd-45b7-b040-4b3e1fcfe5c8" />

## Day2_lec17 : Velocity saturation at lower and higher electric fields

- For a short-channel device, the Id–Vgs characteristic shows a more linear trend as Vgs increases, mainly due to the velocity saturation effect.
- Thus, in lower technology nodes, the MOSFET exhibits four regions of operation: Cutoff, Linear, Saturation, and Velocity Saturation.
  
<img width="899" height="490" alt="image" src="https://github.com/user-attachments/assets/7bb4ce10-8e38-4d8e-a45c-70347c9ac485" />

- In velocity saturation, carrier velocity is related to the electric field by v = μE, where v is velocity, μ is mobility, and E is the electric field. Initially, velocity increases linearly with the electric field, but beyond a critical field, it saturates due to increased carrier scattering and reduced effective mobility. This effect becomes dominant in short-channel devices where high electric fields are present near the drain.

<img width="896" height="500" alt="image" src="https://github.com/user-attachments/assets/f4c879c1-161e-4d27-9b7c-762677d4e1a7" />

- Velocity saturation occurs at higher gate-to-source voltages, where the electric field in the channel becomes strong enough to drive carrier velocity to its saturation limit.

<img width="853" height="412" alt="image" src="https://github.com/user-attachments/assets/a62f0a6d-4553-4a5d-b28e-d64dbc89fac4" />

## Day2_lec18 : Velocity saturation drain current model

- Since we are dealing with higher values of Vgs, we denote the overdrive voltage as Vgt = Vgs − Vt. The previously discussed drain current equation will be applied, and for small Vds values, the channel length modulation effect (λ) can be ignored for simplicity.

- Another key technology parameter is Vdsat, which indicates the drain-to-source voltage at which the device begins to enter the velocity saturation region.

<img width="867" height="453" alt="image" src="https://github.com/user-attachments/assets/c1b82173-5dda-4f70-a937-6104b8c94137" />

<img width="897" height="464" alt="image" src="https://github.com/user-attachments/assets/df473c90-561a-4ea1-9422-08604c9832d4" />

<img width="887" height="488" alt="image" src="https://github.com/user-attachments/assets/fed606c2-7246-4bd0-9f73-f09c9484bbfa" />

<img width="887" height="502" alt="image" src="https://github.com/user-attachments/assets/0cbe9c34-f686-42b8-8ed8-8965fa2d8b2e" />

- From the equation, it appears that if W is kept constant and L is reduced, the drain current Id should increase because Id is inversely proportional to L. However, in practical short-channel devices, this expected increase is not fully observed.

- Observation 2 – For lower technology nodes, the saturation current is actually smaller instead of larger. This happens because velocity saturation causes the device to enter saturation at a lower Vds, limiting the carrier velocity and hence restricting the maximum achievable current. As a result, the peak current in short-channel (lower node) devices is lower compared to long-channel (higher node) devices, despite the reduced channel length.

<img width="922" height="511" alt="image" src="https://github.com/user-attachments/assets/1cda506d-1974-4af4-94d3-f21c94e73b12" />

##  Day2_lec19 : Labs Sky130 Id-Vgs
- Now, we will perform simulations for a lower technology node using the day2 design file. In this setup, the device dimensions are defined as L = 0.15 µm and W = 0.39 µm.

- The resulting plot shows Id versus Vds for different values of Vgs. For smaller Vgs values, the characteristics follow a quadratic trend, while for higher Vgs values, the behavior becomes more linear due to velocity saturation effects.

- To determine the peak current at Vgs = 1.8 V, simply left-click on the corresponding curve in the plot. The cursor indicates x ≈ 1.79505 V and y ≈ 0.00198232 A, which corresponds to a drain current of approximately 198 µA.

<img width="908" height="470" alt="image" src="https://github.com/user-attachments/assets/b2fc1dbf-3abf-4278-b31d-83b53e829c92" />

- Id vs Vgs:
- In this case, we again use L = 0.15 µm and W = 0.39 µm. The drain-to-source voltage Vds is kept constant at 1.8 V, while Vgs is swept from 0 to 1.8 V in steps of 0.1 V.

- From the resulting plot, it is evident that due to short-channel effects, the Id–Vgs characteristic shows a more linear trend at higher Vgs values, even though Vds is maintained constant.

<img width="968" height="479" alt="image" src="https://github.com/user-attachments/assets/bcab6693-dfea-46db-aad7-7dbc448fc176" />

## Day2_lec20 : Labs Sky130 Id-Vgs
- We determine the threshold voltage (Vt) from the Id vs Vgs characteristic curve.

- Vt is identified as the point where the drain current starts increasing sharply for a small change in Vgs.

- To calculate it, we draw a tangent to the steep portion of the curve and find its intercept on the Vgs axis.

- From the graph, the threshold voltage is approximately 0.76 V.

<img width="634" height="581" alt="image" src="https://github.com/user-attachments/assets/9d7732a1-4146-4cad-a9e0-39b9f13dafc7" />

## CMOS voltage transfer characteristics (VTC):
## Day2_lec21 : MOSFET as a switch

<img width="743" height="313" alt="image" src="https://github.com/user-attachments/assets/179bad44-e2a2-4e58-a4fd-58fb8a169a70" />

<img width="1831" height="1080" alt="image" src="https://github.com/user-attachments/assets/49a714af-b83e-4068-8d9c-9cc143989c8b" />

- A MOSFET used as a switch operates in two main states: OFF (open switch) and ON (closed switch), controlled by the gate voltage.

- When Vgs is below the threshold voltage (Vt), the device remains in cutoff and behaves like an open switch, preventing current flow.

- When Vgs is sufficiently higher than Vt, the MOSFET turns fully ON, offering very low channel resistance and acting like a closed switch.

- In digital and switching applications, the device is intentionally driven completely ON or OFF to ensure efficient current control and minimal power loss, rather than operating in the amplification region.

## Day2_lec22 : Introduction to standard MOS voltage current parameters

- We analyze the CMOS circuit for both input conditions (Vin HIGH and Vin LOW) to understand its behavior, draw the Voltage Transfer Characteristics (VTC), and use that information to estimate the cell delay.

<img width="961" height="498" alt="image" src="https://github.com/user-attachments/assets/56c5f6b3-8ec9-4ea6-a71e-5ce97e5c5127" />

- When Vin is HIGH (equal to Vdd), the PMOS turns OFF and the NMOS turns ON. In this condition, a conduction path is formed between Vout and Vss, causing the load capacitor (CL) to discharge through the NMOS.

- When Vin is LOW (equal to 0 V), the NMOS turns OFF and the PMOS turns ON. In this case, a conduction path is established between Vdd and Vout, allowing the load capacitor (CL) to charge through the PMOS.

nomenclature:

<img width="978" height="480" alt="image" src="https://github.com/user-attachments/assets/8fb8e668-aa41-4d00-bd5d-6086aac2ca59" />

## Day2_lec23 : PMOS/NMOS drain current v/s drain voltage

<img width="965" height="552" alt="image" src="https://github.com/user-attachments/assets/1529291f-9cf1-4178-b318-cd8bea2b520a" />

- Since the NMOS source is grounded, the gate-to-source voltage of NMOS is equal to the input voltage (VGSN = Vin), and the output voltage is equal to VDS.

- In the PMOS, the drain current flows in the opposite direction compared to NMOS, so with respect to the chosen NMOS reference direction, the PMOS drain current appears negative.

<img width="647" height="355" alt="image" src="https://github.com/user-attachments/assets/ddd9631f-a37d-482d-b945-a5ee6f507ad1" />

- When the gate voltage exceeds the threshold voltage, the transistor turns ON and current begins to flow. As the gate voltage increases further, the drain current also increases. The characteristic curve shows both the linear (triode) region and the saturation region of operation.

- The PMOS exhibits similar behavior, but with opposite voltage polarity. Since both the voltage and current directions are reversed, its current–voltage characteristics appear in the negative quadrant. 

## Day2_lec24 : Step1 – Convert PMOS gate-source-voltage to Vin

- Although we analyzed various internal node voltages, from a user’s perspective only the external input (Vin) and output (Vout) are observable.

- Using Vin and Vout, we plot the Voltage Transfer Characteristics (VTC), which helps us understand the switching behavior and calculate the propagation delay.

- Now, we will outline the steps to obtain the VTC of a static CMOS inverter.

- Assumption: Consider a long-channel device with Vdd = 2 V.

<img width="994" height="571" alt="image" src="https://github.com/user-attachments/assets/6c2e9925-b9d6-44ee-aa28-00556cdb3e9c" />

- Since Vgsp = Vin − Vdd, we can rewrite it as Vin = Vgsp + Vdd, allowing us to express all voltages in terms of Vin and Vout.

- The objective is to represent both NMOS and PMOS currents using Vin and Vout so that the analysis becomes consistent.

- We then plot the PMOS characteristics in terms of Idsn, where the corresponding Vin values are obtained from the converted Vgsp values.

- The graph is plotted accordingly, using the Vin values derived from the relation shown in the table.

<img width="650" height="325" alt="image" src="https://github.com/user-attachments/assets/ef552dc0-f0d0-4621-8f68-6ab438b67e52" />

## Day2_lec25 : Step2 & Step3 – Convert PMOS and NMOS drain-source-voltage to vout

- We now express Vdsp in terms of the output voltage, using the relation Vdsp = Vout − Vdd.

- Rearranging this equation allows us to rewrite the PMOS drain-to-source voltage as a function of Vout.

- To obtain Vout from Vdsp, we effectively shift the value by Vdd toward the left-hand side.

<img width="988" height="330" alt="image" src="https://github.com/user-attachments/assets/9ba363e2-ccde-4b94-9e00-31da3f88bba9" />

-When Vout = 2 V (with Vdd = 2 V), we get Vdsp = 0 V.

-In this condition, the PMOS current becomes zero, and the output capacitor is fully discharged.

-This situation is valid when the PMOS operates together with the NMOS in a CMOS inverter configuration.

- Consider another case where Vout = 0 V.

- Here, Vdsp = −2 V (since Vdsp = Vout − Vdd and Vdd = 2 V).

- At this point, for different values of Vin, a finite current flows through the PMOS.

- Since Vout = 0 V indicates that the output capacitor is completely discharged, a charging current is required to pull the output high.

- The variation of this current with respect to Vin gives the load curve of the PMOS.

<img width="383" height="307" alt="image" src="https://github.com/user-attachments/assets/17f0a15c-d09b-411e-9b2d-d838a7bab760" />

<img width="250" height="183" alt="image" src="https://github.com/user-attachments/assets/71880c19-7d98-4377-b170-0e7ac0f2ff01" />

- Next, we derive the load curve for the NMOS transistor using the given equations.

- For NMOS, the voltage relationships are straightforward:

  Vgsn = Vin

  Vdsn = Vout

- Since both voltages are directly expressed in terms of Vin and Vout, plotting the NMOS characteristics becomes simple.

- Using these relations, we can directly obtain the corresponding current–voltage graphs for the NMOS.

<img width="985" height="567" alt="image" src="https://github.com/user-attachments/assets/87aa34d2-f285-4e0e-8467-3b35458c517e" />

## Day2_lec26 :  Step4 – Merge PMOS – NMOS load curves and plot VTC

- We now combine the NMOS and PMOS load curves to obtain the Voltage Transfer Characteristics (VTC) of the CMOS inverter.

- This is done by superimposing both load curves on the same graph.

- The purpose of superimposing them is to determine the common operating point where the currents of NMOS and PMOS are equal.

- This intersection point gives the relationship between Vin and Vout, which forms the VTC of the CMOS inverter.

<img width="859" height="288" alt="image" src="https://github.com/user-attachments/assets/d1719ee1-d9cb-4f27-bb31-c9ebe256f1f3" />

- The operating range of both Vin and Vout is from 0 V to 2 V.

- When Vin = 0 V:
 Vout = 2 V
 NMOS operates in cut-off region
 PMOS operates in linear region

- When Vin = 0.5 V:
 1.5 V < Vout < 2 V
 NMOS is in saturation region
 PMOS remains in linear region

- When Vin = 1 V:
 0.5 V < Vout < 1.5 V
 Both NMOS and PMOS operate in the saturation region

- When Vin = 1.5 V:
 0 V < Vout < 0.5 V
 NMOS is in the linear region
 PMOS is in the saturation region

- When Vin = 2 V:
 Vout = 0 V
 NMOS operates in the linear region
 PMOS is in cut-off region

<img width="976" height="552" alt="image" src="https://github.com/user-attachments/assets/202c556f-5ba8-4467-95d4-eb8d54c16529" />

## CMOS Switching threshold and dynamic simulations
## Voltage transfer characteristics - SPICE simulations
## Day3_Lec27 : SPICE deck creation for CMOS inverter

- We will now perform the VTC simulation, which requires creating a SPICE deck.

- A SPICE deck is essentially the netlist, containing the connectivity details of all circuit components.

- Since substrate connections are included, the CMOS inverter circuit is defined accordingly, where:

  M1 represents the PMOS transistor
  M2 represents the NMOS transistor

- Next, we specify the component parameters, assuming identical W/L ratios for both NMOS and PMOS devices.

  <img width="513" height="455" alt="image" src="https://github.com/user-attachments/assets/c96832fc-187c-4ef4-8a54-5c77b0e25668" />

- We then define the required voltage sources, including Vin and Vdd, along with the expected Vout node.

  <img width="602" height="449" alt="image" src="https://github.com/user-attachments/assets/74fa65a8-b547-4125-bbd5-d25601f1615c" />

- The next step is to identify and label the nodes (a node is a junction where two or more components are connected).

  <img width="612" height="389" alt="image" src="https://github.com/user-attachments/assets/268abe00-7a49-44c5-a52f-239ad0ae91a9" />


- In the model file, voltage sources are defined between nodes, for example:

- The input source is connected between node Vin and ground (0).

- The supply Vdd is connected between node Vdd and ground (0).

- After defining all components, parameters, and node connections, we can proceed to write the complete SPICE netlist (SPICE deck) for simulation.

<img width="972" height="465" alt="image" src="https://github.com/user-attachments/assets/016cf4f6-7539-4665-93dc-0b8150e05aa3" />

## Day3_Lec28 : SPICE simulation for CMOS inverter

<img width="612" height="300" alt="image" src="https://github.com/user-attachments/assets/77bed8bc-33cc-438d-9c3d-ef66892f5d74" />

<img width="591" height="274" alt="image" src="https://github.com/user-attachments/assets/130de4fa-17ee-4bc9-80be-6e4abc2fab54" />

- The next step is to define the simulation commands in the SPICE deck.

- We perform a DC sweep of the input gate voltage (Vin) from 0 V to 2.5 V, with an increment of 0.05 V.

- Since our objective is to obtain the Voltage Transfer Characteristics (VTC), we sweep only the input voltage and observe the corresponding output voltage (Vout).

- Finally, we include the model files in the SPICE deck.

- These model files contain all the technology-specific parameters, such as threshold voltage, mobility, oxide thickness, and other device-related characteristics required for accurate simulation.

<img width="955" height="489" alt="image" src="https://github.com/user-attachments/assets/6850ad9f-1976-465b-9048-13452f5472ff" />

- We now perform the SPICE simulation using the following device dimensions:
 Wn = Wp = 0.375 µm
 Ln = Lp = 0.25 µm

- This gives a ratio of:
   Wn/Ln = Wp/Lp = 1.5

- With these parameters defined in the netlist, the simulation is executed.

- The resulting output is the Voltage Transfer Characteristic (VTC) curve corresponding to the specified device dimensions.

<img width="614" height="467" alt="image" src="https://github.com/user-attachments/assets/2077f057-5ff2-4598-a2a5-032aebdb2ab8" />

- Next, we perform the SPICE simulation with updated device dimensions:

  Wn = 0.375 µm
  Wp = 0.9375 µm
  Ln = Lp = 0.25 µm

- The corresponding aspect ratios are:

   Wn/Ln = 1.5
   Wp/Lp = 2.5

- Here, the PMOS width is 2.5 times the NMOS width, making the PMOS stronger compared to the previous case.

- With these parameters, we obtain a new VTC curve and can observe the shift in switching threshold due to the increased PMOS strength.

<img width="617" height="465" alt="image" src="https://github.com/user-attachments/assets/57f9f3d0-24a4-4449-9d9a-aa1d64fffa03" />

- On observing the previous VTC curve, we notice a slight leftward shift.

- This shift occurs because, in that case, the NMOS was stronger than the PMOS (equal W/L but higher electron mobility).

- Since NMOS has higher drive strength, it pulls the output down more effectively, causing the switching threshold to move toward a lower Vin value.

## Day3_Lec28 : Labs Sky130 SPICE simulation for CMOS

- We obtain the VTC characteristics of the CMOS inverter using both PFET and NFET devices.

- In this design, the W/L ratio of the PMOS is approximately 2.33 times that of the NMOS, ensuring balanced drive strength.

- A DC sweep of Vin from 0 V to 1.8 V is performed with a step size of 0.01 V, and the corresponding Vout is plotted to generate the VTC curve.

<img width="560" height="276" alt="image" src="https://github.com/user-attachments/assets/cedca045-11b1-4160-8068-4756a1fb0a43" />


- The switching threshold (Vm) is determined from the graph at the point where Vin = Vout.

- For W/L ≈ 2.3, the switching threshold is observed to be approximately 0.876 V under the typical process corner.

- Next, instead of a DC sweep, we apply a transient input pulse with the following parameters:
  
  Voltage swing: 0 V to 1 V
  Initial delay: 0
  Rise time: 0.1 ns
  Fall time: 0.1 ns
  Pulse width: 2 ns
  Time period: 4 ns

- With these pulse parameters defined, we proceed to run the transient simulation.
<img width="558" height="276" alt="image" src="https://github.com/user-attachments/assets/f235f47c-67f2-46e9-8724-96f9a2f76334" />

- So for rise delay and fall delay, we need to consider 50% of output curve i.e. at 0.9V; out-in.
   x0 = 2.483213e-09, y0 = 0.899574
   x0 = 2.17411e-09, y0 = 0.8987673
  Therefore Rise delay = 2.482ns-2.174ns = 0.308ns

   x0 = 4.33561e-09, y0 = 0.895468
   x0 = 4.04656e-09. y0 = 0.905634
  Therefore fall delay = 0.291ns

## Static behaviour evaluation-CMOS inverter robustness-Switching Threshold
## Day3_Lec30 : Switching Threshold, Vm

  <img width="915" height="440" alt="image" src="https://github.com/user-attachments/assets/14051b20-31f0-48e9-ba4a-4b4e7dbe7fb4" />

- Let us compare two CMOS inverters having different W/L ratios for PMOS and NMOS.

- In both cases, the overall shape of the VTC curve remains the same.

- The primary difference observed is a shift in the switching threshold voltage (Vm).

- This indicates that changing the device sizing mainly affects the switching point, while the inverter characteristics remain consistent.

- Hence, this demonstrates the robustness and reliability of the CMOS inverter design.

<img width="920" height="470" alt="image" src="https://github.com/user-attachments/assets/788b6aa2-09f8-4ab0-9239-4bd48d5ce037" />

- To determine the switching threshold voltage (Vm) in both cases, we draw a 45-degree line (Vin = Vout) on the VTC plot.

- The point where this line intersects the VTC curve gives the value of Vm.

- In the first case, the switching threshold is approximately 0.9 V.

- In the second case, the switching threshold shifts to around 1.2 V.

- This variation confirms that the switching threshold depends on the relative W/L ratios of the PMOS and NMOS transistors.

<img width="913" height="474" alt="image" src="https://github.com/user-attachments/assets/889d9084-4529-4d33-8f59-926cb112f165" />

- This region corresponds to the condition where both PMOS and NMOS operate in the saturation region.

- In this state, both transistors conduct simultaneously, creating a direct current path from Vdd to ground.

- As a result, significant current flows through the inverter.

- This leads to higher power dissipation, making it a critical and potentially undesirable operating region.

## Day3_Lec31 : Analytical expression of Vm as a function of (W/L)p and (W/L)n

<img width="906" height="472" alt="image" src="https://github.com/user-attachments/assets/da2653d0-7c9b-4f18-bce0-47a6f6623b3a" />

- Switching threshold (Vm) occurs when Idsn = −Idsp and Vin = Vout. Solving the current equations gives Vm = (R / (1 + R)) · Vdd, where R = (Kp · Vdsatp) / (Kn · Vdsatn) and depends on transistor (W/L) sizing.

- When Wp = Wn, Vm ≈ 0.98 V. Increasing PMOS width (Wp > Wn) increases pull-up strength and shifts Vm higher (≈ 1.2 V), improving inverter switching balance and noise margin.

## Day3_Lec32 : Analytical expression of (W/L)p and (W/L)n as a function of Vm

<img width="908" height="489" alt="image" src="https://github.com/user-attachments/assets/ac2cffba-0fb9-4b3e-9cda-212539aff423" />

- We want to determine the required W/L ratios of PMOS and NMOS such that the switching threshold Vm = Vdd/2 = 1.25 V (for Vdd = 2.5 V).

- Since Vm is given, we work in reverse by applying the current equality condition at switching point:

   Idsn = −Idsp

- At Vm, both transistors are in saturation, so we use their saturation current equations.

- Expanding the gain factors,
   Kn = (1/2) μn Cox (Wn/Ln)
   Kp = (1/2) μp Cox (Wp/Lp),
   and equating the currents allows us to find the required Wp/Wn ratio.

<img width="896" height="476" alt="image" src="https://github.com/user-attachments/assets/2395cd7b-913c-415c-91d6-59d2eb76b9e0" />

- In the derived equation, all the terms on the right-hand side are constants, whose values can be obtained from the model files, except for Vm.

- Once the desired Vm is specified, we can directly calculate the required W/L ratios.

- This helps us determine how much (Wp/Lp) should be greater than (Wn/Ln) for a given switching threshold.

- Next, we analyze the behavior of the CMOS inverter for different W/L ratios of PMOS and NMOS to observe the impact on its characteristics.

## Day3_Lec33 : Static and dynamic simulation of CMOS inverter

- For (W/L)n = (W/L)p = 1.5
  
<img width="555" height="426" alt="image" src="https://github.com/user-attachments/assets/c60ee1d7-9f39-4bf8-b036-89d10b3c6a68" />

- We can also determine the rise delay and fall delay using transient analysis, similar to the earlier procedure.

- By applying a pulse input and observing the output waveform, we measure the time taken for the output to transition.

- The rise delay corresponds to the time required for the output to transition from low to high.

- The fall delay corresponds to the time required for the output to transition from high to low.

<img width="907" height="500" alt="image" src="https://github.com/user-attachments/assets/b191a9b7-0193-41e7-8697-cfff1f86244e" />

## Day3_Lec34 : Static and dynamic simulation of CMOS inverter with increased PMOS width

- We perform SPICE simulations by increasing the width of the PMOS transistor and compare the results with the previous design.

- As the PMOS becomes stronger (due to larger width), the switching threshold (Vm) shifts to a higher value.

- A stronger PMOS provides higher charging current, which affects the inverter’s switching behavior.

- It is observed that the rise delay decreases as the PMOS width increases.

- This happens because a wider PMOS can charge the output load capacitor faster, reducing the time required for the output to transition from low to high.

- The improvement in charging speed is due to the larger effective device area and higher drive strength.

<img width="885" height="500" alt="image" src="https://github.com/user-attachments/assets/3beaba2e-2893-4cba-9f3e-6808885f2f10" />

<img width="898" height="503" alt="image" src="https://github.com/user-attachments/assets/a16ac9ad-7056-4e77-a906-cbb904935e99" />

<img width="886" height="497" alt="image" src="https://github.com/user-attachments/assets/34643654-bdb0-47c1-8a3c-5a932a180b8f" />

<img width="903" height="504" alt="image" src="https://github.com/user-attachments/assets/04fbe246-174d-45df-a71d-8f3c77f5539c" />

## Day3_Lec35 : Applications of CMOS inverter in clock network and STA

- During fabrication, small variations may occur in the dimensions of PMOS and NMOS, causing slight deviations from the intended W/L ratios.

- However, the CMOS inverter is highly robust, and these minor size variations do not significantly affect the switching threshold (Vm).

- When (W/L)p ≈ 2(W/L)n, the rise delay and fall delay become approximately equal.

- By simulation, we can fine-tune the exact sizing ratio required to achieve equal rise and fall delays.

- This condition reflects the symmetry of the CMOS inverter, which is especially important in clock inverters or buffers.

- For other logic cells, the sizing may be adjusted differently depending on the specific data path requirements.

<img width="914" height="517" alt="image" src="https://github.com/user-attachments/assets/d4afd05b-e9a6-4c98-843e-d6dcfdab572e" />

## CMOS Noise Margin robustness evaluation
## Static behaviour evaluation-CMOS inverter robustness-Noise Margin
## Day4_Lec36 : Introduction to noise margin

- We now study the robustness of the CMOS inverter with respect to Noise Margin and evaluate how well it tolerates disturbances.

- Noise Margin is defined as the maximum amount of unwanted electrical noise that can be superimposed on the input signal without causing an incorrect logic output.

- It indicates the reliability of a logic gate in distinguishing between valid logic ‘0’ and logic ‘1’.

- In an ideal inverter, an input of 0 produces an output of 1, and an input of 1 produces an output of 0.

- For such an ideal case, the transition between logic states is instantaneous, meaning the slope of the switching characteristic is infinite.

<img width="269" height="276" alt="image" src="https://github.com/user-attachments/assets/c63be136-30cc-4339-8c00-a6941a4231a0" />

- In practical circuits, the switching slope is not infinite.

- Due to the presence of parasitic resistances and capacitances, the output cannot change instantaneously.

- These parasitic elements introduce propagation delay during switching.

- As a result, the VTC transition region has a finite slope instead of an abrupt vertical transition.

<img width="587" height="403" alt="image" src="https://github.com/user-attachments/assets/2524c2ca-1fd7-4ff7-890d-dde922a699d0" />

- When the input voltage lies between 0 and VIL (Input Low Voltage), the output remains at VOH (Output High Voltage).

- In this region, the inverter correctly interprets the signal as logic ‘0’ and produces a logic ‘1’ at the output.

- When the input voltage lies between VIH (Input High Voltage) and Vdd, the output switches to VOL (Output Low Voltage).

- In this case, the inverter recognizes the input as logic ‘1’ and generates a logic ‘0’ at the output.

## Day4_Lec37 : Noise margin voltage parameters

- The CMOS inverter VTC divides the input voltage into three regions: logic 0 (0 to VIL), transition (VIL to VIH), and logic 1 (VIH to VDD).

- When the input is between 0 and VIL, the output remains at VOH (logic high).

- When the input is between VIH and VDD, the output settles at VOL (logic low).

- Due to practical non-idealities, VOH is slightly less than VDD and VOL is slightly greater than 0 V.

- For proper cascading of logic gates, the conditions VOL < VIL  & VIH < VOH must be satisfied.

- The VTC transition region has a finite negative slope (close to −1 near the switching point) because of parasitic resistances and capacitances.

<img width="634" height="390" alt="image" src="https://github.com/user-attachments/assets/85238c05-ecc6-436f-8ef0-9cceab125758" />

## Day4_Lec38 : Noise margin equation and summary

- By plotting the voltage levels on a 1D graph, we can clearly identify the Noise Margins of the CMOS inverter.

- Noise Margin High (NMH) is defined as NMH = VOH − VIH. It represents the maximum noise voltage that can be tolerated when the signal is at logic ‘1’ without causing an incorrect interpretation.

- Noise Margin Low (NML) is defined as NML = VIL − VOL. It indicates the maximum noise that can be tolerated when the signal is at logic ‘0’.

- The region between VIL and VIH is the undefined (transition) region, where the logic level is uncertain and signals may be misinterpreted.

- To ensure reliable operation, the circuit should avoid this undefined region, as noise margin reflects the tolerance of the circuit to noise, glitches, or voltage disturbances.

  <img width="573" height="391" alt="image" src="https://github.com/user-attachments/assets/877f1f89-f542-40c2-b398-b8211008067a" />

<img width="642" height="371" alt="image" src="https://github.com/user-attachments/assets/587df44d-1c99-48ce-82f5-d80cf54f589d" />

## Day4_Lec39 : Noise margin variation with respect to PMOS width

- To evaluate robustness, we analyze how noise margins vary with changes in PMOS width, keeping NMOS sizing as reference. The key points are obtained from the VTC by locating where the slope equals −1 and extending tangents to intersect the voltage axes.

<img width="900" height="502" alt="image" src="https://github.com/user-attachments/assets/3b861754-fa42-49ea-8e00-4a9c9d8d01bd" />

- The larger the noise margin, the stronger and more noise-immune the CMOS inverter becomes.

  <img width="907" height="508" alt="image" src="https://github.com/user-attachments/assets/10937472-c6ae-4637-b50f-609f2f345ccf" />

- SPICE simulations are used to study noise margins under different PMOS/NMOS W/L ratios, by examining the DC transfer curve and extracting the corresponding voltage limits.

- Increasing the PMOS width generally improves Noise Margin High (NMH); for example, NMH increases from about 0.3 V to 0.42 V when PMOS size is scaled to 5× that of NMOS.

  <img width="897" height="510" alt="image" src="https://github.com/user-attachments/assets/9341a6c2-e7f8-4e06-8a44-a3d7bc6114f8" />

-However, beyond roughly 3× W/L of NMOS, the Noise Margin Low (NML) shows a slight reduction, indicating a trade-off.

<img width="898" height="501" alt="image" src="https://github.com/user-attachments/assets/70829805-63a6-4f9a-8c91-6abae976b43d" />

-For cases such as (W/L)p = 4×(W/L)n and 5×(W/L)n, the noise margins remain nearly the same, showing that further width increase does not significantly change performance.

- This behavior confirms the robustness of the CMOS inverter, as moderate fabrication variations in sizing cause only small changes in noise margins.

<img width="536" height="216" alt="image" src="https://github.com/user-attachments/assets/ad845528-c215-42ce-b804-e2c46ab61aa6" />

- Hence, CMOS inverters are well suited for digital design, where small margin variations (±5%) do not affect functionality, while the transition region defines the boundary between digital and analog operation.

<img width="532" height="414" alt="image" src="https://github.com/user-attachments/assets/5a97982e-37d2-41a2-b671-f68bb710f79a" />

<img width="501" height="414" alt="image" src="https://github.com/user-attachments/assets/413eed76-e77a-4574-9baa-65da3b5feb5a" />

##  Day4_Lec40 :  Sky130 Noise margin labs

- Noise Margin Calculation using SPICE (Modified Example)

- W/L ratio: (W/L)p / (W/L)n ≈ 2.8

- DC Sweep: Vin from 0 V to 1.8 V with a step size of 0.01 V

- From the VTC curve, identify the points where the slope (dVout/dVin) = −1, and project them to the axes to obtain:

   X-axis → VIL and VIH
   Y-axis → VOH and VOL

  <img width="882" height="434" alt="image" src="https://github.com/user-attachments/assets/95687978-1170-4d11-95d5-e4ec6a35cd79" />

- Assume extracted values (example case):
   VOH ≈ 1.72 V
   VIH ≈ 0.99 V
   VIL ≈ 0.78 V
   VOL ≈ 0.10 V

- Noise Margin High (NMH) = VOH − VIH ≈ 0.73 V

- Noise Margin Low (NML) = VIL − VOL ≈ 0.68 V

- Since both NMH and NML are reasonably large and close in value, this confirms good noise immunity and balanced inverter performance.

## CMOS power supply and device variation robustness evaluation
## Static behavior evaluation – CMOS inverter robustness – Power supply variation
## Day5_Lec41 : Smart SPICE simulation for power supply variations

- We studied how the CMOS inverter behaves when the power supply (VDD) is gradually reduced.

- The PMOS is kept wider than the NMOS to balance mobility differences and maintain proper switching symmetry, with a load capacitance of 10 fF.

- In SPICE, VDD is swept from 2.5 V down to 0.5 V in steps of 0.5 V.

<img width="861" height="501" alt="image" src="https://github.com/user-attachments/assets/a42a166c-6b59-42aa-80b7-e63b234a2cf4" />

- As the supply voltage decreases, the overall VTC shape remains similar, and the switching behavior is preserved.

- Even at 0.5 V, the inverter continues to function, showing that the CMOS inverter is highly robust under power scaling.

<img width="698" height="524" alt="image" src="https://github.com/user-attachments/assets/fe96a410-b59f-4403-8fa9-769f01078180" />

## Day5_Lec42 : Advantages and disadvantages using low supply voltage
Advantages:
 - Higher Gain:
   
<img width="910" height="515" alt="image" src="https://github.com/user-attachments/assets/09de5d54-accb-491d-9efe-47ab5440f163" />

<img width="906" height="500" alt="image" src="https://github.com/user-attachments/assets/41924ce0-e015-4347-a9c4-fd285bdafaa7" />

  A 0.5 V supply shows nearly 50% higher gain compared to operation at 2.5 V.

  Reducing the supply voltage increases the steepness of the normalized transition region.

  This means the inverter transitions more sharply between logic levels when viewed relative to VDD.

  As a result, even at lower supply voltages, the switching characteristic remains strong and well-defined.



- Lower Energy Consumption:
  
<img width="905" height="499" alt="image" src="https://github.com/user-attachments/assets/980ff609-36f8-4e10-9c46-b3e15fee2a11" />

<img width="899" height="497" alt="image" src="https://github.com/user-attachments/assets/1aaf017b-e6b5-4be3-8b32-9195b8cfc569" />

- The switching energy is proportional to C · VDD², so reducing the supply voltage significantly lowers the energy required for charging and discharging.

- Reducing VDD from 2.5 V to 0.5 V cuts the switching energy by about 90%, making low-VDD operation ideal for low-power designs.

- Disadvantages:
    At low supply voltages, the charging and discharging of the load capacitor becomes slower due to reduced drive current.
    As a result, both rise delay and fall delay increase, leading to degraded overall circuit performance.

## Day5_Lec43 : Sky130 Supply Variation Labs

- The supply voltage is reduced from 1.8 V to 0.8 V in steps of 0.2 V, completing six iterations.

   At VDD = 0.8 V, |Gain| ≈ 9.4.
   At VDD = 1.0 V, |Gain| ≈ 8.95
   At VDD = 1.2 V, |Gain| ≈ 8.60
   At VDD = 1.4 V, |Gain| ≈ 8.25
   At VDD = 1.6 V, |Gain| ≈ 7.95
   At VDD = 1.8 V, |Gain| ≈ 7.6.

- The higher gain at lower VDD shows that supply scaling increases the magnitude of inverter gain.

<img width="905" height="447" alt="image" src="https://github.com/user-attachments/assets/c4616850-ac83-49c8-95c5-ab1874850649" />

## Static behaviour evaluation-CMOS inverter robustness-Device variation
## Day5_Lec44 : Sources of variation – Etching process

<img width="904" height="437" alt="image" src="https://github.com/user-attachments/assets/63434fe5-b583-4660-bfa6-81f147b31482" />


- Device Dimensions and Fabrication Variations

  In a CMOS inverter, the channel length (L) is defined by the polysilicon gate, and the channel width (W) is set by its overlap with the diffusion region.

  Manufacturing imperfections in lithography and etching introduce small variations in effective W and L.

  These variations impact threshold voltage, drive strength, and propagation delay, making robustness to process variation essential.

<img width="896" height="485" alt="image" src="https://github.com/user-attachments/assets/53ef2474-08d6-4f51-9d95-7041deb87b40" />

<img width="369" height="465" alt="image" src="https://github.com/user-attachments/assets/3d426d01-b8f8-4dee-9163-e7498fcc0968" />

- Technology Node and Scaling

  The technology node is determined by the minimum gate length (e.g., 180 nm, 65 nm).

  As the node scales down, device density and switching speed increase, but sensitivity to variations also becomes more significant.

<img width="899" height="474" alt="image" src="https://github.com/user-attachments/assets/f8a755ba-c5d7-4cb1-a26d-eeded6c1f448" />

- Inverter Chain Effects

  In an inverter chain, local process variations (dimension changes, impurity fluctuations, edge roughness) cause slight differences in each stage.

  These variations accumulate across stages, affecting delay, switching threshold, and overall timing predictability.

  ## Day5_Lec45 : Sources of variation – oxide thickness

  <img width="896" height="478" alt="image" src="https://github.com/user-attachments/assets/f4a07d25-17c1-402c-99d5-228b5320c69c" />

- Oxide Thickness (tox) Variation

    Oxide thickness (tox) is a significant source of process variation in CMOS devices.

    A thinner oxide increases Cox, lowers effective channel resistance, and increases drive current.

    A thicker oxide decreases Cox, raises effective resistance, and weakens drive current.

    In a CMOS cross-section, the gate oxide lies directly beneath the polysilicon (or metal) gate, and in practice, its thickness is not perfectly uniform.

  <img width="608" height="503" alt="image" src="https://github.com/user-attachments/assets/7e567b92-d060-443c-abc9-daf1c3914bc5" />


- Impact on Inverter Chains

    Variations in tox cause small shifts in threshold voltage, drain current, and propagation delay, which accumulate along an inverter chain.

   Middle inverters may experience partial averaging of variations, while edge inverters often show higher variability due to layout surroundings.

   Despite these effects, CMOS inverters continue to operate correctly, showing strong robustness to oxide-thickness variations.

   <img width="898" height="423" alt="image" src="https://github.com/user-attachments/assets/3ef9a01b-969a-454e-9fb4-766ed377e8b5" />

   ## Day5_Lec46 : Sources of variation – oxide thickness

  - Here, we intentionally apply extreme variations in PMOS and NMOS widths to check whether the inverter’s DC characteristics remain stable.

- The objective is to confirm that even under significant device imbalance, the CMOS inverter continues to function reliably.

<img width="896" height="504" alt="image" src="https://github.com/user-attachments/assets/7ffe8f8d-1bb2-4474-a9fb-a90b7cc86d34" />

- Case 1: Strong PMOS (1.875 µm), Weak NMOS (0.375 µm).

- Case 2: Weak PMOS (0.375 µm), Strong NMOS (1.875 µm).

- Widths are swept from 0.375 µm to 1.875 µm in 0.375 µm steps (5 iterations).

- For each width combination, a DC sweep is performed in SPICE, generating multiple VTC curves for comparison.

<img width="534" height="416" alt="image" src="https://github.com/user-attachments/assets/e62bda3f-9b7d-409d-9304-c4484d1d2ecc" />

