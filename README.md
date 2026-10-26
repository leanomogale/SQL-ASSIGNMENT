Sizwe Coffee – SQL Analysis

Project overview
Year-end review analysis for Sizwe Coffee (Pty) Ltd, a coffee roastery and wholesale supplier in Isando, Johannesburg (about 1,400 business customers, R480m revenue in FY2025, financial year ending 30 June). I recently joined as a junior data analyst and was asked to answer eight questions from Nomsa Dlamini (Financial Director) and Bongani Twala (National Sales Manager):

1. Channel revenue FY2024 vs FY2025 and growth
2. Profit and margin by product line
3. Collections performance by channel
4. Top ten customers by FY2025 revenue
5. Large Wholesale customers with no trade promotions
6. Sales rep performance against monthly target
7. Monthly revenue, month-on-month change and rolling average
8. Why gross margin fell from 34.7% to 33.0%

Dataset
Tables used: 'customers' (1,400), 'products' (23), 'sales_orders' (48,144), 'sales_lines' (168,172), 'ar_ledger' (48,144), 'reps' (18), 'trade_promotions' (640).
Joins: 'sales_orders.customer_id → customers', 'sales_orders.order_id → sales_lines', 'sales_lines.sku → products', 'customers.rep_id' / 'sales_orders.rep_id → reps', 'ar_ledger.customer_id → customers', 'trade_promotions.customer_id → customers'. Revenue lives on 'sales_lines'; channel on orders and customers agrees in every row.

Skills demonstrated
Technique                                                        Tasks
Multi-table joins                                                1–8
Aggregation and conditional aggregation ('FILTER', 'CASE')       1, 2, 3
'LEFT JOIN'+ 'COALESCE' so nobody is dropped                     4, 6
Anti-join with 'NOT EXISTS'                                      5
CTEs                                                             1, 6, 7, 8
Window functions ('LAG', rolling 'AVG', share via 'SUM() OVER')  7, 8
Date handling ('DATE_TRUNC', 'DATEDIFF')                         3, 7

Key insights
For Nomsa (Finance)
- Revenue grew 8.8% in both channels: Wholesale R308.2m → R335.4m, Subscription R132.8m → R144.6m. Total went from R441.0m to R480.0m.
- The margin fall (34.7% → 33.0%) is entirely a mix effect. Line margins are flat, but Bulk Commercial (19.9% margin) grew 46.4% and rose from 25.0% to 33.6% of revenue. Applying FY2024 mix to FY2025 margins gives 34.7%.
- Collections is a Wholesale problem: 68.7 days average to settle vs 3.8 for Subscription, and R87.8m outstanding across 3,454 open invoices vs R0.75m for Subscription. Wholesale days to settle rose from 56.9 (FY2024 invoices) to 84.1 (FY2025).
- House Blend earns the most profit (R107.1m); Single Origin earns the highest margin (44.3%).
- Revenue is seasonal: December is the quietest month (R29.9m in 2023, R32.6m in 2024) and revenue peaks around June–July.

For Bongani (Sales)
- Halvane Retail Group is the biggest account by far at R38.4m in FY2025 (about 11.4% of revenue), over ten times the next customer.
- Three large Wholesale customers have had no trade promotions: Umhlanga Fresh 108 (R6.2m), Ridgeway Foods 308 (R4.4m) and Kalahari Kitchen 42 (R4.4m).
- 17 of 18 reps are above their monthly target. Karabo van Wyk is highest at 250.3% and Johan Naidoo is the only one clearly under at 77.6% (Sipho Steyn is at 98.0%).
