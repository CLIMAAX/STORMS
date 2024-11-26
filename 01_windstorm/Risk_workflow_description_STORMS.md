# Risk assessment for windstorm
Windstorms can cause significant damage to buildings and infrastructure, especially when structures aren't strong enough to handle the powerful forces of the storm. This workflow is designed to help identify areas where windstorms could lead to high costs and severe damage.

While projections suggest that the wind gust speed of future storms may not increase dramatically in Europe, their paths may shift northward [(Seneviratne et al., 2023)](https://doi.org/10.1017/9781009157896.013) by about 150km in Europe [(Chang et la., 2012)](https://doi.org/10.1029/2012JD018578). As a result, this analysis does not include future projections for specific locations. Instead, regions can use historical storm data from both their own location and areas to the south to prepare for potential future storms. This approach helps regions anticipate and prepare for potential future storms, ensuring they are better equipped to handle the risks.

By applying this workflow, regions can better understand their vulnerabilities and take proactive steps to protect their communities and infrastructure.

## Risk assessment methodology

This event-based windstorm risk workflow can be used to see damages of a storm by combining hazard, exposure and vulnerability. The workflow is a simplified version of the work by [Koks & Haer (2020)](https://doi.org/10.1038/s41598-020-63580-w). Here the hazard is represented by the map of the maximum 3-second wind gust during a storm. Exposure is expressed in terms of a map of assets and their maximum damage that can occur per square meter of the asset; each asset is assigned an exposure class. Vulnerability is defined as a collection of damage curves where the 3-second wind gusts are matched to a degree to which an asset would be damaged (in %).

 By combining all datasets, it is possible to assign to each asset the following information:
 - the type of asset (asset class)
 - the maximum damage of the asset (in economic terms)
 - the vulnerability curve of the asset (wind gust vs. relative damage)
 - the windspeed at the asset location during the storm. 
 
 With this information, one can do the damage calculation per asset. Based on the wind gust speed during the storm, the vulnerability curve is applied to determine to what extent is the asset damaged by this wind speed. Multiplying the maximum cost of the damage to this asset by the damage percentage results in the estimated damage by the storm to that asset. Performing this calculation for all asset locations in the region results in a damage map, that helps to determine locations that are most affected (have the highest costs of the damages).

## Datasets

### Hazard data
Using the Copernicus Climate Data store, [historical storm footprints](https://doi.org/10.24381/cds.9b4ea013) can be retrieved. Next to that, [synthetic storms footprints](https://doi.org/10.24381/cds.ce973f02) can be found that are physically realistic and are plausible representations of possible storms. These synthetic storms can be useful to create a larger overview of possible events that can affect the area in the current climate. Both datasets give the footprints of the maximum 3-second gust per 72 hours per grid cell.

### Exposure data
An example dataset that can be used in this workflow is the [LUISA Land Cover data](https://data.jrc.ec.europa.eu/dataset/51858b51-8f27-4006-bf82-53eba35a142c).  When using this dataset, we define an asset as a 50x50m grid cell with a given type of land use. Each land cover type is assigned a certain asset class that can be associated with the vulnerability curves.

Each land cover type is also assigned maximum damage value per square meter. A first estimation of the maximum damages are based on [JRC maximum damage estimates](https://dx.doi.org/10.2760/16510) per country. This data can be made more precise by using values corresponding to the local situation.

### Vulnerability data
Each asset class from the exposure dataset is associated with a vulnerability curve. The vulnerability data consists of six curves determined by [Feuerstein et al. (2011)](https://doi.org/10.1016/j.atmosres.2010.12.026). The asset classes are differentiated by the type of buildings that are mainly present in the asset. These estimate damage curves can be found in the supplied material (on GitHub).

## Output of the workflow

The outputs of this workflow are:
 - Absolute and relative damage calculation for different asset classes
 - Spatially-explicit maps of damages (in economic terms)

Storm damage is calculated by combining the vulnerability (damage) curves and the wind gust maps. For each grid point, the damage is calculated based on the windspeed, land use type, damage curves, and economic information that approximate the economic value of different land use types (this is provided in a separate Excel sheet, where the GDP of the country needs to be adjusted).

## Contributors

**Authors**:
- Ted Buskop (Deltares & Vrije Universiteit Amsterdam, IVM)

**References**:

- Koks, E.E., Haer., T. A high-resolution wind damage model for Europe. Sci Rep 10, 6866 (2020). https://doi.org/10.1038/s41598-020-63580-w

- Copernicus Climate Change Service, Climate Data Store, (2022): Winter windstorm indicators for Europe from 1979 to 2021 derived from reanalysis. Copernicus Climate Change Service (C3S) Climate Data Store (CDS). DOI: 10.24381/cds.9b4ea013 (Accessed on DD-MMM-YYYY)

- Copernicus Climate Change Service, Climate Data Store, (2022): Synthetic windstorm events for Europe from 1986 to 2011. Copernicus Climate Change Service (C3S) Climate Data Store (CDS). DOI: 10.24381/cds.ce973f02 (Accessed on DD-MMM-YYYY)

- Chang, E. K. M., Guo, Y., & Xia, X. (2012). CMIP5 multimodel ensemble projection of storm track change under global warming. Journal of Geophysical Research: Atmospheres, 117(D23). https://doi.org/10.1029/2012JD018578

- Feuerstein, B., Groenemeijer, P., Dirksen, E., Hubrig, M., Holzer, A. M., & Dotzek, N. (2011). Towards an improved wind speed scale and damage description adapted for Central Europe. Atmospheric Research, 100(4), 547-564. https://doi.org/10.1016/j.atmosres.2010.12.026

- Pigaiani, C. and Batista E Silva, F., The LUISA Base Map 2018, EUR 30663 EN, Publications Office of the European Union, Luxembourg, 2021, ISBN 978-92-76-34207-6,  https://doi.org/10.2760/503006, JRC124621.

- Seneviratne, S. I., Zhang, X., Adnan, M., Badi, W., Dereczynski, C., Luca, A. D., Ghosh, S., Iskandar, I., Kossin, J., Lewis, S., Otto, F., Pinto, I., Satoh, M., Vicente-Serrano, S. M., Wehner, M., & Zhou, B. (2023). Weather and Climate Extreme Events in a Changing Climate. In Climate Change 2021 – The Physical Science Basis: Working Group I Contribution to the Sixth Assessment Report of the Intergovernmental Panel on Climate Change (pp. 1513–1766). Cambridge University Press. https://doi.org/10.1017/9781009157896.013


