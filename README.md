# bundesliga-xt-model
An Expected Threat (xT) model to value player actions in the 2023-2024 Bundesliga season
Expected Threat (xT) Model for the Bundesliga ⚽
Overview
This project is an implementation of an Expected Threat (xT) model built from scratch using Python. Unlike traditional metrics like Expected Goals (xG), which only value the final shot, an xT model values every on-ball action—every pass and every dribble—based on how much it increases a team's probability of scoring.

The model was trained on over 100,000 on-ball events from the entire 2023-2024 Bundesliga season, using open data provided by StatsBomb.

Key Results & Visualizations
1. The xT Surface

The model successfully learned the threat level of every zone on the pitch without being told where the goals were. The resulting heatmap clearly shows that the most dangerous areas (highest xT value) are concentrated in and around the opponent's penalty box.

2. Top 15 Most Threatening Players

By calculating the "xT Added" for every pass and dribble, the model can identify the players who were most effective at progressing the ball into dangerous areas over the entire season.

player
Granit Xhaka                   20.53
Edmond Fayçal Tapsoba          18.00
Jonathan Tah                   15.34
Alejandro Grimaldo García      11.85
Odilon Kossonou                 9.96
Robert Andrich                  9.07
Piero Martín Hincapié Reyna     8.64
Florian Wirtz                   8.15
Exequiel Alejandro Palacios     7.83
Lukáš Hrádecký                  5.95
Josip Stanišić                  5.57
Jonas Hofmann                   3.91
Manuel Riemann                  3.48
Jeremie Frimpong                2.20
Eric Dier                       1.82
Core Insight

The model's final player rankings told a fascinating story about the champions, Bayer Leverkusen. Instead of being topped by strikers, the leaderboard is dominated by their deep-lying playmaker (Granit Xhaka) and central defenders (Tapsoba, Tah). This quantitatively proves that Leverkusen's historic undefeated season was built on an elite ability to progress the ball safely and effectively from deep positions, a non-obvious insight that simple goal and assist stats would miss.

Methodology
Data Acquisition: Programmatically acquired event data for the entire 300+ match Bundesliga season using the statsbombpy library.

Data Preparation: Filtered and processed the raw data to isolate all on-ball actions (passes, dribbles, shots) and extract their start/end coordinates.

Probability Modeling: Discretized the pitch into a 16x12 grid and calculated two key matrices from the data:

A Shot Probability matrix for each zone.

A Transition Probability matrix, representing the chance of moving from any zone to any other zone.

xT Calculation: Built the model using an iterative algorithm that solved for the xT value of each zone based on the underlying probabilities.

Player Analysis: Applied the completed xT grid to the event data to calculate the "xT Added" for each player and rank them accordingly.

Technologies Used
Python

Pandas & NumPy

Scikit-learn

Matplotlib, Seaborn, & mplsoccer for visualization

Jupyter Notebook
