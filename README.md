S&OP Planning Workbook: Capacity vs Demand for Three Departments
Business question

If monthly capacity changes by plus or minus 10%, how much sales is lost, and how much does storing extra stock cost?

Data
Source: Dunnhumby “The Complete Journey” transaction data (about 2.6 million rows), reduced in Python to a monthly table.
Scope: three departments: GROCERY, DRUG GM, and PRODUCE. KIOSK-GAS and MISC SALES TRAN were excluded because their units do not match their prices.
Period: 26 four-week planning periods. Weeks were grouped as (WEEK_NO - 1) // 4 + 1.
Price basis: average selling price per department and period (sales divided by units).
Assumptions

Capacity, holding rate, and scenario change are assumed, not observed.

Assumption	Value
Monthly capacity, GROCERY	15,000 units
Monthly capacity, DRUG GM	3,000 units
Monthly capacity, PRODUCE	4,000 units
Holding rate	2% of stock value per period
Scenario change	-10%, 0%, +10%

Target stock cover (0.5 periods) is documented in the workbook but not used by any formula.

Results

Base case (0%)

Department	Shortfall (units)	Lost revenue	Holding cost
GROCERY	1,806,755	$3,368,489	$74.54
DRUG GM	276,547	$824,576	$40.07
PRODUCE	218,136	$379,210	$75.01

Sensitivity: lost revenue by scenario

Department	-10%	0%	+10%
GROCERY	$3,438,539	$3,368,489	$3,298,439
DRUG GM	$846,956	$824,576	$802,196
PRODUCE	$396,706	$379,210	$361,714

Totals

Scenario	Lost revenue	Holding cost
-10%	$4,609,872	$102.42
0%	$4,572,275	$190.02
+10%	$4,534,375	$276.82

Adding 10% capacity recovers about $35,000 to $70,000 of lost revenue per department, and adds about $87 of holding cost in total.

Recommendation

Capacity is the binding constraint. Almost every period is short of capacity, so storage cost is small, and the sales recovered by extra capacity are far larger than the storage cost it adds. The real decision is whether the cost of adding capacity (labour, equipment, contracts) is less than the lost revenue it recovers. That cost is not modelled here.

Limitations
Capacity values are assumptions, not observed data.
Lost revenue uses average price, so it is an estimate.
Holding cost counts storage only, not the cost of adding capacity.
Target stock cover is documented but not used.
No lead times, supplier constraints, or minimum order quantities.
Four-week periods, not calendar months.
Two years of data from one retailer.
Files
SOP_P[S&OP Planning.xlsx](https://github.com/user-attachments/files/34460005/S.OP.Planning.xlsx) : Inputs, Demand, Calculations, Dashboard
[sop_demand_monthly (1).csv](https://github.com/user-attachments/files/34460097/sop_demand_monthly.1.csv) : monthly export from Python
[S&OP_planning.ipynb](https://github.com/user-attachments/files/34460090/S.OP_planning.ipynb) : export code
