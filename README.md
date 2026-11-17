# Glow & Co. | Brand Action Performance (2023-2025)

**Live dashboard:** [Tableau Public](https://public.tableau.com/app/profile/felipe.lima5576/viz/GlowCo-BrandActionPerformance/BrandActionPerformance)

> **Synthetic data.** Glow & Co. is a fictional premium beauty retailer in Brazil, inspired by my retail background. No real company data was used.

## Business question

The commercial director set one rule: every brand action (Brand Day, Weekend Event or Product Launch) must sell at least **+20% over the same period of the previous year**. She wants to know:

1. Which brands and stores met the target in 2024 and 2025?
2. Are the actions bringing real profit, or just sales with discounts?
3. Where should she act first?

## Data

- 4,710 rows, one per week, store and brand (Jan 2023 to Dec 2025)
- 6 stores (São Paulo x2, Rio de Janeiro, Belo Horizonte, Curitiba, Brasília), 5 brands and 4 categories
- Columns: week, store, city, state, brand, category, event type, units, gross sales, discounts, net sales, COGS and new loyalty members (all values in R$)

## What I did (Tableau Public)

- **Action flag:** a calculated field that marks each week as "Action" or "No action" based on the event type.
- **Averages, not sums:** months have 4 or 5 Mondays, so monthly sums created artificial peaks. Using average weekly sales removed them.
- **Year-over-year growth** of average weekly net sales, separately for action weeks and no-action weeks. No-action growth is the natural growth baseline.
- **Discount rate** = discounts / gross sales.
- **Net margin** = (net sales - COGS) / net sales.
- **Gross profit (R$)** = net sales - COGS.
- **Design:** everything is greyed out except what needs attention (orange = brand, red = store).

## Findings

- **Target:** only Pure Lab hit +20% in action weeks in 2024 (22.6%). In 2025 no brand did; Vineyard Botanics came closest (16.7%).
- **Pure Lab:** in 2024 its action weeks grew 14.2 p.p. more than its no-action weeks; in 2025 they grew 2.6 p.p. less. The effect had worn off.
- **Profit:** in 2025, action weeks earned more gross profit than no-action weeks in 4 of 5 brands, although the margin was 2-3 p.p. lower (10% discount instead of 4%). Terra Hair is nearly tied (R$ 3.0K vs R$ 2.8K).
- **Velvet Studio:** action-week sales fell 17.7% in 2025. Its discount rate rose to 18% (10% for the other brands), and gross profit in action weeks (R$ 3.8K) was lower than in no-action weeks (R$ 4.4K).
- **Batel store:** the only store with falling sales in 2025 (-2.3% in action weeks, -1.9% in no-action weeks), after a strong 2024 in action weeks (+20.0%). It also had the slowest gross profit growth of the six stores in all five brands.

## Limitations

- The year-over-year comparison uses averages of action weeks, not the same calendar weeks matched one to one.
- Product Launch has few rows, so its numbers are fragile.
- The data does not include the cost of running the actions (staff, set-up, gifts), so "action weeks earn more gross profit" does not mean they are profitable overall. Where the gap is small (Terra Hair), it may flip.
- The data shows what changed, not why. Explanations such as store location or competition would require other data.
- The dataset is synthetic.

## What I learned

- **Totals can be misleading.** My first monthly chart showed peaks and drops that were not real: some months had five Mondays, which meant one extra week of sales. Switching to average weekly sales removed them and changed my conclusion about growth: every month grew year over year, not just seven.
- **A year-over-year number combines two things.** An action week that grew 30% also includes the business's natural growth, so I used no-action weeks as a baseline and compared the gap in percentage points.
- **Sales alone do not answer "is it worth it?"** Action weeks sell more, but they keep a smaller share of each sale as profit. I had to look at discount rate, margin and gross profit in R$ together.
- **Big in R$ does not mean best.** Morumbi sells the most, but when I ranked stores by growth, Batel was the one in trouble. I treated my explanations about store location and competition as hypotheses to investigate, not as findings, because the data cannot test them.
- **Tableau skills I practiced:** calculated fields, table calculations (percent difference and a nested rank), reference lines, and dashboard layout and formatting.

## Next steps

- Repeat the analysis in SQL on the same dataset.
- Pair action weeks with comparable weeks of the previous year.
- Add action costs to measure real profitability.
