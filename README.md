# G4++: nuclear physics lab on your laptop 

A NO-CODE BROWSER  FRONT-END FOR GEANT4 SIMULATIONS

---
<br>

This software emerged from my efforts in teaching nuclear physics at the Central University of Karnataka. Some of the intriguing experiments in nuclear physics, which yield significant outcomes, often lose their appeal due to a lack of contextual understanding. Students may struggle to grasp the reasons behind certain experimental methods.

While classroom demonstrations effectively convey ideas and engage students in active learning, conducting practical demonstrations for nuclear physics can be challenging due to time constraints, complex setups, or safety concerns. To address these issues, I developed a desktop application called Simple. This tool allowed students to simulate particle interactions and understand how particles propagate through various materials.

*Know more about Simple:*  
<a> https://github.com/deepaksamuel/simple  </a>


Simple was integrated into the nuclear physics lab curriculum, serving as a valuable aid in teaching essential concepts. However, its reliance on specific Linux versions prevented students from using their own laptops for simulations. Moreover, it was incompatible with smartboards running Windows, hindering classroom demonstrations.

To overcome these limitations, I envisioned creating a browser-based front-end for simulations, eliminating the need for software installation and ensuring accessibility with just an internet connection. Despite my initial lack of expertise in web design, tools like ChatGPT and Gemini proved invaluable in simplifying the development process. The outcome of this endeavor is G4++.

G4++ aims to streamline Geant4 simulations, enabling students to grasp nuclear and particle physics concepts effortlessly. In addition to its educational benefits, G4++ facilitates the generation of datasets crucial for machine-learning projects in nuclear physics. This data also serves as a practical resource for teaching data analysis and statistics, essential skills in today's data-driven era.

I invite your support and eagerly await your feedback on this project. Your suggestions will be invaluable as we continue to refine and improve G4++. 

Please write to deepaksamuel@gmail.com for any help, suggestions or comments!

## Using G4++

- Signin: Only Google accounts are allowed for the time-being.
- Pricing: Free of cost 
- Limitations: 
    - Maximum particles: 50000
    - Tracks available for visualization: First 100 tracks only
    - Physics list: Only major reference lists
    - Geometry: Only Cube, Sphere (hollow) and Cylinder (hollow)

## After signing in
You will see a empty scene with a menu bar and a side bar. 

## World settings [`Project`]
All experiments take place inside a hall or a room. You can imagine the `World` to be a similar place inside which all you detectors, targets and beams are present. Ideally, you should start by changing the settings of the World. This is done on `Project` tab on the side bar.
### Physics list:
You should select a physics list that suits your application. If you don't know what that means, leave it to the default value. If you want to study radioactive decays, you can select the ones with `_HP` extension. For more details visit: https://geant4-userdoc.web.cern.ch/UsersGuides/PhysicsListGuide/html/reference_PL/index.html

### World size:
Set your world (cube) size to an optimal value such that it encompasses all the things in your simulation. If your detector or any other object is outside the World, the simulation will fail. Making the world volume too big might result in slow simulations. 

### Magnetic field:
Set this to an optimal value if you want to study particle propagation in magnetic fields.

### World material:
`G4_Galactic` is the name for Vaccum. The other alternative is `G4_AIR`. 

```
As a first step to check if everything works, set the world material to `G4_AIR` and click on `Run --> Shoot Particles` on the top menubar. You should see some particle tracks.
``` 

## Adding Geometries [`Add`]
Right now, you can only three types of geometries:  

    - Box (cube)  
    - Cylinder (hollow 0.001 mm thickness)  
    - Sphere (hollow 0.001 mm thickness)    

This is done by clicking on the `Add` on the top menubar and then on `Mesh`. 

Once you add a geometry, you should see that appearing on the scene. Objects in the scene appear on the `Scene` tab on the sidebar.
---
### Setting properties of a Geometry
On the `Scene` tab, clicking on a geometry will automatically show new tabs

    - Object
    - Geometry
 
**Object tab:**  
Sets the position, rotation and material of the selected object. Scaling is disabled for the timebeing. 

**Record data:**   
In the `Object` tab, enabling `Record data` will make the simulation store the values of the position [mm], time [ns], energy [MeV] and momentum directions when any particle cross the object.

**Geometry tab:**  
In the  `Geometry` tab, you can set the dimensions (size, in mm) of the selected object.

---

### Setting the Gun properties [`Gun`]
In any nuclear physics experiment you will have a source of particles. The properties of this source can be set in the `Gun` tab in the sidebar.

You can either use a particle source or an ion source (for studying radioactive decay). Remember for radioactive decays, the physicslist should be one with a `_HP` extension.

