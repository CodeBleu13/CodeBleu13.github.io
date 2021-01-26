# The Bleu Game Awards 2020 Final

The votes have been Cast. Let's see the results



```python
import pyrankvote as prv
from pyrankvote import Candidate, Ballot
import pandas as pd

%matplotlib inline
```


```python
votes = pd.read_csv("BGAs.csv", index_col="Timestamp", parse_dates=True)
```


```python
GOTY2020 = votes.iloc[:,0:6]
PERF2020 = votes.iloc[:,6:9]
MUSI2020 = votes.iloc[:,9:13]
ARTS2020 = votes.iloc[:,13:17]
NARR2020 = votes.iloc[:,17:21]
COOP2020 = votes.iloc[:,21:25]
MULT2020 = votes.iloc[:,25:28]
ONGO2020 = votes.iloc[:,28:33]
DLCS2020 = votes.iloc[:,33:41]
OPWO2020 = votes.iloc[:,41:43]
ACTI2020 = votes.iloc[:,43:46]
ACAD2020 = votes.iloc[:,46:48]
STRA2020 = votes.iloc[:,48:50]
RPGS2020 = votes.iloc[:,50:59]
SPOR2020 = votes.iloc[:,59:63]
FAMI2020 = votes.iloc[:,63:66]
REMA2020 = votes.iloc[:,66:71]
INDI2020 = votes.iloc[:,71:75]
CONT2020 = votes.iloc[:,75:79]

GOTYqq = votes.iloc[:,79:82]
PERFqq = votes.iloc[:,82:86]
MUSIqq = votes.iloc[:,86:88]
ARTSqq = votes.iloc[:,88:90]
NARRqq = votes.iloc[:,90:93]
COOPqq = votes.iloc[:,93:99]
OPWOqq = votes.iloc[:,99:102]
ACTIqq = votes.iloc[:,102:109]
ACADqq = votes.iloc[:,109:111]
STRAqq = votes.iloc[:,111:117]
RPGSqq = votes.iloc[:,117:122]
SPORqq = votes.iloc[:,122:126]
FAMIqq = votes.iloc[:,126:133]
INDIqq = votes.iloc[:,133:143]
```

## Quinquo Games

### Best Performance


```python
cans = {'Ashley Johnson as Ellie from The Last of Us Part 1':Candidate('Ashley Johnson as Ellie from The Last of Us Part 1'),
        'Laura Bailey as Kait Diaz from Gears 5':Candidate('Laura Bailey as Kait Diaz from Gears 5'),
        'Andrew Lackey as Ori from Ori and the Blind Forest':Candidate('Andrew Lackey as Ori from Ori and the Blind Forest'),
        'Troy Baker as Joel from The Last of Us Part 1':Candidate('Troy Baker as Joel from The Last of Us Part 1')}
PERFqq.replace(cans, inplace=True)

canidates = [Candidate('Ashley Johnson as Ellie from The Last of Us Part 1'),Candidate('Laura Bailey as Kait Diaz from Gears 5'),
            Candidate('Andrew Lackey as Ori from Ori and the Blind Forest'),Candidate('Troy Baker as Joel from The Last of Us Part 1')]
ballots = []
i=0
while (i < len(PERFqq)) :
    ballots.append(Ballot(ranked_candidates=PERFqq.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
# print(result)
print(result.get_winners())
```

    [<Candidate('Ashley Johnson as Ellie from The Last of Us Part 1')>]
    

### Best Musical Score


```python
# MUSIqq

cans = {'Ori and the Blind Forest':Candidate('Ori and the Blind Forest'),
        "Marvel's Spider-Man":Candidate("Marvel's Spider-Man")}
MUSIqq.replace(cans, inplace=True)

canidates = [Candidate('Ori and the Blind Forest'),Candidate("Marvel's Spider-Man")]
ballots = []
i=0
while (i < len(MUSIqq)) :
    ballots.append(Ballot(ranked_candidates=MUSIqq.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
# print(result)
print(result.get_winners())
```

    [<Candidate('Ori and the Blind Forest')>]
    

### Best Art Direction


```python
# ARTSqq

cans = {'Ori and the Blind Forest':Candidate('Ori and the Blind Forest'),
        "Marvel's Spider-Man":Candidate("Marvel's Spider-Man")}
ARTSqq.replace(cans, inplace=True)

canidates = [Candidate('Ori and the Blind Forest'),Candidate("Marvel's Spider-Man")]
ballots = []
i=0
while (i < len(ARTSqq)) :
    ballots.append(Ballot(ranked_candidates=ARTSqq.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
# print(result)
print(result.get_winners())
```

    [<Candidate('Ori and the Blind Forest')>]
    

### Best Narrative


```python
#NARRqq

cans = {'Ori and the Blind Forest':Candidate('Ori and the Blind Forest'),
        "Hellblade: Senua's Sacrifice":Candidate("Hellblade: Senua's Sacrifice"),
        'The Last of Us Part 1':Candidate('The Last of Us Part 1')}
NARRqq.replace(cans, inplace=True)

canidates = [Candidate('Ori and the Blind Forest'),Candidate("Hellblade: Senua's Sacrifice"),
            Candidate('The Last of Us Part 1')]
ballots = []
i=0
while (i < len(NARRqq)) :
    ballots.append(Ballot(ranked_candidates=NARRqq.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
# print(result)
print(result.get_winners())

```

    [<Candidate('The Last of Us Part 1')>]
    

### Best Co-op Game


```python
#COOPqq

cans = {'Gears 5':Candidate('Gears 5'),
        'Destiny 2':Candidate('Destiny 2'),
        'Killing floor 2':Candidate('Killing floor 2'),
        'Minecraft':Candidate('Minecraft'),
        'Stardew Valley':Candidate('Stardew Valley'),
        'World War Z':Candidate('World War Z'),}
COOPqq.replace(cans, inplace=True)

canidates = [Candidate('Gears 5'),Candidate('Destiny 2'), Candidate('Minecraft'), Candidate('Stardew Valley'),
            Candidate('Killing floor 2'), Candidate('World War Z')]
ballots = []
i=0
while (i < len(COOPqq)) :
    ballots.append(Ballot(ranked_candidates=COOPqq.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())
print('\l\l')
print(result)


```

    [<Candidate('Minecraft')>]
    \l\l
    ROUND 1
    Candidate          Votes  Status
    ---------------  -------  --------
    Destiny 2              4  Hopeful
    Minecraft              3  Hopeful
    Gears 5                2  Hopeful
    Stardew Valley         2  Rejected
    World War Z            0  Rejected
    Killing floor 2        0  Rejected
    
    ROUND 2
    Candidate          Votes  Status
    ---------------  -------  --------
    Minecraft              5  Hopeful
    Destiny 2              4  Hopeful
    Gears 5                2  Rejected
    Stardew Valley         0  Rejected
    World War Z            0  Rejected
    Killing floor 2        0  Rejected
    
    FINAL RESULT
    Candidate          Votes  Status
    ---------------  -------  --------
    Minecraft              6  Elected
    Destiny 2              5  Rejected
    Gears 5                0  Rejected
    Stardew Valley         0  Rejected
    World War Z            0  Rejected
    Killing floor 2        0  Rejected
    
    

