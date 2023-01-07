# Supply_Chain_Projects
Supply_Chain_Projects


The objective of this text is to describe a production planning process using Python to create an optimal plan to meet customer demand while minimizing total production costs.

Introduction: The master production schedule is the main communication tool between the commercial team and production. Your customers send purchase orders with specific quantities to be delivered at a certain time. Production planning is used to minimize the total cost of production by finding a balance between minimizing inventory and maximizing the quantity produced per setup.

<b>How to plan your production with Python?<b>
Scenario: You are a production planning manager in a small factory producing radio equipment that serves local and international markets. Customers send Purchase Orders (PO) to your commercial team with quantities and expected delivery dates. Your role is to schedule production to deliver on time with a minimum total cost of production that includes setup costs, production costs, and holding costs. In our example, the customer ordered products for the next 12 months.

Setup vs. Inventory Costs: The main challenges for you are reducing the average inventory on hand to minimize the storage costs and minimize the number of production setups. However, these two constraints are antagonistic. Therefore, it is difficult for you to find an intuitive way to build an optimal plan. Example 1: Minimize Inventory. In this example, you produce the exact demand quantity each month. Pros: no excess inventory. Cons: you get production set up for each month with a positive demand. Example 2: Minimize the number of production setups. In this example, you build stock to minimize the number of setups. Pros: only two production setups for the whole period. Cons: a large stock on hand that increase the inventory costs.

Conclusion: You need an optimization algorithm to balance the two constraints. Solution: You can find the source code with dummy data here: Github.

Assumptions: Let us suppose that you receive a purchase order for the next 12 months with the quantities presented in the chart above. Set up cost: 500 $. Holding cost: 1 $/unit/month. Production cost per unit: 50 $/unit. Units produced month m can be shipped the same month. Inventory costs are charged from the month m+1.

Wagner-Whitin Algorithm: This problem can be seen as a generalization of the economic order quantity model that takes into account that demand for the product varies over time. Wagner and Whitin developed an algorithm for finding the optimal solution by dynamic programming. The idea is to understand each month if adding the current month's demand quantity to past months' orders can be more economic than setting up a new cycle of production.

Forward Calculation: Start at period 1. Calculate the total cost to satisfy the demand of month 1, D(1). Period N. Calculate the total cost to satisfy the demand of month t, D(t). Look at all past orders (t=1 .. N) and find the cost for ordering for D(t) by adding the quantity to past orders D(t-1). Take the most economic option and go to t = N+1.

Backward Calculation: Start from period t = N and work backwards to find the lowest options to satisfy the demand of each D(t).

Results & Conclusion: Feel free to follow me on medium for more articles related to Data Analytics and Supply Chain Management. Forward Calculation: You should export the results of the forward calculation using a table like the one below. Period 1, if you produce for the first month demand only (D(1) = 200 units): 500$. Two first months (D(1) + D(2) = 350 units): 650$. Backward Calculation: We can use the table above
