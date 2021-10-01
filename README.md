# Industry-Energy-Tool (IET)
The Industry Energy Tool (IET) is a calculator developed by NREL for projecting energy efficiency and fuel switching scenarios for the U.S. industrial sector energy use and emissions at the Census Region and county-level. The IET is built on a foundation of county-level industry end use data primarily derived from facility-level emissions data and the U.S. Energy Information Administration's (EIA) 2010 Manufacturing Energy Consumption Survey.
The IET is currently comprised of modules for calculating stock turnover, and implementing changes to energy efficiency and industry energy fuel mix (i.e., fuel switching). A material efficiency module, which includes a hybrid input-output (IO) model of U.S. energy use and implementation of the RAS algorithm, has been developed, but is not yet integrated with the rest of the tool.

## Data Foundation (Base-Year Dataset)
The foundation of IET's base-year (2014) dataset is facility-level combustion energy data calculated from greenhouse gas emissions reported under the [U.S. EPA's Greenhouse Gas Reporting Program (GHGRP)](https://www.epa.gov/ghgreporting). Please see the [Industrial Heat Demand Analysis repo](https://github.com/NREL/Industrial-Heat-Demand-Analysis) for more information about this methodology. Remaining industrial energy use is estimated from various publicly-available sources, including data from EIA, U.S. Department of Agriculture, and U.S. Census Bureau. Please consult the Data Foundation directory for additional discussion of the data sources and calculation methodology.

## Greenhouse Gas Emissions (GHG)
GHG emission are calculated from projected energy use by fuel type. All non-electricity emissions are calculated using EPA default emission factors for CO2 and CH4. Electricity emission factors are based on [EPA eGRID](https://www.epa.gov/energy/emissions-generation-resource-integrated-database-egrid); [AEO 2017](https://www.eia.gov/outlooks/archive/aeo17/) grid mix projections are used to modify eGRID emission factors in future years. IET also includes the option to modifiy renewable electricity deployment by region.

## Stock Turnover
The IET approximates capital equipment stock retirements and purchases by assuming a user-specified lifetime for pre- and post-2014 equipment and assuming linear retirement. Additionally, due to difficulties of modeling industrial equipment stock (e.g., little data on physical stock, investment decisions unrelated to equipment age [c.f., [Worrell and Biermans (2005)](https://doi.org/10.1016/j.enpol.2003.10.017), [Doms and Dunne (1998)](https://doi.org/10.1006/redy.1998.0011)]), the IET takes an approach similar to EIA's National Energy Modeling System (NEMS) by using annual value of shipments as a proxy for capital stock. IET does not capture stock vintages and does not distinguish stock behavior by equipment type/end use.    

## Energy Efficiency
The IET assumes a baseline energy efficiency improvement for pre- and post-2014 stock and existing stock by industry and end use that is based on 2014 technical possibility curves (TPCs) used in the Industrial Demand Module of NEMS (see [Table 6.3](https://www.eia.gov/outlooks/archive/aeo14/assumptions/pdf/0554(2014).pdf)). Energy efficiency scenarios for post-2014 stock are implemented by scaling either state-of-the-art or practical minimum efficiency levels identified by [DOE "bandwidth studies"](https://www.energy.gov/eere/amo/energy-analysis-data-and-reports). Note that bandwidth studies do not cover all industrial sectors.

## Fuel Switching
The IET assumes linear adoption of new equipment for fuel switching by 2050. Currently only switching from combustion fuels to electricity (i.e., electrification) is caputured. Users have the ability to specifiy fuel switching by industry, end use, and/or temperature range.  

## Material Efficiency / Circular Economy
Although it is not currently integrated with the IET, a hybrid IO model (i.e., energy units for energy industry transactions and monetary units for transactions of all remaining industries) was developed to estimate the direct and indirect energy requirements of the U.S. economy. A RAS implementation is included for dynamic rebalancing. Ideally, this module will be populated with energy projections from the IET and expanded to include additional hybrid models for materials to allow exploration of the energy implications of energy efficiency and material efficiency strategies. See [McMillan (2018)](https://www.nrel.gov/docs/fy18osti/70609.pdf) for a discussion of the analysis intent.  

A new model, the [Hybrid Supply and Use Table (HSUT) Model](./HSUT_model/) has been developed as foundation to conduct input-output analysis. See the model's directory for more background and instruction on its use.
