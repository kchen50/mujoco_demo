## Setup (VS Code + venv)

### 1. Create a virtual environment in VS Code

1. Clone this code onto your computer. (`git clone https://github.com/kchen50/mujoco_demo/`)
2. Open this folder in VS Code (`mujoco_demo`).
3. Make sure the Python extension is enabled.
4. Open the Command Palette:
  - `Ctrl+Shift+P` (Windows/Linux) or `Cmd+Shift+P` (macOS)
5. Run: `Python: Select Interpreter`
6. Choose: `Create Environment...`
7. Select:
  - Environment type: `venv`
  - Location: usually `.venv` inside this folder
8. Wait for VS Code to finish creating the environment, then select the created interpreter if prompted.

### 2. Open a terminal inside the virtual environment

In VS Code:

1. `Terminal` -> `New Terminal`
2. Activate it with:
  ```bash
   source .venv/bin/activate
  ```

### 3. Install dependencies

From the `mujoco_demo` folder:

```bash
pip install -r requirements.txt
```

## Run

### 4. Run a Python script

Default (viewer window):

```bash
python sim.py
```

Other useful scripts:

```bash
python set_action.py
python set_sim_state.py
```

## Change the sim stuff (what to edit)

All scripts load the MuJoCo scene from:

- `./mujoco_menagerie/unitree_a1/scene.xml` 
- You can change `unitree_a1` to your desired robot platform.

Main things you should tweak in the scripts:

- In `sim.py`: `scene_path` / simulation stepping parameters (`m.opt.timestep`, `m.opt.impratio`).
- In `set_action.py`: control signal, e.g. this line sets only one actuator:
  - `d.ctrl[ctrl_inds[1]] = theta`
- In `set_sim_state.py`: state target, e.g. this line sets only one set of joints:
  - `d.qpos[joint_inds] = theta`

