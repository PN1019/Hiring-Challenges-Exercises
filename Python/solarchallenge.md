# Solar Power Plant Energy Generation Case Study 



![image](https://user-images.githubusercontent.com/16081831/140916676-d3df24a7-43e7-4db8-a327-bffa53605d9c.png)



## Data : https://github.com/PN1019/Hiring-Challenges-Exercises/blob/main/Python/solar_generation_energy_price.csv
![image](https://user-images.githubusercontent.com/16081831/140917478-73316fbd-b84f-41ff-a7fa-3b8d13a90c5a.png)
## Problem Statement :
An indicative year’s worth of hypothetical solar generation time series and associated wholesale energy market prices are provided in CSV format. Assume that these are representative of the whole project life (term). A list of assumptions are provided below to assist with the calculations.
### Capital Costs (CAPEX):
  - Solar:
     * \$1.28/W installed;
     * \$5M connection costs (includes transformers, switch gear, etc.);
- Storage:
  * \$300,000 / MWh for batteries installed;
  * \$15,000 / MW for inverters installed;
  * \$200,000 / container which houses 2MWh of batteries;
  * \$5M connection costs (includes transformers, switch gear, etc.);
### Operational Costs (OPEX)
- Solar:
  * Annual OPEX at 2% of CAPEX
- Storage:
  * Annual OPEX at 2% of CAPEX
### Escalation rates
- CPI:2.5%
- Discount rate (weighted average cost of capital): 9%
### Efficiencies
- Storage round trip efficiency (Charge – Discharge): 88%
- Parasitic loads: Assume none
- Storage degradation: Assume 1% of capacity per year. ### Project Life
- Assume 20 year project life
- No terminal value

Based on the provided data and assumptions do the following tasks:

1. Calculate Levelised Cost of Energy (LCOE) and Internal Rate of Return (IRR) for the solar project alone;
2. Calculate the volume weighted average market revenue for the solar project, and compare this against the LCOE;
3. Devise a model that utilises energy storage to shift solar energy to higher price periods
      a.  Note that degrees of freedom include storage sizes on a MW and MWh basis
4. Calculate new volume weighted average market revenues and compare to changed LCOE (due to storage addition) and new market revenue IRR’s and comment.


![image](https://user-images.githubusercontent.com/16081831/140917662-0e483e7c-f396-4c73-b3df-e719db60b4e4.png)

## Solution: https://github.com/PN1019/Hiring-Challenges-Exercises/blob/main/Python/solarenergygenerationpriceanalysis.ipynb

![image](https://user-images.githubusercontent.com/16081831/140917893-821d2c74-1213-498f-a278-d82864e3b0fa.png)

### Solution also published on Kaggle: https://www.kaggle.com/purvanahar/solarenergygenerationpriceanalysis 
