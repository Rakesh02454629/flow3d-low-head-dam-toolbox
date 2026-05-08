\## 3. Data and Model Setup



\### Example Description



This training example demonstrates a FLOW-3D CFD modeling workflow for evaluating hazardous hydraulic conditions at a low-head dam. The example focuses on identifying reverse-roller behavior, high-velocity zones, free-surface response, and flow patterns relevant to drowning-potential assessment.



\### Geometry Preparation



o   Obtain detailed weir dimensions from as-built drawings, design blueprints, or site surveys.

o   Key parameters: crest shape, length, height, slopes, steps (if any), pier and abutment layout, and venting systems.



Before importing the geometry into FLOW-3D, check the following:



\- Confirm that the geometry uses the correct unit system.

\- Confirm that the geometry scale is correct.

\- Confirm that the upstream and downstream directions are correctly oriented.

\- Check whether the structure and channel surfaces are properly represented.

\- Check whether the geometry has gaps, overlaps, or unrealistic features.

\- Simplify unnecessary details that may increase computation time without improving hydraulic interpretation.



\### Bathymetry and Terrain Preparation



•  Conduct a bathymetric survey of the upstream and downstream channel to capture the channel bed topography and flow parameters such as discharge, velocity and depth.

•  Use ADCP for bathymetric survey and LiDAR for overall terrain. Very high-resolution DEM is required for flow simulation. Survey channel banks and surrounding terrain to define computational boundaries and capture natural topography of channel (Fig-5).

•  Take two cross-sections (2 and 3) just upstream and downstream of LHD, and third (1) and fourth (4) cross-section upstream and downstream from 2 and 3. The distance between cross sections are decided based on the channel bank and bed irregularities (any presence of sudden changes) and upstream and downstream boundary conditions for CFD modeling.



If bathymetry, DEM, or cross-section data are included, the terrain should be prepared before creating the FLOW-3D model. Recommended checks include:



Processing LiDAR DEM in ArcGIS Pro compatible for FLOW-3D



Check the LiDAR DEM file resolution and coordinate system. Now the dem is added to Arc GIS pro/GIS where, all cross section from bathymetric surveys are added on DEM layer. Then following steps are followed to get final DEM for simulation work (Fig-6).

•	Convert point data cross section to point shape file.

•	Create TIN using all point shape files.

•	Create channel mask polygon

•	Extract by mask  

•	Mosaic to new raster

•	Export raster as ASCII file.

Check:

\- Confirm horizontal and vertical units.

\- Convert elevations to the unit system used in FLOW-3D.

\- Remove obvious survey errors or unrealistic bed elevations.

\- Interpolate between surveyed cross sections if needed.

\- Clip or mask the terrain to the modeling domain.

\- Export the terrain or bed surface in a format compatible with the geometry workflow.





\### Create Stereolithography file (.STL) for simulation in Flow3D



Prepare a 3D solid model of the weir geometry using AutoCAD, Civil 3D, or Sketchup etc., in a scale. Incorporate all relevant structural features such as the weir crest, side walls, training walls, and stilling basin. Similarly, generate the terrain surface using DEM or surveyed topographic data. Note that once both the weir and terrain models are complete, convert them to stereolithography (STL) format using the CAD software or equivalent tools to ensure compatibility with FLOW-3D. Ensure the geometry is watertight and free of gaps or overlaps before exporting (Fig-7). 



Note:While preparing the solid geometry for FLOW-3D in CAD software, ensure that the User Coordinate System (UCS) is aligned as follows and unit of prepared geometry matches unit of FLOW-3. 

•	Z-axis: Upward (vertical direction)

•	X-axis: Flow direction (longitudinal)

•	Y-axis: Channel width (lateral)

This alignment matches FLOW-3D’s coordinate system and ensures correct geometry orientation during import.

Then import as STL file(s) into FLOW-3D. Assign appropriate geometry types: subcomponent, fluid region boundary, etc. (Fig-8 \& Fig-9)



\### Assign floating/moving object properties (Moving object setup if required to simulate trapped floating body)

Coefficient of restitution= Vr(after collision)/Vr(before collision)

