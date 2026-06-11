**PROJECT DETAIL REPORT:FUN(D) RAISING- STARTUP FUNDRAISING SIMULATION**

# 1\. General Information (Group Footprint)

Project **FUN(D) RAISING**This isn't just a simulation game; it's a complex educational (EdTech) tool designed to address practical challenges in corporate finance and behavioral psychology. You play the role of a project founder, managing metrics like funding progress and transparency, and persuading investors to achieve goals through each phase. The game is suitable for economics students, startup enthusiasts, or anyone who wants to learn while playing and play while learning about crowdfunding. The product helps transform dry formulas into practical decision-making reflexes.

**Project information sheet:**

|     |     |
| --- | --- |
| Criteria | Detail |
| **Product name** | FUN(D) RAISING |
| **Slogan** | "When you have funds you have fun" |
| **Group code** | G04 |
| **Repository** | [Link GitHub G04](https://github.com/FTU-Legacy-62/G04) |
| **Demo Link** | This will be updated after the final assignment is submitted. |
| **Class** | NHA408E(2526-2)GD2.01 |
| **Instructor** | Assoc. Prof. Dr. Phan Tran Trung Dung |

**List of team members:**

1.  **Vu Bach Duong** – 2312380808
2.  **Kim Hye Jin** – 2312380803
3.  **Ha Bao Khanh** – 2314380702
4.  **Nguyen Ngoc Minh** – 2313380019
5.  **Ngo Thi Diem Phuc** – 2312380804

**_Overall_**_:_In modern financial education, the biggest risk is the gap between theory and practice. FUN(D) RAISING acts as a tactical "buffer zone," where mistakes in capital structure or confidence management can be identified and corrected without jeopardizing the actual survival of the business.

# 2\. The Problem the Team Wants to Solve

The current situation reveals a severe "information asymmetry" between founders and investors. Students and early-stage startups often master valuation formulas but lack the "survival instinct" to understand how financial indicators interact with market sentiment.

- **Challenge analysis:** Connecting operational indicators (Gross Margin, Burn Rate, Runway) with psychological variables (FOMO, confidence, risk appetite) often requires a very high price in cash or years of hard-earned experience.
- **Affected parties:** Finance students need practice in a high-pressure environment, and early-stage founders often enter their first funding round with tactical naivety.
- **So What?:** A lack of practical experience is more dangerous than a lack of theoretical formula. An unrealistic valuation or a lack of transparency regarding capital structure is a leading cause of startup failure in the first funding round. This project addresses that gap by transforming knowledge into strategic reflexes.

# 3\. Target Users

Identifying the target audience helps optimize the depth of simulation scenarios, ensuring both challenge and educational value.

- **User segmentation:**
    - **Finance students:** A low-risk practice environment is needed to receive immediate, quantitative feedback.
    - **Pre-seed/Founder:** It's necessary to experiment with different capital strategies and understand how to balance hype and transparency.
- **Core needs:** An instant feedback system on project "health" allows for continuous trial and error to build a mindset for managing cash flow and investor relations.
- **Usage context:** This product is ideal for Fintech classes, end-of-term practical exams, or group startup workshops for 2-10 people, moderated by a host.

# 4\. Current Product Functionality

FUN(D) RAISING is a complete web-based multiplayer financial simulation platform, integrating a sophisticated financial calculation engine.

- **Session management:**The host creates rooms, coordinates the phases, and monitors the leaderboard in real time.
- **Deep project initiation:**Players establish a financial profile ranging from sales prices and production costs to a detailed capital structure.
- **Tactical card game mechanism:**

The 42 Active cards are categorized into 3 strategic groups, and the cards are also balanced according to 3 energy cost levels to differentiate between small actions, medium actions, and large strategic decisions.

- - **Market Momentum (Red):** Stimulating growth and market heat.
    - **Resilience & Trust (Blue):** Strengthening trust and transparency.
    - **Capital & Governance (Purple):** Optimizing capital structure and governance.

Reaction card system: 7 reaction cards focus on emergency situations related to the survival of the startup.

**200 Investor Bot System:**

- - **FOMO:**Following trends and media coverage.
    - **Value Hunter:** Focus on the fundamental indicators (Intrinsic Score).
    - **Whale:** Large investors are extremely sensitive to capital structure and **Valuation Sanity** (Reasonableness of valuation).
    - **Random:** Represents market noise and uncertainty.
- **So What?:** Using bots with distinct psychological profiles creates an objective and consistent market. Players not only learn how to "win" but also how to react to different types of capital flows, developing a selective mindset for choosing suitable investors.

# 5\. Input Data

The reliability of the simulation results depends on the accuracy of the input data. The system applies strict thresholds derived from real-world conditions.

|     |     |
| --- | --- |
| **Input or information** | **Financial meaning** |
| Project scale | Project size, affects funding target and number of phases |
| Retail price (USD) | Listed price before channel discounts |
| E-commerce fee (%) | Marketplace platform fee |
| Retail fee (%) | Trade discount for physical retail partners |
| Direct channel fee (%) | Cost of selling via own website/fanpage |
| Direct materials (USD) | Raw materials per unit |
| Direct packaging (USD) | Box, bag, label, manual per unit |
| Direct labor (USD) | Factory wages per unit |
| Defect allowance (%) | Percentage of products lost due to defects (0–10%) |
| Month 1 units | Expected sales in first month (0–100,000) |
| Month 3 units | Expected sales in month 3 (0–100,000) |
| Month 6 units | Expected sales in month 6 (0–100,000) |
| Fixed operating cost (USD/month) | Monthly expenses that do not vary with output (1,000–100,000) |
| Marketing cost (USD/month) | Monthly budget for ads, promotions (0–100,000) |
| Owner equity (USD) | Cash invested by founders (0–300,000) |
| Bank loan (USD) | Borrowed amount from bank (0–300,000) |
| Loan interest rate (%/year) | Annual interest rate on loan (5–100%) |
| Equity offered (%) | Percentage of company sold to investors (0.1–99.9%) |
| Target funding (USD) | Amount of money to raise from investors (depends on scale) |
| Scenario events (random from 24 scenarios) | Simulates market, internal, regulatory risks/opportunities |
| Active card (player selects from deck) | Short‑term strategic decision |
| Reaction card (triggered by condition) | Crisis response |
| Investor bot preferences (200 bots with weights, memory decay, sensitivity) | Simulates different investor behaviors |
| All financial & market data | Overall startup evaluation |

# 6\. Processing Logic and Rules

The financial engine is the "heart" of the system, processing data through six tightly coupled layers of logic:

|     |     |     |     |
| --- | --- | --- | --- |
| **Indicator / Component** | **Formula in Code** | **Why This Metric** | **Why Needed in Game** |
| Step 0 -Pre-processing (shared by all indicators below) |     |     |     |
| price_real | total_fees = fee_ecom + fee_retail + fee_direct price_real = price × (1 − total_fees/100) | Actual net revenue per unit after paying channel commissions. The player enters a single price, but actual revenue must subtract channel fees. | Without this, gross margin would be miscalculated - a project looks profitable but is losing money to channels. The bot would be misled into investing in weak projects. |
| cogs_unit | cogs_unit = (material + packaging + labor) × (1 + defect_rate/100) | Actual unit production cost, including scrap rate. A 5% defect_rate requires 105 units to sell 100. | Separating COGS into 4 fields (by form design) reflects true cost structure. Labor-intensive projects are penalized harder when defect_rate is high. |
| monthly_burn | monthly_burn = fixed_cost + marketing_cost + loan × interest_rate/100/12 | Total mandatory monthly cash outflow regardless of sales volume. Includes fixed costs, marketing, and monthly loan interest. | Critical survival metric: a startup that runs out of cash before raising enough capital goes bankrupt. Used to calculate burn_score, runway, and bankruptcy checks in process_phase. |
| Group A -Intrinsic Score (max 100 points, 6 components) |     |     |     |
| gm_score (0–30 pts) | gm = (price_real − cogs_unit) / price_real if gm > 0.2: score = 20 + 10×(1−e^{−5×(gm−0.2)/0.6}) else: score = max(0, 20×(gm/0.2)) | Gross margin measures gross profit per revenue dollar. Highest weight (30 pts) because it is the most fundamental metric -a negative-margin project cannot survive long-term. Exponential function above 0.2 rewards high-margin projects with diminishing returns. | The bot uses intrinsic score as a baseline for investment decisions. gm_score has the highest weight because in real startups, gross margin is the first thing investors look at -it shows how much is left to cover fixed costs and generate profit. |
| burn_score (0–20 pts) | burn_rate = monthly_burn / target_funding if burn_rate < 0.3: score = 15 + 5×(1−e^{−4×(0.3−r)/0.25}) else: score = max(0, 15×(1−(r−0.3)/0.7)) | Burn rate = ratio of monthly expenditure to total target funding. Measures how quickly the startup burns cash. A threshold of 0.3 means spending >30% of target funding monthly starts penalizing. | A high-burn project will run out of cash before closing its funding round. The bot needs to recognize this -otherwise it would invest in soon-to-be-bankrupt startups. burn_score naturally steers the bot away from 'high burn, low runway' projects. |
| growth_score (0–20 pts) | growth = (units_m6 / units_m1) − 1 if growth > 0: score = 10 + 10×(1−e^{−3×g/0.5}) else: score = max(0, 10×(1+g/0.5)) | Volume growth rate from month 1 to month 6, measuring project momentum. Exponential function rewards fast growth with diminishing returns -prevents gaming by entering an inflated units_m6. | The game simulates multiple phases. A project with strong volume growth naturally attracts the bot across multiple rounds -which is realistic: investors look not just at current state but at trajectory. |
| revenue_score (0–10 pts) | avg_units = (units_m1 + units_m6) / 2 revenue_year = avg_units × 12 × price_real score = min(10, log10(revenue_year/100000)/2 × 10) | Projected annual revenue, log-scaled. Log scale means a $1B project doesn't score 10× a $100M project -reflects how investors actually think about absolute size. | revenue_year is also used to calculate estimated_valuation via P/S ratio. Higher-revenue projects get higher valuations -but not linearly. Weight of 10 pts (lower than GM and burn) because size matters but less than efficiency. |
| efficiency_score (0–10 pts) | annual_profit = (price_real−cogs_unit) × units_m6×12 − burn×12 roe = annual_profit / total_capital score = min(10, roe×10) | ROE (Return on Equity) measures profit generated per unit of capital. Unlike gm_score which measures ratios, this measures absolute profit after fixed costs -a high-margin project with excessive fixed costs gets penalized here. | A capital-efficient startup generates more profit than competitors using the same amount of capital. The bot needs to distinguish 'profitable' from 'efficient' projects -they are not the same thing. |
| leverage_score (0–10 pts) | debt_ratio = loan / owner_equity if ratio < 0.5: score = 5 + ratio×10 elif ratio ≤ 1.5: score = 10−(ratio−0.5)×5 else: score = max(0, 5−(ratio−1.5)×3) | Evaluates debt-to-equity structure. Trapezoidal function: low ratio (0–0.5) gets average score (too conservative); moderate ratio (0.5–1.5) gets highest score (good leverage); high ratio (>1.5) penalized (insolvency risk). | Reflects financial principles: some debt is good (leverage), too much is dangerous. A fully equity-funded project misses leverage benefits; over-leveraged projects see monthly_burn rise with interest and face higher bankruptcy risk. |
| security_penalty & reg_risk_penalty | sec_pen = max(0, (50−security)/5) reg_pen = reg_risk / 10 intrinsic = max(0, intrinsic−sec_pen−reg_pen) | Deducts intrinsic points for projects neglecting security and regulatory compliance. Every 5 security points below 50 deducts 1 pt; every 10% reg_risk deducts 1 pt. Applied after all 6 components are calculated. | Added after testing showed the bot couldn't distinguish projects careless about compliance. These penalties force players to consider security and licensing -not just financial optimization. |
| Group B -Valuation & ROI |     |     |     |
| estimated_valuation | ps_ratio = 3.0 (baseline) if hype>70: ps_ratio += 2 elif hype&lt;30: ps_ratio −= 1 if growth&gt;0.5: ps_ratio += 1.5 ps_ratio = clamp(ps_ratio, 1.5, 15) valuation = revenue_year × ps_ratio | Uses P/S ratio (Price-to-Sales) -common valuation method for pre-profit startups. Baseline 3×, adjusted by hype (market sentiment) and growth. clamp(1.5, 15) prevents absurd valuations. | Valuation is a key result players see on the dashboard. Hype affects P/S because in reality, hot startups are always valued above fundamentals -this accurately reflects the VC market. |
| roi_norm | raw_roi = max(0, (valuation−total_invested)/total_invested×100) roi_norm = min(100, 20×log10(raw_roi+1)) | ROI normalized to \[0, 100\] using a log function to avoid outliers. A 10% and 1000% ROI project shouldn't differ by 100× in score -log scale smooths the gap. | final_score uses roi_norm to calculate roi_score. The bot also uses it indirectly through attractiveness(). Projects with good ROI retain bot investment across multiple phases. |
| valuation_sanity | mult = valuation / revenue_year if mult < 1: score = 30−(1−mult)/1×30 elif mult ≤ 3: score = 80+(mult−1)/2×20 elif mult ≤ 5: score = 80−(mult−3)/2×40 else: score = max(0, 40−(mult−5)/2×40) | Checks if valuation is 'healthy' -P/S 1–3× is considered reasonable (highest score); P/S &lt;1 (undervalued) or &gt;5 (overvalued) is penalized. Trapezoidal function reflects the valuation sweet spot. | Prevents players from gaming revenue_year to artificially inflate valuation. The bot recognizes overvalued projects and invests less -similar to how real VCs reject deals with excessive ask prices. |
| reg_risk | base = 20 if has_license else 80 if legal_cost ≥ 5% target_funding: base += 20 reg_risk = clamp(base−transparency/10, 0, 100) | Composite regulatory risk from: having a license (−60 risk), investing in legal costs (−20 risk), high transparency reduces further. Inverse metric -higher is worse. | Used in reg_risk_penalty (deducts intrinsic) and in the bot's attractiveness(). Projects with high reg_risk are avoided by the bot -reflecting that regulatory risk is the most common reason startups fail in Vietnam. |
| runway | avail = available_cash (or equity + loan) runway = floor(avail / monthly_burn) = 999 if monthly_burn = 0 | Months a startup can survive on current cash. The simplest but most important metric: if runway < remaining phases, the project will almost certainly go bankrupt before raising enough capital. | process_phase uses runway (indirectly via available_cash) to check bankruptcy after each phase. Players see runway on the dashboard -it is the most intuitive indicator of remaining time. |

1.  **Calculate core metrics:**
    - Net Price = Retail Price × (1 – Fees/100). (Condition: Net Price > Adjusted COGS).
    - Monthly Burn = Fixed Cost + Marketing + (Loan × Interest / 12).
    - Runway = Available Cash / Monthly Burn.
2.  **Intrinsic Score (0-100):** Aggregated from 6 weighted factors: Profit Margin (GM - 30 points), Burn Rate Control (20 points), Growth (20 points), Revenue Size (10 points), Efficiency (10 points), Leverage (10 points).
3.  **Pricing and ROI:**
    - **Valuation Sanity:** Evaluation based on P/S ratio from**1.5x to 15x**.
    - **ROI Norm:** 20 × log10(Estimated Valuation / Total Invested + 1), limit 100.
4.  **Bot Investment Logic:** Use **Softmax function** to allocate capital based on attractiveness.
    - **Withdrawal mechanism:**The bot will withdraw its investment if the project's attractiveness decreases by more than 2.**5 points** total OR decreases over **5 points** only in a single phase.
    - **Memory Decay:**Bots learn from past belief mistakes and use them to penalize their current fundraising capabilities.
5.  **Exclusion conditions (Bankrupt):** If the cash balance is negative (**Cash < 0** The project was immediately disqualified.
6.  **The formula for calculating the final score:** Final Score = \[Funding_Progress × 30 + (100 – Phases_Used) × 0.2 + (ROI_Norm/100) × 30 + (Transparency/100) × 20\] × scale_factor × (1 + Funding_Progress).

|     |     |     |     |
| --- | --- | --- | --- |
| **Component** | **Formula in Code** | **Weight & Rationale** | **Why Needed in Game** |
| funding_score (max 40 pts) | funding_score = funding_progress × 40 | Weight 40% -highest. Reason: the core objective of the game is successful fundraising. A project that raises 100% of target gets 40 pts; 50% gets 20 pts. Highest weight ensures the main win condition is most strongly reflected in the score. | If funding_score only accounted for 20–25%, players could win without raising full funding -losing the game's core logic. 40% ensures the main objective cannot be ignored. |
| speed_score (max 20 pts) | if complete_phase is not None: speed = 20×(1−(complete_phase−1)/(max_phase−1)) else: speed = 0 | Weight 20%. Linear formula: completing at phase 1 gives 20 pts, at the last phase gives 0 pts. Equal weight to roi_score and trans_score: speed is a competitive advantage, not a requirement -important but not more so than ROI. | Creates competition when multiple players all raise full funding. Without speed_score, the game flattens when everyone finishes. Also reflects reality: raising quickly saves burn and captures better market timing. |
| roi_score (max 20 pts) | roi_score = min(20, (roi_norm/100) × 20) | Weight 20%. roi_norm is already normalized to \[0, 100\] in calculate_metrics, so it maps directly to \[0, 20\]. Equal to speed_score: good ROI signals high-quality project design but is not the deciding factor -it's a tiebreaker. | Rewards players who design genuinely high-ROI projects, not just those who raise full funding. Prevents a 'spam many small investments' strategy -the bot only invests heavily in high-ROI projects. |
| trans_score (max 20 pts) | trans_score = max(0, min(20, (transparency/100) × 20)) | Weight 20%. Transparency is a metric players build through cards and actions (0–100). Linear mapping to \[0, 20\]. Equal to ROI weight because transparency is a prerequisite investors demand -without it, even high ROI projects get avoided by the bot. | Forces players to invest in transparency, not just financial optimization. Reflects reality: startups lacking transparency (no audits, no reporting) get rejected by investors even if numbers look good. |
| scale_factor | scale_map = {S:0.8, M:0.9, L:1.0} final = raw × scale_factor × bonus | Adjustment factor based on project scale chosen at game start. Scale S is harder to fund so gets 0.8 (lower max points); Scale L gets 1.0. Not a penalty -just game balance for different scale choices. | Without scale_factor, players would always choose Scale L for higher points. This factor creates a trade-off: Scale S raises less money and can finish early (high speed_score) but total points are multiplied by 0.8. |
| funding_bonus | funding_bonus = (1 + funding_progress)/2 final = raw × scale_factor × funding_bonus | Bonus multiplier at the end, ranging 0.5–1.0 based on funding_progress. Projects raising 100%: bonus = 1.0. Raising 0%: bonus = 0.5 (half points). Purpose: amplify the gap between successful and failed projects. | Without funding_bonus, a project raising 60% and one raising 100% could score similarly if ROI/speed is good. This bonus ensures funding_progress has a non-linear effect -the more raised, the faster points grow. |

The use of the Softmax function and a strict withdrawal mechanism helps the simulation move away from monotonous linear algorithms, creating a market that reacts sensitively to management signals.

|     |     |     |     |
| --- | --- | --- | --- |
| Mission | Describe | Input | Output |
| Create 200 virtual investors | Create bots with unique personalities (FOMO, Value Hunter, Whale, Random). Each bot has a wealth class, capital amount, hype_sens, trans_sens, memory_decay_rate, and weight vector. random.seed(42) ensures reproducibility. | Generated using seeded randomness. | The BOTS list (200 dicts) is used by Phuc in process_phase() and stored by Jin in room state. |
| Caculate project attractiveness | Weighted average tối đa 8 metric keys với per-bot sensitivity multipliers; valuation_sanity penalty (tối đa −45 pts); trust scaling (×trust/100); bounded noise ±5 (±10 với Random). | Project metrics from Phúc; trust_scores from Jin. | An attractiveness score (0-100) is assigned to each bot-project pair to guide invest/withdrawal decisions. |
| Bot ramp-up for each phase | Phase 1: 20% of bots are active (40 bots). Each subsequent phase increases the number by 20%, up to 200 bots in phase 5 and above. This creates a realistic investor activity ramp. | Current phase number. | The active bot subset has been moved into the investment loop. |
| Memory-decay blending | Attractiveness history for each bot (last 5 phases). Weighted average (more recent phases have higher weight). Blended with current attractiveness using type-specific decay rate. | attractiveness_history từ bot_memory trong room. | final_attr (float) dùng trong investment/withdrawal decision. |
| Withdrawal logic | Nếu attractiveness difference giữa best project và current project > 25 → withdraw 50%. Nếu diff > 15 → withdraw 25%. Nếu funding_progress > 80% → withdrawal × 0.3 (bảo vệ near-funded projects). | Ma trận A (bot×project), current alloc_entry. | Reduce perProject amounts; return idle funds; funding_progress and total_invested are updated. |
| Investment distribution (Softmax) | Softmax with temperature /35 (adjusted from /20) + diversity penalty (saturation × 30 minus Softmax) to disperse capital. Per-bot cap: 15% of target funding in phase 1, 20% from phase 2. | Shifted attractiveness scores, idle capital. | Funds are allocated to projects; funding_progress is updated; funding_complete_phase is recorded. |
| Stability helpers | get_bot_memory(): always uses str(bot_id) to correct Flask JSON int→string key conversion. ensure_room_lists(): normalizes all per-player list fields to the correct length on every request. ensure_bot_alloc(): normalizes bot_alloc after JSON deserialization. | Room dict (possibly round-tripped via JSON). | A safe and consistent room state is established for all subsequent operations. |
| Aggregate_bot_actions() | Group raw per-bot action events by (type, action, player_index) and sum the amounts. Return a clean list to display the logs. | List of raw bot action dicts from process_phase(). | Aggregated bot action logs are easy to read and display on the host dashboard. |

# 7\. User Flow

The experience is designed to separate the roles of strategic coordination and project execution.

- HOST FLOW:

1\. Host opens the app and clicks "Create Room."

2\. The system generates unique join links for each player slot (2–10 players).

3\. Host shares links with players.

4\. Host waits for all players to submit their projects and build their decks.

5\. Host clicks "Start Game" to begin Phase 1.

6\. After players have played their cards and clicked "Ready," host clicks "Run Phase."

7\. The system applies the random event, card effects, reaction triggers, and bot decisions.

8\. Host monitors the leaderboard and repeats from step 6 until all phases are complete.

9\. Host views the final ranking and announces the winner.

- PLAYER FLOW:

1\. Players access the site via a link.

2\. Players fill in the financial indicators (scale, price, COGS, forecast, opex, capital).

3\. Players choose 22 active cards and a maximum of 3 reaction cards.

4\. Players wait for the host to start the game.

5\. Through each round: Players experience random events from the market.

6\. Players choose to play from 5 cards, with each card costing a maximum of 3 energy to play.

7\. (Optional) The player shuffles the deck to draw 5 new cards.

8\. (Optional) The player activates a reaction card if the activation condition occurs during gameplay.

9\. Players click "Ready". Once all players are ready, the manager will begin the phase.

10\. Players review the statistics and update the leaderboard rankings after the bot selection is made.

11\. Repeat steps 5–10 for all stages. See the final score when the game ends.

# 8\. Output Data

Immediate feedback is key to learning through experience.

- **Real-time leaderboard:** Updated percentages, hype, transparency, and score forecast.
- **Project details:**Displays Intrinsic Value, Valuation Sanity (based on P/S ratio), Runway, Hype, and a list of current investors.
- Cash and Cashflow for each player's phases.
- **Event Log:** Record the entire card history and bot decisions. This is invaluable data for the process. This helps instructors analyze students' decision-making processes after each play session.

# 9\. Key Design Choices

To optimize educational value within resource constraints, we have made the following strategic choices:

- **Card mechanism:**Simplifying multiple-choice gameplay, which involves complex business interactions, into discrete decisions allows players to focus on trade-offs and reduces the burden on creators.
- **200 Bots:**Having consulted crowdfunding platforms from various sources, this figure ensures consistency and continuous competitive pressure, regardless of class size.
- **Optimizing the Engine for UX/UI:**Utilize Python Flask and pure HTML/JS to prioritize resources for complex financial calculations over flashy UI effects that are unnecessary for EdTech goals.
- **Reductions (MVP):**Replace WebSocket with a 3-second HTTP polling mechanism to ensure stability.**In-memory state**during a short development period.

# 10\. What the Group Did Well

- **Financial depth:** Successfully integrating six layers of logic into a smooth game loop. The financial reasoning is comprehensive and consistent. All six core formulas (intrinsic score, valuation reasonableness, ROI standard, retention time, attractiveness, final score) are implemented and coordinated accurately.
- The system of 200 bots successfully differentiates investor behavior based on project indicators. FOMO, Value Hunter, Whale, and Random bots react differently to the same project, creating educational diversity.
- **Thematic Consistency:** The card design is carefully considered. Each of the 42 active cards and 10 reactive cards reflects a real-world business strategy, and the card counting system (which card fits which scenario) adds strategic depth.
- **End-to-end operation:** The system runs stably, allowing 2-10 players to play simultaneously without serious synchronization errors.
- The multiplayer backend system handles simultaneous player actions and manages room state without significant crashes, which is a considerable technical challenge.
- The user interface (UI) template includes all the necessary screens, including the room owner's control panel, the player's project submission screen, the deck-building tool, and the game screen, with a clear visual hierarchy and user-friendly interactions.
- **Clear architecture:**A good separation between Data, Metrics, Bots, and APIs makes the system easily scalable. The team clearly divided responsibilities according to the architecture: Minh handled data and the tag system, Phuc handled financial metrics and scoring, Khanh handled the bot system and market response, Jin handled the Flask backend and API routing, and Duong handled UI/UX design and frontend implementation.

# 11\. Current Limitations

- **Scale imbalance:** The current scoring formula is imposing excessively heavy penalties on Large (9-phase) projects due to its components. Phases_Used in the formula.
- Players who end project with small phase need to wait others while doing nothing can lead to boredom
- When a project ends or bankrupts, there is no visualized pop-up on the screen. It still demands players to interacting with other elements to pop-up
- It is difficult to obtain maximum final score since the metrics have several penalty

# 12\. What the Group Learned

- **Logical thinking before the interface:** Finalizing your financial model in Excel before coding is a crucial lesson.
- **Scope Creep Management:** Adding features like Bot memory decay or Mulligan is interesting but has slowed down the core system stabilization process.
- **Playtest:** Only through gameplay can we discover the dominant strategies that disrupt the game's balance.

# 13\. Suggestions for Future Students

- **Algorithm improvements:** Use **Logarithmic function**Instead of a linear function for the time penalty in the scoring formula, this balances the opportunities for large-scale projects.
- **Technical upgrade:**Switch to WebSockets to eliminate HTTP polling latency.
- **Additional features:**Develop a detailed post-game "Debrief" screen to specifically explain the variables that led to success/failure.

**Conclude:** FUN(D) RAISING has demonstrated great potential in modernizing financial education. With algorithmic refinements and real-time experience upgrades, it will be a powerful tool for anyone wanting to master startup fundraising skills.
