<h2> FLOW-3D Walkthrough: Step by step procedure </h2>

<p>
This section provides step-by-step guidance for setting up, running, and interpreting a CFD simulation of flow over a low-head dam using FLOW-3D HYDRO. The procedure focuses on simulating complex free-surface flow, hydraulic jumps, reverse roller formation, and associated hydraulic hazards.
</p>

<h3>Step 1: Create a New Simulation</h3>

<p><strong>Purpose:</strong> Create a new FLOW-3D HYDRO simulation using the appropriate unit system and project configuration.</p>

<p><strong>Action:</strong></p>

<ol>
<li>Open FLOW-3D HYDRO.</li>
<li>Create a new workspace or simulation project.</li>
<li>Select the appropriate unit system (SI or US customary units).</li>
<li>Assign a descriptive simulation name, such as <code>LHD_reverse_roller_training_case</code>.</li>
<li>Save the simulation in the designated project directory.</li>
</ol>

<p><strong>Expected Outcome:</strong> A new FLOW-3D simulation is created and ready for geometry import.</p>

<hr>

<h3>Step 2: Import Geometry</h3>

<p><strong>Purpose:</strong> Import the low-head dam and channel geometry into the computational model.</p>

<p><strong>Action:</strong></p>

<ol>
<li>Import the structure geometry file from the <code>02_Geometry</code> folder.</li>
<li>Check that the imported geometry uses the correct units and scale.</li>
<li>Verify the orientation and position of the dam relative to the flow direction.</li>
<li>Confirm that the dam crest, upstream channel, downstream apron, and riverbed are represented correctly.</li>
<li>Check the geometry for unintended gaps, overlaps, or missing surfaces.</li>
</ol>

<p><strong>Expected Outcome:</strong> The hydraulic structure and surrounding channel geometry are correctly positioned within the FLOW-3D modeling environment.</p>

<p><a href="02_geometry_import.png">View Figure 3: Geometry Imported into FLOW-3D</a></p>

<p><strong>Figure 3.</strong> Imported geometry of a low-head dam and surrounding channel in FLOW-3D HYDRO.</p>

<hr>

<h3>Step 3: Define the Computational Domain</h3>

<p><strong>Purpose:</strong> Establish a computational domain that includes all hydraulic features necessary to simulate reverse roller formation and downstream flow behavior.</p>

<p><strong>Action:</strong></p>

<ol>
<li>Define the upstream boundary sufficiently far from the dam to minimize boundary effects on approaching flow.</li>
<li>Extend the downstream boundary beyond the expected reverse roller and hydraulic jump region.</li>
<li>Set the lateral domain limits to include the full channel width or the representative modeled section.</li>
<li>Provide sufficient vertical space for the expected free-surface fluctuations and air entrainment.</li>
<li>Ensure that the computational domain adequately captures the upstream approach, dam crest, downstream toe, recirculation region, and flow recovery zone.</li>
</ol>

<p><strong>Expected Outcome:</strong> The computational domain fully encompasses the flow region of interest while minimizing artificial boundary effects.</p>

<hr>

<h3>Step 4: Generate the Computational Mesh</h3>

<p><strong>Purpose:</strong> Develop a computational mesh capable of resolving complex hydraulic behavior while maintaining reasonable computational efficiency.</p>

<p><strong>Action:</strong></p>

<ol>
<li>Create a computational mesh block covering the complete simulation domain.</li>
<li>Apply finer mesh resolution near the dam crest, downstream toe, hydraulic jump, and reverse roller region.</li>
<li>Ensure adequate resolution of geometric features and strong velocity gradients.</li>
<li>Evaluate the total number of computational cells and expected computational cost.</li>
<li>Conduct mesh refinement tests to determine whether the predicted hydraulic results are sufficiently mesh-independent.</li>
</ol>

<p><strong>Expected Outcome:</strong> A computational mesh that adequately resolves the critical flow features associated with reverse roller formation.</p>

<p><a href="03_mesh_setup.png">View Figure 4: Computational Mesh and Refinement</a></p>

<p><strong>Figure 4.</strong> Computational mesh showing local refinement near the low-head dam and reverse roller region.</p>

<hr>

<h3>Step 5: Select Physics Models</h3>

<p><strong>Purpose:</strong> Activate the relevant physical models required to simulate turbulent free-surface flow and hydraulic jump behavior.</p>

<p><strong>Action:</strong></p>

<ol>
<li>Activate gravity and verify its direction and magnitude.</li>
<li>Enable the appropriate free-surface flow formulation.</li>
<li>Select a suitable turbulence model, such as RNG k-epsilon, and evaluate alternative models where necessary.</li>
<li>Enable air entrainment modeling when required and supported by the available measurements.</li>
<li>Activate the General Moving Objects (GMO) model if the simulation includes moving or floating objects.</li>
<li>Review fluid properties, including density and viscosity.</li>
</ol>

<p><strong>Expected Outcome:</strong> The relevant physical models are configured to simulate turbulent flow, free-surface deformation, and reverse roller formation at low-head dams.</p>

<hr>

<h3>Step 6: Apply Boundary Conditions</h3>

<p><strong>Purpose:</strong> Define the hydraulic conditions controlling flow through the computational domain, particularly upstream discharge and downstream tailwater elevation.</p>

<p><strong>Action:</strong></p>

<ol>
<li>Assign the upstream inflow boundary using an appropriate discharge, velocity, or pressure-based condition.</li>
<li>Specify the downstream boundary condition using the corresponding tailwater elevation, pressure condition, or suitable discharge-stage relationship.</li>
<li>Assign wall boundary conditions to the dam structure and channel bed.</li>
<li>Specify lateral boundary conditions based on the channel geometry and modeling assumptions.</li>
<li>Configure the upper boundary consistently with the selected free-surface and air-pressure treatment.</li>
<li>Verify that all boundary conditions correspond to the intended hydraulic scenario.</li>
</ol>

