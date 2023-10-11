# retail_uplift
*University final project*

Project based on [X5 Retail Hero: Uplift Modeling for Promotional Campaign competition](https://ods.ai/competitions/x5-retailhero-uplift-modeling). The main goal was to *estimate* CATE - conditional average treatment effect, rank clients using it and predict average responce to treatment for 30% of most promicing clients.

## What is calculated there and why is it important?
Depending on reaction to communication, you can divide clients into four groups:
+ *Persuadabes* will not perform target action without treament and will perform it with treatment
+ *Sleeping dogs*, or The *Do not disturbs* will perform target action without treatment and will not perform with it
+ *Sure Things* will perform target action with or without communication
+ *Lost Causes* will not perform target action with or without communication

Non-specific classification algorythms can successfully select individual who will perform needed action (Percuadables and Sure Things), but in certain cases the second group might be pretty large, and communicating will be ineffective and costly.

Uplift modelling allows us to pick individuals who will react on treatment. It does so by comparing the reaction of a certain individual on treatment and its absence. You can describe it with the **uplift coefficient**. It's value is close to 1 if the individual will react positive on treatment (Persuadabes), close to -1 if the reaction wil be negative (Sleeping dogs), and 0 if individual will not change its' mind about performing target action (Sure things *and* Lost Causes).

The main problem of this value is that it is purely theoretical. *You cannot treat and not treat the individual at the same time.*

Here are some great articles on a problem and basic methods of solving it: [Habr articles by MTS company (rus)](https://habr.com/ru/companies/ru_mts/articles/485980/), [scikit-uplift documentation (en)](https://www.uplift-modeling.com/en/latest/user_guide/introduction/comparison.html). I used [Class Transformation model]([https://www.uplift-modeling.com/en/latest/user_guide/models/two_models.html#two-dependent-models](https://www.uplift-modeling.com/en/latest/user_guide/models/revert_label.html)) (which ended up giving the best results) and [Two Dependent model](https://www.uplift-modeling.com/en/latest/user_guide/models/two_models.html#two-dependent-models) approach.

## Datasets description
The data provided (not included in the repository, but can be found at competition page):
+ **Client data**: unique code, age, first issue and first redeem date
+ **Product data**: weight, brand and vendor code, mark if it is alcohol or shops' own trademark production, and many other coded fields
+ **Purchases data**: products purchased, their amount and price, store id, amount of points received and spent during transaction
+ **Experimantal group data**: client code, flag for whether there was communication, flag for if client made purchase or not

The result is evaluated uplift of each client from the test dataset.

## Instruments used
+ **[pandas](https://pandas.pydata.org/), [numpy](https://numpy.org/)** to import, export & handle data
+ **[matplotlib](https://matplotlib.org/), [seaborn](https://seaborn.pydata.org/)** to draw cool diagrams (including labeled heatmap)
+ **[sklift](https://www.uplift-modeling.com/en/latest/)** (scikit-uplift) to model & estimate everything and visualize specific coefficients
+ **[LightGBM](https://lightgbm.readthedocs.io/en/stable/)** to use as classifier in uplift model
+ **Jupyter Notebook** to run it all
