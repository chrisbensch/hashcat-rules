# hashcat-rules


## What is this? 

This is a suite of rules for hashcat, to be used for cracking hashes in educational, pentesting, or hobby settings. More specifically, it is a “super rule” made by testing ~76 million pre-existing rules written/generated by other people (as well as my own set of ~70 million PACK generated rules and 1,000,000,000 randomly generated ones) against 100 million hashes using two different wordlists, then sorting the resulting data by how often each rule cracked a hash. 


## There are so many good rule lists. Why make another? 

While there are a ton of awesome rule lists made by the cracking community, there just aren't a lot of them (at least among publicly-available ones that I'm aware of) that are a meta-analysis of other rulesets in this fashion, and I really like the idea since it makes the resulting list backed by objective data as to how often each rule is likely to be useful. Techtrip.rule (https://forum.hashkiller.io/index.php?threads/hashcat-rules.41361/) is based on this idea (as is OneRuleToRuleThemAll to a lesser extent), but I wanted to see it applied to more recent data and on a larger scale, which is how this project came to be. 


## What's in the “unicorn generated” folder? 

These are rules generated with either PACK or hashcat's built-in rule generation function that cracked at least one hash with rockyou.txt after every pre-existing rule had been tried and failed. While not particularly efficient or meant to be used as a stand-alone ruleset like the main one, they're worth a try for “difficult” hashes that you've already exhausted other rulesets on. 


## What are the “sequential” files about? 

You may have noticed that each rule folder has a corresponding zip file with the word “sequential” in the name. The purpose for these is simple: 

Since each rule file simply contains the top N rules per its size, every file effectively contains every other one under it in the hierarchy (for example, unicorn10k contains the entirety of unicorn5k, unicorn1k, etc.) 

Now, what it you've already run unicorn5k and now want to run unicorn10k with the same wordlist? Normally, half of the cycles you use in doing so will be redundant. 

Instead, you can simply unzip “unicorn rules sequential” and run “5k-10k.rule”. This contains every rule from 5000th up to 10000th in the list without the need to repeat any rules that have already been used, which can save a lot of time and resources on larger projects. 

The “sequential” name comes from the fact that you could, in theory, run these sequentially with the option to stop (or continue moving up the hierarchy) at any time, all without wasting any cycles by re-running rules that have already been used. 


## What about the “full” files?

These simply list all of the rules (one is exclusively generated by me, the other is all of the rules) that cracked at least one hash in testing. They're ordered by frequency just like the smaller rule files and can be used to create your own rulesets of custom length. 


## How many rules does each file have?

Most of the rule files are self-explanatory. The exceptions are UnicornSmol (100 rules), TheOneTrueUnicorn (52,000 rules), DiveIcorn (100,000 rules), UnicornLorge (400,000 rules), Pantacorn (600,000 rules), and SuperUnicorn (the largest rule file besides the "full" ones -- 1,077,833 rules). 


## What hashes did you use? Can I download them? 

All of the hashes used to make this rule are publicly-available and can be downloaded here as either NTLM or SHA-1 (I chose NTLM for efficiency):  https://haveibeenpwned.com/Passwords

For the sake of time, I only used the top 100 million hashes, though the full list contains over 800 million. 


## What rules did you use? Can I download them?

All of the pre-existing rules used to make this are publicly-available and can be downloaded. They include: 

- OneRuleToRuleThemAll
- pantagrule (all variants)
- NSAKEY dive rules as well as the original dive.rule
- all of hashcat's included rules
- all of blandyuk's rules included with hashcat GUI
- d3ad0ne/d3adhob0, hob064 
- evil.rule
-  the fordy rules
-  generated, generated2-full, and generated3
-  top_5000.rule and toprules2020
- prince_generated/optimized
-  Korelogic's rules
- Robot's rules
- Shooter3k's public rules
- Skallman's rules
- Techtrip's rules
-  hashes-org-rules
- ProbWL rules
- Pengo's rules
- Dipepe's rules
- Nyxgeek's rules, 
-  and the miscellaneous ones that don’t fit under any above category: 
-efensive.rule, 10k rules, 1940-2017, email_by_simplify, expanded-cutb-clean.rule, giveen_combo.rule, cyclone_250, haku34k.rule, huge.rule, kamaji34k.rule, mail_Milzo.rule, newtt v1 and v2, OptimizedUpToDate.rule, Oscommerce.rule, PrependRockYou60000, toggles5, yubaba64, wpa.rule, specific.rule and specific_2
(not an exhaustive list but I believe that names most of the major ones)     

I downloaded them from the link in this doc: (https://docs.google.com/spreadsheets/d/1qQNwggWIWtL-m0EYrRg_vdwHOrZCY-SnWcYTwQN0fMk/edit#gid=1952927995) and from hashkiller user UncleJay's link in this thread: (https://forum.hashkiller.io/index.php?threads/user-recommended-wordlists-rules.50001/) but I'm sure they can be obtained from numerous sources. 


## What wordlists did you use? Can I download them? 

I used the canonical rockyou.txt to validate and test all the rules against every hash, as well as cyclone_hk.txt to test the top 2.5-ish million rules from that run against every hash. These can both be found at weakpass.com for either direct download or torrent, as well as many other places on the web. 

Additionally, hashmob's “large combined” and “user full” lists were used to generate rules with PACK. While these are dynamic and any future version(s) downloaded won't be exactly the same as the ones used for this project, you can access them here: https://hashmob.net/resources/hashmob


## Why those resources? Why didn't you use [insert hash list/word list/ rule list]?

I chose the hashes, rules, and wordlists that I did partly out of convenience as well as a desire to mostly use publicly-available resources that are very popular/well-known and/or canonical/authoritative in some way. 

Rockyou.txt was chosen partly because it's extremely well-known, widely used, etc. and because it's short – testing all of these rules with something like weakpass_3a would've taken ages. At the same time, I recognize that modern wordlists might be longer or different, which is cyclone_hk was also used. 

PwnedPasswords V8 was chosen mainly because it's a huge list that would give me no shortage of hashes to work with, and it's available in one place for anyone who wishes to access it. While I admit it's not the “best” resource for the project in any objective way, I don't see any inherent flaws in its use either. 

The rules were mostly chosen based on what I was able to find, what seems popular in the cracking community, and what happened to appear in the large, consolidated lists I sourced from. 

While this project is completed, if there's some other resource you believe would benefit a project like this, I'm open to suggestions for when/if I do a V2. 


## What programs were used to do this? 

-Hashcat 6.2.5 was used for all rule testing/validation, as well as generating random rules. 

-PACK for python 3 was used to generate most of the original rules ( https://gist.github.com/rarecoil/8b964b473eb8d47c70dea0a86b772f60)

-Duprule was used to remove functional duplicates from the final list (https://github.com/mhasbini/duprule)

The rest was done with windows cmd/linux terminal commands (mainly a lot of sort | uniq -c | sort -nr as well as using copy to combine files together) plus vbs script + batch files for automation and some python scripting. 


## Did you write/generate these rules? 

For the most part, no. 

The majority of these rules are not mine, and I don't mean to take credit for them – I simply tested them against a lot of hashes and sorted by frequency. This excludes those contained in the folder “unicorn generated” which were generated by me using both PACK and hashcat's built-in random rule generation. 


## Is this project ongoing? Will there be updates? 

No. This project is completed. 
 

## How was this developed?  

As mentioned above, the first 100 million hashes from PwnedPassswords V8 were used for testing. These were divided into 50 batches of 2 million. Rockyou.txt was used as a wordlist, and the first batch of ~40 million rules (~33 million de-duped) was tested: these were the rules downloaded from the link in this doc: (https://docs.google.com/spreadsheets/d/1qQNwggWIWtL-m0EYrRg_vdwHOrZCY-SnWcYTwQN0fMk/edit#gid=1952927995). I simply used the included “combined.rule” file that contains all the others. This was the single most time-consuming step and took about a month on a 3080 Ti, though part of this was due to “hiccups” in getting the automation to work smoothly, me not de-duping the list beforehand, and the like, as I estimate actual runtime to be closer to 600 hours. After this I was left with 18,468,746 hashes.

Next, the rules from UncleJay's link in this thread (https://forum.hashkiller.io/index.php?threads/user-recommended-wordlists-rules.50001/) were tested. While many of the rules had already been contained in combined.rule, there were definitely some I hadn't tried yet, mainly the massive “KoreLogicRulesAppend6NumbersSpecial” which is 575 MB and contains 38 M rules, simply being every possible combination of 6 numbers and a special character. I figured the test wasn't complete without it though and threw it (along with any other rules I hadn't yet tried) into a file titled combined_2. This yielded an additional 43.3-ish million rules to try, but only took about 6 days since I was now processing only 10 batches of ~1.8 million hashes each. When this was finished, I was left with 17,659,603 uncracked hashes and – after sort | uniq -c | sort -nr -ing and some sed commands -- a tidy little 48 MB file with 3,478,237 rules, in order of frequency. Good so far. 

I wanted to improve it though which I had a two-step plan to do: the first step involved PACK for python 3 (https://gist.github.com/rarecoil/8b964b473eb8d47c70dea0a86b772f60), and the second involved hashcat's built-in random rule generation. 

So first PACK: I fed PACK the large-combined list from hashmob https://hashmob.net/resources/hashmob) as well as rockyou.txt as a “base” wordlist. It processed 47.5 M passwords, and generated 51,272,903 rules after a sort | uniq. This took about 9 ½ days running on a linux VM powered by 8 “P-cores” from a 12700K. 

I wasn't satisfied with this though and downloaded the Hashmob User Full list. I removed all lines that had already been contained in the large-combined list, and set it running in a similar manner. This ran for about 10 days on the same VM before eventually being cut for time. It processed 7.4 M passwords and, after sort | uniq -ing everything, generated an additional 19,123,250 rules for a total of 70.4 M. 

Running these rules against the remaining hashes took about 9 days of runtime, and honestly didn't produce the results I expected; it cracked an additional 3,796,380 hashes but none of the rules made it into the top 5,000 and I estimate only about 20,000 of them made it into the top 1,000,000. Still, if nothing else this just goes to show the quality of the rules that went into this project and the list that had already formed – not to mention every little bit helps -- so I don't count it as a loss.

Finally, I decided to randomly generate some rules. This was done in-part while PACK was running, and involved having hashcat try 111,111,112 rules for each of 9 batches – for a total of just over 1,000,000,000. This was done in two runs over about 10 days and each rule that cracked at least one hash was saved to a debug file. After sorting and uniq-ing, these rules were tried against every hash that remained after the PACK rules. In the end this didn't crack many hashes and produced even fewer useful rules than the PACK attempt had, but several hundred did make it into the top million. 

At this point, every generated rule that had cracked a hash was documented and the resulting list sorted by frequency and cleaned to make the “generated” rules which, while perhaps not useful as a stand-alone ruleset, should be well-suited to cracking “difficult” hashes that are left over after trying other rulesets. 

With this, I sort and uniq-ed the ruleset, and was left with a list of 6,791,339 rules that had cracked at least one hash. I sorted them by frequency and copied them out into smaller rulesets. 

I wasn't done yet though; While rockyou.txt is a great resource, modern wordlists might be bigger, have different entries, incorporate more recent “founds”, etc. The list also hadn't been dupruled and contained a few “dead” rules that would return an error in hashcat and refuse to run. I wanted to optimize it to take all of this into account. 

First, I limited the list to only hashes that had cracked at least two hashes to eliminate “random” rules. This left me with 2,428,545 rules. Then, I dupruled and removed “dead” rules – while there were very few duplicates due to the way this list was developed, I did manage to remove 92 duplicates and 4 dead rules, leaving me with 2,428,449. 

Then, I set about cracking the entire set of 100M hashes with cyclone_hk.txt. The first step to this was simply running cyclone_hk.txt against them with no rules, which cracked about 45% of the hashes leaving 54,779,911. 

Next, I ran the first 200k rules against the remaining hashes. This cracked an additional 43%, leaving 11,340,775. Finally, I ran the remaining 2,228,449 rules against the remaining hashes. This cracked ~30% of the remaining hashes and – after sort-uniq-ing the debug data, left me with the makings for the “optimized” ruleset – which was then divided into smaller files per effectiveness. 

As I tested these rules, I realized that each set had some strong points and some shortcomings – mainly, the original set performed quite well on the small end (ie 64 – 250 rules) while the “optimized” set performed more poorly than I would like on the small end but performed well enough in the middle (ie 50k-ish rules). At the larger end (ie 100k – 1M), they traded blows. I wanted a ruleset with consistent good performance so I sought to “hybridize” them and, and did so by combining the debug data from both runs into one file, then sort-uniq-ing as usual. 

I found this resulting ruleset performed anywhere from in-between the original and optimized to better than either one depending on the size, did particularly well on larger sizes, and met my expectations in just about every case. Therefore I chose it as the best candidate to go forward with as “the” product of this project rather than having 3 separate lists with much of the same content. 

The top 1,077,874 rules (ie those that had cracked a hash at least 5 times between the two runs) were selected to be the largest ruleset. This was then dupruled and one “dead” rule was removed (bringing the total down to 1,077,833). The smaller rulesets were then copied from this sorted/cleaned file. 





