Author: Enrique Corpa Rios  
Release: …

Version: 0.1  
Date: 21.09.2023  
Place: 9472 Grabs (CH)  

**PRODUCT REQUIREMENT SPECIFICATIONS**

EP3562 Dynamic Signal + Noise Analyzer

M = Firm demand ("Must")1

S = Should be implemented, if all MUST requirements can be fulfilled
anyway ("Should")

C = Desired, can be implemented if fulfillment of higher-level
requirements is not affected ("Could")

W = will not be implemented this time, but will be reserved for the
future ("Won't")

# Introduction

Overall goal: development of a modern Dynamic Signal Analyzer (DSA)
based on the ancientHP3562A.

-   Dual-channel spectrum analyzer with a range between 64 μHz to 100
    kHz and with a dynamic range of 80 dB

-   Modular 2-board system: a Single Board Computer (SBC), meant to be
    reusable between different instruments, and the second
    “Instrumentation Board” which will contain the analog front-end,
    ADCs and communication interfaces

-   The interface to the instrument will be through Ethernet (with or
    without PoE) or Wi-Fi

-   The instrument control panel will be accessed over IP in a web
    browser to achieve following advantages:

    -   Design of the GUI becomes a web UI design problem
    -   Web UI are platform independent (no need to develop a desktop
        app for multiple systems)
    -   Modern web UI are responsive: they adapt to the device they are
        viewed on (tablets, laptops, phones, etc.)
    -   The application-level processing occurs directly in the
        instrument, not in an external device
    -   The instrument can be accessed from a single computer, LAN or
        the internet, which helps in automation and test benches

# General Requirements

|         |                       |                                                                                             |              |         |
|---------|-----------------------|---------------------------------------------------------------------------------------------|--------------|---------|
| **Nr.** | **Category**          | **Request**                                                                                 | **Comments** | **Typ** |
| 1.1     | General Construction  | Two board design: SBC and motherboard with analog-fronted, signal generator, etc.           |              | M       |
| 1.2     | Target price ex works | TBD \[CHF\]                                                                                 |              | M       |
| 1.3     | Target Market         | Worldwide                                                                                   |              | M       |
| 1.4     | Stand alone operation | Must be possible to connect a mouse and keyboard to use the instrument as it’s own computer |              | M       |

# Hardware Requirements

### 3.1 Dynamic Analyzer Characteristics

|         |                                   |                                 |                                                     |         |
|---------|-----------------------------------|---------------------------------|-----------------------------------------------------|---------|
| **Nr.** | **Category**                      | **Request**                     | **Comments**                                        | **Typ** |
| 3.1.1   | Bandwidth                         | 200 kHz                         |                                                     | M       |
| 3.1.2   | Input Range Max                   | +27 dBVrms (22 V)               |                                                     | M       |
| 3.1.3   | Input Range Min                   | \- 131 dBVrms (300 nV range)    | -51 from HP3562, but since we have 10000 gain → 131 | M       |
| 3.1.4   | Range Steps                       | 2 dB                            |                                                     | S       |
| 3.1.5   | Maximum input level               | 42 Vpk                          |                                                     | M       |
| 3.1.6   | Cross Talk                        | -135 dB                         | Between channels                                    | M       |
| 3.1.7   | Input Channels                    | 2                               |                                                     | M       |
| 3.1.8   | Input configuration               |                                 |                                                     | M       |
| 3.1.9   | Dual Channel Sample rate          | Must not be reduced in dual mod |                                                     | M       |
| 3.1.10  | FFT Dynamic Range                 | 110 dB                          |                                                     | M       |
| 3.1.11  | Swept Sine Dynamic Range          | 150 dB                          | SR785 has 145 dB                                    | M       |
| 3.1.12  | Real Time FFT Bandwidth           | 200 kHz                         | SR785 has full BW                                   | M       |
| 3.1.13  | Amplitude Accuracy Single Channel | ±0.2 dB                         | SR785                                               | M       |
| 3.1.14  | Amplitude Accuracy Cross Channel  | ±0.05 dB                        | SR785                                               | M       |
| 3.1.15  | Display update Rate               | 30 Hz                           |                                                     | M       |
| 3.1.16  | Amplitude resolution              | 24 bit                          | Raw resolution                                      | M       |

### 3.2 Signal Generator

