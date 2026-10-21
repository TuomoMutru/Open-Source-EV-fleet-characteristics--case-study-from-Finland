# Open-source EV fleet characteristics model: A case study from Finland

The rapid adoption of electric vehicles (EVs) is increasing their impact on transport systems, public infrastructure, and electricity grids. As EV penetration grows, understanding the characteristics of the national EV fleet becomes increasingly important for accurately assessing charging demand, electricity consumption, flexibility potential, and future infrastructure needs. While this is important factor, EV fleet characteristics is largely unknown and many recent studies rely on heavy simplifications on this topic.

To fill this gap of knowledge, this GitHub version proposes novel open-source method to create more extensive outlook for local EV fleet characteristics. The case study is conducted in Finland, where open-source (CC BY-SA 4.0 licensed) registration dataset (Traficom, 2026) is combined with open-source (CC BY-SA 4.0 licensed) EV statistics dataset (Gaia-charge/EVDB, 2026).

The merging is done by finding the closest “BRAND_MODEL” match between registration (Traficom. 2026) and EV statistics (Gaia-charge/EVDB, 2026) data. If an EV has a direct match in the EV statistics, its specifications are used accordingly. However, some EV manufacturers have multiple vehicle variants under the same model’s name and registration data (at least in Finnish case) is not accurate enough to provide all of these specifications. In these cases, the variants are averaged over all matching “BRAND_MODEL” variants found from EV statistics. More detailed merging logic is explained visually in "EV model statistics.png".

After the preprocessing steps 91.13 % of registration data found some match with EV statistics. This resulted in 44 distinct EV brands, 299 EV models, and total of 155,910 EV matches. Because some models were combined from multiple model variants, the uncertainty of the results were measured accordingly:

U_X = (X_max - X_min) / (2 * X_median)

Where U_X is uncertainty, X_max is max value among model variants, X_min is min value among model variants, and X_median is median value among model variants.

From matched models, average uncertainty in usable battery capacity was 7.92 % and in WLTP energy consumption was 6.47 %, which both indicated rather low uncertainty. As a disclaimer, unmatched models with 100% uncertainty increased total uncertainty to 16.09% and 25.62%, respectively. Increased uncertainty from unmatched models supports to continue extending EV statistics to the unmatched EV models as a future work, to decrease total uncertainty of EV fleet characteristics.

Final important insight from Finnish case study is that top 10 EV brands has a market share of 75 % from total fleet and top 10 EV models cover 38 % of the total EV fleet. This is observed to result higher concentrations in EV statistics where dominating EV models are. These concentrations can be more seen from the visuals where distribution of usable battery capacity and WLTP energy consumption are plotted.

While proposed method is not fully perfect, it increases the accuracy of being more closer from realistic EV fleet, which can help to create fleet specific analyses on EV related studies.

I will be happy if you are interested contributing on this specific case of using this method on your areas of study. The method and data are both available with CC BY-SA 4.0 license, similarly as the datasets used for this study.

References:

- Traficom. 2026. Open data for vehicles contains registration, approval and technical information for all vehicles in use from the register maintained by Traficom. [Online]. Accessed: 28.9.2026. Available: https://opendata.traficom.fi/Content/Ajoneuvorekisteri.zip

- EVDB - Public domain EV database. 2026. Gaia-Charge. [Online]. Accessed: 28.9.2026. Available: https://github.com/gaia-charge/evdb

- Creative Commons. 2026. Attribution-ShareAlike 4.0 International (CC BY-SA 4.0). [Online]. Accessed: 20.10.2026. Available: https://creativecommons.org/licenses/by-sa/4.0/deed.en
