Course: CS220 – University of Wisconsin–Madison (Spring 2024)
Project: P12 Analyzing Stars and Planets
Submitter: nwray2
Partner: jjgartner

**Overview
In Project 11, we delve deeper into the exoplanet and star dataset introduced in Project 10. We perform various data manipulations, outlier removal, and recursive file searches to complete an end-to-end analysis of exoplanets and their host stars. By exploring equilibrium temperatures, orbital mechanics, and stellar properties, we investigate which (if any) planets might plausibly support human habitation in the (far) future.

Learning Objectives
Data Analysis:

Build on the dataset parsed in Project 10
Visualize and interpret scatter plots (Kepler's Third Law, Stefan-Boltzmann, HR diagram, etc.)
Remove outliers and validate physical laws from the data
Recursion:

Recursively traverse a directory (broken_data) to locate and read JSON files containing exoplanet mappings
Functions & Namedtuples:

Create namedtuples Star and Planet to store relevant attributes
Write helper functions (get_surface_gravity, get_distances_to_star, get_liquid_water_distances, etc.) to derive planetary conditions
Visualizations:

Generate scatter plots for star classification, temperature-luminosity relationships, and more
Compare density and luminosity across Red Giants, White Dwarfs, and Neutron Stars
Planet Habitability:

Combine criteria (surface gravity, distance from star, surface temperature range) to identify potentially habitable exoplanets
Project Structure
Your directory layout should look like this (simplified):

bash
Copy code
p11/
├── p11.ipynb                  # Main Notebook
├── p11.py                     # Script (generated by jupytext)
├── public_tests.py            # Testing scripts
├── expected_plots.json        # Reference for autograder plot checks
├── data/                      # Data directory from P10
│   ├── planets_1.csv
│   ├── planets_2.csv
│   ├── ...
│   ├── stars_1.csv
│   ├── stars_2.csv
│   ├── ...
│   └── mapping_*.json
└── broken_data/               # Directory containing split-up mappings for 'planets_5.csv'
    ├── k2s.json
    ├── others.json
    ├── kepler/
    ├── toi/
    └── ...
Important: Make sure the file structure is exactly as stated in the assignment instructions. Using os.path.join for file paths is mandatory to avoid cross-platform issues.

Dependencies and Setup
Python 3.7+
Jupyter Notebook or JupyterLab
matplotlib (for plotting)
json (built into standard library)
collections (namedtuple)
csv, os, math, statistics (standard library modules)
If you’re working on your own environment (e.g., local machine, Anaconda, or virtualenv), ensure you have the needed libraries:

bash
Copy code
conda install matplotlib
# or
pip install matplotlib
Running the Project
Clone / Download this repository to your local machine:

bash
Copy code
git clone https://github.com/<YourUsername>/p11-analyzing-stars-and-planets.git
cd p11-analyzing-stars-and-planets
Open Jupyter:

bash
Copy code
jupyter notebook
Then open p11.ipynb in your browser.

Run All Cells:

Go to Kernel > Restart & Run All.
This ensures that all code cells execute from top to bottom.
Check Outputs:

Review scatter plots for Kepler’s Third Law verification, the Stefan-Boltzmann law checks, the Hertzsprung–Russell diagram, etc.
Verify that the questions are answered (e.g., which exoplanets might be “habitable”).
Submit:

The provided grader.export cell creates a ZIP file for Gradescope submission.
If you worked with a partner, add them via “Add Group Member” on Gradescope.
Key Functions
The project requires implementing (or copying from P10) several core functions:

star_cell, planet_cell:
Utility functions to parse rows from CSV data.

get_stars, get_planets:
Creates dictionaries/lists of Star and Planet namedtuples from CSV and JSON mappings.

get_all_paths_in(directory):
Recursively enumerates all paths in a directory, ignoring hidden files (.DS_Store, etc.) and sorting them in reverse alphabetical order.

get_surface_gravity(planet):
Computes the ratio of planetary surface gravity relative to Earth.

get_distances_to_star(planet):
Returns the perihelion and aphelion distances based on orbital eccentricity and semi-major axis.

get_liquid_water_distances(planet):
Determines a star’s habitable zone boundaries from star’s stellar_luminosity.

get_surface_temperatures(planet):
Calculates the min/max possible surface temperatures from the planet’s equilibrium_temperature and estimated albedo range.

We then compose these functions to filter exoplanets that might be in a habitable zone given gravity, distance, and temperature constraints.

Key Observations
Kepler’s Third Law: Verified for subsets like GJ 9827 planets by comparing orbital period squared with semi-major radius cubed.
Stefan-Boltzmann: Relationship between insolation_flux and (equilibrium_temperature)^4 visualized; outliers removed for clarity.
Hertzsprung–Russell Diagram: Plots stellar_luminosity vs. stellar_effective_temperature, with color and size mapped to stellar_age and stellar_mass.
Habitability Criteria: Combining surface gravity, orbital distances, and estimated temperatures pinpoints a small subset of potentially habitable planets (e.g., certain Kepler exoplanets).
**
