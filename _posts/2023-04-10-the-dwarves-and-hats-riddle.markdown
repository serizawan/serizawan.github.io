---
layout: single
title: "The Dwarves and Hats Riddle"
date: 2023-04-10
categories: riddles
header:
  teaser: /assets/images/posts/teasers/dwarves.png
---

Difficulty: ⭐⭐⭐

A wicked sorcerer has captured ten dwarves and decides to challenge them with a logical puzzle.

The ten dwarves are forced to queue in a straight line, with the tallest dwarf at the back and the shortest dwarf at the front.

The sorcerer puts either a black hat or a white hat on each dwarf's head at his discretion. Any combinations of black and white hats are allowed without any constraint on the number of hats by colour.

Each dwarf can see the color of the hats of the dwarves in front of him, but cannot see neither the color of his own hat nor the hats of the dwarves behind him.

The sorcerer informs the dwarves that he will ask each of them, starting with the tallest, to guess the color of his own hat. If a dwarf guesses correctly, he will be set free. If a dwarf guesses incorrectly, he will be turned into a toad. Dwarves hear the guess (and the rightness) of their previous fellows. The dwarves are allowed to confer before the sorcerer puts hats on their head. But once the guessing begins, they may not communicate with one another in any way.

What strategy can the dwarves use to maximize the number of dwarves who guess correctly, and how many dwarves can they guarantee will be set free?

⚠️ Spoiler alert: The sections below this image walkthrough solutions of this riddle.  

{% include figure image_path="/assets/images/posts/main/dwarves_and_hats_puzzle.png" alt="A snapshot of dwarves playing for their destiny" caption="A snapshot of dwarves playing for their destiny." %}

I was asked this riddle when I was a teenager. I was amazed by the effectiveness of the best strategy the dwarves could craft and how this collaborative problem solving was interesting in term of thought process. Since then, I have kept asking this brain teaser to my fellows who were fond of riddles and I was surprised how many different strategies they could craft some more or less powerful.

Despite it is not enforced in the statement, we can add the condition that sorcerer can listen to the dwarves strategy to have them failed as much as possible in order to prevent situational guess. So that we will evaluate dwarves strategies when they encounter the "worst-case" pattern.

Let's walk through the strategies starting from the less efficient to the best one! Note that we estimate the efficiency of a strategy regarding the number of certainly saved dwarves. Lucky guess (meaning the dwarf is not 100% sure to be saved) are counted as failures. We will still mention a lucky score in order to decide rank in case of equality on the previous metric.

## The *one color* strategy
![Rate](https://progress-bar.dev/0/?title=Rate&width=150&color=babaca)

Here the dwarves pick a color during the strategy phase. Once the guessing phase starts, they claim the agreed color one after the other. As the sorcerer can listen to them, he will simply take care setting the color's hat to the remaining one causing the metamorphosis of all of them without letting even them a single chance to pass.

The efficiency is 0% and the efficiency with luck is 0%.

## The *random* strategy
![Rate](https://progress-bar.dev/0/?title=Rate&width=150&color=babaca)

Now the dwarves just take their decision randomly once the guess phase starts. It is still a 0% efficiency as none is sure of his guess but at least the sorcerer cannot prevent them from succeeding by luck with an appropriate set-up. They can hopefully expect to save half of them. So this option is slightly better than the former one.

The efficiency is 0% and the efficiency with luck is 50%.

## The *max* strategy
![Rate](https://progress-bar.dev/50/?title=Rate&width=150&color=babaca)

As dwarf #1 will see 9 hats in front of him, he will necessarily see one predominant color. He will sacrify himself to provide others this information. Following dwarves will then claim this color as their own. A wicked sorcered would then put half white, half black hats to be sure that at most only 50% are saved (and certainly saved).

The efficiency is 50% and the efficiency with luck is 50%.

## The *neighbour* strategy
![Rate](https://progress-bar.dev/50/?title=Rate&width=150&color=babaca)

Dwarves agree that every odd dwarfs will tell the next dwarf's hat color to rescue him by sacrifying himself.

Hence, dwarves #2, #4, #6, #8 and #10 are certainly saved. By alternating the color's hat, the sorcered can certainly have odd numbered dwarves failed.

The efficiency is 50% and the efficiency with luck is 50%.

## The *two-in-a-row* strategy
![Rate](https://progress-bar.dev/60/?title=Rate&width=150&color=babaca)

The dwarves agree on the following strategy: The first dwarf looks at the next two hats. If they have the same color he claims "Black" otherwise he claimes "White". He sacrifies himself to give information to others.

Now the second dwarf knows if he has the same hat's color as the next fellow or if it differs. He then can infer his own and save himself. The third dwarf also know the similarity information and has heared the previous guess, he can then deduce his own.

Repeating this scenario leads to:
  - Sacrifying dwarf #1 to save dwarves #2 and #3
  - Sacrifying dwarf #4 to save dwarves #5 and #6
  - Sacrifying dwarf #7 to save dwarves #8 and #9

So 6 dwarves are certainly saved. Sorcerer can configure the hats to have #1, #4 and #7 miss certainly.

Dwarf #10 can try a random guess and hopefully pass the guess.

The efficiency is 60% and the efficiency with luck is 65%.

## The *binary* strategy
![Rate](https://progress-bar.dev/70/?title=Rate&width=150&color=babaca)

The dwarves agree that they will save the first 3 dwarves in order to encode the number of white hat in the next 7 heads. Using black as 0 and white as 1, they can encode up to 7 which is sufficient.

The first three dwarves are sacrified but now #4 dwarf knows how many white hats there are in total. He can infer his own color. Dwarf #5 update the count based on the previous dwarf guess and also infer his own. Step by step all dwarfs can rightly guess their color.

The efficiency is 70% and the efficiency with luck is 70%.

## The *best* strategy
![Rate](https://progress-bar.dev/90/?title=Rate&width=150&color=babaca)

If you can think of any innovative strategy not listed here please comment, I will add your proposal to the list!

## Others strategies:
### Braining the sorcerer

## Elaborate on strategies