# Anomaly Extractor<br>

An algorithm to automatically vectorize anomalies caused by archaeological features in magnetograms and calculate a number of statistical parameters.<br/>
The tool is being developed by the German Archaeological Institute.<p/>
**See an article about the tool:<br/>**
Goldmann, L. and Komp, R. (2025), The Anomaly Extractor—An Open-Source GIS-Tool for Object-Based Image Analyses of Large-Scale Geomagnetic Data.<br/>
Archaeological Prospection.<br/>
https://doi.org/10.1002/arp.1987
## Installation
  In QGIS open *Processing Toolbox* and choose *Add Model to Toolbox ...*<br/>
  Tested QGIS Version: 3.34.8<br>
## Usage
### Input parameters
   * **input_threshold**<br/>
      Formula to define at which threshold (usually in nT) anomalies will be vectorized:<br>
      - 1.1) Default: if(abs("A@1")>5,1,0/0) = +/- 5 nT<br>
      - 1.2) Example 1: if("A@1"<-5,1,0/0) = -5 nT<br>
      - 1.3) Example 2: if("A@1">5,1,0/0) = +5 nT  <br>
        Notes:
        - The cipher "5" in these examples is the relevant term, which defines the desired theshold (to be modified according individual needs).<br>
        - The term "0/0" is an expression for "NULL".<br>

   * **input_extent**<br>
      Optional, used to run algorithm on a part of a dataset only:
      - 2.1) Default: No input ([0,0,0,0]) = uses the entire input raster.<br>
      - 2.2) Possible inputs are manual coordinates, mask layers, map canvas extent or manually drawn rectangles.
    
   * **input_holesize**<br>
      Optional, deletes interior holes/rings within a vectorized polygon that are smaller than the given value in the unit of the chosen CRS:
      - 3.1) Default: 1 (usually m²)<br>
      - 3.2) Delete all rings: 0<br>
      - 3.3) Option: Float, 0 - 100000 <br>
    
   * **input_raster**<br>
      The input raster has to be a GeoTiff holding numeric measurement values, usually in nT.<br>

### Outputs
 * **ExtractedAnomalies**<br/>
    Extracted anomalies as single polygon features.<br>
## 
Algorithm author: Rainer Komp/Lukas Goldmann 2024-08-01<br/>
Help author: Lukas Goldmann 2024-08-01<br>
Algorithm version: 1.6.4 2024-08-01<br>
