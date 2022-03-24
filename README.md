# Spatial Tools and Utilities

### The United Kingdom postcodes to British National Grid References

> File: [postcode_to_british_national_grid.ipynb](postcode_to_british_national_grid.ipynb)

> CSV and Parquet files can be generated using `postcode_to_british_national_grid.ipynb` notebook.

Maps UK postcodes to British national grid references and produces parquet and CSV files containing 100, 50, 20, 10, 5, 1km grid references for each postcode.

Output has the following structure:

| Postcode   |     lat |       lon | 100km_grid   | 50km_grid   | 20km_grid   | 10km_grid   | 5km_grid   | 1km_grid   |
|:-----------|--------:|----------:|:-------------|:------------|:------------|:------------|:-----------|:-----------|
| XX0 1XX    | 50.1234 | -0.123456 | XX           | XXXX        | XX00        | XX00        | XX00NW     | XX1234     |
| XX012XX    | 50.1234 |  0.789456 | XX           | XXXX        | XX00        | XX00        | XX00NE     | XX1234     |


### British National Grid to Easting and Northing Converter

> File: [bng2en.py](bng2en.py)

> _Adapted to Python from the original Perl code by Ben Soares for EDINA national datacentre._

**Sample Usage:**
```bash
> python bng2en.py NZ20NE SW
425000, 505000
```

### Pandas utility to map UK postcodes to British National Grid

> File: [postcode_to_national_grids.py](postcode_to_national_grids.py)

Map UK postcodes to British National Grid (100, 50, 20, 10, 5, 2*, 1km grid
references) and coordinates (as WGS 84) in  `lat` and `lon` columns. This file depends on the output of `postcode_to_british_national_grid.ipynb` (in parquet format) which contains grid references indexed by postcodes.

> _💡 Works with pandas series and dataframes._

> \* 2km grid is not a standard ONS grid. Therefore returning 2km grid references is optional. These can be generated by merging two consecutive 1km grids horizontally and vertically. 2km grid references follow 1km grid reference naming convention where easing and northing numbers are always odd.


## Resources

- https://digimap.edina.ac.uk/help/our-maps-and-data/bng/
- https://getoutside.ordnancesurvey.co.uk/guides/beginners-guide-to-grid-references/

## License

Required data to run scripts and notebooks are subject to the following licenses:

- Contains OS data © Crown copyright and database right 2019-2022
- Contains Royal Mail data © Royal Mail copyright and database right 2019-2022
- Source: Office for National Statistics licensed under the Open Government Licence v.3.0

Shared code and notebooks licensed under MIT License.

© 2022 - Bubo.AI