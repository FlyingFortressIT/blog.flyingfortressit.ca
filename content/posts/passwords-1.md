---
title: "All About Passwords: Part 1"
subtitle: Choosing a Good Password
date: 2017-08-15T20:31:50-05:00
author: Travis Friesen
categories:
   - Security
   - Passwords
tags:
   - Security
   - Passwords
---

For the first post in my series on passwords, I'm going to discuss some methods for choosing good, strong passwords that are still easy to remember.

<!--more-->

It is only fitting that my first set of articles on security revolve around passwords. Passwords have been with us for centuries, since long before computers were around, and despite attempts to kill passwords with various new techniques and approaches, they will remain a cornerstone of digital security for many, many years to come, maybe forever. They are the most basic and the most obvious way that security touches the day-to-day lives of every user.

A typical article or series of articles on security follows a general pattern: we would discuss the nature of the problem, show why it's important, maybe how to exploit it, why existing approaches are no good, and THEN present the solution at the end. But this time, I felt that letting people know what the solution is from the get-go has much more value. The sooner I give you the tools to improve your personal or corporate security, the better. That way, as soon as you are convinced of the issue, you can take appropriate steps to improve the situation. On top of that, many people are already aware that their approach to how they handle passwords is... inadequate.

## Good and Bad Passwords

So. What makes a good password? For this part, I'm going to set aside considerations such as password re-use, password rotation and password safes, which I will discuss in later articles, and simply focus on this question. How can a user choose a password which is both strong but easy to remember?

