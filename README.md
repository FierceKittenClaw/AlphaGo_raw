# AlphaGo_raw
This repo contains thinking time data of Google DeepMind Challenge: Lee Sedol vs. AlphaGo
The data is hand-coded by myself watching the games. So there's a chance that this data contains some minor errors, but pretty sure they are accurate.

More details about the data:

columns
- turn_index: this refers to the move index of each player. Turn index is different from 'ply' or 'n-th move'. For example, Lee's 78th move of the game 4's turn_index was his 39th turn_index.
- Lee_Sedol: Lee Sedol's time stamp when he laid his stone. At turn_index 0, this is 02:00:00 (hh:mm:ss)
- AlphaGo: same as Lee_Sedol
- Countdown: this column indicates when the players entered the countdown period. countdown -1 means the player used one chance to extend his countdown period. -2 means two chances at one turn_index. -3 doesn't exist in the dataset as neither of them failed to keep the countdown rule.
- Lee_Sedol_ott: Lee Sedol's time stamp in the countdown period. This column has the same data format as 'Lee_Sedol' but the content is just the opposite. In the countdown period, the countdown starts from 00:01:00 to 00:00:00. When not in the countdown period you only have to subtract the n-1th timestamp from nth time_stamp. In the countdown phase, however, thinking time is calculated by substracting n-th timestamp from 01:00:00.
  Let's say, Lee have 00:00:30 left and he entered countdown. He used his first countdown chance and laid his stone at 00:00:01. Then, the total thinking time at this turn_index would be 00:00:30 + 00:01:00 + (00:01:00 - 00:00:01) = 00:02:29
- AlphaGo_ott: same as Lee_Sedol_ott


When a player resigns..
- if Black resigns, the time stamp for that move is not recorded as the game finishes before White moves.
- if White resigns, the time stamp for that move is recorded as the game finishes after Black moves.