**Particle source**
Enable the `Particle source` button and choose any particle like `Alpha` or `electrons` etc.    

**Particle source position**  
You can set the position of the particle source (in mm) by setting this value.


**Particle source direction**  
You can set the direction in which the particles from the source move in this section. For example 0, 0, -1 will make the particles move in the `-z` direction.


**Particle source shape**  
- Point: All the particles start from the same point
- Rectangular/Circular/Elliptical: Particle positions are uniformly distributed on a rectangular/circular/elliptical plane
    - Adjust the plane settings in the `Plane` field.
- Cube/Cylinder/Shpere: Particle positions are uniformly distributed inside the volume of a Cube/Cylinder/Sphere

**Particle source size**  
This is the parameter used to determine the size if the shape is not a point source.
TBD: the labels have to be upated accordingly

**Angular distribution**
This can be used to spread the angular distribution of the sources to mimic real world scenarios. Use the Phi, Theta and Sigma to modify the distribution parameters

**Energy spectrum**
- Monoenergetic: all particle will have the same energy as the first parameter (minimum) in Energy (min/max) field. 
- Lin: Spectrum will be a linear function of energy, slope and inctercept can be modified in the spectrum parameters. 
- TBD: spectrum parameters labels to be modified
- Pow: Spectrum will be a power law function of energy, use spectrum parameters to control settings.
- Exp: Spectrum will be a exponential function of energy, use spectrum parameters to control settings.
 
 **Polarization**  
 Not used.

**Number of events (particles)**  
To adjust the number of particle to be shot, change the number in the `Events` field.

**Simulating ion sources / radioactive sources**  
Disable the `Particle source` field. This will make the source a ion source Choose the mass number and atomic number of the element in the ion A/Z field. For example, 60 27 will simulate the radioactive decay of Cobalt. 

---
### Starting your simulations  

Click on Run --> Shoot Particles and wait for few seconds until you see your tracks. The progress is displayed on the top right side of the menubar. AS soon as the simulations are over, you will see the tracks of the particles appear on the screen. Due to computation over head, only the first 50 tracks are shown.

---

### Gettting your datasets [`Data`]
On the sidebar, after your simulations are over, if any of your geometries have the `Record data` flag enabled, the data will be shown here in this table.

You can also download the dataset for advance analysis offline.

--- 
### Plotting [`Plot`]

On the sidebar, after your simulations are over, if any of your geometries have the `Record data` flag enabled, the data will be temporarily stored. Histograms of the data members in the dataset can be plotted.

TBD: Advanced plotting ...

---

# List of experiments

## 1. Scattering of alpha particles by gold foil: Rutherford experiment

### Goal

To study the propagation of alpha particles in matter and analyse the angular distribution due to scattering by alpha particles.

### Setup

Place a very thin gold foil in the path of alpha particles. Place a detector on the other side to detect the particle positions and analyze the data to get the angular distribution.

- Gun Settings: 

    - Particle source: Enabled
    - Paricle: Alpha
    - Position: 0,0,0 
    - Direction: 0,0,-1
    - Shape: Point source
    - Spectrum: Monoenergetic
    - Energy [MeV]: 6, 6
    - Events: 10000

- World settings:
    - Physics list: FTFP_BERT
    - Size (mm): 10, 10, 10 
    - Mag field: 0, 0, 0
    - World material: G4_AIR

- Geometries:
    - Box (Gold foil)  
        - Position (mm): 0, 0, -1.0
        - Rotation: 0, 0, 0
        - Material: G4_AU
        - Record data: No
        - Width, Height, Depth: (1,1,0.01) mm 
    - Box (detector)  
        - Position (mm): 0, 0, -4.0
        - Rotation: 0, 0, 0
        - Material: G4_AIR
        - Record data: Yes
        - Width, Height, Depth: (1,1,0.01) mm 

Run and Shoot particles to see the tracks and get the data. You cannot see the back scattering as you need a minimum of 10000 events and the visualization is only for the first 50 tracks.

Activities:
- Plot the angular distribution of the alpha particles
- Change the particle energy and see at what energy the foil stops them
- Analyze the intensity of particles as a function of target thickness
- Change the Gold foil to other materials and repeat the analysis

You can download the alpha-scattering.json file in this repository and open it using the file menu to get all these settings.  You can then click on `Shoot Particles` to start the simulations.

---

## 2. Spectrum of Co 60
### Goal

To study the energy/particle spectrum of Co-60 and the spectrum of beta-particles, study end-point energy
### Setup

Place a Co-60 source at the centre and place a spherical dectector that encloses such that particle emitted in all 4pi directions can be detected.

