# Basic Momentum Strategy

This repository contains a simple momentum strategy that pulls historical asset data from OKX's exchange API, processes the data, calculates returns, and identifies the top 5 and bottom 5 performing assets at each time step. The strategy then tracks the future performance of these selected assets, which can be used to assess the efficacy of momentum-based trading.

## Table of Contents

- [Overview](#overview)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Details of the Strategy](#details-of-the-strategy)
- [Future Work](#future-work)
- [License](#license)

---

## Overview

Momentum strategies typically look to capture asset performance trends by identifying the highest-performing assets in a defined time frame. This strategy:

1. Pulls data from OKX via their public API.
2. Cleans and formats the data for analysis.
3. Creates a DataFrame of returns for a selected set of tradable assets (not taking into account capital constraints for larger accounts).
4. Identifies the top 5 and bottom 5 performers at each time step.
5. Tracks the future performance of these top and bottom 5 performers.


## Requirements

- Python 3.8+
- Libraries:
  - `pandas` (for data manipulation)
  - `requests` (for making API requests)
  - `numpy` (for numerical operations)
  - `datetime` (for timestamp operations)
  - `matplotlib` (for plotting data)

The OKX Public API doesn't require any authentification so if the libraries are installed that is all that is needed.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/ssineee/basic-momentum.git
   cd basic-momentum
   ```

## Usage

1. **Run the code:**  
   Preferably run the code on a Jupyter-Notebook since it is much better to visualize the data and also if you want to take a deeper look at the data.

## Details of the Strategy

1. **Data Collection**  
   The script connects to the OKX API to pull historical price data. This data is parsed and structured into a pandas DataFrame.

2. **Data Cleaning and Formatting**  
   The script cleans the raw data, handling missing values and formatting timestamps. The data is then transformed into a DataFrame containing returns for each asset in the tradable universe.

3. **Momentum Ranking**  
   Each row in the DataFrame represents returns for a specific timeframe. The script ranks the assets by performance, identifying the top 5 and bottom 5 performers for each row.

4. **Performance Tracking**  
   The strategy registers the next row’s performance of these top and bottom 5 performers, storing the results in a list.

## Possible Improvements

This basic momentum strategy can be further enhanced by:

- Adding risk management constraints, especially if using leverage as is common in crypto.
- Running the strategy with a real account to see results and identify what might be some elements that are not taken into account.
- Exploring alternative ranking metrics/factors to get better performance from our picks
- Filtering down a more realistic tradable universe. For instance a coin that has very thin order book liquidity cannot be traded with an account that has significant capital or if leverage is used, that can lead to complications in closing down a position.
- Applying transaction costs to improve the realism of the strategy, slippage and trading fees are the main trading costs.

