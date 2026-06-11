## [HOME PAGE](../)

# <p style="text-align: center;">Categorization of Forest Loss within the Adirondack Park </p>

<b> Goal:</b> To create a map that illustrates the spatial distribution of forest loss within the Adirondack Park and categorize those areas based on their current cover type. 

![Image not loading](../../assets/images/adk_forest_loss_map.png)
[Full size image](../../assets/images/adk_forest_loss_map.png)

## Methodology
### I. Data Acquisition & Cloud Computing
Primary forest change data was sourced from the Hansen Global Forest Change (v1.12) dataset. Using Google Earth Engine, the study area was constrained to the Adirondack Park Boundary. The forest loss cells were isolated and extracted to a local TIFF file at the native 30-meter resolution
### II. Raster Processing & Classification
The forest loss raster was re-calculated to an integer type where 1 = "Documented Forest Loss" and 0 = "No Change/No Data". The resulting raster was converted to a vector polygon layer and "No Change/No Data" areas were removed. Vecor processing was achieved using PostGIS queries.
### III. Land Cover Integration and Vector Analysis
NLCD (National Land Cover Database) raster data was extracted within the park boundary using extract by mask in QGIS and converted to a polygon layer. A PostGIS Query was used to dissolve both layers into the minimum number of features. 
### Spatial Synthesis
The vectorized land cover data was clipped to within the boundaries of forest loss polygons. Finally, current cover types were grouped according to the table to below:

<table>
  <thead>
    <tr>
      <th style="font-weight: bold; border-bottom: 2px solid black;">NLCD Cover Type</th>
      <th style="font-weight: bold; border-bottom: 2px solid black;">Simplified Cover Type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Woody Wetlands</td>
      <td rowspan="8" style="vertical-align: middle; text-align: center; border-left: 1px solid #ccc;">Regeneration</td>
    </tr>
    <tr><td>Shrub/Scrub</td></tr>
    <tr><td>Open Water</td></tr>
    <tr><td>Mixed Forest</td></tr>
    <tr><td>Grassland/Herbaceous</td></tr>
    <tr><td>Evergreen Forest</td></tr>
    <tr><td>Emergent Herbaceous Wetland</td></tr>
    <tr><td>Deciduous Forest</td></tr>
    <tr>
      <td style="border-top: 1px solid black;">Pasture/Hay</td>
      <td rowspan="2" style="vertical-align: middle; text-align: center; border-top: 1px solid black; border-left: 1px solid #ccc;">Agriculture</td>
    </tr>
    <tr><td>Cultivated Crops</td></tr>
    <tr>
      <td style="border-top: 1px solid black;">Developed, Open Space</td>
      <td rowspan="2" style="vertical-align: middle; text-align: center; border-top: 1px solid black; border-left: 1px solid #ccc;">Developed</td>
    </tr>
    <tr><td>Developed (All Intensities)</td></tr>
    <tr>
      <td style="border-top: 1px solid black;">Barren Land</td>
      <td style="vertical-align: middle; text-align: center; border-top: 1px solid black; border-left: 1px solid #ccc;">Barren</td>
    </tr>
  </tbody>
</table>



