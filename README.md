Link to complete Jupyter notebook: https://github.com/joshdailey99/used_car/blob/main/prompt_II.ipynb

## Project Background

This project is a practice application that is part of the UC Berkeley ML/AI Professional Certification coursework.

The assignment prompt given was as follows:

* In this application, you will explore a dataset from Kaggle. The original dataset contained information on 3 million used cars. The provided dataset contains information on 426K cars to ensure the speed of processing. Your goal is to understand what factors make a car more or less expensive. As a result of your analysis, you should provide clear recommendations to your client—a used car dealership—as to what consumers value in a used car.

* To frame the task, throughout these practical applications, we will refer to a standard process in the industry for data projects called CRISP-DM. This process provides a framework for working through a data problem.

### CRISP-DM Framework

#### Business Understanding

A car dealership’s objective is to correctly estimate fair-market listing prices for used vehicles. This is necessary to support business decisoin-making with respect to acquisition bids, retail pricing, trade-in offers, and markdown cadence.

Our data analysis objective is to develop a predictive function f(X)→log(price) from vehicle attributes (nominal/ordinal categoricals like fuel, drive, type, odometer_bin; and numerics like model year, odometer miles), using a train/test split and optimizing generalization error (MSE on the log scale).

We will compare three modeling families:

* a multiple linear regression with One-Hot encoding as an interpretable baseline;

* a polynomial regression (degree sweep) to capture any nonlinearities and interactions; and

* a Ridge-regularized linear regression with a cross-validated alpha sweep.

Deliverables should include the best model selection and feature effect estimates that will translate the model outputs into pricing and acquisition recommendations for decision-makers in the used car business.

#### Data Understanding
* Reviewed data for missing values
* Reviewed categorical data for distribution of enumaration values
* Reviewed numeric data for illogical/extreme values

#### Data Preparation
* Dropped extraneous columns
* Dropped rows with na values (when row impact is small)
* Replaced nan with "unknown" string value (when row impact is large)
* Regrouped categorical data
* Dropped numeric outliers
* Constructed new features (e.g. odometer bins)

#### Modeling 
* Created and fitted 3 models
  * multiple linear regression with One-Hot encoding as an interpretable baseline;
  * a polynomial regression (degree sweep) to capture any nonlinearities and interactions; and
  * a Ridge-regularized linear regression with a cross-validated alpha sweep.

#### Evaluation
* Selected model with lowest test MSE (log-price) value
  * Polynomial w/degree 3
* Analyzed marginal impact of coefficients within categorical attributes
* Analyed marginal impact of changes to numeric values
  * Increase in car age
  * Increase in 10K mileage
  * Clean Title boolean
     
#### Deployment (Findings and Recommendations)

##### Fuel

Finding: 

- Diesel shows about a +89–90% premium vs hybrid/electric (largest fuel spread in your table).

Recommendation:

- Pricing: Price diesel units assertively; price hybrids/EVs more competitively unless you have local-specific demand.

##### Condition

Finding: 

- Roughly +78% spread from salvage → new; condition is a major price driver.

Recommendation:

- Reconitioning ROI: Approve reconditioning that credibly moves a car up a condition rung if expected uplift > recon cost.

- Pricing: Feature “Like New / Excellent” prominently; price fair/salvage units to clear.

##### Cylinders

Finding: 

- About +51% spread between 8+ cylinders vs ≤4 cylinders.

Recommendation:

- Inventory Mix: Favor V8 trucks/SUVs

##### Type (Body Style)

Finding: 

- Around +36% spread truck vs sedan.

Recommendation:

- Acquisition: Tilt inventory toward trucks if local market demand absorbs them; likewise constrain sedans unless they move quickly.

##### Drive

Finding: 

- About +29% 4WD vs FWD.

Recommendations:

- Prioritize 4WD/AWD in cold/rural markets; redistribute FWD to urban stores where they sell better.

- Pricing: Highlight 4WD in titles/photos; set tighter prices on FWD to drive velocity.

##### Transmission

Finding: 

- ~+9% manual vs automatic (small but present).

Recommendation:

- Segmentation: Price manuals confidently for sport trims (coupe, convertibles); otherwise treat cautiously (smaller buyer pool).

##### Paint Color

Finding: 

- Only about +5% total spread across all colors (small effect).

Recommendation:

- Acquisition: Don’t pay up just for color; use it as a tie-breaker.


##### Clean title (≈ +30.8% premium)

Finding: 

- For two otherwise identical vehicles, the model predicts that a clean title will list for about 30.8% higher than a non-clean title. Equivalently, a non-clean title implies an expected price that is about 23.5% lower than a comparable clean-title vehicle.

Recommendations:

- Acquisition / trade-ins: Only take non-clean titles when the acquisition discount ≥ ~24% versus an equivalent clean unit.  Consider that this will imply slower sales cycle.

- Merchandising: Call out “Clean Title” prominently in listings and photos; make it a headline feature.


##### Vehicle age (≈ −8.97% per year)

Finding:

- Keeping all other attributes the same, an additional year of age is associated with an average 8.97% drop in predicted price—roughly 0.75% per month.

Recommendation:

- Implement a time-based markdown of about 0.5–0.75% per month on aging units to stay ahead of depreciation and carrying costs.

##### Mileage (≈ −1.72% per 10,000 miles)

Finding: 

- For two otherwise identical vehicles, every additional 10,000 miles reduces predicted price by about 1.72% on average (≈ 0.172% per 1,000 miles; on a $25,000 car that’s ~$430 per 10k miles or $0.043 per mile).

Recommendation:

- Acquisition / trade-ins: When comparing two candidates, pay extra for the lower-mileage unit up to this %.






