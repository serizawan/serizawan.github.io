---
layout: single
title: "The Dwarves and Hats Puzzle"
date: 2023-04-17
categories: Puzzle
permalink: /:categories/:title/
header:
  teaser: /assets/images/posts/teasers/dwarves.png
---

<link rel="stylesheet" href="{{ '/assets/css/custom.css' | relative_url }}">

Difficulty: ⭐⭐⭐

A wicked sorcerer has captured ten dwarves and challenges them with a logical puzzle.

The ten dwarves are forced to queue in a straight line, with the tallest dwarf at the back and the shortest dwarf at the front.

The sorcerer places either a black hat or a white hat on each dwarf's head at his own discretion. There are no restrictions on the number of hats of each color, so any combination of black and white hats is allowed. There are 2^10 (or 1024) possible setups. 

Each dwarf can see the color of the hats worn by the dwarves in front of him, but cannot see neither the color of his own hat nor the hat color of the dwarves behind him.

The sorcerer informs the dwarves that he will ask each of them, starting with the tallest, to guess the color of their own hat. If a dwarf guesses correctly, he will be set free. If a dwarf guesses incorrectly, he will be turned into a toad. Dwarves hear the claim of their preceding companions. The dwarves are allowed to confer before the sorcerer places hats on their head. However once the guessing begins, they may not communicate with one another in any way other than by stating within a few seconds their hat's color once using a neutral voice.

What strategy can the dwarves craft and apply to maximize the number of saved dwarves? 

{% include figure image_path="/assets/images/posts/main/dwarves_and_hats_puzzle_my_version.png" alt="A snapshot of dwarves playing their destiny" caption="A snapshot of dwarves playing their destiny." %}

*Spoiler alert*: The sections below walkthrough solutions of this riddle. Close the page if you want to take time thinking about your own way.

I was asked this riddle when I was a teenager. I was amazed by how powerful the best strategy dwarves could craft was and how this collaborative problem solving was interesting in term of thought process. Since then, I have kept asking this brain teaser to my fellows who were fond of puzzles and I was surprised how many different strategies they could think of, some more or less efficient but always recreational.

Despite it is not enforced in the statement, we can add the condition that the sorcerer can listen to the dwarves strategy discussion phase to have them failed as much as possible in order to prevent situational guess. We can even add dwarves don't know they are monitored (so that they don't try any brain). We will evaluate dwarves strategies when they encounter the "worst-case" pattern to their algorithm.

Let's walk through the strategies starting from the less efficient to the best one! Note that we estimate the efficiency of a strategy regarding the number of certainly saved dwarves. Lucky guess (where dwarves are not 100% sure to be saved) are counted as failures. We will still mention a lucky score in order to decide ranking in case of equality on the previous metric.

## The *one color* strategy ![Rate](https://progress-bar.dev/0/?title=Rate&width=100&color=babaca)

Here the dwarves pick a color during the strategy phase. Once the guessing phase starts, they claim the agreed color one after the other. As the sorcerer can listen to them, he will simply take care setting the color's hat to the remaining one causing the metamorphosis of all of them without letting even them a single chance to pass.

The success rate is 0% and the success rate with luck is 0%.

## The *random* strategy ![Rate](https://progress-bar.dev/0/?title=Rate&width=100&color=babaca)

Now the dwarves just take their decision randomly once the guess phase starts. It is still a 0% success rate as none is sure of their guess but at least the sorcerer cannot prevent them from succeeding by luck with an appropriate preset-up. They can hopefully expect to save half of them. So this option is slightly better than the former one.

The success rate is 0% and the success rate with luck is 50%.

## The *max* strategy ![Rate](https://progress-bar.dev/50/?title=Rate&width=100&color=babaca)

As dwarf #1 can see 9 hats in front of him, he will necessarily see one predominant color. He will sacrify himself to provide others this information by claiming this color as his own. Following dwarves will then walk into his footsteps. A wicked sorcerer would then put half white, half black hats to be sure that at most only 50% are saved (and certainly saved).

