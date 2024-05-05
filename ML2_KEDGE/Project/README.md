# ML Project  - Humanitarian supply chain network ( Indonesian Red Cross Society)

This project aims to help the Indonesian Red Cross Society (Palang Merah Indonesia, PMI) optimize its operations and improve its performance through data analytics and artificial intelligence.

One of the most important tasks of PMI is the distribution of emergency supplies to victims in affected areas during humanitarian crises. PMI operates a humanitarian supply chain network to receive supplies from suppliers and donors, store them in its warehouses during normal times, and deliver them to victims during crises. PMI's warehouse network is divided into three levels, including 1 regional warehouse, 1 provincial warehouse, and 20 district warehouses.

### Dataset Overview

![image](https://github.com/Jhonnatan7br/ML-Project--Humanitarian-supply-chain-network---Indonesian-Red-Cross-Society-/assets/104907786/b85b83ed-1f0d-40f9-82e4-c5d408f77744)

>[!IMPORTANT]
>To operate this humanitarian supply chain network, PMI must manage sourcing, transport, replenishment, and 
distribution activities. And for each type of activity, PMI has two different policies.

| Activity    | Definition                                                                            | Policy 0                                                      | Policy 1                                                    |
|-------------|--------------------------------------------------------------------------------------|---------------------------------------------------------------|-------------------------------------------------------------|
| Sourcing    | Assign a warehouse to meet a particular demand of relief supplies, move relief supplies from other warehouses to the assigned warehouse as needed. | Hierarchical sourcing: Assign the closest warehouse to meet the particular demand. If needed, the relief supplies can be moved only from upstream to downstream (from regional warehouses to provincial warehouses and from provincial warehouses to district warehouses). | Matrix sourcing: Assign the closest warehouse to meet the particular demand. The relief supplies can be moved from any warehouse to the assigned warehouse as needed. |
| Transport   | Transport relief supplies from warehouses to affected areas and delivering them to victims. | Dedicated delivery: Each transport only have one destination. | Consolidated delivery: Each transport can have multiple destinations. |
| Replenishment | Procure relief supplies from suppliers to maintain adequate inventory levels in the warehouse network. | Slow replenishment: It takes 15 days to complete the replenishment. The price of the replenishment is cheaper. | Fast replenishment: It takes 3 days to complete the replenishment. The price of the replenishment is more expensive. |
| Distribution | Decide the order of fulfillment of different demand                                     | First in first out (FIFO): The first received demand is fulfilled first. | Equity: All demands are partially fulfilled by sharing the available relief supplies among the various demands. |


PMI has developed a simulation model to simulate its operations and performance under different situations. The simulation is repeated 12,000 times, each corresponding to a specific scenario characterized by the following features:

- The sourcing, transport, replenishment, and distribution policies. (The combination of hierarchical sourcing and consolidated delivery is considered as infeasible.)
- Total demand: The total demand of the relief supplies to meet (unit: aid kit)
- Initial inventory: The initial inventory in each regional, provincial, and district warehouse (unit: aid kit)

Given a specific scenario, the simulation can output a curve over time of the percentage of demands fulfilled since the beginning of the humanitarian crisis. According to this output, the experts in PMI defined a performance indicator called readiness to evaluate the performance. The readiness ranges from 0% to 100% The higher the value, the better the performance. If the readiness is 100%, it indicates PMI is 100% ready to respond to the particular humanitarian crisis in the simulated situation.
PMI now wants to use this simulated dataset (containing 12,000 simulated scenarios) to optimize its operations and performance

| Feature                  | Description                                                                                           |
|--------------------------|-------------------------------------------------------------------------------------------------------|
| Sourcing                 | Likely represents the process of sourcing or acquiring goods from suppliers.                          |
| Transport                | Indicates the transportation activities, possibly related to moving goods between different locations.|
| Replenishment            | Represents the replenishment activities, involving restocking inventory to maintain desired levels.   |
| Distribution             | Likely represents the distribution process, involving delivering goods to customers or points of sale.|
| Total demand             | The total demand for the product or products being managed.                                           |
| Initial RW Inv           | Initial inventory level of a certain type (could be raw materials).                                   |
| Initial PW Inv           | Initial inventory level of another type (possibly work-in-progress inventory).                         |
| Initial DW Inv Total     | Initial inventory level of finished goods inventory.                                                  |
| Initial DW Inv 0-19      | Represents the initial inventory levels of finished goods across different time periods or categories.|
| Demand coverage after X hours | Likely represents the percentage of demand that can be covered after certain time intervals.         |
| Readiness (%)            | Represents the readiness of the supply chain or inventory system, indicating how prepared it is to meet demand. |

![Imagen de WhatsApp 2024-04-11 a las 15 50 13_c6d485bf](https://github.com/Jhonnatan7br/ML-Project--Humanitarian-supply-chain-network---Indonesian-Red-Cross-Society-/assets/104907786/c72b64c0-dceb-413d-867a-20a2ddcd3df7)

### Models

![Imagen de WhatsApp 2024-04-11 a las 16 19 22_613f0979](https://github.com/Jhonnatan7br/ML-Project--Humanitarian-supply-chain-network---Indonesian-Red-Cross-Society-/assets/104907786/a325e6d0-77dd-45b3-8db9-a581d446ee44)

>[!NOTE]
>This is a visualization of how could be structured the different models, but it is necessary to get into detail of different parameters to fit it well to obtain the desired target

### Model 1 readiness
For predicting the final readiness value in advance, up to 10 days after the start of a humanitarian crisis.
  - Information you can use: the policies, total demand, initial inventory, and the first 10 days demand coverage curve
  - Expected prediction: the readiness.
  - Feedforward neural networks, convolutional neural networks (CNNs), or recurrent neural networks (RNNs) like Long Short-Term Memory (LSTM) networks or Gated     
  Recurrent Units (GRUs). @Andre Kedge & @Mona Laraki 
  - URL: https://colab.research.google.com/drive/1hNhgtGZqFN0LysL-ZFstCUardq7FtKn5?usp=sharing 

### Model 2 demand coverage
For predicting subsequent demand coverage curve, up to 10 days after the start of a humanitarian crisis.
  - Information you can use: the policies, total demand, initial inventory, and the first 10 days demand coverage curve
  - Expected prediction: the demand coverage curve after the first 10 days, from the 11th day to the end of the crisis (the 24th day).
  - Deep learning architecture for time-series forecasting. Options may include recurrent neural networks (RNNs) like Long Short-Term Memory (LSTM) networks or Gated   Recurrent Units (GRUs), or more @Cristian Medina - Data Analytics  & @Mélanie Kedge 
  - URL: https://colab.research.google.com/drive/1o9TKLApndriNatjOt9NEB_EKoJW67mvK?usp=sharing 

### Extra
Models that require a shorter wait time after the start of the crisis? For example, waiting only 5 days instead of 10 days to get the prediction