### Best Open World Game


```python
# OPWOqq

cans = {"Assassin's Creed Odyssey":Candidate("Assassin's Creed Odyssey"),
        "Marvel's Spider-Man":Candidate("Marvel's Spider-Man"),
        'Ori and the Blind Forest':Candidate('Ori and the Blind Forest')}
OPWOqq.replace(cans, inplace=True)

canidates = [Candidate("Assassin's Creed Odyssey"),Candidate("Marvel's Spider-Man"), Candidate('Ori and the Blind Forest')]
ballots = []
i=0
while (i < len(OPWOqq)) :
    ballots.append(Ballot(ranked_candidates=OPWOqq.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())
print('\l\l')
print(result)

```

    [<Candidate('Marvel's Spider-Man')>]
    \l\l
    FINAL RESULT
    Candidate                   Votes  Status
    ------------------------  -------  --------
    Marvel's Spider-Man             8  Elected
    Assassin's Creed Odyssey        3  Rejected
    Ori and the Blind Forest        0  Rejected
    
    

### Best Action Game


```python
# ACTIqq

cans = {'Gears 5':Candidate('Gears 5'),
        'Apex: Legends':Candidate('Apex: Legends'),
        'Bulletstorm: Full Clip Edition':Candidate('Bulletstorm: Full Clip Edition'),
        "Marvel's Spider-Man":Candidate("Marvel's Spider-Man"),
        'Metro Exodus':Candidate('Metro Exodus'),
        'My Friend Pedro':Candidate('My Friend Pedro'),
        'Rage 2':Candidate('Rage 2'),}
ACTIqq.replace(cans, inplace=True)

canidates = [Candidate('Gears 5'),Candidate('Apex: Legends'), Candidate('Bulletstorm: Full Clip Edition'), Candidate("Marvel's Spider-Man"),
            Candidate('Metro Exodus'), Candidate('My Friend Pedro'),Candidate('Rage 2')]
ballots = []
i=0
while (i < len(ACTIqq)) :
    ballots.append(Ballot(ranked_candidates=ACTIqq.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())
print('\l\l')
print(result)

```

    [<Candidate('Marvel's Spider-Man')>]
    \l\l
    FINAL RESULT
    Candidate                         Votes  Status
    ------------------------------  -------  --------
    Marvel's Spider-Man                   9  Elected
    Gears 5                               2  Rejected
    Metro Exodus                          0  Rejected
    My Friend Pedro                       0  Rejected
    Apex: Legends                         0  Rejected
    Bulletstorm: Full Clip Edition        0  Rejected
    Rage 2                                0  Rejected
    
    

### Best Action Adventure Game


```python
# ACADqq

cans = {"Assassin's Creed Odyssey":Candidate("Assassin's Creed Odyssey"),
        'Ori and the Blind Forest':Candidate('Ori and the Blind Forest'),}
ACADqq.replace(cans, inplace=True)

canidates = [Candidate("Assassin's Creed Odyssey"),Candidate('Ori and the Blind Forest')]
ballots = []
i=0
while (i < len(ACADqq)) :
    ballots.append(Ballot(ranked_candidates=ACADqq.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())
print('\l\l')
print(result)

```

    [<Candidate('Assassin's Creed Odyssey')>]
    \l\l
    FINAL RESULT
    Candidate                   Votes  Status
    ------------------------  -------  --------
    Assassin's Creed Odyssey        8  Elected
    Ori and the Blind Forest        3  Rejected
    
    

### Best Strategy Game


```python
# STRAqq

cans = {'Microsoft Flight Simulator':Candidate('Microsoft Flight Simulator'),
        'Crusader Kings III':Candidate('Crusader Kings III'),
        'Fire Emblem: Three Houses':Candidate('Fire Emblem: Three Houses'),
        "Gears Tactics":Candidate("Gears Tactics"),
        'Rimworld':Candidate('Rimworld'),
        'Sins of a Solar Empire':Candidate('Sins of a Solar Empire')}
STRAqq.replace(cans, inplace=True)

canidates = [Candidate('Microsoft Flight Simulator'),Candidate('Crusader Kings III'), Candidate('Fire Emblem: Three Houses'), Candidate("Gears Tactics"),
            Candidate('Rimworld'), Candidate('Sins of a Solar Empire')]
ballots = []
i=0
while (i < len(STRAqq)) :
    ballots.append(Ballot(ranked_candidates=STRAqq.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())
print('\l\l')
print(result)

```

    [<Candidate('Gears Tactics')>]
    \l\l
    ROUND 1
    Candidate                     Votes  Status
    --------------------------  -------  --------
    Fire Emblem: Three Houses         3  Hopeful
    Gears Tactics                     3  Hopeful
    Rimworld                          3  Hopeful
    Crusader Kings III                2  Rejected
    Sins of a Solar Empire            0  Rejected
    Microsoft Flight Simulator        0  Rejected
    
    ROUND 2
    Candidate                     Votes  Status
    --------------------------  -------  --------
    Fire Emblem: Three Houses         5  Hopeful
    Gears Tactics                     3  Hopeful
    Rimworld                          3  Rejected
    Crusader Kings III                0  Rejected
    Sins of a Solar Empire            0  Rejected
    Microsoft Flight Simulator        0  Rejected
    
    FINAL RESULT
    Candidate                     Votes  Status
    --------------------------  -------  --------
    Gears Tactics                     6  Elected
    Fire Emblem: Three Houses         5  Rejected
    Rimworld                          0  Rejected
    Crusader Kings III                0  Rejected
    Sins of a Solar Empire            0  Rejected
    Microsoft Flight Simulator        0  Rejected
    
    

As it turns out, Gears Tactics was a 2020 game, and the BGA coordinators didn't catch it. As a result, Fire Emblem: Three Houses wins

### Best RPG


```python
# RPGSqq

cans = {'Kingdom Hearts III':Candidate('Kingdom Hearts III'),
        'Borderlands 2':Candidate('Borderlands 2'),
        'Metro Exodus':Candidate('Metro Exodus'),
        "Assassin's Creed Odyssey":Candidate("Assassin's Creed Odyssey"),
        'Nier: Automata':Candidate('Nier: Automata')}
RPGSqq.replace(cans, inplace=True)

canidates = [Candidate('Kingdom Hearts III'),Candidate('Borderlands 2'), Candidate('Metro Exodus'), Candidate("Assassin's Creed Odyssey"),
            Candidate('Nier: Automata')]
ballots = []
i=0
while (i < len(RPGSqq)) :
    ballots.append(Ballot(ranked_candidates=RPGSqq.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())
print('\l\l')
print(result)
```

    [<Candidate('Assassin's Creed Odyssey')>]
    \l\l
    ROUND 1
    Candidate                   Votes  Status
    ------------------------  -------  --------
    Assassin's Creed Odyssey        5  Hopeful
    Nier: Automata                  3  Hopeful
    Metro Exodus                    3  Rejected
    Borderlands 2                   0  Rejected
    Kingdom Hearts III              0  Rejected
    
    FINAL RESULT
    Candidate                   Votes  Status
    ------------------------  -------  --------
    Assassin's Creed Odyssey        7  Elected
    Nier: Automata                  4  Rejected
    Metro Exodus                    0  Rejected
    Borderlands 2                   0  Rejected
    Kingdom Hearts III              0  Rejected
    
    

### Best Sports Game


```python
# SPORqq

cans = {'FIFA 20':Candidate('FIFA 20'),
        'Dirt Rally 2':Candidate('Dirt Rally 2'),
        'Mortal Kombat 11':Candidate('Mortal Kombat 11'),
        "Super Smash Ultimate":Candidate("Super Smash Ultimate")}
SPORqq.replace(cans, inplace=True)

canidates = [Candidate('FIFA 20'),Candidate('Dirt Rally 2'), Candidate('Mortal Kombat 11'), Candidate("Super Smash Ultimate")]
ballots = []
i=0
while (i < len(SPORqq)) :
    ballots.append(Ballot(ranked_candidates=SPORqq.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())
print('\l\l')
print(result)
```

    [<Candidate('Mortal Kombat 11')>]
    \l\l
    ROUND 1
    Candidate               Votes  Status
    --------------------  -------  --------
    Mortal Kombat 11            4  Hopeful
    Super Smash Ultimate        3  Hopeful
    FIFA 20                     3  Hopeful
    Dirt Rally 2                1  Rejected
    
    ROUND 2
    Candidate               Votes  Status
    --------------------  -------  --------
    Mortal Kombat 11            5  Hopeful
    Super Smash Ultimate        3  Hopeful
    FIFA 20                     3  Rejected
    Dirt Rally 2                0  Rejected
    
    FINAL RESULT
    Candidate               Votes  Status
    --------------------  -------  --------
    Mortal Kombat 11            6  Elected
    Super Smash Ultimate        5  Rejected
    FIFA 20                     0  Rejected
    Dirt Rally 2                0  Rejected
    
    

### Best Family/E10+ Game


```python
# FAMIqq

cans = {'House Flipper':Candidate('House Flipper'),
        "Luigi's Mansion 3":Candidate("Luigi's Mansion 3"),
        'Minecraft':Candidate('Minecraft'),
        "Ori and the Blind Forest":Candidate("Ori and the Blind Forest"),
        "Spyro Reignited":Candidate("Spyro Reignited"),
        "Stardew Valley":Candidate("Stardew Valley"),
        "Super Mario Maker 2":Candidate("Super Mario Maker 2")}
FAMIqq.replace(cans, inplace=True)

canidates = [Candidate('House Flipper'),Candidate("Luigi's Mansion 3"), Candidate('Minecraft'), Candidate("Ori and the Blind Forest")
                        , Candidate("Spyro Reignited"), Candidate("Stardew Valley"), Candidate("Super Mario Maker 2")]
ballots = []
i=0
while (i < len(FAMIqq)) :
    ballots.append(Ballot(ranked_candidates=FAMIqq.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())
print('\l\l')
print(result)
```

    [<Candidate('Minecraft')>]
    \l\l
    ROUND 1
    Candidate                   Votes  Status
    ------------------------  -------  --------
    Minecraft                       3  Hopeful
    Super Mario Maker 2             3  Hopeful
    Ori and the Blind Forest        2  Hopeful
    Spyro Reignited                 1  Hopeful
    House Flipper                   1  Hopeful
    Luigi's Mansion 3               1  Rejected
    Stardew Valley                  0  Rejected
    
    ROUND 2
    Candidate                   Votes  Status
    ------------------------  -------  --------
    Minecraft                       3  Hopeful
    Super Mario Maker 2             3  Hopeful
    Spyro Reignited                 2  Hopeful
    Ori and the Blind Forest        2  Hopeful
    House Flipper                   1  Rejected
    Luigi's Mansion 3               0  Rejected
    Stardew Valley                  0  Rejected
    
    ROUND 3
    Candidate                   Votes  Status
    ------------------------  -------  --------
    Minecraft                       4  Hopeful
    Super Mario Maker 2             3  Hopeful
    Spyro Reignited                 2  Hopeful
    Ori and the Blind Forest        2  Rejected
    House Flipper                   0  Rejected
    Luigi's Mansion 3               0  Rejected
    Stardew Valley                  0  Rejected
    
    ROUND 4
    Candidate                   Votes  Status
    ------------------------  -------  --------
    Minecraft                       5  Hopeful
    Spyro Reignited                 3  Hopeful
    Super Mario Maker 2             3  Rejected
    Ori and the Blind Forest        0  Rejected
    House Flipper                   0  Rejected
    Luigi's Mansion 3               0  Rejected
    Stardew Valley                  0  Rejected
    
    FINAL RESULT
    Candidate                   Votes  Status
    ------------------------  -------  --------
    Minecraft                       7  Elected
    Spyro Reignited                 4  Rejected
    Super Mario Maker 2             0  Rejected
    Ori and the Blind Forest        0  Rejected
    House Flipper                   0  Rejected
    Luigi's Mansion 3               0  Rejected
    Stardew Valley                  0  Rejected
    
    

### Best Game by an Indie Game Studio


```python
# INDIqq

cans = {'House Flipper':Candidate('House Flipper'),
        "Among Us":Candidate("Among Us"),
        'Afterparty':Candidate('Afterparty'),
        "Dead Cells":Candidate("Dead Cells"),
        "Devious Dungeon":Candidate("Devious Dungeon"),
        "Little Missfortune":Candidate("Little Missfortune"),
        "My Friend Pedro":Candidate("My Friend Pedro"),
        "Sally Face":Candidate("Sally Face"),
        "Untitled Goose Game":Candidate("Untitled Goose Game"),
        "What the Golf":Candidate("What the Golf")}
INDIqq.replace(cans, inplace=True)

canidates = [Candidate('House Flipper'),Candidate("Among Us"), Candidate('Afterparty'), Candidate("Dead Cells")
                        , Candidate("Devious Dungeon"), Candidate("Little Missfortune"), Candidate("My Friend Pedro")
                        , Candidate("Sally Face"), Candidate("Untitled Goose Game"), Candidate("What the Golf")]
ballots = []
i=0
while (i < len(INDIqq)) :
    ballots.append(Ballot(ranked_candidates=INDIqq.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())
print('\l\l')
print(result)
```

    [<Candidate('Among Us')>]
    \l\l
    FINAL RESULT
    Candidate              Votes  Status
    -------------------  -------  --------
    Among Us                   7  Elected
    House Flipper              2  Rejected
    Untitled Goose Game        1  Rejected
    Little Missfortune         1  Rejected
    My Friend Pedro            0  Rejected
    Dead Cells                 0  Rejected
    Afterparty                 0  Rejected
    What the Golf              0  Rejected
    Devious Dungeon            0  Rejected
    Sally Face                 0  Rejected
    
    

### Game of the Year


```python
# GOTYqq

cans = {"Marvel's Spider-Man":Candidate("Marvel's Spider-Man"),
        "The Last of Us Part 1":Candidate("The Last of Us Part 1"),
        'Gears 5':Candidate('Gears 5'),
        }
GOTYqq.replace(cans, inplace=True)

canidates = [Candidate("Marvel's Spider-Man"),Candidate("The Last of Us Part 1"), Candidate('Gears 5')]
ballots = []
i=0
while (i < len(GOTYqq)) :
    ballots.append(Ballot(ranked_candidates=GOTYqq.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())
print('\l\l')
print(result)
```

    [<Candidate('Marvel's Spider-Man')>]
    \l\l
    FINAL RESULT
    Candidate                Votes  Status
    ---------------------  -------  --------
    Marvel's Spider-Man          7  Elected
    The Last of Us Part 1        2  Rejected
    Gears 5                      2  Rejected
    
    

## 2020 Winners

### Best Performance


```python
# PERF2020

cans = {'Ashley Johnson as Ellie from The Last of Us Part 2':Candidate('Ashley Johnson as Ellie from The Last of Us Part 2'),
        'Cameron Monaghan as Cal Kestis from Star Wars Jedi: Fallen Order':Candidate('Cameron Monaghan as Cal Kestis from Star Wars Jedi: Fallen Order'),
        'Elizabeth Grullon as Trilla from Star Wars Jedi: Fallen Order':Candidate('Elizabeth Grullon as Trilla from Star Wars Jedi: Fallen Order')}
PERF2020.replace(cans, inplace=True)

canidates = [Candidate('Ashley Johnson as Ellie from The Last of Us Part 2'),Candidate('Cameron Monaghan as Cal Kestis from Star Wars Jedi: Fallen Order'),
            Candidate('Elizabeth Grullon as Trilla from Star Wars Jedi: Fallen Order')]
ballots = []
i=0
while (i < len(PERF2020)) :
    ballots.append(Ballot(ranked_candidates=PERF2020.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())

print(result)
```

    [<Candidate('Cameron Monaghan as Cal Kestis from Star Wars Jedi: Fallen Order')>]
    ROUND 1
    Candidate                                                           Votes  Status
    ----------------------------------------------------------------  -------  --------
    Cameron Monaghan as Cal Kestis from Star Wars Jedi: Fallen Order        5  Hopeful
    Ashley Johnson as Ellie from The Last of Us Part 2                      5  Hopeful
    Elizabeth Grullon as Trilla from Star Wars Jedi: Fallen Order           1  Rejected
    
    FINAL RESULT
    Candidate                                                           Votes  Status
    ----------------------------------------------------------------  -------  --------
    Cameron Monaghan as Cal Kestis from Star Wars Jedi: Fallen Order        6  Elected
    Ashley Johnson as Ellie from The Last of Us Part 2                      5  Rejected
    Elizabeth Grullon as Trilla from Star Wars Jedi: Fallen Order           0  Rejected
    
    

### Best Musical Score


```python
# MUSI2020

cans = {"Hades":Candidate("Hades"),
        "Ori and the Will of the Wisps":Candidate("Ori and the Will of the Wisps"),
        "Pokemon Sword/Shield":Candidate("Pokemon Sword/Shield"),
        "Star Wars Jedi: Fallen Order":Candidate("Star Wars Jedi: Fallen Order")}
MUSI2020.replace(cans, inplace=True)

canidates = [Candidate("Hades"),Candidate("Ori and the Will of the Wisps"), Candidate("Pokemon Sword/Shield"),Candidate("Star Wars Jedi: Fallen Order")]
ballots = []
i=0
while (i < len(MUSI2020)) :
    ballots.append(Ballot(ranked_candidates=MUSI2020.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())

print(result)
```

    [<Candidate('Ori and the Will of the Wisps')>]
    ROUND 1
    Candidate                        Votes  Status
    -----------------------------  -------  --------
    Ori and the Will of the Wisps        4  Hopeful
    Star Wars Jedi: Fallen Order         4  Hopeful
    Hades                                3  Rejected
    Pokemon Sword/Shield                 0  Rejected
    
    FINAL RESULT
    Candidate                        Votes  Status
    -----------------------------  -------  --------
    Ori and the Will of the Wisps        6  Elected
    Star Wars Jedi: Fallen Order         5  Rejected
    Hades                                0  Rejected
    Pokemon Sword/Shield                 0  Rejected
    
    

### Best Art Direction


```python
# ARTS2020

cans = {"Hades":Candidate("Hades"),
        "Ori and the Will of the Wisps":Candidate("Ori and the Will of the Wisps"),
        "Ghost of Tsushima":Candidate("Ghost of Tsushima"),
        "Star Wars Jedi: Fallen Order":Candidate("Star Wars Jedi: Fallen Order")}
ARTS2020.replace(cans, inplace=True)

canidates = [Candidate("Hades"),Candidate("Ori and the Will of the Wisps"), Candidate("Ghost of Tsushima"),Candidate("Star Wars Jedi: Fallen Order")]
ballots = []
i=0
while (i < len(ARTS2020)) :
    ballots.append(Ballot(ranked_candidates=ARTS2020.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())

print(result)
```

    [<Candidate('Hades')>]
    ROUND 1
    Candidate                        Votes  Status
    -----------------------------  -------  --------
    Hades                                3  Hopeful
    Ori and the Will of the Wisps        3  Hopeful
    Star Wars Jedi: Fallen Order         3  Hopeful
    Ghost of Tsushima                    2  Rejected
    
    ROUND 2
    Candidate                        Votes  Status
    -----------------------------  -------  --------
    Hades                                4  Hopeful
    Ori and the Will of the Wisps        4  Hopeful
    Star Wars Jedi: Fallen Order         3  Rejected
    Ghost of Tsushima                    0  Rejected
    
    FINAL RESULT
    Candidate                        Votes  Status
    -----------------------------  -------  --------
    Hades                                6  Elected
    Ori and the Will of the Wisps        5  Rejected
    Star Wars Jedi: Fallen Order         0  Rejected
    Ghost of Tsushima                    0  Rejected
    
    

### Best Narrative


```python
# NARR2020

cans = {"Hades":Candidate("Hades"),
        "Ori and the Will of the Wisps":Candidate("Ori and the Will of the Wisps"),
        "The Last of Us Part 2":Candidate("The Last of Us Part 2"),
        "Star Wars Jedi: Fallen Order":Candidate("Star Wars Jedi: Fallen Order")}
NARR2020.replace(cans, inplace=True)

canidates = [Candidate("Hades"),Candidate("Ori and the Will of the Wisps"), Candidate("The Last of Us Part 2"),Candidate("Star Wars Jedi: Fallen Order")]
ballots = []
i=0
while (i < len(NARR2020)) :
    ballots.append(Ballot(ranked_candidates=NARR2020.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())

print(result)
```

    [<Candidate('Star Wars Jedi: Fallen Order')>]
    ROUND 1
    Candidate                        Votes  Status
    -----------------------------  -------  --------
    Star Wars Jedi: Fallen Order         5  Hopeful
    The Last of Us Part 2                4  Hopeful
    Hades                                2  Rejected
    Ori and the Will of the Wisps        0  Rejected
    
    FINAL RESULT
    Candidate                        Votes  Status
    -----------------------------  -------  --------
    Star Wars Jedi: Fallen Order         7  Elected
    The Last of Us Part 2                4  Rejected
    Hades                                0  Rejected
    Ori and the Will of the Wisps        0  Rejected
    
    

### Best Co-op Game


```python
# COOP2020 

cans = {"Phasmaphobia":Candidate("Phasmaphobia"),
        "Grounded":Candidate("Grounded"),
        "Animal Crossing: New Horizons":Candidate("Animal Crossing: New Horizons"),
        "Fall Guys":Candidate("Fall Guys")}
COOP2020.replace(cans, inplace=True)

canidates = [Candidate("Phasmaphobia"),Candidate("Grounded"), Candidate("Animal Crossing: New Horizons"),Candidate("Fall Guys")]
ballots = []
i=0
while (i < len(COOP2020)) :
    ballots.append(Ballot(ranked_candidates=COOP2020.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())

print(result)
```

    [<Candidate('Phasmaphobia')>]
    ROUND 1
    Candidate                        Votes  Status
    -----------------------------  -------  --------
    Fall Guys                            4  Hopeful
    Animal Crossing: New Horizons        3  Hopeful
    Phasmaphobia                         2  Hopeful
    Grounded                             2  Rejected
    
    ROUND 2
    Candidate                        Votes  Status
    -----------------------------  -------  --------
    Phasmaphobia                         4  Hopeful
    Fall Guys                            4  Hopeful
    Animal Crossing: New Horizons        3  Rejected
    Grounded                             0  Rejected
    
    FINAL RESULT
    Candidate                        Votes  Status
    -----------------------------  -------  --------
    Phasmaphobia                         7  Elected
    Fall Guys                            4  Rejected
    Animal Crossing: New Horizons        0  Rejected
    Grounded                             0  Rejected
    
    

### Best Multiplayer (PvP) Game


```python
# MULT2020 

cans = {"Call of Duty: Modern Warfare":Candidate("Call of Duty: Modern Warfare"),
        "Rogue Company":Candidate("Rogue Company"),
        "Fall Guys":Candidate("Fall Guys")}
MULT2020.replace(cans, inplace=True)

canidates = [Candidate("Call of Duty: Modern Warfare"),Candidate("Rogue Company"),Candidate("Fall Guys")]
ballots = []
i=0
while (i < len(MULT2020)) :
    ballots.append(Ballot(ranked_candidates=MULT2020.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())

print(result)
```

    [<Candidate('Fall Guys')>]
    FINAL RESULT
    Candidate                       Votes  Status
    ----------------------------  -------  --------
    Fall Guys                           7  Elected
    Call of Duty: Modern Warfare        4  Rejected
    Rogue Company                       0  Rejected
    
    

### Best Ongoing Game


```python
# ONGO2020 

cans = {"Destiny 2":Candidate("Destiny 2"),
        "Fortnite":Candidate("Fortnite"),
        "Among Us":Candidate("Among Us"),
        "Apex Legends":Candidate("Apex Legends"),
        "Minecraft":Candidate("Minecraft")}
ONGO2020.replace(cans, inplace=True)

canidates = [Candidate("Destiny 2"),Candidate("Fortnite"), Candidate("Among Us"),
                Candidate("Apex Legends"),Candidate("Minecraft")]
ballots = []
i=0
while (i < len(ONGO2020)) :
    ballots.append(Ballot(ranked_candidates=ONGO2020.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())

print(result)
```

    [<Candidate('Destiny 2')>]
    ROUND 1
    Candidate       Votes  Status
    ------------  -------  --------
    Minecraft           4  Hopeful
    Destiny 2           4  Hopeful
    Among Us            2  Rejected
    Apex Legends        1  Rejected
    Fortnite            0  Rejected
    
    FINAL RESULT
    Candidate       Votes  Status
    ------------  -------  --------
    Destiny 2           6  Elected
    Minecraft           5  Rejected
    Among Us            0  Rejected
    Apex Legends        0  Rejected
    Fortnite            0  Rejected
    
    

### Best DLC for a Game


```python
# DLCS2020 

cans = {"Control: AWE":Candidate("Control: AWE"),
        "House Flipper: Garden Flipper DLC":Candidate("House Flipper: Garden Flipper DLC"),
        "Island Saver: Dinosaur Island":Candidate("Island Saver: Dinosaur Island"),
        "Kingdom Hearts III Re:Mind":Candidate("Kingdom Hearts III Re:Mind"),
        "Minecraft":Candidate("Minecraft"),
        "Pokemon Sword/Shield":Candidate("Pokemon Sword/Shield"),
        "Raft":Candidate("Raft"),
        "Super Smash Bros":Candidate("Super Smash Bros")}
DLCS2020.replace(cans, inplace=True)

canidates = [Candidate("Control: AWE"),Candidate("House Flipper: Garden Flipper DLC"), Candidate("Island Saver: Dinosaur Island"),
                Candidate("Kingdom Hearts III Re:Mind"),Candidate("Minecraft"),Candidate("Pokemon Sword/Shield"),Candidate("Raft"),
                Candidate("Super Smash Bros")]
ballots = []
i=0
while (i < len(DLCS2020)) :
    ballots.append(Ballot(ranked_candidates=DLCS2020.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())

print(result)
```

    [<Candidate('Minecraft')>]
    ROUND 1
    Candidate                            Votes  Status
    ---------------------------------  -------  --------
    Minecraft                                3  Hopeful
    Pokemon Sword/Shield                     2  Hopeful
    House Flipper: Garden Flipper DLC        2  Hopeful
    Raft                                     1  Hopeful
    Super Smash Bros                         1  Hopeful
    Control: AWE                             1  Hopeful
    Island Saver: Dinosaur Island            1  Rejected
    Kingdom Hearts III Re:Mind               0  Rejected
    
    ROUND 2
    Candidate                            Votes  Status
    ---------------------------------  -------  --------
    Pokemon Sword/Shield                     3  Hopeful
    Minecraft                                3  Hopeful
    House Flipper: Garden Flipper DLC        2  Hopeful
    Raft                                     1  Hopeful
    Super Smash Bros                         1  Hopeful
    Control: AWE                             1  Rejected
    Island Saver: Dinosaur Island            0  Rejected
    Kingdom Hearts III Re:Mind               0  Rejected
    
    ROUND 3
    Candidate                            Votes  Status
    ---------------------------------  -------  --------
    Pokemon Sword/Shield                     3  Hopeful
    Minecraft                                3  Hopeful
    House Flipper: Garden Flipper DLC        3  Hopeful
    Raft                                     1  Rejected
    Super Smash Bros                         1  Rejected
    Control: AWE                             0  Rejected
    Island Saver: Dinosaur Island            0  Rejected
    Kingdom Hearts III Re:Mind               0  Rejected
    
    ROUND 4
    Candidate                            Votes  Status
    ---------------------------------  -------  --------
    Minecraft                                4  Hopeful
    Pokemon Sword/Shield                     4  Hopeful
    House Flipper: Garden Flipper DLC        3  Rejected
    Raft                                     0  Rejected
    Super Smash Bros                         0  Rejected
    Control: AWE                             0  Rejected
    Island Saver: Dinosaur Island            0  Rejected
    Kingdom Hearts III Re:Mind               0  Rejected
    
    FINAL RESULT
    Candidate                            Votes  Status
    ---------------------------------  -------  --------
    Minecraft                                6  Elected
    Pokemon Sword/Shield                     5  Rejected
    House Flipper: Garden Flipper DLC        0  Rejected
    Raft                                     0  Rejected
    Super Smash Bros                         0  Rejected
    Control: AWE                             0  Rejected
    Island Saver: Dinosaur Island            0  Rejected
    Kingdom Hearts III Re:Mind               0  Rejected
    
    

### Best Open World Game


```python
# OPWO2020

cans = {"Death Stranding":Candidate("Death Stranding"),
        "Pokemon Sword/Shield":Candidate("Pokemon Sword/Shield")}
OPWO2020.replace(cans, inplace=True)

canidates = [Candidate("Death Stranding"),Candidate("Pokemon Sword/Shield")]
ballots = []
i=0
while (i < len(OPWO2020)) :
    ballots.append(Ballot(ranked_candidates=OPWO2020.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())

print(result)
```

    [<Candidate('Pokemon Sword/Shield')>]
    FINAL RESULT
    Candidate               Votes  Status
    --------------------  -------  --------
    Pokemon Sword/Shield        6  Elected
    Death Stranding             5  Rejected
    
    

### Best Action Game


```python
# ACTI2020 

cans = {"Doom Eternal":Candidate("Doom Eternal"),
        "Hades":Candidate("Hades"),
        "Maneater":Candidate("Maneater")}
ACTI2020.replace(cans, inplace=True)

canidates = [Candidate("Doom Eternal"),Candidate("Hades"), Candidate("Maneater")]
ballots = []
i=0
while (i < len(ACTI2020)) :
    ballots.append(Ballot(ranked_candidates=ACTI2020.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())

print(result)
```

    [<Candidate('Hades')>]
    FINAL RESULT
    Candidate       Votes  Status
    ------------  -------  --------
    Hades               6  Elected
    Doom Eternal        5  Rejected
    Maneater            0  Rejected
    
    

### Best Action Adventure Game


```python
# ACAD2020 

cans = {"Star Wars Jedi: Fallen Order":Candidate("Star Wars Jedi: Fallen Order"),
        "Ori and the Will of the Wisps":Candidate("Ori and the Will of the Wisps")}
ACAD2020.replace(cans, inplace=True)

canidates = [Candidate("Star Wars Jedi: Fallen Order"),Candidate("Ori and the Will of the Wisps")]
ballots = []
i=0
while (i < len(ACAD2020)) :
    ballots.append(Ballot(ranked_candidates=ACAD2020.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())

print(result)
```

    [<Candidate('Star Wars Jedi: Fallen Order')>]
    FINAL RESULT
    Candidate                        Votes  Status
    -----------------------------  -------  --------
    Star Wars Jedi: Fallen Order         9  Elected
    Ori and the Will of the Wisps        2  Rejected
    
    

### Best Strategy Game


```python
# STRA2020 

cans = {"Gears Tactics":Candidate("Gears Tactics"),
        "Microsoft Flight Simulator":Candidate("Microsoft Flight Simulator")}
STRA2020.replace(cans, inplace=True)

canidates = [Candidate("Gears Tactics"),Candidate("Microsoft Flight Simulator")]
ballots = []
i=0
while (i < len(STRA2020)) :
    ballots.append(Ballot(ranked_candidates=STRA2020.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())

print(result)
```

    [<Candidate('Gears Tactics')>]
    FINAL RESULT
    Candidate                     Votes  Status
    --------------------------  -------  --------
    Gears Tactics                    10  Elected
    Microsoft Flight Simulator        1  Rejected
    
    

### Best RPG


```python
# RPGS2020 

cans = {"Final Fantasy VII":Candidate("Final Fantasy VII"),
        "Genshin Impact":Candidate("Genshin Impact"),
        "Maneater":Candidate("Maneater"),
        "Marvel's Avengers":Candidate("Marvel's Avengers"),
        "Minecraft Dungeons":Candidate("Minecraft Dungeons"),
        "Pokemon Sword/Shield":Candidate("Pokemon Sword/Shield"),
        "Star Wars Jedi: Fallen Order":Candidate("Star Wars Jedi: Fallen Order"),
        "Wasteland 3":Candidate("Wasteland 3"),
        "Yakuza: Like a Dragon":Candidate("Yakuza: Like a Dragon")}
RPGS2020.replace(cans, inplace=True)

canidates = [Candidate("Final Fantasy VII"),Candidate("Genshin Impact"), Candidate("Maneater"),
                Candidate("Marvel's Avengers"),Candidate("Minecraft Dungeons"),Candidate("Pokemon Sword/Shield"),Candidate("Star Wars Jedi: Fallen Order"),
                Candidate("Wasteland 3"),Candidate("Yakuza: Like a Dragon")]
ballots = []
i=0
while (i < len(RPGS2020)) :
    ballots.append(Ballot(ranked_candidates=RPGS2020.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())

print(result)
```

    [<Candidate('Star Wars Jedi: Fallen Order')>]
    ROUND 1
    Candidate                       Votes  Status
    ----------------------------  -------  --------
    Star Wars Jedi: Fallen Order        6  Hopeful
    Genshin Impact                      2  Hopeful
    Final Fantasy VII                   2  Rejected
    Wasteland 3                         1  Rejected
    Yakuza: Like a Dragon               0  Rejected
    Maneater                            0  Rejected
    Marvel's Avengers                   0  Rejected
    Minecraft Dungeons                  0  Rejected
    Pokemon Sword/Shield                0  Rejected
    
    FINAL RESULT
    Candidate                       Votes  Status
    ----------------------------  -------  --------
    Star Wars Jedi: Fallen Order        8  Elected
    Genshin Impact                      3  Rejected
    Final Fantasy VII                   0  Rejected
    Wasteland 3                         0  Rejected
    Yakuza: Like a Dragon               0  Rejected
    Maneater                            0  Rejected
    Marvel's Avengers                   0  Rejected
    Minecraft Dungeons                  0  Rejected
    Pokemon Sword/Shield                0  Rejected
    
    

### Best Sports Game


```python
# SPOR2020 

cans = {"FIFA 21":Candidate("FIFA 21"),
        "Dirt 5":Candidate("Dirt 5"),
        "Madden NFL 21":Candidate("Madden NFL 21"),
        "Tony Hawk Pro Skater 1 + 2":Candidate("Tony Hawk Pro Skater 1 + 2")}
SPOR2020.replace(cans, inplace=True)

canidates = [Candidate("FIFA 21"),Candidate("Dirt 5"), Candidate("Madden NFL 21"),
                Candidate("Tony Hawk Pro Skater 1 + 2")]
ballots = []
i=0
while (i < len(SPOR2020)) :
    ballots.append(Ballot(ranked_candidates=SPOR2020.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())

print(result)
```

    [<Candidate('Tony Hawk Pro Skater 1 + 2')>]
    FINAL RESULT
    Candidate                     Votes  Status
    --------------------------  -------  --------
    Tony Hawk Pro Skater 1 + 2        6  Elected
    FIFA 21                           5  Rejected
    Dirt 5                            0  Rejected
    Madden NFL 21                     0  Rejected
    
    

### Best Family/E 10+ Game


```python
# FAMI2020

cans = {"Animal Crossing: New Horizons":Candidate("Animal Crossing: New Horizons"),
        "Fall Guys":Candidate("Fall Guys"),
        "Ori and the Will of the Wisps":Candidate("Ori and the Will of the Wisps")}
FAMI2020.replace(cans, inplace=True)

canidates = [Candidate("Animal Crossing: New Horizons"),Candidate("Fall Guys"), Candidate("Ori and the Will of the Wisps")]
ballots = []
i=0
while (i < len(FAMI2020)) :
    ballots.append(Ballot(ranked_candidates=FAMI2020.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())

print(result)
```

    [<Candidate('Animal Crossing: New Horizons')>]
    ROUND 1
    Candidate                        Votes  Status
    -----------------------------  -------  --------
    Animal Crossing: New Horizons        5  Hopeful
    Fall Guys                            3  Hopeful
    Ori and the Will of the Wisps        3  Rejected
    
    FINAL RESULT
    Candidate                        Votes  Status
    -----------------------------  -------  --------
    Animal Crossing: New Horizons        7  Elected
    Fall Guys                            4  Rejected
    Ori and the Will of the Wisps        0  Rejected
    
    

### Best Remaster/Remake


```python
# REMA2020 

cans = {"Destroy All Humans":Candidate("Destroy All Humans"),
        "Final Fantasy VII":Candidate("Final Fantasy VII"),
        "Kingdoms of Amalur Re-Reckoning":Candidate("Kingdoms of Amalur Re-Reckoning"),
        "Mafia 2":Candidate("Mafia 2"),
        "Resident Evil 3":Candidate("Resident Evil 3")}
REMA2020.replace(cans, inplace=True)

canidates = [Candidate("Destroy All Humans"),Candidate("Final Fantasy VII"), Candidate("Kingdoms of Amalur Re-Reckoning"),
                Candidate("Resident Evil 3"),Candidate("Mafia 2")]
ballots = []
i=0
while (i < len(REMA2020)) :
    ballots.append(Ballot(ranked_candidates=REMA2020.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())

print(result)
```

    [<Candidate('Final Fantasy VII')>]
    ROUND 1
    Candidate                          Votes  Status
    -------------------------------  -------  --------
    Final Fantasy VII                      5  Hopeful
    Resident Evil 3                        5  Hopeful
    Mafia 2                                1  Rejected
    Kingdoms of Amalur Re-Reckoning        0  Rejected
    Destroy All Humans                     0  Rejected
    
    FINAL RESULT
    Candidate                          Votes  Status
    -------------------------------  -------  --------
    Final Fantasy VII                      6  Elected
    Resident Evil 3                        5  Rejected
    Mafia 2                                0  Rejected
    Kingdoms of Amalur Re-Reckoning        0  Rejected
    Destroy All Humans                     0  Rejected
    
    

### Best Game Made by an Indie Studio


```python
# INDI2020 

cans = {"Fall Guys":Candidate("Fall Guys"),
        "Hades":Candidate("Hades"),
        "Carrion 2":Candidate("Carrion 2"),
        "Phasmaphobia":Candidate("Phasmaphobia")}
INDI2020.replace(cans, inplace=True)

canidates = [Candidate("Fall Guys"),Candidate("Hades"), Candidate("Carrion 2"),
                Candidate("Phasmaphobia")]
ballots = []
i=0
while (i < len(INDI2020)) :
    ballots.append(Ballot(ranked_candidates=INDI2020.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())

print(result)
```

    [<Candidate('Hades')>]
    FINAL RESULT
    Candidate       Votes  Status
    ------------  -------  --------
    Hades               6  Elected
    Phasmaphobia        3  Rejected
    Fall Guys           2  Rejected
    Carrion 2           0  Rejected
    
    

### Content Creator of the Year


```python
# CONT2020 

cans = {"Unus Annus by Markiplier and CrankGamePlays":Candidate("Unus Annus by Markiplier and CrankGamePlays"),
        "TimTheTatman":Candidate("TimTheTatman"),
        "DrLupo":Candidate("DrLupo"),
        "Anthony_Kongphan":Candidate("Anthony_Kongphan")}
CONT2020.replace(cans, inplace=True)

canidates = [Candidate("Unus Annus by Markiplier and CrankGamePlays"),Candidate("TimTheTatman"), Candidate("DrLupo"),
                Candidate("Anthony_Kongphan")]
ballots = []
i=0
while (i < len(CONT2020)) :
    ballots.append(Ballot(ranked_candidates=CONT2020.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,ballots)
print(result.get_winners())

print(result)
```

    [<Candidate('TimTheTatman')>]
    ROUND 1
    Candidate                                      Votes  Status
    -------------------------------------------  -------  --------
    TimTheTatman                                       3  Hopeful
    Anthony_Kongphan                                   3  Hopeful
    Unus Annus by Markiplier and CrankGamePlays        3  Hopeful
    DrLupo                                             2  Rejected
    
    ROUND 2
    Candidate                                      Votes  Status
    -------------------------------------------  -------  --------
    Anthony_Kongphan                                   5  Hopeful
    TimTheTatman                                       3  Hopeful
    Unus Annus by Markiplier and CrankGamePlays        3  Rejected
    DrLupo                                             0  Rejected
    
    FINAL RESULT
    Candidate                                      Votes  Status
    -------------------------------------------  -------  --------
    TimTheTatman                                       6  Elected
    Anthony_Kongphan                                   5  Rejected
    Unus Annus by Markiplier and CrankGamePlays        0  Rejected
    DrLupo                                             0  Rejected
    
    

### Game of the Year


```python
cans = {'Star Wars Jedi: Fallen Order':Candidate('Star Wars Jedi: Fallen Order'),
        'Hades':Candidate('Hades'),
        'Ori and the Will of the Wisps':Candidate('Ori and the Will of the Wisps'),
        'Animal Crossing: New Horizons':Candidate('Animal Crossing: New Horizons'),
        'The Last of Us Part 2':Candidate('The Last of Us Part 2'),
        'Doom Eternal':Candidate('Doom Eternal')}
# GOTY2020.replace(cans, inplace=True)

canidates = [Candidate('Star Wars Jedi: Fallen Order'),Candidate('Hades'),Candidate('Ori and the Will of the Wisps'),
                    Candidate('Animal Crossing: New Horizons'),Candidate('The Last of Us Part 2'),Candidate('Doom Eternal')]
dBallots = []
i=0
while (i < len(GOTY2020)) :
    dBallots.append(Ballot(ranked_candidates=GOTY2020.iloc[i].tolist()))
    i += 1

result = prv.instant_runoff_voting(canidates,dBallots)
print(result.get_winners())
print()
print(result)
```

    [<Candidate('Star Wars Jedi: Fallen Order')>]
    
    ROUND 1
    Candidate                        Votes  Status
    -----------------------------  -------  --------
    Star Wars Jedi: Fallen Order         5  Hopeful
    Hades                                3  Hopeful
    Ori and the Will of the Wisps        1  Hopeful
    Animal Crossing: New Horizons        1  Rejected
    The Last of Us Part 2                1  Rejected
    Doom Eternal                         0  Rejected
    
    FINAL RESULT
    Candidate                        Votes  Status
    -----------------------------  -------  --------
    Star Wars Jedi: Fallen Order         6  Elected
    Hades                                4  Rejected
    Ori and the Will of the Wisps        1  Rejected
    Animal Crossing: New Horizons        0  Rejected
    The Last of Us Part 2                0  Rejected
    Doom Eternal                         0  Rejected
    
    


```python
GOTY2020
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Game of the Year 2020 [Choice 1]</th>
      <th>Game of the Year 2020 [Choice 2]</th>
      <th>Game of the Year 2020 [Choice 3]</th>
      <th>Game of the Year 2020 [Choice 4]</th>
      <th>Game of the Year 2020 [Choice 5]</th>
      <th>Game of the Year 2020 [Choice 6]</th>
    </tr>
    <tr>
      <th>Timestamp</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2020-12-07 17:44:53</th>
      <td>Star Wars Jedi: Fallen Order</td>
      <td>Ori and the Will of the Wisps</td>
      <td>Hades</td>
      <td>Doom Eternal</td>
      <td>The Last of Us Part 2</td>
      <td>Animal Crossing: New Horizons</td>
    </tr>
    <tr>
      <th>2020-12-07 17:53:37</th>
      <td>Star Wars Jedi: Fallen Order</td>
      <td>Ori and the Will of the Wisps</td>
      <td>Doom Eternal</td>
      <td>Animal Crossing: New Horizons</td>
      <td>Hades</td>
      <td>The Last of Us Part 2</td>
    </tr>
    <tr>
      <th>2020-12-08 20:16:38</th>
      <td>Ori and the Will of the Wisps</td>
      <td>Animal Crossing: New Horizons</td>
      <td>The Last of Us Part 2</td>
      <td>Star Wars Jedi: Fallen Order</td>
      <td>Hades</td>
      <td>Doom Eternal</td>
    </tr>
    <tr>
      <th>2020-12-08 20:18:55</th>
      <td>Star Wars Jedi: Fallen Order</td>
      <td>Animal Crossing: New Horizons</td>
      <td>The Last of Us Part 2</td>
      <td>Ori and the Will of the Wisps</td>
      <td>Doom Eternal</td>
      <td>Hades</td>
    </tr>
    <tr>
      <th>2020-12-10 20:07:31</th>
      <td>Animal Crossing: New Horizons</td>
      <td>Hades</td>
      <td>Star Wars Jedi: Fallen Order</td>
      <td>Ori and the Will of the Wisps</td>
      <td>Doom Eternal</td>
      <td>The Last of Us Part 2</td>
    </tr>
    <tr>
      <th>2020-12-11 22:36:17</th>
      <td>Hades</td>
      <td>Star Wars Jedi: Fallen Order</td>
      <td>Doom Eternal</td>
      <td>Ori and the Will of the Wisps</td>
      <td>Animal Crossing: New Horizons</td>
      <td>The Last of Us Part 2</td>
    </tr>
    <tr>
      <th>2020-12-12 04:53:10</th>
      <td>Hades</td>
      <td>Animal Crossing: New Horizons</td>
      <td>The Last of Us Part 2</td>
      <td>Ori and the Will of the Wisps</td>
      <td>Doom Eternal</td>
      <td>Star Wars Jedi: Fallen Order</td>
    </tr>
    <tr>
      <th>2020-12-12 13:57:23</th>
      <td>Star Wars Jedi: Fallen Order</td>
      <td>Hades</td>
      <td>Ori and the Will of the Wisps</td>
      <td>Doom Eternal</td>
      <td>The Last of Us Part 2</td>
      <td>Animal Crossing: New Horizons</td>
    </tr>
    <tr>
      <th>2020-12-12 14:31:30</th>
      <td>Star Wars Jedi: Fallen Order</td>
      <td>Hades</td>
      <td>Doom Eternal</td>
      <td>Ori and the Will of the Wisps</td>
      <td>Animal Crossing: New Horizons</td>
      <td>The Last of Us Part 2</td>
    </tr>
    <tr>
      <th>2020-12-12 18:53:24</th>
      <td>Hades</td>
      <td>The Last of Us Part 2</td>
      <td>Doom Eternal</td>
      <td>Animal Crossing: New Horizons</td>
      <td>Ori and the Will of the Wisps</td>
      <td>Star Wars Jedi: Fallen Order</td>
    </tr>
    <tr>
      <th>2020-12-12 19:36:41</th>
      <td>The Last of Us Part 2</td>
      <td>Star Wars Jedi: Fallen Order</td>
      <td>Hades</td>
      <td>Ori and the Will of the Wisps</td>
      <td>Doom Eternal</td>
      <td>Animal Crossing: New Horizons</td>
    </tr>
  </tbody>
</table>
</div>


