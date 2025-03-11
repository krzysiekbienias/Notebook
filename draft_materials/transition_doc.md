# Purpose and scope.
Trade reconciliation is a critical process in financial operations, aimed at ensuring that trade data from various systems align and discrepancies are identified and resolved. This document outlines the methodology for reconciling trades transferred from the Kronos system to the Orca system. A key objective of this reconciliation effort is to monitor various risk metrics associated with the trades, thereby enhancing data integrity and reducing the potential for financial reporting errors. By systematically comparing records from Kronos and Orca, we will establish a robust framework that supports effective risk management and promotes transparency in our trade operations. This guide will detail the procedures, tools, and best practices employed in this essential function.

# VCE Data Base

# Algorithm of reconciliation
### High-Level Algorithm for Trade Reconciliation

The reconciliation algorithm aims to ensure data consistency and accuracy between two trade populations sourced from the Kronos and Orca systems. The process is outlined as follows:

#### Input:

- **Trade Populations**: 

  - **Kronos Trades**: Data containing various trade records.
  - **Orca Trades**: Data containing a separate set of trade records.

#### Steps:

1. **Extract Clean Trade IDs from Kronos**:

   - Initiate the process by retrieving the unique `clean_trade_id` values from the Kronos trade population. This step ensures that only valid and relevant trades are considered for reconciliation.

2. **ISIN ID Extraction**:

   - Using the clean trade IDs obtained from Kronos, query the appropriate table in the TWP (Trade Warehouse Platform) to extract the corresponding International Securities Identification Number (ISIN) values. This is critical for identifying trades related to specific financial instruments.

3. **Merge with Orca Trade Population**:

   - With the retrieved ISIN values, merge the Orca trade population data. This step aligns the trades from both sources based on their related ISIN values, facilitating a direct comparison.

4. **Identify Missing Trades in Orca**:

   - Analyze the merged dataset to identify any trades present in the Kronos population that are missing from the Orca population. This step is essential to highlight discrepancies and gaps in the trade records.

5. **Compare Risk Metrics**:

   - Finally, compare key risk metrics between the corresponding trades from Kronos and Orca. This includes assessing values such as exposure, volatility, and other relevant risk indicators to ensure consistency and accuracy across both datasets.

# T-Copula method
