COOLING SYSTEM SIMULATION
=========================

1. Overview
-----------

This Simulink model represents the behaviour of a complete liquid cooling loop.
It combines coolant flow, pressure-loss, heat-transfer, pump, and radiator
behaviour in one system-level simulation.

The model was developed in MATLAB R2025a. It may work in later releases, but
compatibility with other MATLAB versions has not yet been verified.


2. Development Status and Reliability
--------------------------------------

This simulation is incomplete and should be treated as work in progress. Its
reliability and accuracy have not yet been verified against physical test data,
so its results should not be treated as validated predictions.

Parameters in several modules still require review, completion, and validation.
This includes, but is not limited to, the piping blocks within the motor,
inverter, and hose modules. Check all relevant component parameters before
using the model for design decisions or comparisons.


3. Required MATLAB Add-Ons
--------------------------

The following MathWorks products are required:

- Simulink
  Provides the block-diagram environment used to open, configure, and run the
  overall cooling-system model.

- Simscape
  Provides the physical-modelling framework and foundational components used
  to represent connected engineering systems.

- Simscape Fluids
  Provides specialised thermal-liquid components for modelling coolant flow,
  pressure losses, pumps, pipes, valves, reservoirs, and heat exchangers.


4. Installing the Required Add-Ons
----------------------------------

1. Open MATLAB.
2. On the Home tab, select Add-Ons, then select Get Add-Ons.
3. Search for and install each of the following:
   - Simulink
   - Simscape
   - Simscape Fluids
4. Sign in to your MathWorks account if prompted.
5. Follow the installation prompts and restart MATLAB if requested.

These products must be covered by your MATLAB licence. University-managed
computers may require installation through the university software service or
assistance from an administrator.

To confirm installation, open the Add-On Manager and check that all three
products appear under Installed.


5. Required Files
-----------------

The simulation requires the following model and supporting data. The filenames
shown are the current names:

- Main_Model_v0.slx
- air_params.m
- motor efficiency map.mat
- README.txt

These files may be renamed or stored in different folders. Before running the
main model, run the air-parameter script and load the motor
efficiency-map data into the MATLAB workspace. If either supporting file is
renamed, use its new name when running or loading it.


6. Opening and Running the Simulation
-------------------------------------

1. Open MATLAB.
2. Locate the air-parameter script and run it to place the required air
   parameters in the MATLAB workspace. With the current filename, run
   air_params.m.
3. Locate the motor efficiency-map data file and load it into the MATLAB
   workspace. With the current filename, this can be done by double-clicking
   the file in the Current Folder panel or by entering:

       load('motor efficiency map.mat')

   Use the full file path, or first navigate to its folder, if it is not in the
   MATLAB Current Folder or on the MATLAB path.
4. Steps 2 and 3 may be completed in either order, but both must be completed
   before the main model is run.
5. Open the main Simulink model (currently Main_Model_v0.slx).
6. Click Run in the Simulink toolstrip to start the simulation.

If MATLAB reports an undefined variable, first confirm that the air-parameter
script has been run and the motor efficiency-map data has been loaded before
the main model. Also confirm that MATLAB can access their current locations.


7. Motor Efficiency Map
-----------------------

The motor efficiency map is used as a two-dimensional look-up table. It matches
the motor efficiency to the torque and rotational speed of the rotor, allowing
the model to determine the appropriate efficiency for each operating point.

If a different motor is used, replace or update the look-up table with the
corresponding torque, rotor-speed, and efficiency data for that motor. Keep the
data structure and variable names expected by the model, or update the relevant
look-up-table block and model references accordingly.


8. Notes for Users
------------------

- The model and supporting files may be renamed or stored in different
  locations. Always run or load the two supporting files before running the
  main model, using their current names and paths.
- Before saving changes, consider creating a new model version so that the
  previous working version remains available.
- Results can depend on the parameter values and data contained in the two
  supporting files.
- The model is incomplete and has not yet been validated against test data.
  Review its module parameters and treat all results as provisional.