<p><strong>Expected Outcome:</strong> The computational model represents the appropriate upstream and downstream hydraulic controls required for reverse roller simulation.</p>

<hr>

<h3>Step 7: Define Initial Conditions</h3>

<p><strong>Purpose:</strong> Establish physically reasonable initial water levels and flow conditions to improve numerical stability and reduce initialization time.</p>

<p><strong>Action:</strong></p>

<ol>
<li>Define the initial upstream and downstream water surface elevations.</li>
<li>Specify the initial fluid regions within the computational domain.</li>
<li>Initialize the flow field using physically reasonable conditions.</li>
<li>Check that the initial fluid distribution is consistent with the dam geometry and hydraulic conditions.</li>
<li>Avoid unintended dry areas or excessive fluid volumes that could cause numerical instability.</li>
</ol>

<p><strong>Expected Outcome:</strong> The simulation begins from physically reasonable initial hydraulic conditions.</p>

<hr>

<h3>Step 8: Configure Simulation Controls</h3>

<p><strong>Purpose:</strong> Define simulation duration, output frequency, monitoring locations, and numerical control parameters.</p>

<p><strong>Action:</strong></p>

<ol>
<li>Specify the total simulation duration to allow the hydraulic jump and reverse roller to develop.</li>
<li>Define output intervals sufficient to capture free-surface fluctuations and transient flow behavior.</li>
<li>Configure restart files when necessary.</li>
<li>Review time-step controls and numerical stability settings.</li>
<li>Define monitoring points for water surface elevation, velocity, and pressure where appropriate.</li>
<li>Ensure that the simulation duration is sufficient to evaluate steady, quasi-steady, or transient hydraulic behavior.</li>
</ol>

<p><strong>Expected Outcome:</strong> The simulation control parameters are configured for stable computation and effective hydraulic result extraction.</p>

<hr>

<h3>Step 9: Run the Simulation</h3>

<p><strong>Purpose:</strong> Execute the FLOW-3D simulation and evaluate numerical stability and hydraulic convergence.</p>

<p><strong>Action:</strong></p>

<ol>
<li>Run the model preprocessor to check geometry, mesh, physics, and boundary conditions.</li>
<li>Review preprocessing warnings and correct identified problems.</li>
<li>Start the simulation.</li>
<li>Monitor the computational time step, fluid volume, numerical warnings, and solution stability.</li>
<li>Inspect the evolution of the free surface and reverse roller formation.</li>
<li>Verify that the hydraulic solution reaches the intended steady, quasi-steady, or statistically stationary condition.</li>
<li>Investigate and resolve numerical instability before accepting the simulation results.</li>
</ol>

<p><strong>Expected Outcome:</strong> The simulation runs successfully and generates reliable hydraulic output files for post-processing.</p>

<hr>

<h3>Step 10: Post-Process Simulation Results</h3>

<p><strong>Purpose:</strong> Visualize, analyze, and extract hydraulic parameters using FLOW-3D POST.</p>

<p><strong>Action:</strong></p>

<ol>
<li>Open the completed simulation results in FLOW-3D POST.</li>
<li>Create longitudinal and transverse sections through the hydraulic structure and reverse roller region.</li>
<li>Generate velocity magnitude and velocity-component contour plots.</li>
<li>Visualize water surface elevation and free-surface fluctuations.</li>
<li>Extract pressure distributions, turbulence quantities, and vorticity fields.</li>
<li>Generate streamlines or other appropriate flow visualizations to identify recirculation patterns.</li>
<li>Estimate reverse roller length, location, and reverse-flow characteristics.</li>
<li>Export figures, animations, and numerical data for further analysis.</li>
</ol>

<p><strong>Expected Outcome:</strong> Hydraulic results are available for quantitative analysis, visualization, and documentation of reverse roller behavior.</p>

<hr>

<h3>Step 11: Interpret Hydraulic Hazard Conditions</h3>

<p><strong>Purpose:</strong> Evaluate the simulated hydraulic conditions to identify reverse roller formation, recirculation intensity, and potential drowning hazards downstream of low-head dams.</p>

<p><strong>Action:</strong></p>

<ol>
<li>Determine whether a reverse roller develops downstream of the dam under the simulated hydraulic conditions.</li>
<li>Identify the location, length, and extent of the recirculation region.</li>
<li>Examine upstream-directed surface velocities and downstream-directed near-bed flow.</li>
<li>Identify regions of high velocity, strong turbulence, and significant pressure fluctuations.</li>
<li>Compare simulated water levels and velocity distributions with available field or laboratory measurements.</li>
<li>Evaluate how variations in discharge and tailwater elevation affect reverse roller formation and intensity.</li>
<li>Compare existing and modified dam configurations to assess the effectiveness of potential mitigation measures.</li>
<li>Summarize hydraulic conditions across the investigated discharge and tailwater ranges.</li>
<li>Communicate the identified hydraulic hazards using figures, tables, and animations.</li>
</ol>

<p><strong>Expected Outcome:</strong> Users can identify and interpret hydraulic conditions associated with reverse rollers, evaluate potential drowning hazards, and support the assessment of appropriate mitigation strategies.</p>

<p><strong>Important Note:</strong> The presence of a reverse roller, strong recirculation, or upstream-directed surface flow indicates potentially hazardous hydraulic conditions. However, velocity and flow-pattern results alone do not provide a validated quantitative probability of drowning. Comprehensive risk assessments may require additional information on hydrodynamic forces, exposure conditions, and human safety.</p>

<hr>