The success rate is 50% and the success rate with luck is 50%.

{% include figure image_path="/assets/images/posts/main/dwarves_and_hats_puzzle_max_strategy.png" alt="An example of dwarves status after they applied the max strategy." caption="An example of dwarves status after they applied the max strategy." %}

## The *neighbour* strategy ![Rate](https://progress-bar.dev/50/?title=Rate&width=100&color=babaca)

Dwarves agree that every odd dwarfs will tell the next dwarf's hat color to rescue him by sacrifying himself.

Hence, dwarves #2, #4, #6, #8 and #10 are certainly saved. By alternating the color's hat, the sorcerer can certainly have odd numbered dwarves failed.

The success rate is 50% and the success rate with luck is 50%.

## The *two-in-a-row* strategy ![Rate](https://progress-bar.dev/60/?title=Rate&width=100&color=babaca)

The dwarves agree on the following strategy: The first dwarf looks at the next two hats. If they have the same color he claims "Black" otherwise he claims "White". He sacrifies himself to give information to his two next fellows.

Now the second dwarf knows if he has the same hat's color as the next one or if it differs based on the martyr dwarf information. He then can infer his own and save himself. The third dwarf also know the similarity (or disimilarity) between hats and has heared the previous guess, he can then deduce his own.

Repeating this scenario leads to:
  - Sacrifying dwarf #1 to save dwarves #2 and #3
  - Sacrifying dwarf #4 to save dwarves #5 and #6
  - Sacrifying dwarf #7 to save dwarves #8 and #9

So 6 dwarves are certainly saved. Sorcerer can configure the hats to have #1, #4 and #7 miss certainly.

Dwarf #10 can try a random guess and hopefully pass the test.

The success rate is 60% and the success rate with luck is 65%.

## The *advanced two-in-a-row* strategy ![Rate](https://progress-bar.dev/70/?title=Rate&width=100&color=babaca)
The dwarves leverage the previous "two-in-a-row" technique except they base their encoding language after the hat's assignment on the 10th dwarf hat color:
- If 10th dwarf hat is white, they will pick the following translation mapper: White -> Two next hats have the same color and Black -> Two next hats have different colors.
- If 10th dwarf hat is black, they will pick the opposite translation mapper: White -> Two next hats have different colors and Black -> Two next hats have the same colors.

#1 to #9 see the #10 hat's color and know the translation dictionnary, they can apply the previous strategy. But now, dwarf #10 has heard dwarves #2 and #3 colors and deduce the mapper picked by dwarf #1 which gives him his own hat color!

The success rate is 70% and the success rate with luck is 70%.

## The *binary* strategy ![Rate](https://progress-bar.dev/70/?title=Rate&width=100&color=babaca)

The dwarves agree that they will sacrify the first 3 dwarves in order to encode the number of white hat on the next 7 heads. Using black as 0 and white as 1 alphabet, they can encode up to 2^3 - 1 = 7 which is sufficient.

The first three dwarves are sacrified but now #4 dwarf knows how many white hats there are in total. He can infer his own color. Dwarf #5 update the count based on the previous dwarf guess and also infer his own. Step by step all dwarfs can rightly guess their color.

The success rate is 70% and the success rate with luck is 70%.

Note that encoding the number of hat color in minority leads to:
- Encode 0, 1, 2, 3, 4 for 8 dwarves (hence 5 values with 2 remaining first dwarf which is NOT possible)
- Encode 0, 1, 2, 3 for 7 dwarves (hence 4 values which requires only 2 dwarves, the last can try a random guess which is slightly better than the standard binary strategy)
- Encode 0, 1, 2, 3 for 6 dwarves (hence 4 values which requires only 2 dwarves, the last two can apply a neighbour strategy, this leads to the same efficiency as the standard binary strategy)

