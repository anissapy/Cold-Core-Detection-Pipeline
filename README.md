# Cold-Core-Molecular-Detection-Pipeline

The "Cold Core Molecular Detection Pipeline" is a script written in the Python programming language, which can be used to make molecular detections in cold, dense sources (e.g., prestellar and starless cores). This workflow makes use of the Pyspeckit package (https://pyspeckit.readthedocs.io/en/latest/) to perform Gaussian fits of each detection line. We also use Matplotlib, Numpy, Pandas, and Math Python libraries/packages. I compiled it myself in the summer of 2024, for my REU project under mentorship from Dr. Samantha Scibelli at the National Radio Astronomy Observatory (NRAO). 

While this pipeline was specifically written for the use of Yebes 40m data with a broad frequency range from 30 - 50 GHz, it can be adapted for any single-dish spectral line data in a similar format. This pipeline uses ASCII/txt files (spectral line data), finds peaks above 3 sigma of main-beam temperature, cleans the data, and matches 3 sigma lines to SPLATALOGUE line information within 1.5 MHz of each line frequency. The pipeline then performs a Gaussian fit of each 'matched' line and produces a diagnostic plot and fit information compiled into an Excel spreadsheet for further analysis.

In this workflow, the user has the option to mask bad channel ranges after manually inspecting the data. The user also has the ability to customize the minimum FWHM (linewidth) and desired vlsr (source velocity) range for their data. I originally used this pipeline to compile molecular inventories of 15 different prestellar cores, so it is made to be efficiently used for multiple sources.

Before running the pipeline, the following files are required:

1.) spectral line data (ASCII or txt files)

2.) SPLATALOGUE molecular information file (https://splatalogue.online/#/advanced)
  - Ensure that the frequency is in MHz units
  - Include species, chemical name, frequency, measured frequency, CDMS/JPL intensity, resolved QNs, E_L in cm^-1 units, E_U in cm^-1 units, E_L (lower energy) in K units, E_U (upper energy) in K units, Linelist (JPL, CDMS, etc.), Sij, Aij (Einstein A), Upper State Degeneracy (g_u)
  - The user can create their own constraints on the lines included in your SPLATALOGUE file, to limit detections that are energetically favorable for their sources

The SPLATALOGUE file I used for my detections of Yebes 40m (30-50 GHz) data is included in this repository for reference purposes.
