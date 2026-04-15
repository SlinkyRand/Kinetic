# Kinetic  
### Mobile AI Exercise App Prototype

---

## Overview

Kinetic is an **effortless workout tracking app with AI-assisted exercise identification** designed for advanced gym-goers who want high visibility on per-muscle recovery status with minimum effort.

The app removes friction from exercise logging by automatically identifying exercises from existing machine labels and visualizing muscle recovery in real time.

---

## Section A — Design Rationale

### Target User

Advanced, independently competent gym-goers who exercise frequently and prefer flexible, self-directed workouts.

### Problem

Most fitness apps require excessive interaction (scrolling through large exercise libraries, searching for movements, and manually logging data. This creates cognitive overhead at the exact moment users are physically fatigued.

**Most workout logging is tedious and interrupts the workout instead of clarifying the workout.**
**Without detailed logs, most gym-goers lack visibility into the optimal recovery windows required for their next session to yield athletic progression.**


### Solution

A **camera-powered, AI-assisted logging system**:

- Take a photo of a machine label (or use voice for free weights)
- AI identifies the exercise and associated muscle groups
- User inputs only:
  - Weight
  - Reps
- The system updates a **visual anatomical model** in real time.

This enables minimum cognitive load for maximum progress, specifically through:
- Fast exercise logging (10 seconds or less)
- Zero-click rest timer
- Continuous muscle recovery tracking
- Tailored exercise recommendation, with timing based on peack recovery times used by elite athletes to ensure progress.


### Why This Direction

- Multimodal AI enables reliable image-based classification
- Works across **any gym, any equipment**
- Supports **real-world variability** (machines often occupied, so user is not stuck waiting for a popular machine)
- Tracks what users *actually do*, not prescribed plans


### Secondary Goal

**Injury prevention and education**

- Visualizes **primary AND supporting muscle groups**
- Helps users identify imbalances and understand the many layers of their body musculature.
- Plans adapt for balance even when users emphasize aesthetic muscle groups. 


### Key Assumptions

- Advanced users prefer **low-friction tracking** over structured programs  
- AI can reliably identify exercises from images or voice input  
- Visual muscle feedback improves decision-making  

**Highest-risk assumption:** AI accuracy



### Success Metrics

- ≥95% exercise detection accuracy (Top-1 Accuracy)  
- MAU greater than 50%
- <10 seconds per log
- Token overhead cost per user exercise session: $0.015 or less
- Increased engagement with supporting muscle groups
- ~25% conversion rate on gear recommendations for active users



### MVP Scope

I focused on a **single, end-to-end flow**: Home → Capture → Confirm Load → Update Live Muscle Status

Intentionally excluded:
- Workout planning (just hand-wavy layout example for how a workout progression would be visually structured)
- Recovery analytics  (navigation space reserved, no analytics view)
- Scheduling 
- Deep personalization  

---

## Section B — Design Decisions & Next Steps

### 1. AI-first logging vs manual tracking

**Trade-off:** Operational cost vs user friction  
**Gain:** Near-zero effort logging, faster workflows, higher engagement. This is a core competitive edge.
**Loss:** AI cost + dependency on accuracy  

- Estimated $0.0001 per image classification (high end could be $0.0005/image)
- High estimate of ~30 images/workout = ~$0.015 per session  

This cost is low enough to recover via **affiliate monetization**.


### 2. Flexible flow vs structured workouts

**Trade-off:** Adaptability vs hand-holding. May lose some beginner gym-goers who want a fixed workout.
**Gain:** Matches real gym behavior
**Loss:** Less control over ideal training sequences  

Users adapt to machine availability. The system adapts with them.


### 3. Flat images vs 3D Anatomical model

**Trade-off:** Speed of development vs free-flow exploration for users
**Gain:** Less UI issues for MVP. No animations or pinch-navigation to refine. 
**Loss:** Requires an extensive dataset of flat imagery for all muscle-groups. More expensive than 3D and likely app footprint bloat even with texture atlas compression.

The anatomical model is a **decision surface** more than a reporting tool.

### 4. Fully Generated Branding vs Competitive assessment

**Trade-off:** Speed of development vs competitive edge during marketing
**Gain:** Complete prototype with UI refinements within alloted time
**Loss:** Branding power.

---

### If Given Another 30 Minutes

- Upgrade to **accurate 3D anatomical model** with swivel + pince 
- Show **supporting muscle groups clearly**
- Persist model across all screens
- Add **camera guidance (machine label example)**
- Expand **Gear tab (affiliate monetization)**
- Add **user preferences (male, female, nonbinary models)**

### If Given Another 8 hours:

- Improve input feedback at the "log set" step. I ran out of time, but that screen needs a "next exercise" button under the confirm set, and the rest timer needs a start button. In the MVP the user is directed to the current workout session prematurely. 
- Set up full state management logic for full functionality
- Build user cloud sync via fully secured S3 buckets on AWS
- Upgrade to **accurate 3D anatomical model** with muscle layer filtering, swivel + pinch navigation, and coded color highlights
- Perform competitive assessment and rename app with human-directed branding plan for maximum marketing efficiency. 
- Export functioning beta prototypes w/mobile install files ready to go

### User Research Approach

- Partner with a local gym  
- Place QR code for prototype access  
- Observe real usage during workouts  

Track:
- Time to log  
- Drop-off rates  
- Repeat usage  

Evaluate: 
- Points of confusion  
- Friction moments
- AI detection accuracy and failure points
- App latency & offline efficacy in gyms with poor cell service

---

## Section C — AI Usage Log

### Stage 1. Idea Capture (GPT + dictation)

- **Input:** Spoken idea dump. Expressed full vision in three minutes.   
- **Output:** Requested a concise, structure prompt to feed Stitch for prototype design.  
- **Kept:** The whole output was acceptable.
- **Changed:** Reduced to MVP  
- **Why:** Needed tight scope for 60-minute timeline. 


### Stage 2. UI generation (Stitch)

- **Input:** Product prototype prompt from GPT. 
- **Output:** 6 initial screens  
- **Kept:** ~50% of layouts  
- **Changed:** Refined navigation, removed fluff, added high-value detail. Manually updated imagery because the AI-generated anatomical models were way off.  
- **Why:** Because we don't build garbage, that's why. Strong attention to detail in the MVP sets the stage for the product's life. 


### Stage 3. Navigation refinement (Stitch)

- **Input:** Duplicated several views to show engagement variations at key navigation forks. Unified navigation. 
- **Output:** 
- **Changed:** Removed non-essential tabs  
- **Added:** Monetization path (Gear)  
- **Why:** This product’s differentiation hinges on minimizing input friction, so I prioritized optimizing the end-to-end user flow in the prototype.


### Stage 4. Prototype generation (Stitch + AI Studio)

- **Output:** Interactive prototype. AI Studio was buggy today, so I fell back on Stitch's native prototyper and got a high-fidelity result that matched the wireframes exactly. 
- **Kept:** Most connections were correct. 
- **Changed:** Added an extra view to clarify "what if this machine had multiple modes" interaction.
- **Why:** Fast, shareable, interactive artifact with consistent display.

---

### Stage 5. README drafting (GPT + dictation)

- **Input:** Spoken rationale to rapidly answer all criteria questions. 
- **Output:** Structured README in markup format.  
- **Kept:** 70% of output. 
- **Edited:** Clarity + alignment. Customized to clarify project-specific details and add a dash of personality. =D
- **Why:** Maximize prototyping time  

---

### Stage 6. Future Steps, actual building (Antigravity vs Perplexity)

- **Input:** Full design files 
- **Output:** Structured README in markup format.  
- **Kept:** 70% of output. 
- **Edited:** Customized to clarify project-specific details, actual workflow, and add a dash of personality. =D
- **Why:** Maximize prototyping time  
