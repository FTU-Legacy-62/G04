# Branh này bị lỗi, hãy đọc trong branh "Fix_blanks"

**Group Code:** G04

## Members

| Full Name | Student ID | Main Role |
|-----------|------------|------------|
| Nguyễn Ngọc Minh | 2313380019 | Database structure, scenario system, card engine and tester |
| Ngô Thị Diễm Phúc | 2312380804 | Financial metrics, player input structure, game flow controller for host and tester |
| Hà Bảo Khanh | 2314380702 | Investor bot system, reaction management, and tester |
| Kim Hye Jin | 2312380803 | Team leader, Flask backend, API routing, room management, and tester |
| Vũ Bạch Dương | 2312380808 | UX/UI design, frontend implementation, and tester |

## Brief Product Description

**Fun(d) Raising** is a web-based startup fundraising simulation game for 2–10 players. Each player builds their own project (choosing scale, valuation, capital structure, revenue forecast), designs a custom deck of 22 action cards and up to 3 reaction cards. Over several phases (5–9 phases depending on scale), players face random events (market, internal, regulatory) and make card-playing decisions to attract capital from 200 AI investors (FOMO, Value Hunter, Whale, Random). The host controls the game pace, and the system automatically calculates a final score based on funding progress, speed, ROI, and transparency – the highest score wins.

## Problem the Product Solves

Finance students and aspiring entrepreneurs lack a safe, low‑cost environment to practice real‑world fundraising decisions. In real life, trial and error in fundraising strategies can cause severe financial consequences or missed opportunities.

The product solves this by providing an interactive simulation where users can immediately see the impact of their decisions on core financial metrics (gross margin, burn rate, ROE, valuation sanity, cash runway) and investor behavior. This issue matters because it directly affects the ability to raise capital successfully – a vital skill for any startup project.

## Target Users

- **Finance, Banking, and Business Administration students** who need to understand the link between financial decisions (price, COGS, leverage, spending plans) and actual fundraising outcomes.
- **Early‑stage startup founders** who want to test fundraising strategies, balance short‑term "hype" vs. long‑term "transparency", and learn how to respond to adverse market events.
- **Lecturers** teaching corporate finance or venture capital who use the game as an interactive teaching tool, letting students experience competitive fundraising in a classroom setting.

## Main Features

- **Multiplayer simulation with host control:** A host creates a room (2–10 players), controls phase progression, and monitors all players in real time via a dedicated dashboard.
- **AI investor bot ecosystem:** 200 bots with 4 distinct behavioral profiles   FOMO, Value Hunter, Whale, and Random   dynamically invest or withdraw capital based on each project's financial metrics and attractiveness score.
- **Dynamic financial simulation per phase:** Each phase, a project receives a random event (24 scenarios). Players use energy (3/phase) to play action cards, trigger reaction cards when conditions are met. The system recalculates metrics: Intrinsic Value, Valuation Sanity, ROI Norm, Runway, Funding Progress.
- **Strategic card system with random events:** Each phase, players draw active cards (from a custom deck of 22) and respond to random market, regulatory, internal, or external events; reaction cards can be triggered automatically under specific crisis conditions.
- **Leaderboard by scale and overall:** The host can view real‑time progress, hype, transparency, and scores of all players. The game automatically ends when all projects have completed their phases or gone bankrupt, displaying a final score (0–100) to determine the winner.

## How to Open or Run the Product

1. Open the link game: https://g04-sh5t.onrender.com/
2. The host clicks "Create Room" to generate a game session and unique join links for each player.
3. Each player opens their unique join link and fills in their startup's financial profile.
4. Each player builds their deck: select exactly 22 active cards and up to 3 reaction cards.
5. When all players are ready, the host clicks "Start Game" to begin Phase 1.
6. Each phase: a random event is applied → players draw 5 cards and spend energy to play cards → host clicks "Run Phase" → system bots invest or withdraw → metrics update on the leaderboard.
7. Repeat for the number of phases determined by project scale (Small: 5, Medium: 7, Large: 9).
8. After the final phase, view the leaderboard and final scores (0–100) to determine the winner.

