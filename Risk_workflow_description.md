# Risk assessment for river flooding

## Risk assessment methodology

This event-based windstorm risk workflow can be used to see damages of a storm by combining hazard, exposure and vulnerability. The workflow is a simplified version of the work by [Koks & Haer (2020)](https://doi.org/10.1038/s41598-020-63580-w). Here the hazard is a map with the maximum 3-second wind gust of a storm. Exposure is determined by a map in which assets are associated with maximum damage that can occur per square meter of the asset and a certain exposure class is given to the asset. Vulnerability is defined as a collection of damage curves where the 3 second wind gusts are matched to a percentage of the asset that is damad

 When overlaying the sets, all assets contain information on the type of asset class it is, the maximum damage that can occur at the asset, the vulnerability curve of the asset, and the windspeed at the asset location. With this information, one can do the damage calculation per asset. Step one is to inspect the vulnerability curve and how much of the asset is destroyed by the wind speed. This results in a fraction of the maximum damage value that occurs. Multiplying the maximum damage by the found damaged fraction results in the damage estimation of that asset. Doing this calculation for all asset locations in the region results in a map of the most affected locations.

## Datasets

### Hazard data
Using the Copernicus Climate Data store, [historical storm footprints](https://doi.org/10.24381/cds.9b4ea013) can be retrieved. Next to that, [synthetic storms footprints](https://doi.org/10.24381/cds.ce973f02) can be found that are physically realistic and thus plausible storms. These synthetic storms can be useful to create a larger overview of possible events that can affect the area in current-day situations. Both datasets give the footprints of the maximum 3-second gust per 72 hours per grid cell.  

### Exposure data
An example dataset that can be used in this workflow is the [LUISA Land Cover data](https://data.jrc.ec.europa.eu/dataset/51858b51-8f27-4006-bf82-53eba35a142c).  With this dataset, the exposed asset is a 50x50m grid cell. Each land cover type is given a certain asset class that can be associated with the vulnerability curves. 

Each land cover type is also associated with a maximum damage per square meter. A first estimation of the maximum damages are based on [JRC maximum damage estimates](https://dx.doi.org/10.2760/16510) per country.

### Vulnerability data  
Each asset class from the exposure dataset is associated with a vulnerability curve. The vulnerability data consists of six curves determined by [Feuerstein et al. (2011)](https://doi.org/10.1016/j.atmosres.2010.12.026). The asset classes are differentiated by the type of building that are mainly present in the asset. These estimate damage curves can be found in the supplied material. 

## Output of the workflow

The outputs of this workflow are:  
 - Absolute and relative damage calculation for asset classes and spatially explicit maps.
 
Flood damage is calculated by applying damage curves to the flood inundation depth maps, taking into account the local situation. For each grid point, the damage is calculated based on the windspeed, land use type, damage curves, and country-specific parameters (can be defined by the user using the provided excel sheet) that approximate the economic value of different land use types.

## Contributors

**Authors**: 
- Ted Buskop (Deltares & Vrije Universiteit Amsterdam, IVM)

**References**: 

- Koks, E.E., Haer., T. A high-resolution wind damage model for Europe. Sci Rep 10, 6866 (2020). https://doi.org/10.1038/s41598-020-63580-w

- Copernicus Climate Change Service, Climate Data Store, (2022): Winter windstorm indicators for Europe from 1979 to 2021 derived from reanalysis. Copernicus Climate Change Service (C3S) Climate Data Store (CDS). DOI: 10.24381/cds.9b4ea013 (Accessed on DD-MMM-YYYY)

- Copernicus Climate Change Service, Climate Data Store, (2022): Synthetic windstorm events for Europe from 1986 to 2011. Copernicus Climate Change Service (C3S) Climate Data Store (CDS). DOI: 10.24381/cds.ce973f02 (Accessed on DD-MMM-YYYY)

- Feuerstein, B., Groenemeijer, P., Dirksen, E., Hubrig, M., Holzer, A. M., & Dotzek, N. (2011). Towards an improved wind speed scale and damage description adapted for Central Europe. Atmospheric Research, 100(4), 547-564. https://doi.org/10.1016/j.atmosres.2010.12.026

- Pigaiani, C. and Batista E Silva, F., The LUISA Base Map 2018, EUR 30663 EN, Publications Office of the European Union, Luxembourg, 2021, ISBN 978-92-76-34207-6,  https://doi.org/10.2760/503006, JRC124621.