e = 1: perfectly elastic body

e = 0: body stick together

Used in modeling to model how objects rebound

Coefficient of friction = resistance to sliding body



\### Computational Domain



The computational domain should include:



\- Sufficient upstream length for inflow development.

\- The dam crest or hydraulic-structure region.

\- The downstream apron or stilling-floor region.

\- Sufficient downstream length to capture the reverse roller and recovery zone.

\- Adequate vertical clearance above the expected water surface.



\### Mesh Setup



Mesh refinement should be concentrated near:



\- The dam or weir crest.

\- The nappe or overflow region.

\- The toe of the structure.

\- The reverse-roller region.

\- The downstream recirculation and energy-dissipation zone.

\- Any floating-body or moving-object region, if included.



A coarser mesh can be used farther from the hydraulic structure to reduce computational cost. Multiple mesh such as mesh block, mesh planes, nested block can be used for refinement in particular region. 



\### Boundary Conditions and Initial conditions



Boundary conditions are the known conditions such as flow depth or discharge that allow the discretized forms of the governing flow equations (mass, momentum, and energy) to be solved at each grid node. In FLOW-3D, upstream boundary conditions can be defined either by specifying flow depth or velocity or discharge, depending on the nature of the channel geometry and flow uniformity. For the downstream boundary, a flow depth or pressure boundary condition is typically assigned to allow the model to compute backwater effects and ensure numerical stability, especially in subcritical flow conditions.

Here, briefly given about BC for containing block mesh (Fig-14 a):

Inflow: specify velocity components or volume flow rate or Pressure. For pressure, it is assigned as stagnation pressure with fluid elevation/height.

Outflow: specify zero gradient, pressure, or elevation.

Wall: Generally, Ymin and Ymax are automatically set as symmetry boundaries for closed domains. If wall shear stress is to be neglected (i.e., assuming frictionless conditions), assigning symmetry is appropriate. Moreover, using symmetry boundaries helps reduce computational cost in cases with symmetrical flow conditions or in 2D simulations.

Bottom (bed): Assign bottom Zmin as wall  

Top surface: Assign Zmax   as stagnation pressure with fluid fraction as zero.

Note: For nested block mesh, symmetry boundary conditions are applied for all boundaries (Fig.14 b).

For the initial conditions, the upstream water level is set up to the weir crest elevation. For the global initial condition (Fig-15 \& Fig-16), the tailwater depth is specified to represent the downstream flow conditions.



Typical boundary conditions are summarized below.



| Boundary | Typical Condition | Notes |

|---|---|---|

| Upstream | Flow rate, velocity, or pressure boundary | Based on measured or design discharge |

| Downstream | Tailwater depth, pressure outlet, or rating curve | Should represent downstream hydraulic control |

| Bottom | Wall boundary | Represents bed and structural surfaces |

| Side walls | Wall or symmetry boundary | Depends on channel/domain representation |

| Top | Atmospheric/free-surface condition | Allows free-surface flow development |





\### Assigning fluid types and their properties:



Assign fluid as water with its details from material library (Fig-17).





\### Global Settings:



It consists of units, temperature, reference pressure, details of file, start and end time of simulation. The end time of simulation should be such that the desired flow gets completely developed (Fig-18).



\### Physics



In Physics, gravity z components can be assigned to -9.81m/s2. Then viscosity and turbulence model for fluid flow should be as Renormalized group (RNG) model to account for fluid motion (Fig-19). Similarly, wall shear stress calculation can be made active to account for shear stress developed at boundary surface as shown. Furthermore, moving object model is set up where collision model can be made active for simulating trapped floating body(Fig-20).



\### Output : Here output variables are selected as per our requirement



\### Solver settings/Numerics: This is set as default.



\### Favour: In FLOW-3D, FAVOR™ means:



Fractional Area/Volume Obstacle Representation



It is used to represent solid geometry inside the computational mesh without requiring the mesh to exactly follow the shape of the object.



What FAVOR does



FAVOR calculates how much of each mesh cell is occupied by solid geometry and how much remains open for fluid flow.



\### Running the Simulation





