+++
title = 'Quick Tips for Working with Languages'
date = 2026-07-13T18:18:41+01:00
draft = false
author = 'Wessel Poelman'
+++

While supervising students with their master thesis and doing my own research, I've developed some guidelines regarding working with languages.
To my surprise, I see these errors very often, even by senior people in my field (computational linguistics / natural language processing).

## 1. Don't refer to languages with flags
This is quite self-explanatory, but you regularly see websites, papers, apps, reports, etc. that have a little Union Jack next to English, a German flag next to German, or an Italian flag next to Italian.
And sure, at first glance, this makes sense since this does quickly convey information.
But what do we do with Switzerland (official languages: German, French, Italian)?
Or Belgium (Dutch, French, German)?
Or should we use the Austrian flag for German instead of the German flag?
What about the US flag for English? Or should we use the flag of Singapore instead?
Similarly, we quickly run out of unique flags when we talk about countries like Ethiopia or India that both have hundreds of languages.
I'm not at all the first one to make this [point](https://www.flagsarenotlanguages.com/blog/why-flags-do-not-represent-language/), but it bears repeating.

So what to do instead?
You could use ISO codes, but these have their own [issues](https://ses.library.usyd.edu.au/handle/2123/9838) and can be quite opaque (the ISO 639-3 code for Modern Greek is `ell` for example).
It's best to use full names or short codes when the context allows for it (a website that's in Dutch and English is fine to list just `nl` and `en`).
See [here](https://www.flagsarenotlanguages.com/blog/best-practice-for-presenting-languages/) for some more good examples.

## 2. State which languages you're using, and why
This is also not a new issue, NLP-people are probably familiar with the [#BenderRule](https://thegradient.pub/the-benderrule-on-naming-the-languages-we-study-and-why-it-matters/): name the languages you use in your research.
I would add that it's also good to describe why you're using the [*language sample*](https://direct.mit.edu/coli/article/52/1/237/133834/A-Principled-Framework-for-Evaluating-on) you're using.
Oftentimes, language selections are implicitly motivated by some idea of [generalizability](https://aclanthology.org/2024.emnlp-main.326/) (*we're using these languages, which cover many families, and therefore our method/dataset is very good*).
There's nothing wrong with that, but it should be motivated properly.
Even just saying "*we use languages, a, b, and c because we have data for them*" is already enough in my opinion.

## 3. Make sure you know which languages you use
Naming languages is a good first step, but research in my field is often done with the goal of scaling™.
This means people take dumps of the internet and find out post hoc which languages they actually have.
Manual inspection is basically impossible at this scale, but even on the language-level this is often assumed to be "good enough."
Why does this matter?
I've seen many (sometimes award-winning) papers that include [Klingon](https://en.wikipedia.org/wiki/Klingon_language), [Toki Pona](https://en.wikipedia.org/wiki/Toki_Pona), [Interlingua](https://en.wikipedia.org/wiki/Interlingua), among other constructed languages (conlangs).
Sure, these languages all have an official ISO 639 code (sometimes multiple!) and they are properly supported by language detection models, but I can't help but think that most NLP researchers don't know about conlangs or don't care.
I'm not against looking into these languages (quite the opposite; it would be very cool), but it should be with intention, not as an accidental byproduct of "massively multilingual language modeling" since it muddies the water of how we're progressing towards the goal of broader language support.
Similarly, many papers treat an ISO 639-3 code as a "language."
This is mostly fine, but this standard covers much more than just languages, including conlangs (as mentioned), dialects, and macrolanguages.
This could be intentional, but here too my gut says that people just don't know.
Make sure you know what's in your data and if it makes sense.

## 4. Properly refer to languages
This is a tricky process since there are a lot of different standards and ways of referring to languages.
I've made a tool that makes this easier ([code](https://github.com/WPoelman/qwanqwa) or in the [browser](/qq)), but even when you don't use it, please make sure to avoid mistakes like Finnish vs 'Finish' or referring to politically-charged name changes (Moldavian vs Romanian, for example).
The same applies to standards: don't use a country code to refer to a language (`gr` refers to the country Greece, `el` to the language Modern Greek, `jp` to Japan, `ja` to Japanese, and so on).

## 5. Languages and scripts are two separate things
A (written) human language is a combination of a vocabulary and grammar.
Which units can be used and how can these be arranged?
I can technically choose to *encode* these units in any symbol system.
For instance, if I use a [Caesar cipher](https://en.wikipedia.org/wiki/Caesar_cipher) and shift the letters in the alphabet by 1, I'm still writing English, but just encoded differently: Uijt jt Fohmjti!
The same applies to scripts and languages; Kazakh can officially be written in Cyrillic, Arabic, and Latin scripts; regardless of which one we choose, the language we're writing is still Kazakh.
Certain *transliterations* (roughly transferring a language from one script to another; for example writing Hindi in Latin script instead of Devanagari) are also officially recognized.
A language is a set units and their arrangement, an encoding is the choice of how to represent this.
So, referring to Arabic or Hebrew as a "right-to-left language" should sound very silly after what I just outlined.
I recommend [this paper](https://aclanthology.org/2023.cawl-1.1/) for more such pitfalls, especially when talking about Chinese, Japanese, and Korean (CJK).
One last point is that *languages* are technically much broader than *human languages*: programming languages, formal languages, context-free languages, and so on.
This is more of a nitpick since context is often enough to know what's being meant, but if you're in a setting where this matters, it's best to use *human language* or *natural language* instead of just *language* when referring to the languages spoken by humans.