## The *combined* strategy ![Rate](https://progress-bar.dev/80/?title=Rate&width=100&color=babaca)
Here, dwarves combine two strategies to reach a better efficiency:
- The binary strategy (using white=1, black=0 language)
- The two-in-a-row strategy

During the strategy-craft time, dwarves agree that the first two dwarves (#1, #2) adapt their strategy on the next two dwarf (#3, #4) hats similarity once the hat assignement is completed. If dwarves #3 and #4:
- (A) have similar hat color, they will encode in binary the number of hat's color in minority on the last 6 hats.
- (B) have different hat color, they will encode in binary the number of hat's color in majority on the last 6 hats minus 3.


|                                 | #1 and #2 encoding if #3 and #4 identical | #1 and #2 encoding if #3 and #4 different |
|---------------------------------|-------------------------------------------|-------------------------------------------|
| hat color's pool sizes: 0 and 6 | BB (0)                                    | WW (3)                                    |
| hat color's pool sizes: 1 and 5 | BW (1)                                    | WB (2)                                    |
| hat color's pool sizes: 2 and 4 | WB (2)                                    | BW (1)                                    |
| hat color's pool sizes: 3 and 3 | WW (3)                                    | BB (0)                                    |

Dwarves #3 and #4 observes the next 6 dwarves and compare the above table to what they see (notice that on the same row, values always differ). They deduce if their hats are identical or not and apply the "two-in-a-row" strategy to save their lives!

Dwarves #5 heared the #3 and #4 hat's color similarity and know which column to refer. He and his following fellows can apply a simple binary strategy one after the other because they know the hats color pool sizes and can infer their own to make it right.

## The *best* strategy ![Rate](https://progress-bar.dev/90/?title=Rate&width=100&color=babaca)

Here the dwarves ask the first one to sacrify and communicate the white hat's parity to the group using the below encoding:
  - "white" for "# of white hats is even"
  - "black" for "# of white hats is odd"

Now, the second dwarf observes the 8 remaining hats, counts the # of white hats and deduce their own hat color by checking if # white hats parity matches communicated information (hence his is black) or not (hence his is white).

The third dwarf updates the # of white hats parity in their slice based on the second dwarf guess (they know to be true). Again, they can deduce their own hat's color with the same reasoning.

The fourth dwarf updates the # of white hats parity in their slice based on second and third dwarves guesses. They then recoup theirs.

Successively, dwarfs keep updating the # of white hats parity based on first dwarf information and previous dwarves guesses.

Following this pattern, dwarves #2 to #10 can rightly guess their hat's color.

The success rate is 90%. First dwarf is doomed by the wicked sorcerer preset-up. Success rate with luck is 90%.


# What I love about this puzzle
There are not so many puzzles where you can progressively find that variety of possible solutions with increasing success levels that it doesn't make this puzzle a black-and-white case (pun intended) where you get it only right or wrong.

The problem is posed in such a way that the puzzler doesn't focus on the best strategy but rather adopts a "can-we-do-better" way of thinking which is common to opitmization problems. I like this mindset as it allows very young puzzlers to find solutions as well as experienced one.


# FAQ
## Can dwarves spit, whistle, blow or touch each other to communicate information to other dwarves?
No! As mentionned in the problem statement: (Dwarves) may not communicate with one another IN ANY OTHER WAY than by stating within a few seconds their hat's color. Meaning also, they can't use their response timing to infer anything to their partners.

## How smart are the dwarves and the sorcerer?
They are both considered pure logicians which means they always perfectly apply their defined plan without any concern of possible mistakes. Note that dwarf don't know they are listened by the sorcered during the strategy-craft time which forces them to assume they will get a random assigment. Also, they can't try braining strategies like: Let's agree on "Black" as the claimed color and switching to "White" at guess time knowing that the sorcered would try to have them failed! That would be a nice brain (efficiency is 100%) but that would also suppose the sorcerer is not enough smart to anticipate a brain. If we suppose them equally smart, they would end in a dead-end brain loop where either all or none would be saved (which actually is not a bad bet).

## Is the problem physically possible?