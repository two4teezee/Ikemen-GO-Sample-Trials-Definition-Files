# Trials for CVS Ryu by Warusaki3
This file contains a Mermaid js diagram that shows the flowchart for the trials definition flie I created for Warusaki3's CVS Ryu. 
You can use this file to better understand how to create fairly complicated trials for branching characters.

## Using `trials.validforvalvar`
Warusaki3's characters use a variable-value pair system to set Grooves, over even alternate characters.

```ini
var(12): specifies the Ryu variant selected
    0 = Normal Ryu,
    10 = Evil Ryu
var(20): specifies the selected Groove 
    0 = C,
    1 = A,
    2 = P,
    3 = S,
    4 = N,
    5 = K,
    6 = EX
```

Therefore, for trials that are specific to a Ryu variant or a specific groove, the trial can be specified this way:

```ini
[TrialDef, Denjin Hadoken] 
trial.showforvarvalpairs = 12, 10, 20, 3 ;display trial only for S-Groove Evil Ryu
trial.p1life = 100

trialstep.1.text = Denjin Hadoken
trialstep.1.glyphs = _HCB_HCB^K
trialstep.1.stateno = 7400
trialstep.1.isproj = true
```

## Trials Flowchart

```mermaid
flowchart TD
%% All Ryu
id0[Hadoken]
id1[Shakunetsu Hadoken]
id2[Tatsumaki Senpuu Kyaku]
id3[Shoryuken]
id4[Crouching Links Into Hadoken]
id5[Crouching Light to Heavy Punch Link]
id6[Cross-Up Combo into Shoryuken]
%% Links
id0 --> id1
id1 --> id2
id2 --> id3
id4 --> id5
id5 --> id6

%% Normal Ryu
id0.1[Shinkuu Hadoken]
id0.2[Shinkuu Tatsumaki Senpuu Kyaku]
id0.3.1[Close Shin Shoryuken]
id0.3.2[Close Shin Shoryuken]
id0.5.1[3x Crouching LK Confirm]
id0.5.2[Crouching Links Into Shinkuu Hadoken]
id0.5.3.1[Cross Up into Close Shin Shoryuken]
id0.5.3.2[Cross Up into Close Shin Shoryuken]
id0.6.1[C-Groove Level 2 Shinkuu Hadoken Cancel]
id0.7.1[A-Groove Normal Ryu Ground Starter Custom]
id0.7.2[A-Groove Again]
id0.8.1[P-Groove Super Cancel Combo]
id0.9.1[S-Groove Combo]
id0.10.1[N-Groove Combo]
id0.11.1[K-Groove Combo]
id0.12.1[EX-Groove Combo]

%% Links
id3 -- Ryu --> id0.1
id0.1 --> id0.2
id0.2 -- C, P, N, K and EX-Groove --> id0.3.1
id0.2 -- S-Groove --> id0.3.2

%% Converge back in
id0.2 -- A-Groove --> id4
id0.3.1 --> id4
id0.3.2 --> id4
id6 -- Ryu --> id0.5.1

id0.5.1 --> id0.5.2
id0.5.2 -- C, P, N and EX-Groove --> id0.5.3.1
id0.5.2 -- S, K-Groove --> id0.5.3.2
id0.5.3.1 -- C-Groove --> id0.6.1
id0.5.2 -- A-Groove --> id0.7.1
id0.5.3.1 -- P-Groove --> id0.8.1
id0.5.3.2 -- S-Groove --> id0.9.1
id0.5.3.1 -- N-Groove --> id0.10.1
id0.5.3.1 -- K-Groove --> id0.11.1
id0.5.3.1 -- EX-Groove --> id0.12.1
id0.7.1 --> id0.7.2

%% Evil Ryu
id10.1[Ashura Senku]
id10.2[Shinkuu Hadoken]
id10.3[Metsu Goshoryu]
id10.4.1[Denjin Hadoken]
id10.4.2[Denjin Hadoken]
id10.5.1[Shun Goku Satsu]
id10.5.2[Shun Goku Satsu]
id10.6[Evil Ryu Target Combo]
id10.7.1[2x Crouching LK Confirm Tatsu Juggle]
id10.7.2[Air Tatsu Combo]
id10.14.1[N-Groove Heavy Kick Combo]

id3 -- Evil Ryu --> id10.1
id10.1 --> id10.2
id10.2 --> id10.3
id10.3 -- C, P, N and EX-Groove --> id10.4.1
id10.3 -- S, K-Groove --> id10.4.2
id10.4.1 --> id10.5.1
id10.4.2 --> id10.5.2
id10.5.1 --> id10.6
id10.5.2 --> id10.6
id10.3 -- A-Groove --> id10.6

%% Converge back in
id10.6 --> id4
id6 -- Evil Ryu --> id10.7.1

id10.7.1 --> id10.7.2
id10.7.2 -- Evil Ryu, C-Groove --> id10.10.1[C-Groove Level 2 Shinkuu Hadoken Cancel]
id10.7.2 -- Evil Ryu, A-Groove --> id10.11.1[A-Groove Normal Ryu Ground Starter Custom]
id10.7.2 -- Evil Ryu, P-Groove --> id10.12.1[P-Groove Super Cancel Combo]
id10.7.2 -- Evil Ryu, S-Groove --> id10.13.1[S-Groove Combo]
id10.7.2 -- Evil Ryu, N-Groove --> id10.14.1
id10.7.2 -- Evil Ryu, K-Groove --> id10.15.1
id10.7.2 -- Evil Ryu, EX-Groove --> id10.16.1
```