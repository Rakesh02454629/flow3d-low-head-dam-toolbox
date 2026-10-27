<h1>Model Calibration</h1>
<p>Model calibration is the systematic adjustment of physically uncertain model parameters, within defensible limits, to improve agreement between simulated and observed hydraulic conditions. For low-head dams, calibration should assess whether FLOW-3D reproduces the <strong>submerged hydraulic jump (reverse roller)</strong>, including its water surface, recirculation pattern, velocity field, and—where measurements are available—air entrainment.</p>
<div class="important">
<p><strong>Important:</strong> Discharge, upstream water level, and tailwater elevation should normally be prescribed from measurements, not freely adjusted to force a match. Evaluate their measurement uncertainty separately through sensitivity analysis.</p>
</div>
<h2>Assemble reference measurements</h2>
<p>Use laboratory or field observations from known discharge and tailwater conditions. Useful measurements include:</p>
<ul>
<li>Inflow discharge and upstream/downstream water surface elevations.</li>
<li>Longitudinal water surface profiles and mean flow depths.</li>
<li>Streamwise and vertical velocity profiles, including flow direction in the roller.</li>
<li>Roller length and position relative to the dam crest or toe.</li>
<li>Air concentration or void fraction, if available.</li>
</ul>
<p>Record measurement locations, instrument uncertainties, averaging periods, and the corresponding hydraulic conditions. Reserve independent datasets for subsequent validation.</p>
<h2>Verify geometry and boundary conditions</h2>
<p>Before calibrating parameters, check:</p>
<ol>
<li><strong>Geometry:</strong> dam crest shape and elevation, downstream apron, channel width, bed topography, and bathymetry.</li>
<li><strong>Inlet:</strong> specified discharge or another physically appropriate inflow condition.</li>
<li><strong>Outlet:</strong> measured tailwater elevation and the boundary's distance from the reverse roller.</li>
<li><strong>Initial conditions:</strong> starting water levels and fluid distribution.</li>
<li><strong>Units and datums:</strong> consistent horizontal/vertical coordinates and elevation references.</li>
</ol>
<p>Tailwater elevation is particularly important: it influences the hydraulic jump location, degree of submergence, and the persistence of reverse flow.</p>
<h2>Run a baseline FLOW-3D simulation</h2>
<ul>
<li>Set up the free-surface flow calculation and a suitable turbulence model for the application.</li>
<li>Run long enough for initial transients to diminish, or characterize persistent unsteady behavior where relevant.</li>
<li>Inspect mass conservation, temporal behavior of water levels, and velocity vectors through the roller region.</li>
<li>Save time-averaged results over a clearly specified analysis window, as well as transient data where needed.</li>
</ul>
<p>Keep a record of all numerical settings and model assumptions before calibration begins.</p>
<h2>Evaluate mesh sensitivity</h2>
<p>Refine cells around the crest, impinging jet, shear layer, reverse roller, and downstream bed. Compare results using several systematically refined meshes.</p>
<table>
<thead>
<tr>
  <th>Mesh</th>
  <th>Illustrative relative cell size</th>
  <th>Evaluation</th>
</tr>
</thead>
<tbody>
<tr>
  <td>Coarse</td>
  <td>$\Delta x$</td>
  <td>Baseline flow pattern</td>
</tr>
<tr>
  <td>Medium</td>
  <td>$\Delta x/1.5$</td>
  <td>Change in roller and water-level predictions</td>
</tr>
<tr>
  <td>Fine</td>
  <td>$\Delta x/2$</td>
  <td>Convergence of important outputs</td>
</tr>
</tbody>
</table>
<p>Compare predicted water surface elevations, roller length, velocity profiles, and recirculation strength. The listed mesh ratios are illustrative, <strong>not prescribed cell sizes</strong>. Establish acceptable changes in the quantities of interest before final parameter calibration.</p>
<h2>Evaluate turbulence modeling</h2>
<p>Test a suitable baseline turbulence closure and, if justified, alternatives available in your FLOW-3D installation (for example, an RNG $k$–$\varepsilon$ model). Evaluate the effects on:</p>
<ul>
<li>Roller location and extent.</li>
<li>Time-averaged reverse-flow velocities.</li>
<li>Shear-layer development and turbulence distribution.</li>
<li>Hydraulic jump structure and energy dissipation.</li>
</ul>
<p>Do not select a model based only on its agreement with one water-level measurement; consider the full flow structure and consistency across cases.</p>
<h2>Calibrate bed and wall roughness</h2>
<p>Specify physically reasonable roughness for the dam, apron, and natural channel bed. Where roughness is uncertain, test values within defensible bounds and compare against observed velocities and water surface profiles.</p>
<p>Avoid compensating for errors in geometry, mesh, or boundary conditions by assigning unrealistic roughness values.</p>
<h2>Evaluate and calibrate air entrainment, if supported by data</h2>
<p>Reverse rollers can involve substantial air entrainment. If the FLOW-3D edition and model configuration include suitable air-entrainment capabilities:</p>
<ol>
<li>Establish reasonable agreement with the bulk hydraulics first.</li>
<li>Enable the appropriate air-entrainment treatment.</li>
<li>Examine predicted entrainment zones and transport.</li>
<li>Compare air concentration or void fraction against measurements, when available.</li>
<li>Evaluate sensitivity to applicable air-entrainment parameters and assumptions.</li>
</ol>
<div class="note">
<p><strong>Note:</strong> Air-entrainment options and parameter names vary by FLOW-3D product and version. Verify the exact settings in the documentation for the installed version. If no air-content observations are available, treat this as a sensitivity analysis rather than claiming calibrated air entrainment.</p>
</div>
<h2>Compare simulated and observed reverse roller characteristics</h2>
<table>
<thead>
<tr>
  <th>Calibration target</th>
  <th>Recommended comparison</th>
