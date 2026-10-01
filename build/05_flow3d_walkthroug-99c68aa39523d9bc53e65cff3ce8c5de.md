<h1>Step-by-Step Walkthrough in FLOW-3D</h1>

<h2>Step 1: Create a New Simulation</h2>

<p>
<strong>Purpose:</strong> Start a new FLOW-3D HYDRO simulation using the correct unit system and project name.
</p>

<p>
<strong>Action:</strong>
</p>

<ol>
  <li>Open FLOW-3D HYDRO.</li>
  <li>Create a new workspace or project.</li>
  <li>Select the correct unit system.</li>
  <li>Save the simulation using a clear name, such as <code>LHD_reverse_roller_training_case</code>.</li>
</ol>

<p>
<strong>Expected outcome:</strong> A new FLOW-3D simulation is created and ready for geometry import.
</p>

<hr>

<h2>Step 2: Import Geometry</h2>

<p>
<strong>Purpose:</strong> Load the low-head dam and channel geometry into the FLOW-3D model.
</p>

<p>
<strong>Action:</strong>
</p>

<ol>
  <li>Import the structure geometry file from the <code>02_Geometry</code> folder.</li>
  <li>Check the model scale.</li>
  <li>Check the model orientation.</li>
  <li>Confirm that the dam, crest, apron, and downstream channel are positioned correctly.</li>
</ol>

<p>
<strong>Expected outcome:</strong> The hydraulic-structure geometry appears correctly within the computational domain.
</p>

<hr>

<h2>Step 3: Define the Computational Domain</h2>

<p>
<strong>Purpose:</strong> Create a model domain that includes the upstream approach, dam crest, downstream apron, reverse-roller zone, and downstream recovery reach.
</p>

<p>
<strong>Action:</strong>
</p>

<ol>
  <li>Define the upstream and downstream domain limits.</li>
  <li>Set the domain width to include the full channel or modeled section.</li>
  <li>Set the vertical extent high enough to contain the expected water surface.</li>
  <li>Leave sufficient downstream distance to capture the reverse roller and flow recovery.</li>
</ol>

<p>
<strong>Expected outcome:</strong> The computational domain fully contains the hydraulic features of interest.
</p>

<hr>

<h2>Step 4: Generate the Mesh</h2>

<p>
<strong>Purpose:</strong> Create a computational mesh that captures key hydraulic behavior while maintaining reasonable computation time.
</p>

<p>
<strong>Action:</strong>
</p>

<ol>
  <li>Create a mesh block covering the full computational domain.</li>
  <li>Refine the mesh near the dam crest, toe, apron, and roller region.</li>
  <li>Check the number of cells and expected runtime.</li>
  <li>Adjust mesh resolution if important features are not well represented.</li>
</ol>

<p>
<strong>Expected outcome:</strong> The mesh is sufficiently refined near the low-head dam and reverse-roller region.
</p>

<hr>

<h2>Step 5: Select Physics Options</h2>

<p>
<strong>Purpose:</strong> Activate the physics models needed for free-surface hydraulic simulation.
</p>

<p>
<strong>Action:</strong>
</p>

<ol>
  <li>Activate gravity.</li>
  <li>Activate free-surface flow.</li>
  <li>Select the appropriate turbulence model.</li>
  <li>Activate air entrainment if required for the simulation purpose.</li>
  <li>Activate the general moving-object model if a floating body is included.</li>
</ol>

<p>
<strong>Expected outcome:</strong> The simulation physics are appropriate for low-head dam free-surface flow and reverse-roller analysis.
</p>

<hr>

<h2>Step 6: Apply Boundary Conditions</h2>

<p>
<strong>Purpose:</strong> Define the upstream inflow and downstream hydraulic control.
</p>

<p>
<strong>Action:</strong>
</p>

<ol>
  <li>Assign the upstream inflow boundary using discharge, velocity, or pressure conditions.</li>
  <li>Assign the downstream boundary using tailwater elevation, pressure, or rating-curve information.</li>
  <li>Assign wall boundaries to the channel bed and structure.</li>
  <li>Assign side-wall or symmetry boundaries as appropriate.</li>
  <li>Confirm that the top boundary allows free-surface behavior.</li>
</ol>

<p>
<strong>Expected outcome:</strong> All boundary conditions are assigned and consistent with the site or laboratory conditions.
</p>

<hr>

<h2>Step 7: Set Initial Conditions</h2>

<p>
<strong>Purpose:</strong> Define initial water levels and flow conditions to improve model stability.
</p>

<p>
<strong>Action:</strong>
</p>

<ol>
  <li>Set the initial water level upstream and downstream.</li>
  <li>Define initial fluid regions.</li>
  <li>Check whether the initial water surface is reasonable.</li>
  <li>Avoid unrealistic dry or overfilled regions unless intentionally modeled.</li>
</ol>

<p>
<strong>Expected outcome:</strong> The model begins from a stable and physically reasonable initial condition.
</p>

<hr>

<h2>Step 8: Set Simulation Control</h2>

<p>
<strong>Purpose:</strong> Set runtime, output intervals, and numerical controls.
</p>

<p>
<strong>Action:</strong>
</p>

<ol>
  <li>Define total simulation time.</li>
  <li>Define output-save intervals.</li>
  <li>Enable restart files if needed.</li>
  <li>Review stability controls and solver settings.</li>
  <li>Set monitoring points or output locations if needed.</li>
</ol>

<p>
<strong>Expected outcome:</strong> The simulation control settings are ready for running the model.
</p>

<hr>

<h2>Step 9: Run the Simulation</h2>

<p>
<strong>Purpose:</strong> Run the model and monitor stability.
</p>

<p>
<strong>Action:</strong>
</p>

<ol>
  <li>Run the preprocessor.</li>
  <li>Check for warnings or errors.</li>
  <li>Start the simulation.</li>
  <li>Monitor time step, volume error, and free-surface behavior.</li>
  <li>Stop and troubleshoot if the model becomes unstable.</li>
</ol>

<p>
<strong>Expected outcome:</strong> The model runs successfully and produces output files for post-processing.
</p>

<hr>

<h2>Step 10: Post-Process Results</h2>

<p>
<strong>Purpose:</strong> Use FLOW-3D POST to visualize and extract hydraulic results.
</p>

<p>
<strong>Action:</strong>
</p>

<ol>
  <li>Open the completed simulation in FLOW-3D POST.</li>
  <li>Create longitudinal and cross-section slices.</li>
  <li>Plot velocity contours.</li>
  <li>Plot water-surface elevation.</li>
  <li>Extract pressure, turbulence, and vorticity results.</li>
  <li>Generate figures and animations.</li>
</ol>

<p>
<strong>Expected outcome:</strong> Hydraulic results are available for interpretation and reporting.
</p>

<hr>

<h2>Step 11: Interpret Hydraulic Hazard Conditions</h2>

<p>
<strong>Purpose:</strong> Use model outputs to assess reverse-roller formation and drowning potential.
</p>

<p>
<strong>Action:</strong>
</p>

<ol>
  <li>Identify whether a reverse roller forms downstream of the dam.</li>
  <li>Locate the recirculation zone and surface return flow.</li>
  <li>Identify high-velocity regions.</li>
  <li>Compare modeled water levels with observed or expected values.</li>
  <li>Evaluate whether structural modifications reduce hazardous hydraulic behavior.</li>
  <li>Summarize results by flow range and probability of exceedance, when applicable.</li>
</ol>

<p>
<strong>Expected outcome:</strong> The user can interpret whether the modeled flow condition may indicate hazardous reverse-roller behavior.
</p>

<hr>