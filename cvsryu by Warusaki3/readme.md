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
id0[Hadoken] --> id1[Shakunetsu Hadoken]
id1 --> id2[Tatsumaki Senpuu Kyaku]
id2 --> id3[Shoryuken]

id3 -- Ryu --> id0.1[Shinkuu Hadoken]
id0.1 --> id0.2[Shinkuu Tatsumaki Senpuu Kyaku]
id0.2 -- C, P, N, K and EX-Groove --> id0.2.1[Close Shin Shoryuken]
%% id0.2 -- S-Groove --> id0.2.2[Close Shin Shoryuken]
id0.2.1 --> id0.3.1[Crouching Links Into Hadoken]
%% id0.2.2 --> id0.3.1[Crouching Links Into Hadoken]
id0.3.1 --> id0.3.2[Crouching Light to Heavy Punch Link]
id0.3 -- Ryu, C-Groove --> id0.4.1[C-Groove Level 2 Shinkuu Hadoken Cancel]
id0.3 -- Ryu, A-Groove --> id0.5.1[A-Groove Normal Ryu Ground Starter Custom]
id0.3 -- Ryu, P-Groove --> id0.6.1[P-Groove Super Cancel Combo]
id0.3 -- Ryu, S-Groove --> id0.7.1[S-Groove Combo]
id0.3 -- Ryu, N-Groove --> id0.8.1[N-Groove Combo]
id0.3 -- Ryu, K-Groove --> id0.9.1[K-Groove Combo]
id0.3 -- Ryu, EX-Groove --> id0.10.1[EX-Groove Combo]
id0.6.1 --> id0.6.2[P-Groove Super Cancel Corner Combo]
id0.7.1 --> id0.7.2[stuff]


id3 -- Evil Ryu --> id10.1[Ashura Senku];
id10.1 --> id10.2[Shinkuu Hadoken];
id10.2 --> id10.3[Metsu Goshoryu];
id10.3 -- C, P, N, K and EX-Groove --> id10.4.1[Denjin Hadoken]
id10.3 -- S-Groove --> id10.4.2[Denjin Hadoken]
id10.4.1 --> id10.5.1[Shun Goku Satsu]
id10.4.2 --> id10.5.2[Shun Goku Satsu]
id10.5.1 --> id10.6[Evil Ryu Target Combo]
id10.5.2 --> id10.6
id10.3 -- A-Groove --> id10.6
id10.6 --> id10.7[Crouching Light to Heavy Punch Link]
id10.7 --> id10.8[Crouching LK Confirm]
id10.8 --> id10.9[Air Tatsu Combo]

id10.9 -- Evil Ryu, C-Groove --> id10.10.1[C-Groove Level 2 Shinkuu Hadoken Cancel]
id10.9 -- Evil Ryu, A-Groove --> id10.11.1[A-Groove Normal Ryu Ground Starter Custom]
id10.9 -- Evil Ryu, P-Groove --> id10.12.1[P-Groove Super Cancel Combo]
id10.9 -- Evil Ryu, S-Groove --> id10.13.1[S-Groove Combo]
id10.9 -- Evil Ryu, N-Groove --> id10.14.1[N-Groove Combo]
id10.9 -- Evil Ryu, K-Groove --> id10.15.1
id10.9 -- Evil Ryu, EX-Groove --> id10.16.1
```