</tr>
</thead>
<tbody>
<tr>
  <td>Water surface elevation</td>
  <td>Measured and simulated longitudinal profiles</td>
</tr>
<tr>
  <td>Roller length</td>
  <td>Observed and simulated recirculation extent</td>
</tr>
<tr>
  <td>Roller location</td>
  <td>Position relative to crest/toe</td>
</tr>
<tr>
  <td>Velocity field</td>
  <td>Streamwise and vertical velocities at matching locations</td>
</tr>
<tr>
  <td>Reverse-flow region</td>
  <td>Extent and magnitude of negative time-averaged streamwise velocity</td>
</tr>
<tr>
  <td>Air entrainment</td>
  <td>Void fraction and entrainment distribution, if measured</td>
</tr>
<tr>
  <td>Jump regime</td>
  <td>Free, transitional, or submerged jump classification</td>
</tr>
</tbody>
</table>
<p>Use the same coordinate system, sampling locations, and averaging definitions for observations and simulations. Define the roller boundary reproducibly; for example, identify connected regions of negative time-averaged streamwise velocity in a specified longitudinal section.</p>
<h2>Quantify agreement</h2>
<p>The root mean square error (RMSE) for paired observations and predictions is</p>
$$
\mathrm{RMSE}=\sqrt{\frac{1}{N}\sum_{i=1}^{N}(O_i-P_i)^2}
$$
<p>where $O_i$ is an observed value, $P_i$ is the corresponding simulated value, and $N$ is the number of paired values.</p>
<p>For reverse roller length, report the relative absolute error:</p>
$$
E_L=\frac{|L_{r,\mathrm{sim}}-L_{r,\mathrm{obs}}|}{L_{r,\mathrm{obs}}}\times 100\%
$$
<p>Other useful statistics include mean absolute error (MAE) and mean bias error. Report errors for multiple hydraulic variables and operating cases rather than relying on a single statistic.</p>
<h2>Validate using independent conditions</h2>
<p>Keep calibrated settings fixed and evaluate them against measurements <strong>not used for calibration</strong>. Where feasible, test different combinations of discharge and tailwater elevation representing:</p>
<ul>
<li>Free hydraulic jumps.</li>
<li>Transitional or partially submerged jumps.</li>
<li>Fully submerged jumps with persistent reverse rollers.</li>
</ul>
<p>Identify conditions where the model performs poorly and document the limits of its applicability.</p>
<h2>Suggested calibration sequence</h2>
<ol>
<li>Assemble and quality-check hydraulic measurements.</li>
<li>Verify geometry, units, initial conditions, and boundary conditions.</li>
<li>Run a baseline FLOW-3D simulation.</li>
<li>Complete mesh-sensitivity testing and evaluate turbulence models.</li>
<li>Calibrate uncertain physical parameters such as roughness.</li>
<li>Assess air entrainment when observations support it.</li>
<li>Compare the reverse roller against measured water levels, velocities, and roller extent.</li>
<li>Quantify errors and document the final model settings.</li>
<li>Validate against independent hydraulic conditions.</li>
</ol>
<h2>Calibration checklist</h2>
<ul>
<li class="task-list-item"><input class="task-list-item-checkbox" type="checkbox" disabled/>Geometry and vertical datum verified.</li>
<li class="task-list-item"><input class="task-list-item-checkbox" type="checkbox" disabled/>Measured discharge and tailwater conditions documented.</li>
<li class="task-list-item"><input class="task-list-item-checkbox" type="checkbox" disabled/>Reference measurements and uncertainty recorded.</li>
<li class="task-list-item"><input class="task-list-item-checkbox" type="checkbox" disabled/>Model mass balance and analysis window checked.</li>
<li class="task-list-item"><input class="task-list-item-checkbox" type="checkbox" disabled/>Mesh-sensitivity assessment completed.</li>
<li class="task-list-item"><input class="task-list-item-checkbox" type="checkbox" disabled/>Turbulence-model choice justified.</li>
<li class="task-list-item"><input class="task-list-item-checkbox" type="checkbox" disabled/>Bed/wall roughness within realistic bounds.</li>
<li class="task-list-item"><input class="task-list-item-checkbox" type="checkbox" disabled/>Roller definition applied consistently.</li>
<li class="task-list-item"><input class="task-list-item-checkbox" type="checkbox" disabled/>Calibration metrics reported for multiple variables.</li>
<li class="task-list-item"><input class="task-list-item-checkbox" type="checkbox" disabled/>Independent validation completed.</li>
</ul>
<div class="tip">
<p><strong>Tip:</strong> <strong>For hazard analysis:</strong> a good water-surface match is not sufficient by itself. Confirm that the model also reproduces the <strong>direction, magnitude, and spatial extent of reverse flow</strong> relevant to the drowning hazard.</p>
</div>