<table>
<tbody>
<tr class="odd">
<td><strong>Nr.</strong></td>
<td><strong>Category</strong></td>
<td><strong>Request</strong></td>
<td><strong>Comments</strong></td>
<td><strong>Typ</strong></td>
</tr>
<tr class="even">
<td>3.2.1</td>
<td>Source Output Types</td>
<td></td>
<td>Arbitrary (Should?)</td>
<td>M</td>
</tr>
<tr class="odd">
<td>3.2.2</td>
<td>Amplitude Range Min.</td>
<td>0.01 mVp</td>
<td></td>
<td>M</td>
</tr>
<tr class="even">
<td>3.2.3</td>
<td>Amplitude Range Max.</td>
<td>5 Vp</td>
<td></td>
<td>M</td>
</tr>
<tr class="odd">
<td>3.2.4</td>
<td>Offset adjustment</td>
<td>±5 V</td>
<td></td>
<td>M</td>
</tr>
<tr class="even">
<td>3.2.5</td>
<td>DC Offset accuracy</td>
<td>±10 mV Typ.</td>
<td></td>
<td>M</td>
</tr>
<tr class="odd">
<td>3.2.6</td>
<td>Amplitude Resolution High Range</td>
<td>0.1 mVp (Output &gt;= 500 mVp)</td>
<td></td>
<td>M</td>
</tr>
<tr class="even">
<td>3.2.7</td>
<td>Amplitude Resolution Low Range</td>
<td>0.01 mVp (Output &lt; 500 mVp)</td>
<td></td>
<td>M</td>
</tr>
<tr class="odd">
<td>3.2.8</td>
<td>Amplitude accuracy sine source High Range</td>
<td>0.01</td>
<td>Over the entire BW</td>
<td>M</td>
</tr>
<tr class="even">
<td>3.2.9</td>
<td>Amplitude accuracy sine source Low Range</td>
<td>0.05</td>
<td><p>Over the entire BW.</p>
<p>TBD, maybe 10%?</p></td>
<td>M</td>
</tr>
<tr class="odd">
<td>3.2.10</td>
<td>Output Impedance</td>
<td>&lt; 5 Ω</td>
<td></td>
<td>M</td>
</tr>
<tr class="even">
<td>3.2.11</td>
<td>Output current max.</td>
<td>100 mApk</td>
<td></td>
<td>M</td>
</tr>
<tr class="odd">
<td>3.2.12</td>
<td>Harmonic Distortion</td>
<td>&lt; -80 dBc</td>
<td>Entire BW (With our 24 bit ADC, maybe we should ask for more)</td>
<td>M</td>
</tr>
<tr class="even">
<td>3.2.13</td>
<td>Inter-modulation dist.</td>
<td>&lt; -80 dBc</td>
<td></td>
<td>M</td>
</tr>
<tr class="odd">
<td>3.2.14</td>
<td>Spurious</td>
<td>&lt; -80 dBfs</td>
<td></td>
<td>M</td>
</tr>
<tr class="even">
<td>3.2.15</td>
<td>Full-span FFT noise floor</td>
<td></td>
<td>Check what is possible with our SR560-like front-end</td>
<td>M</td>
</tr>
<tr class="odd">
<td>3.2.16</td>
<td>Residual DC response</td>
<td>&lt; -30 dBfs</td>
<td></td>
<td>M</td>
</tr>
<tr class="even">
<td>3.2.17</td>
<td>Phase Accuracy Single Channel resp. Trigger</td>
<td>± 3 deg.</td>
<td></td>
<td>M</td>
</tr>
<tr class="odd">
<td>3.2.18</td>
<td>Phase Accuracy Single Channel resp. Trigger</td>
<td>± 0.5 deg.</td>
<td></td>
<td>M</td>
</tr>
</tbody>
</table>

### 

### 3.3 Computer

|         |                  |                                        |              |         |
|---------|------------------|----------------------------------------|--------------|---------|
| **Nr.** | **Category**     | **Request**                            | **Comments** | **Typ** |
| 3.3.1   | Format           | SBC in CM4 format                      | Apendix B    | M       |
| 3.3.2   | PCI-e            |                                        |              | M       |
| 3.3.3   | SDD Storage min. | 32 Gb                                  |              | M       |
| 3.3.4   | GPU              | Must be capable of OpenGL acceleration |              | M       |
| 3.3.5   | RAM min.         | 4 Gb                                   |              | M       |
| 3.3.6   | CPU bus          | 64 bit                                 |              | M       |

2.  

### 3.4 Expansion Slots

