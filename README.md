# MAE-547-Project--Torque-Minimization

## Description
This repository contains the code to minimize torque control effort for a 2-link robot that is moving from one position to another. Optimization of the torque control effort takes place in the MATLAB code. The MuJoCo simulation is intended to provide a visual behind the robot motion. 
## Files Included
- `547_Project.mlx` - MATLAB `.mlx` file for optimization and plotting
- `Mujoco_Simulation_of_Unoptimized_and_Optimized_Motion.ipynb` - MuJoCo simulation file
## MATLAB Features 
  - Beginning and end joint positon input.
  - Optmization of torque cost.
  - Visualize in plots.
## MuJoCo Features
  - Load STL meshes for base, link1, and link2.
  - Analyze mesh geometry, bounding boxes, and recommend XML alignment fixes.
  - Forward kinematics checks and body/joint diagnostics.
  - Min-jerk and energy-optimized arm trajectories.
  - PID + inverse dynamics control for smooth motion.
  - Render video of arm motion.
## Requirements to Run
- Python 3.9+
- Packages: numpy, scipy, matplotlib, mediapy, jax, flax, orbax, mujoco, brax, mujoco_playground
- ffmpeg for video rendering
- Optimization toolbox MATLAB
- Install dependencies-
  pip install mujoco mujoco_mjx brax mediapy ml_collections
  pip install git+https://github.com/google-deepmind/mujoco_playground.git
  sudo apt install ffmpeg
## Matlab Quick Start
1. Open the `547_Project.mlx` file in MATLAB.
2. Run the optimization code.
3. Customization
    Adjust start/target joint angles.
    Increase/Decrease the leading value in smooth_penalty to decrease/increase torque choppiness 
## MuJoCo Quick Start
1. Copy STL files to the working directory-
    shutil.copy("base.stl", "base.stl")
    shutil.copy("link1.stl", "link1.stl")
    shutil.copy("link2.stl", "link2.stl")
2. Run mesh analysis-
    vertices, _ = read_stl_file("link1.stl")
    analyze_stl_mesh(vertices, "LINK 1")
3. Simulate unoptimized motion-
    Uses min-jerk interpolation and PD control.
    Renders video via mediapy.
4. Run optimized motion-
    Energy-minimized trajectory using prismatic decoupling.
    PID + inverse dynamics ensures smooth motion.
5. Render video-
    media.show_video(frames, fps=60)
6. Customization
    Adjust start/target joint angles.
    Tune PD/PID gains for smoother or faster response.
    Modify XML for joint ranges, masses, or gear ratios.
    Replace STL files for different arm geometries.
Notes- 
    STL units are mm → scaled to meters (scale=“0.001 0.001 0.001”).
    Min-jerk ensures smooth start/stop; energy optimization reduces torque usage.
    Forward kinematics checks alignment and global positions of links.

## Authors
Kaitlyn Ashcroft, Geneva Feng, Corinne Shankles, and Sydney Wold

