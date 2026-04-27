# Trading / Financial Pattern

Use this pattern when evaluating trading systems, financial strategies, market
edges, execution risk, backtests, capital constraints, or operational risk.

## Foundation (Q1-Q10)

- What is the goal, and how do we get there?
- What is the starting capital and what are the constraints?
- What edge are we exploiting? Is it real or imagined?
- What are the fees and how do they affect profitability?
- What is the minimum move needed to break even on a trade?
- What markets or instruments are available?
- What is the realistic daily or monthly return target?
- What is the maximum acceptable drawdown?
- What historical data is available for validation?
- What does the competition look like?

## Mechanics (Q11-Q30)

- Entry signal definition with exact rules
- Exit signal definition with exact rules
- Position sizing formula
- Stop-loss mechanics: client-side vs exchange-side
- Order types and execution strategy
- Data pipeline for prices, indicators, and account state
- Latency requirements
- State persistence and crash recovery
- Risk management rules: daily limits, consecutive losses, exposure caps
- Market regime detection

## Stress Testing (Q31-Q50)

- What happens during a flash crash?
- What if the exchange goes down mid-position?
- What if spreads widen 10x during volatility?
- What if the strategy has 10 losses in a row?
- What if fees increase?
- What if liquidity dries up on target instruments?
- What if the market regime changes permanently?
- What is the risk of ruin at current position sizing?
- How does slippage affect real vs backtested returns?
- What if API rate limits change?

## Competitive Analysis (Q51-Q65)

- Who else is running similar strategies?
- What advantages do institutional players have?
- What advantages do we have that they do not?
- Is this edge durable or will it be arbitraged away?
- What public research exists on this approach?

## Feasibility (Q66-Q80)

- Can this be backtested with available data?
- Is the backtest realistic: fees, slippage, partial fills, latency, and survivorship bias?
- What is the minimum viable version?
- What infrastructure is needed?
- What is the total cost to operate?

## Refinement (Q81-Q90)

- Which parameters are most sensitive to changes?
- What can be simplified without losing edge?
- What monitoring is needed to detect strategy decay?
- How should the strategy adapt as capital grows?

## Synthesis (Q91-Q100)

- Revised strategy with specific parameters
- Honest P&L projections: conservative, base, optimistic
- Top risks and mitigations
- Build order and phased rollout plan
