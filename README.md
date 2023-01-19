# Pairs_Trading_v1 Algorithm

### Overview

1. Data Collection:
   - Get 2 years of 1m data from polygon.io data provider.
   - Clean, match timings of data, and merge close prices.
   
  2. Pair Identification:
     - Get correlation matrix and pick a (ideally same scale) pair with high correlation.
     - Run augmented Engle-Granger two-step cointegration test.
     - If p-value less than critical-value, the close price series of the pair is cointegrated.
     - Run augmented Dickey-Fuller Test for each pair, spread, and ratio to figure stationary series. Use for next step.
     <p align="center">
     <img src = 'https://github.com/Jim2E/pairs_trading_v1/blob/main/plots_ouput/correlation_heatmap_output.png' width = "580" background-color: 'white'>
     </p>
  3. Z-score Strategy:
      - Standardize either ratio or spread, depending on AD fuller test from last step, and get z-scores.
      - Plot z-scores and identify key levels where spread or ratio diverge then converge to mean spread or ratio.
      - When key-level is crossed, long/short pair A and short/long pair B respectively.
      - Close positions when ratio or spread return to mean(0).
      
  <p align="center">
  <img src = 'https://github.com/Jim2E/pairs_trading_v1/blob/main/plots_ouput/ratio_z_scores.png' width = "580">
  </p>
  
  4. View Performance:
     
<p align="center">
  <img src = 'https://github.com/Jim2E/pairs_trading_v1/blob/main/plots_ouput/Open_Closes_of_AAVEUSD_Trades.png' width = "580">
</p>
<p align="center">
  <img src = 'https://github.com/Jim2E/pairs_trading_v1/blob/main/plots_ouput/collateral_over_time.png' width = "580">
</p>
