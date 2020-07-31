{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# MODULE 2 FINAL PROJECT\n",
    "by Dolci Sanders"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " ## Introduction\n",
    "\n",
    "For my project, I decided to explore Air BNB prices in Cape Town, South Africa. After gathering data from Inside AirBNB (https://insideairbnb.com) as well as data from Wazimap (https://wazimap.co.za) based on available census data. I was able to download the data and manipulate it in numbers before transforming it to a .csv for integration into the AirBNB data. For this project, I hope to be able to use modeling to precict prices of AirBNB's for the Cape Town, South Africa market. By collecting this data, I hopenbe able to answer the following questions.\n",
    "\n",
    "\n",
    "1. Is there a statistically significant difference in price closer to tourist attractions?\n",
    "2. Does the crime rate in certain wards influence the prices of Air BNB's in the area? \n",
    "3. Does the minimum night stay have a statistical significance on the price? \n",
    "4. Can I make a model that predicts price better than the baseline? \n",
    "\n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## File Structure\n",
    "\n",
    "- listings.csv from Inside AirBNB 2020 (AirBNB data)\n",
    "- SA_crime_ward.csv (crimes per 10,000 by ward)\n",
    "- Final_Cape_Town_AirBNB.ipynb \n",
    "    - Cleans data, merges, and creates new columns based off of the received data\n",
    "    - Feature engineering of new features\n",
    "    - Statistical testing and Visualizations\n",
    "    - Baseline Model\n",
    "    - Test models with RMSE focused scoring "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Data Collection & Data Cleaning\n",
    "\n",
    "I browsed many data sets before landing on data provided by Inisde AirBNB. The data turned out to be challenging with less useful features than I had anticipated, and I was able to find some 2011 crime statistics data from the last census in South Africa to supplement it. \n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Data Cleaning and Feature Engineering\n",
    "\n",
    "After cleaning the data, I started playing with different features I engineered to help predict Air BNB costs. \n",
    "\n",
    "   - The data set had used partially ZAR and partially USD in the price catergory, so after researching where the break down was happening, I was able to convert a portion to dollars, and found that the conversion rate for Air BNB was 14.23 ZAR/USD rather than the current conversion rate of 16.5 ZAR/USD. \n",
    "   - Some ward crime statistics were also not provided, and I was able to inpute the mean of the surrounding wards to create a best guess for the four missing wards. \n",
    "   - Referencing AirBNB I was also able to edit rather than drop data by checking the lisitngs online if a value seemed off. This helped me edit zeros as well as find errors that stemmed from the original listing such as prices of $0 or minimum night stay of 1125. \n",
    "    \n",
    "    \n",
    "  - Limited minimum nights to 14 nights or less as some seemed to be 30, 90, rr 365 day stays, which are not helpful to predict vacation airbnb rentals.\n",
    "  - Limited price_usd to between $20 - $2500.\n",
    "    "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "My target for this project is price, more specifically price_usd_log. \n",
    "On the right is the price before it is made into a log function. On the right, it is still skewed, but somewhat more normally distributed. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "<img src=\"skewed_price.png\"><img src=\"normalized_price.png\">"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Baseline Model"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Once the data was cleaned to the point of running a baseline model, I used the DummyRegressor to create a mean and median based baseline model. The original scores for the baseline model based on median were RMSE: 548.7970187273733 r2:  -0.04000143686100621"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Statistical Tests and Visualizations "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "    1. Two Sample T-test\n",
    "    2. ANOVA\n",
    "    3. CHI-Sqared\n",
    "    "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Crime per 10,000 People shown above shows the layout of capedown. The costal areas have between 100-300 crimes per 10,000. This affects price of the airbnb to some significance as per a Two Sample Test included in the Final_Cap"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "<img src=\"Crime_bright.png\"><img src=\"price_map.png\">"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "   "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "   "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Price by Minimum Nights \n",
    "This graph was not exactly what I expected, and there was large amount of expensive houses at 11 nights minimum.\n",
    "I found this to be pretty odd. \n"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "<img src=\"Price_Min_Night.png\">"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Final Models"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "    1. Poly 3 \n",
    "        Testing RMSE: 519.8636117866749\n",
    "        R2: .9950 (The part of the variation that is explained by my engeineered features did increase!)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "    2. Lasso\n",
    "        Testing RMSE:   515.0013547581824\n",
    "        This ended up being the best model. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "    3. Poly 3 through Lasso\n",
    "        Testing RMSE:  518.5546707977804"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "    4. Linear Regression\n",
    "        Testing RMSE:  519.8636117866749"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Compared to baseline: \n",
    "    RMSE 548.7970187273733 R2:  -0.04000143686100621"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    " "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Conclusions "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "This model proved challenging to work with as the amount of features was somewhat smaller than I had hoped. In combination with crime statistics, it did seem to be enough to help bring the baseline RMSE down $33 but pushed the R2 up to .995! I would say for the accuracy of the model, I would advise more data would be needed to accurately predict the pricing of an AirBnBs in Cape Town such as bedrooms and amenities. The crime rates in Cape Town do seem to play a major role in where AirBnBs are located as well as having Entire house/apt listed rather than a shared room. "
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.7.6"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 4
}