|         |                           |                                                                                      |              |         |
|---------|---------------------------|--------------------------------------------------------------------------------------|--------------|---------|
| **Nr.** | **Category**              | **Request**                                                                          | **Comments** | **Typ** |
| 3.4.1   | Number of expansion slots | 1                                                                                    |              | S       |
| 3.4.2   | Type                      | TBD                                                                                  |              | S       |
| 3.4.3   | Connector                 | TBD                                                                                  |              | S       |
| 3.4.4   | Function                  | Any hardware connected to the expansion slot should be accesible by the SBC and FPGA |              | S       |

### 3.5 Connectivity

|         |                                   |                                                                                    |                                               |         |
|---------|-----------------------------------|------------------------------------------------------------------------------------|-----------------------------------------------|---------|
| **Nr.** | **Category**                      | **Request**                                                                        | **Comments**                                  | **Typ** |
| 3.5.1   | Front Panel Connectors            |                                                                                    |                                               | M       |
| 3.5.2   | Back Panel Connectors             |                                                                                    |                                               | M       |
| 3.5.3   | Front Panel Illumination          | Input channels and source output must have RGB illumination for status information |                                               | S       |
| 3.5.4   | Wifi                              | Must have Wifi connectivity                                                        |                                               | M       |
| 3.5.5   | Back Panel USB                    | All USB 3.0                                                                        |                                               | S       |
| 3.5.6   | Power Input Connector             | USB type C                                                                         |                                               | M       |
| 3.5.7   | Ethernet                          | Normal Ethernet Connector                                                          |                                               | M       |
| 3.5.8   | Ethernet Speed                    | 1 Gbps                                                                             |                                               | M       |
| 3.5.9   | Input Channel Connectors          | BNC                                                                                | TBD: Check with rico for lowest noise options | M       |
| 3.5.10  | Input Channel Grounding Connector | Standard by HP3562A                                                                |                                               | M       |
| 3.5.11  | Source Output Connector           | BNC                                                                                | TBD                                           | M       |

### 3.6 Analog front-end (RS560 based)

|         |                         |                                                                   |                                                                                                              |         |
|---------|-------------------------|-------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|---------|
| **Nr.** | **Category**            | **Request**                                                       | **Comments**                                                                                                 | **Typ** |
| 3.6.1   | Compatibility           | Front end must be reusable in HFLNA project with minimum changes. |                                                                                                              | M       |
| 3.6.2   | Bandwidth               | -3 db @ 1 MHz, 1-pole roll-of                                     | Instrument bandwidht is different: 200 kHz this is meant to be used in the HFLNA project                     | M       |
| 3.6.3   | Coupling                | AC and DC coupling                                                |                                                                                                              | M       |
| 3.6.4   | Coupling AC HPF         | 0.03 Hz 1 – Pole                                                  | This is the minimum AC filter of the RS560                                                                   | M       |
| 3.6.5   | Imput Impedance         | 100 Mohm + 25 pF                                                  |                                                                                                              | M       |
| 3.6.6   | Noise SPD Shorted Input | Equal or lover SR560                                              | See apendix                                                                                                  | M       |
| 3.6.7   | Noise @ 1 kHz           | 4 nV/sqrt(Hz) or lower                                            |                                                                                                              | M       |
| 3.6.8   | Bandwidth Flatness      | ±0.3 dB to 300 kHz                                                | \*Check HP3562A                                                                                              | M       |
| 3.6.9   | Signal Distortion       | 0.01% @ 1 kHz                                                     |                                                                                                              | M       |
| 3.6.10  | CMRR                    | 100 dB from DC to 1 kHz                                           | 100 mV common mode input at 1 kHz, gain of 100, low noise mode. Decreases by 6 dB/octave from 1 kHz to 1 MHz | M       |

### 3.7 Power Supply

|         |              |                              |              |         |
|---------|--------------|------------------------------|--------------|---------|
| **Nr.** | **Category** | **Request**                  | **Comments** | **Typ** |
| 3.7.1   | Type         | External                     |              | M       |
| 3.7.2   | Interface    | Power Delivery Through USB C |              | M       |

### 3.8 Housing

|         |                |                                                         |              |         |
|---------|----------------|---------------------------------------------------------|--------------|---------|
| **Nr.** | **Category**   | **Request**                                             | **Comments** | **Typ** |
| 3.8.1   | Height         | 50 mm                                                   | Bode100      | S       |
| 3.8.2   | Width          | 260                                                     | Bode100      | S       |
| 3.8.3   | Depth          | 265                                                     | Bode100      | S       |
| 3.8.4   | Repair-ability | Access to main components with minimum work by the user |              | M       |

### 3.9 Environmental Operating Restrictions 

