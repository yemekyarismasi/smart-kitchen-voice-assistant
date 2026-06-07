# Yemek AI: Open-Source Smart Kitchen Voice Assistant
**Offline Edge Computing Architecture for IoT Home Appliances (HFSCA Methodology)**  

*Document Version: 2.1.0 (Production-Verified Deployment)*  
*Author: YemekYarismasi.com Engineering Team*  
*License: GNU Affero General Public License v3.0 (AGPL-3.0)*

---

## Abstract
This specification defines the production-ready micro-architectures constituting the Hands-Free Semantic Culinary Assistant (HFSCA) engine, the core technology powering Yemek AI. In smart appliance manufacturing and distributed ambient computing environments (e.g., smart kitchens, connected ovens, display-integrated refrigerators), deploying continuous multimodal cloud infrastructure for local task execution creates an unsustainable financial burden. Cloud-based Large Language Model (LLM) processing loops and neural Text-to-Speech (TTS) rendering degrade linearly under multi-source ambient acoustic disruptions (e.g., kitchen exhaust fans, running water, blenders) and suffer from non-deterministic latency.

Yemek AI's HFSCA methodology completely decouples stateful computational culinary intelligence from the physical hardware execution layer. By operating as an asynchronous Edge-Computing runtime engine, the system structures monolithic recipe data into sequential streaming primitives (The Smart Playlist Matrix). Through deterministic on-device finite automata (DFA), client-side hardware abstractions (Screen Wake Lock API), memory-retention locks, localized data-pruning maps, and autonomous health-tech tracking layers, Yemek AI ensures 0-millisecond navigational latency, absolute network independence, and **0 USD server-side inference costs**.

---

## 1. Architectural Blueprint & Component Deconstruction
The Yemek AI platform isolates its execution footprint into four decoupled, independent modules. Commercial enterprises may consume these components as an integrated runtime ecosystem or implement individual modular layers inside existing embedded operating systems.

```text
[USER INTERACTION: MONOLITHIC RECIPE DETECTED]
                             |
                             v
+-------------------------------------------------------+
|          MODULE 3: HARDWARE PERSISTENCE               |
|          (Wake Lock Enforced & GC Lock)               |
+-------------------------------------------------------+
                             |
                             v
+-------------------------------------------------------+
|            MODULE 1: THE SMART PLAYLIST               |
|            (Deterministic State-Machine)              |
+-------------------------------------------------------+
        |                                      |
 [Volumetric Intent]                    [Acoustic Tokens]
        v                                      v
+-----------------------------+  +-----------------------------+
|  MODULE 2: PRAGMATIC METRIC |  | MODULE 1.2: ACOUSTIC IGNORE |
|  CALIBRATOR (SUPABASE/ALG)  |  |  SHIELD (IS_SPEAKING_REF)   |
+-----------------------------+  +-----------------------------+
                             |
                             v
+-------------------------------------------------------+
|      MODULE 4: AUTONOMOUS NUTRITIONAL PROFILING       |
|      (State Recovery & Gamification End-State)        |
+-------------------------------------------------------+
```

---

## 2. Component Specifications

### 2.1 MODULE A: On-Device Acoustic State Machine & Acoustic Ignore Shield (AASM-AIS)

#### 2.1.1 Finite State Mapping
The execution loop manages state transactions entirely on the device CPU, wrapping native browser or operating system Speech-to-Text (STT) abstractions without streaming raw audio data to remote clusters.

#### 2.1.2 The Acoustic Ignore Shield (Anti-Loop Mitigation)
Continuous microphone capturing in high-reflectivity acoustic environments causes echo loops where the assistant re-captures its own spoken output. Forcing physical hardware interrupts causes driver-level audio clicking noises ("Bloop" transients).

