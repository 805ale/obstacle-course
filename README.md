# Obstacle Course (Unity)

A playful 3D obstacle-course prototype: move a nimble character from **START** to **FINISH** while dodging spinners, rollers, and droppers. Built while following the “Obstacle Course” section of a Unity intro. Core loop: **move & dodge to get from A to B**. 


---

## 🎮 Gameplay Snapshot
- Third-person follow camera (Cinemachine).
- Movement tuned to be frame-rate independent with `Time.deltaTime`.
- Hazards:
  - **Spinner**: rotating arms to time your pass.
  - **Roller**: moving/rotating cylinders in a corridor.
  - **Dropper**: waits, becomes visible, then falls. 
- “Bump” tally (lightweight score on collisions). 


---

## 🧠 What I Learned (highlights)

- **Core loop & player experience:** design for nimble, agile movement; “get from A to B” with readable hazards. 
- **Start/Update & callbacks:** Unity calls lifecycle methods; I added my logic inside `Update()` and custom methods I call explicitly. 
- **Variables & `SerializeField`:** expose tweakable movement values in the Inspector for quick iteration. 
- **Input & movement:** used `Input.GetAxis` (or the new system) and scaled by `Time.deltaTime` + `moveSpeed` to keep motion consistent across frame rates.  
- **Cinemachine follow camera:** Virtual Camera following the player with tuned distance/FOV for clarity.  
- **Physics & collisions:** `OnCollisionEnter` to detect wall bumps and increment a simple counter for feedback/scoring. 
- **Methods & `GetComponent<>()`:** structured logic into small functions and fetched components safely where needed. 
- **Timers & conditions:** used `Time.time` + `if` checks to delay actions (e.g., make a Dropper visible, enable gravity after N seconds).  
- **Rotation utilities:** parameterized X/Y/Z angular speeds for the Spinner.  
- **Prefabs & reuse:** packaged **Dropper**, **Spinner**, **Roller**, and a generic **Obstacle** for rapid level blocking. 

---

## 🧩 Level Layout (current)

1. **Start** zone with onboarding hint.  
2. **Roller corridor** (timing gates).  
3. **Spinner platform** (pattern reading).  
4. **Dropper lane** (staggered delays).  
5. **Finish** (confetti hook).  

---

## 🗂 Project Structure
- Assets/
- Art/ # low-poly props & materials
- Prefabs/ # Spinner, Roller, Dropper, Obstacle
- Scripts/
- Mover.cs
- Spinner.cs
- Dropper.cs
- ObjectHit.cs
- Scorer.cs
- Scenes/
- SampleScene.unity
- Docs/
- README 

---

## ▶️ How to Run

- **Unity**: 2020+ works (I’m on 202x/URP; update if needed).  
- Open the project, load `SampleScene`, press **Play**.

---

## 🛠 Tech Notes

- **Physics:** Continuous collision for fast movers; hazards have colliders; ground uses Mesh/Box/Terrain Collider.  
- **Camera:** Cinemachine Brain on Main Camera, one Virtual Camera targets Player. :contentReference[oaicite:14]{index=14}  
- **Scoring:** `OnCollisionEnter` increments a bump count (console/UI hook). :contentReference[oaicite:15]{index=15}  
- **Timing:** `Time.time` for delayed actions (Dropper “wait then fall”). :contentReference[oaicite:16]{index=16}

---

## 🧭 Next Steps

- Add checkpoints & simple UI.
- Juice: particles on finish, sfx on bumps.
- Difficulty curve: speed ramps & pattern variety.
- Optional: switch to the new Input System.

---

## 📚 Notes / Attribution

Course notes summarized from my slide deck for the “Obstacle Course” section (variables, methods, collisions, `Time.deltaTime`, Cinemachine, prefabs, etc.). 