|         |                         |                     |              |         |
|---------|-------------------------|---------------------|--------------|---------|
| **Nr.** | **Category**            | **Request**         | **Comments** | **Typ** |
| 3.9.1   | Ambient Temperature Min | 0 ºC                |              | M       |
| 3.9.2   | Ambient Temperature Max | 55 ºC               |              | M       |
| 3.9.3   | Relative Humidity Min   | 0.15                |              | M       |
| 3.9.4   | Relative Humidity Max   | 95% @ 40 ºC         |              | M       |
| 3.9.5   | Vibrations              | 1.5 Grms 5 – 500 Hz |              | M       |
| 3.9.6   | Shock                   | 5 Grms              | TBD          | M       |
| 3.9.7   | Max. Altitude           | 4600 m              |              | M       |

### 3.10 Regulatory Approvals

|         |              |             |                |         |
|---------|--------------|-------------|----------------|---------|
| **Nr.** | **Category** | **Request** | **Comments**   | **Typ** |
| 3.10.1  | CE Marking   |             |                | M       |
| 3.10.2  | CISPR21      |             | Newest version | M       |

# Software Requirements

## 4.1 OS and Libraries

|         |                  |                                                           |              |         |
|---------|------------------|-----------------------------------------------------------|--------------|---------|
| **Nr.** | **Category**     | **Request**                                               | **Comments** | **Typ** |
| 4.1.1   | Operating System | Linux based                                               | Details TBD  | M       |
| 4.1.2   | User API         | User API to call all instruments within the device itself | Details TBD  | M       |

## 4.2 Communication protocols

|         |              |             |              |         |
|---------|--------------|-------------|--------------|---------|
| **Nr.** | **Category** | **Request** | **Comments** | **Typ** |
| 4.2.1   | SCPI         |             | Details TBD  | S       |
| 4.2.2   | LXI          |             | Details TBD  | S       |

## 4.3 Functions

|         |                  |                                          |                                     |         |
|---------|------------------|------------------------------------------|-------------------------------------|---------|
| **Nr.** | **Category**     | **Request**                              | **Comments**                        | **Typ** |
| 4.3.1   | User Interface   | Web browser interface                    |                                     | M       |
| 4.3.2   | User Interface   | Full vector graphics                     | For infinite resolution scalability | M       |
| 4.3.3   | Function         | Data storage in USB flash drive          |                                     | S       |
| 4.3.4   | Function         | Display output through USB C on the back |                                     | S       |
| 4.3.5   | Measurement Mode | Bode Plotter                             |                                     | M       |
| 4.3.6   | Measurement Mode | Real Time Spectrum                       |                                     | M       |

# Definitions

**DSA**: Dynamic Signal Analyzer

**BW**: Bandwidth

**SBC**: Single Board Computer

**OS**: Operating System

**TBD**: To Be Determined

# Appendix A

<img src="Pictures/10000001000003450000025B1ED4C346E00BFAB1.png" style="width:6.1028in;height:4.3965in" />

# Appendix B

<img src="Pictures/10000001000003C2000002B8C62EC254D9681E75.png" style="width:6.3in;height:4.5575in" />See
also CM4-Datasheet section 3.1

# MoSCoW prioritization

The criteria in this specification are organized according to MoSCoW
prioritization.

MUST

(M absolutely required)

MUST refers to requirements that are essential to the project and
non-negotiable. Failure to implement them in whole or in part would lead
to the failure of the project. Requirements of this type are summarized
in the project timebox1. MUST is also an acronym - Minimal Usable
Subset - and stands for minimum requirement.

SHOULD

(S - should be implemented if all MUST requirements can still be met).

Although SHOULD requirements are not critical to the success of the
project, they are highly relevant and should be taken into account in
the project implementation as long as they do not interfere with MUST
requirements. SHOULD requirements can often be implemented in different
ways.

COULD

(C - can be implemented if the fulfillment of higher level requirements
is not affected)

COULD requirements have a low relevance and are often described as "nice
to have". They are only taken into account if capacities are still
available in addition to the priority processing of MUST and SHOULD
requirements. But COULD requirements should not be ignored across the
board. Often, a few simple COULD requirements can generate significant
added value at minimal additional development costs.

WON'T

(W - will not be implemented this time, but bookmarked for the future).

WON'T requirements are of lowest priority for the current project or
planning stage. Classification as WON'T means that the requirement is
important from a business and/or technical point of view, but not
critical in terms of time. Requirements classified in this way are not
forgotten and are considered again in the next release.
