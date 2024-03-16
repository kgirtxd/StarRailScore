# StarRailScore

_SRS_ scoring criteria for Honkai: Star Rail.

## Introduction

_SRS_ judges the number of effective affixes of the relic according to the typical positioning of the role, and calculates the score of the relic according to the weight of different affixes. _SRS_ provides the theoretical highest score to calculate the normalized final score. The main affix and sub affixes each account for 50% of the score.


## Calculation

### Main affix and sub affixes

The normalized score of the main affix is calculated by the level and weight, and the level 0 to 15 correspond to the base value 1/16 to 16/16 respectively. The weight is obtained by looking up the table, and the `main` field is the weight of the main affixes. For example: the weight of the main affixes at level 12 is 0.9, and the normalized score is (12+1)/16 \* 0.9 = 0.61.

The normalized score of the sub affixes is calculated by the number of base values, the number of boost values (x 0.1), and the weight. The `weight` field is the weight of the sub affixes. For example: sub affixes 1 has 3 base values, 2 boost values, and 1 weight; sub affixes 2 has 1 base value, 0.5 weight, and the original score is 3.2 \* 1 + 1.0 \* 0.5 = 3.7. If the `max` field is 8.0, then the normalized score is 3.7/8.0 = 0.46.

### _SRS-N_

_SRS-N_ uses the same weight to combine the scores of the main affix and the sub affixes. According to the example in the previous section, the total score is 0.61 \* 0.5 + 0.46 \* 0.5 = 0.54, which can be expressed as `0.54` `54%` `5.4/10`.

### _SRS-M_

_SRS-M_ takes the square root of the result of _SRS-N_, which has the characteristic that the improvement speed gradually slows down as the score increases. For example, if the result of _SRS-N_ is 0.54, then the result of _SRS-M_ is 0.54^0.5 = 0.73, which can be expressed as `0.73` `73%` `7.3/10`.