- Gun Settings: 

    - Particle source: Disabled
    - Ion A/Z: 60, 27
    - Position: 0,0,0 
    - Direction: 0,0,0
    - Shape: Point source
    - Spectrum: Monoenergetic
    - Energy [MeV]: 0, 0
    - Events: 10000

- World settings:
    - Physics list: FTFP_BERT_HP
    - Size (mm): 10, 10, 10 
    - Mag field: 0, 0, 0
    - World material: G4_AIR

- Geometries:
    - Sphere (detector)  
        - Position (mm): 0, 0, 0
        - Rotation: 0, 0, 0
        - Material: G4_AIR
        - Record data: Yes
        - Radius: (4) mm 

Run and Shoot particles to see the tracks and get the data. If you now plot the energy spectrum, you should see two distinct peaks at 1.1732 MeV and 1.3325 MeV which corresponds to two gamma emission. You can also see the beta spectrum at the lower energies

Activities:
- Plot the globtime variable and check if you can get the half-life of Co-60 from this plot (5.2714 years)
- Download the data and plot the energy spectrum of beta alone.
- Check what type of neutrinos are present and plot the energy spectrum of neutrinos alone.
- Do you see any correlations between the neutrino energy and the electron energy? 
- Calculate the ratio of electrons to gammas in the enetire sample.

You can download the Co-60.json file in this repository and open it using the file menu to get all these settings. You can then click on `Shoot Particles` to start the simulations.

## 3. Measurement of nuclear radius: Hofstadter experiment
## 4. Proton propogation in matter: Bragg peak analysis
## 5. Neutron physics experiments:
## 6. Air shower propagation
## 7. Sampling Calorimeters and energy measurement using magnetic fields


### Goal

To study the propagation of charged particles in magnetic field and measurement of energy using sampling calorimeters

### Setup

Place 5 Iron plates seperated by some Air gap. Shoot muons of a certain energy from the top. Setting the magnetic field to about 1 T, you will observe the particles to take up a curved trajectory with the extent of curvature depending on the energy and the strength of the magnetic field.

- Gun Settings: 

    - Particle source: Enabled
    - Particle type: Mu+ or Mu-
    - Position: 0,200,0 
    - Direction: 0,-1,0
    - Shape: Point source
    - Spectrum: Monoenergetic
    - Energy [MeV]: 1500, 1500
    - Events: 100

- World settings:
    - Physics list: FTFP_BERT
    - Size (mm): 1000, 1000, 1000 
    - Mag field (gauss): 0, 0, 10000
    - World material: G4_AIR

- Geometries:
    - Box  (5)
        - Position (mm): 0, 0, 0 and clone it to produce the others
        - Rotation: 0, 0, 0
        - Material: G4_Fe
        - Record data: No
        - Size: (500, 16, 500) mm 

Run and Shoot particles to see the bending tracks of muons. Visualize the effect of magnetic field and energy of the particle on the curvature of the tracks. You can also shoot mu- instead of mu+ and observe how the curvature changes. 

Observe the curvature for protons.

You can download the sampling-calorimeter.json file in this repository and open it using the file menu to get all these settings. You can then click on `Shoot Particles` to visualize the tracks.

## 8. Muon decay and lifetime measurement
To study the muon decay scheme and to measure its lifetime.

### Setup

Place a muon source at rest and detect the final state particles from its decay.

- Gun Settings: 

    - Particle source: Enabled
    - Particle type: mu-
    - Position: 0,0,0 
    - Direction: 0,0,0
    - Shape: Point source
    - Spectrum: Monoenergetic
    - Energy [MeV]: 0, 0
    - Events: 10000

- World settings:
    - Physics list: FTFP_BERT
    - Size (mm): 10, 10, 10
    - Mag field (gauss): 0, 0, 0
    - World material: G4_AIR

- Geometries:
    - Sphere  (detector)
        - Position (mm): 0, 0, 0
        - Rotation: 0, 0, 0
        - Material: G4_AIR
        - Record data: Yes
        - Radius: 4 mm 

Run and Shoot particles to see the final state particles from the decay. Download the dataset to perform basic analysis

Activities:
- Check the particles in the final state
- Plot the globtime variable for electrons only and fit a exponential function to obtain the lifetime of the muon

You can download the Co-60.json file in this repository and open it using the file menu to get all these settings. You can then click on `Shoot Particles` to start the simulations.

You can download the muon-lifetime.json file in this repository and open it using the file menu to get all these settings. You can then click on `Shoot Particles` to visualize the tracks.

## 9. Designing a simple kalman filter for track fitting

## 10. Study of plastic scintillators

more suggestions welcome!