HFSCA solves this without hardware interrupts via a software-level memory flag:
1. Upon initiating speech synthesis, the execution loop locks `isSpeakingRef.current = true`.
2. While true, the event handler for incoming voice frames intercepts the payload and executes an atomic `return` instruction, destroying the token data locally.
3. Upon completion, a **400ms atomic hardware settlement delay** is enforced before resetting the flag, completely muting echo reflection artifacts.

---

### 2.2 MODULE B: Client-Side Pragmatic Calibrator & Local Data-Pruning Engine (CPC-LDPE)

#### 2.2.1 Density Calculus and Volumetric Translation
Storing the entire global nutritional food database on embedded appliance hardware is impossible due to memory limits. HFSCA enforces a cloud-side data pruning protocol that maps ingredients into a normalized `Gastronomic Density Table`. The transformation uses the fundamental equation:
`Mass (g) = Volume (ml) × Density Coefficient (ρ)`

#### 2.2.2 The Asymmetric Dynamic Multiplier Loop
When a user sets a portion scaling attribute (`m`), the engine recalculates the structural text templates locally via an inline scale-processor (`Rendered_Quantity = Base_Quantity × m`).

---

### 2.3 MODULE C: Embedded Hardware Persistence & Memory-Lock Architecture (EHP-MLA)

#### 2.3.1 Screen Wake Lock Loop Enforcement
HFSCA establishes an unbreakable session boundary by acquiring native hardware wake-state tokens (`navigator.wakeLock.request('screen')`). The visibility state safety hook ensures background tab recovery.

#### 2.3.2 The `utteranceRef` Garbage Collection Protection
Mobile Chromium and WebKit browsers actively dump instantiated speech components from system memory during extended passive listening loops. HFSCA bypasses browser GC memory allocation routines by instantiating the text string array inside a global, immutable memory reference boundary (`utteranceRef`), preventing the browser's native memory garbage-collector from sweeping the active speaker stream.

---

### 2.4 MODULE D: Autonomous Health-Tech Integration & Edge-Timer Recovery (AHT-ETR)

#### 2.4.1 Global Timer Threading and State Recovery
Voice timers are executed on a global thread independent of the DOM unmount/remount cycles. If a user sets a 5-minute timer and navigates through multiple steps, the timer remains intact. When the timer expires, the assistant safely interrupts the current action, announces the alert, and executes a **State Recovery Callback**, autonomously re-reading the exact step the user was currently viewing, ensuring zero cognitive loss.

#### 2.4.2 Silent Nutritional Gamification
Upon reaching the final "Congratulations" execution state, Yemek AI ceases being a mere navigator and acts as an autonomous dietician. It extracts the scaled macronutrients (Protein, Fat, Carbs, Calories) of the active recipe and securely transacts them to the user's database footprint, incrementing a global gamification layer (`total_meals_cooked`) without requiring active user input.

---

## 3. The Intellectual Property & Double-Licensing Blueprint

### 3.1 Prior Art Defense Mechanism
This specification constitutes a detailed, public, and verifiable historical documentation of the HFSCA architecture. Under international patent frameworks (including USPTO Leahy-Smith America Invents Act "First-Inventor-to-File" rules, EPO Article 54 EPC, and WIPO guidelines), this document functions as **Prior Art**. Consequently, no hardware enterprise or corporate entity can legally file patent claims regarding "edge-computed volumetric-to-metric programmatic mapping linked to an on-device local acoustic state machine for cooking environments."

### 3.2 The AGPL-3.0 Commercial Deterrent
As this platform is strictly licensed under the GNU Affero General Public License v3.0, any smart kitchen manufacturer or platform provider that embeds, bundles, or accesses this system architecture over a network inside a proprietary environment is legally mandated to release their entire system's source code to the general public.

To circumvent this copyleft mandate, enterprise commercial operators must enter into a **Proprietary Commercial B2B Dual-Licensing Agreement** with YemekYarismasi.com to obtain commercial SDK binaries and direct API stream authorization for the underlying Gastronomic Volumetric Density Matrix.
