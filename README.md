# retail_uplift
*University final project*
Project based on [X5 Retail Hero: Uplift Modeling for Promotional Campaign competition](https://ods.ai/competitions/x5-retailhero-uplift-modeling). The main goal was to predict CATE -- conditional average treatment effect, rank clients using it and predict average responce to treatment for 30% of most promicing clients.

## What is calculated there and why is it important?
Depending on reaction to communication, you can divide clients into four groups:
+ *Persuadabes* will not perform target action without treament and will perform it with treatment
+ *Sleeping dogs*, or The *Do not disturbs* will perform target action without treatment and will not perform with it
+ *Sure Things* will perform target action with or without communication
+ *Lost Causes* will not perform target action with or without communication
Non-specific classification algorythms can successfully select individual who will perform needed action (Percuadables and Sure Things), but in certain cases the second group mamight be pretty large, and communicating will be ineffective and costly, so... 

## Datasets description
The data provided (not included in the repository, but can be found at competition page):
+ **Client data**: unique code, age, first issue and first redeem date
+ **Product data**: weight, brand and vendor code, mark if it is alcohol or shops' own trademark production, and many other coded fields
+ **Purchases data**: products purchased, their amount and price, store id, amount of points received and spent during transaction
+ **Experimantal group data**: client code, flag for whether there was communication, flag for if client made purchase or not

The result is evaluated uplift of each client from the test dataset.
