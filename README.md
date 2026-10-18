# Marketing Channel Revenue Attribution

A data analysis case study: given a log of 13,303 customer touchpoints across seven marketing channels, work out
how much revenue each channel is responsible for and when customers engage.

## Data

`data/touchpoints.csv`: one row per touchpoint, with customer ID, session ID, timestamp, marketing channel and
revenue. The log covers 10,000 customers, some of whom touch several channels. Each converting touchpoint is
worth a fixed €1,000, as specified in the brief.

## Results

Total attributed revenue: **€1,157,000** from 1,157 converting touchpoints.

| Channel | Revenue | Share |
|---|---|---|
| Direct (non-brand) | €448,000 | 38.7% |
| SEO (brand) | €366,000 | 31.6% |
| Referral | €189,000 | 16.3% |
| SEO (non-brand) | €137,000 | 11.8% |
| Adwords / SEA (non-brand) | €15,000 | 1.3% |
| Referral (non-brand) | €1,000 | 0.1% |
| Social media organic (non-brand) | €1,000 | 0.1% |

Other findings:

- Direct and brand SEO traffic bring in 70% of revenue; paid search and social barely contribute.
- About 70% of touchpoints happen in the afternoon and evening, and only 5% at night (01:00–07:00).
- Sunday generates the most revenue of any day of the week.

## Approach

1. **Cleaning:** parsed the tab-separated export, repaired rows that were split across two lines, cast types
   and set empty revenue to zero.
2. **Exploration:** touchpoints per customer and per channel, and revenue vs. non-revenue touchpoints.
3. **Time analysis:** touchpoints and revenue by time of day and by day of week.
4. **Attribution:** each converting touchpoint is credited to its own channel (single-touch attribution).

## Limitations

With a fixed revenue per conversion and single-touch credit, the results reflect conversion counts rather than
real order values, and they ignore the earlier touchpoints in a multi-channel journey. A multi-touch model
(linear, time-decay or Markov-chain attribution) would give a fairer picture of channels such as SEA that
often start a journey without closing it.

## Running the notebook

```bash
git clone https://github.com/houcem24/marketing-revenue-attribution.git
cd marketing-revenue-attribution
pip install -r requirements.txt
jupyter notebook revenue_attribution.ipynb
```

## Context

Take-home data analysis task from a job interview.

## License

[MIT](LICENSE)
