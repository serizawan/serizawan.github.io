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

A wicked sorcerer has captured ten dwarves and decides to challenge them with a logical puzzle.

The ten dwarves are forced to queue in a straight line, with the tallest dwarf at the back and the shortest dwarf at the front.

The sorcerer puts either a black hat or a white hat on each dwarf's head at his own discretion. Any combinations of black and white hats are allowed without any constraint on the number of hats by colour.

Each dwarf can see the color of the hats of the dwarves in front of him, but cannot see neither the color of his own hat nor the hats' color of the dwarves behind him.

The sorcerer informs the dwarves that he will ask each of them, starting with the tallest, to guess the color of their own hat. If a dwarf guesses correctly, he will be set free. If a dwarf guesses incorrectly, he will be turned into a toad. Dwarves hear the guess (and the rightness) of their previous fellows. The dwarves are allowed to confer before the sorcerer puts hats on their head. But once the guessing begins, they may not communicate with one another in any way than by claiming their hat's color once with a neutral voice (they can't touch each other, wait for seconds, whistle...).

What strategy can the dwarves use to maximize the number of correct guesses, and how many dwarves can they guarantee will be set free? 

{% include figure image_path="/assets/images/posts/main/dwarves_and_hats_puzzle_my_version.png" alt="A snapshot of dwarves playing for their destiny" caption="A snapshot of dwarves playing for their destiny." %}

*Spoiler alert*: The sections below walkthrough solutions of this riddle. Close the page if you want to take time thinking about your own way.

I was asked this riddle when I was a teenager. I was amazed by how powerful the best strategy dwarves could craft was and how this collaborative problem solving was interesting in term of thought process. Since then, I have kept asking this brain teaser to my fellows who were fond of puzzles and I was surprised how many different strategies they could think of, some more or less efficient but always recreational.

Despite it is not enforced in the statement, we can add the condition that the sorcerer can listen to the dwarves strategy discussion phase to have them failed as much as possible in order to prevent situational guess. We can even add dwarves don't know they are monitored (so that they don't try any brain). We will evaluate dwarves strategies when they encounter the "worst-case" pattern to their algorithm.

Let's walk through the strategies starting from the less efficient to the best one! Note that we estimate the efficiency of a strategy regarding the number of certainly saved dwarves. Lucky guess (where dwarves are not 100% sure to be saved) are counted as failures. We will still mention a lucky score in order to decide ranking in case of equality on the previous metric.

## The *one color* strategy
![Rate](https://progress-bar.dev/0/?title=Rate&width=150&color=babaca)

Here the dwarves pick a color during the strategy phase. Once the guessing phase starts, they claim the agreed color one after the other. As the sorcerer can listen to them, he will simply take care setting the color's hat to the remaining one causing the metamorphosis of all of them without letting even them a single chance to pass.

The success rate is 0% and the success rate with luck is 0%.

## The *random* strategy
![Rate](https://progress-bar.dev/0/?title=Rate&width=150&color=babaca)

Now the dwarves just take their decision randomly once the guess phase starts. It is still a 0% success rate as none is sure of their guess but at least the sorcerer cannot prevent them from succeeding by luck with an appropriate preset-up. They can hopefully expect to save half of them. So this option is slightly better than the former one.

The success rate is 0% and the success rate with luck is 50%.

## The *max* strategy
![Rate](https://progress-bar.dev/50/?title=Rate&width=150&color=babaca)

As dwarf #1 can see 9 hats in front of him, he will necessarily see one predominant color. He will sacrify himself to provide others this information by claiming this color as his own. Following dwarves will then walk into his footsteps. A wicked sorcered would then put half white, half black hats to be sure that at most only 50% are saved (and certainly saved).

The success rate is 50% and the success rate with luck is 50%.

## The *neighbour* strategy
![Rate](https://progress-bar.dev/50/?title=Rate&width=150&color=babaca)

Dwarves agree that every odd dwarfs will tell the next dwarf's hat color to rescue him by sacrifying himself.

Hence, dwarves #2, #4, #6, #8 and #10 are certainly saved. By alternating the color's hat, the sorcered can certainly have odd numbered dwarves failed.

The success rate is 50% and the success rate with luck is 50%.

## The *two-in-a-row* strategy
![Rate](https://progress-bar.dev/60/?title=Rate&width=150&color=babaca)

The dwarves agree on the following strategy: The first dwarf looks at the next two hats. If they have the same color he claims "Black" otherwise he claims "White". He sacrifies himself to give information to his two next fellows.

Now the second dwarf knows if he has the same hat's color as the next one or if it differs based on the martyr dwarf information. He then can infer his own and save himself. The third dwarf also know the similarity (or disimilarity) between hats and has heared the previous guess, he can then deduce his own.

Repeating this scenario leads to:
  - Sacrifying dwarf #1 to save dwarves #2 and #3
  - Sacrifying dwarf #4 to save dwarves #5 and #6
  - Sacrifying dwarf #7 to save dwarves #8 and #9

So 6 dwarves are certainly saved. Sorcerer can configure the hats to have #1, #4 and #7 miss certainly.

Dwarf #10 can try a random guess and hopefully pass the test.

The success rate is 60% and the success rate with luck is 65%.

## The *binary* strategy
![Rate](https://progress-bar.dev/70/?title=Rate&width=150&color=babaca)

The dwarves agree that they will sacrify the first 3 dwarves in order to encode the number of white hat on the next 7 heads. Using black as 0 and white as 1 alphabet, they can encode up to 2^3 - 1 = 7 which is sufficient.

The first three dwarves are sacrified but now #4 dwarf knows how many white hats there are in total. He can infer his own color. Dwarf #5 update the count based on the previous dwarf guess and also infer his own. Step by step all dwarfs can rightly guess their color.

The success rate is 70% and the success rate with luck is 70%.

## The *best* strategy
![Rate](https://progress-bar.dev/90/?title=Rate&width=150&color=babaca)

Here the dwarves ask the first one to sacrify and communicate the white hat's parity to the group using the below encoding:
  - "white" for "# of white hats is even"
  - "black" for "# of white hats is odd"

Now, the second dwarf observes the 8 remaining hats, counts the # of white hats and deduce their own hat color by checking if # white hats parity matches communicated information (hence his is black) or not (hence his is white).

The third dwarf updates the # of white hats parity in their slice based on the second dwarf guess (they know to be true). Again, they can deduce their own hat's color with the same reasoning.

The fourth dwarf updates the # of white hats parity in their slice based on second and third dwarves guesses. They then recoup theirs.

Successively, dwarfs keep updating the # of white hats parity based on first dwarf information and previous dwarves guesses.

Following this pattern, dwarves #2 to #10 can rightly guess their hat's color.

The success rate is 90%. First dwarf is doomed by the wicked sorcerer preset-up. Success rate with luck is 90%.