Before I can do that, I need to establish what makes a password strong. There are many guidelines and schemes for choosing strong passwords, such as 8 or more characters, using letters and numbers, etc. There are even websites which will rate the strength of your password for you, such as [Password Meter](http://www.passwordmeter.com/), but many of these password meters adhere to out-of-date notions of what makes a strong password, and are generally [derided by security experts](https://nakedsecurity.sophos.com/2015/03/02/why-you-cant-trust-password-strength-meters/).

For example, Password Meter rates the 8-character password '1Abcdef!' at 52%, or 'Good', while the 14-character beast 'tiarbppduiijae' (Acronym of: 'This Is A Really Bad Password Please Don't Use It It's Just An Example') gets a mere 25%, or 'Weak'. Yet any password cracker will tell you that the latter is much, MUCH stronger than the former - in fact, that 14-character monster would probably never be cracked or guessed, even on high-end, dedicated password cracking hardware. I'll discuss the details of why this is in future articles, but the gist is that effect of all the rules of complexity and character sets pales in comparison to 

1. avoiding dictionary words (though in this case we mean a hacker's dictionary, not necessarily an English dictionary), 
2. avoiding common patterns and 
3. length

These three rules are the most important factors in the strength of passwords.

There are also websites which purport to help you choose strong passwords, such as [Dino Pass])http://www.dinopass.com/) (which you may note does not use encrypted communication, but that is for another day). While Dino Pass is aimed at children, I think it is fair to hold to the standard for adults; if it's not good enough for our own security needs, it's not good enough for our children's, either.

Dino Pass, and other password generators like it, make many of the same mistakes as the out-of-date password strength meters. A focus on passwords that are too short and fall into typical patterns. After generating a few simple passwords, it should be obvious what pattern Dino Pass uses; an adjective, such as 'swift', followed by a common noun, such as 'road', and then two random digits, such as '90', making for a password of 'swiftroad90'. This password is bad on many accounts. While its length, at 12 characters, isn't terrible, it follows too common of a pattern: just two common English words, plus two numbers, which are at the end. In addition, if an attacker knows that you or your organization uses Dino Pass, he or she can further reduce the attack space by limiting guesses to <adjective><noun><two digits>.

The 'strong' passwords on Dino Pass are not much better. The only difference between 'strong' and 'simple' passwords on DinoPass is that second letter is now capitalized, and one of the letters is replaced by a symbol. Again, these are common techniques that attackers are well aware of. If an attacker is going to try longzebra65, he or she is also likely to try longZebr@65.

On the other side of the coin, some security experts recommend choosing passwords that 15 or more randomly generated strings of nonsense, like 'nDSAFm1-3afd51#%%!' or some such. And while such a password is certainly highly secure, it is more than a little difficult to remember. And on top of this, these same experts will often recommend changing your password frequently, and using a different password for every single website and computer! Even a super-genius would have a hard time keeping track of all of those passwords.

Part of the problem is that whenever passwords are memorable, they are also usually guessable. Any time we take shortcuts to help us remember a password, either by using easily memorable words, or keeping it short, and following predictable patterns such as putting an exclamation point at the end, attackers can leverage our laziness to help them guess our passwords more quickly.



## Choosing Strong, Memorable Passwords

### The xkcd method and the correctness of the battery staple, horse.

The good news is that there a few resources out there that seem to 'get it'. One of the most popular methods of generating strong, memorable passwords was proposed by Randall Munroe, author of the popular webcomic [xkcd](https://xkcd.com). In that particular comment, below, Mr. Munroe correctly points out that a generally-accepted 'strong' passwords, in this case 'Tr0ub4dor&3', is very difficult to remember, without being particularly strong. I would quibble with some of his math, with how he estimates password strength, but the idea is still sound.

![Password Strength](https://imgs.xkcd.com/comics/password_strength.png)

He goes on to suggest a method of choosing passwords that seems to solve both the problems of strength and memorability. Basically, choose 4 common, **random**, English words, and string them together. The resulting password is long enough to be strong without the addition of special characters, or even upper case letters. Finally, he demonstrates that the use of common words, even randomly put together, can be used to make helpful mnemonics. In fact, the absurdity of a horse correctly discussing a battery staple makes it even easier to remember.

If you need help choosing a such a password, there are [several sites](http://preshing.com/20110811/xkcd-password-generator/) that will generate one for you. 

Mr. Munroe's system is not perfect, mind you. As I alluded to earlier, anytime a password is memorable, it is generally crackable, and hackers read xkcd, too. Passwords crackers can leverage a technique called 'combinator attacks', which allows them to combine words from multiple dictionaries into a single, long passwords. 

Ultimately, while the search space for passwords in Mr Munroe's method is pretty good (about 10^16 passwords, if you assume 10,000 common English words), it's not great. If you like this scheme, and wish to use it seriously, I would recommend increasing the complexity of the passwords slightly. For instance, capitalize some of the letters, but do so randomly; capitals at the start of words is so passe, and easily guessed. Add some special characters, but in the middle of words, and especially not at the start or the end, and so on. If you want to add numbers, don't make common substitutions, like cow -> c0w.

I also emphasised the word 'random' in the description for a good reason. The four words chosen **must** be random. Don't get lazy and choose words that are related. It makes guessing your password easier.

### The Schneier Scheme

[Bruce Schneier](https://www.schneier.com/) is a bit of a legend in the world of computer security. He and his colleagues laid some of the crucial groundwork in the world of cryptography, and he continues to be an outspoken voice and critic of the current state of computer and internet security. He is so well-regarded, that some fans set up their own version of Chuck Norris [facts for Bruce Schneier](https://www.schneierfacts.com/).

In 2008, Mr. Schneier [described a scheme](https://www.schneier.com/blog/archives/2014/03/choosing_secure_1.html) for choosing passwords that were both strong yet memorable. The basic gist is to choose a phrase that is specific to you, and turn it into a sort of acronym, with a few numbers and other characters thrown in.

My favourite example he uses: "When I was seven, my sister threw my stuffed rabbit in the toilet." becomes the very strong 'WIw7,mstmsritt...'. I might use a phrase like "Flying Fortress IT is the best at security" to make the password "FFITitbest@s!"

It is worth emphasizing that the phrase should be particular to you, and generally not related to whatever you're using the password for. Don't use popular phrases like "You only live once", or lines from well-known literature or movies. 

## Coming Up

So there you have it. I've provided you with not one, but two methods for choosing good passwords - no more excuses for 'Password123'. In the next article in the series, I'm going to give even better news: you really only need to remember 3-4 passwords, so you can afford to make them super-strong. How can you accomplish this? Stay tuned... (password safes. I'm going to talk about password safes.)




