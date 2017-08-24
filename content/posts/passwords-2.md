---
title: "All About Passwords Part 2"
subtitle: Passwords Safes
date: 2017-08-24T19:44:17-05:00
author: Travis Friesen
categories:
   - Security
   - Passwords
tags:
   - Security
   - Passwords
---

For this second post on this series on passwords, I am going to discuss one of the best tools for improving personal passwords security, passwords safes.

<!--more-->

In my [last article](https://blog.flyingfortressit.ca/posts/passwords-1.html) on passwords, I gave some advice on the best way of choosing passwords. However, even using the methods I suggested, remembering passwords can still be a huge pain-in-the-butt, especially if you use unique passwords for every account (which you should). Computers are good at remembering - if only there were some tool we could leverage to remember our passwords for us.

Well, there is, and we call them Password Safes.

Passwords safes, sometimes called password managers, work by storing your passwords in an encrypted safe or 'vault'. When you want to access your passwords, you must provide the password safe tool with the master key for your vault, which decrypts the safe. The tool will usually cache the master key, so it doesn't need to be entered every single time you want one of your passwords. The tool will also generally store usernames and information about the account the passwords is associated with, and also allow you to copy your password to the clipboard, allowing you to paste it into the password field without having to type it out. Most password safes will also help you generate new, strong passwords. Some will even automatically log you into select websites, though this has some downsides from a security perspective.

## Types of Passwords Safes

Password safes generally come in two falvours: online and offline.

As the names suggest, offline password safes are not stored on or involved with the internet. They are basically an encrypted file that sits on your harddrive which contains your passwords, and a friedly user interface to manage them. Two popular offline passwords safes are [KeePass](http://keepass.info/) and Bruce Schneier's (remember him?) [PWSafe](https://pwsafe.org/).

Offline password safes usually include several plugins that allow you to extend their functionality. For example, KeePass has a plugin which allows for browser integration. Browsers often have their own built-in password storage, but these are usually not properly encrypted or secured, and so are not recommended at this time.

Online password safes, on the other hand, are usually hosted on the public internet, and are accessed either through a website, an API, or through a browser extension. I personally use and enjoy [LastPass](https://www.lastpass.com/), while some of my colleagues use [Dashlane](https://www.dashlane.com/) and [1Password](https://1password.com/).

Both online and offline safes have advantages and disadvantages. Online safes sync easily across multiple devices, and you don't have to worry about keeping them secure or backing them up - imagine if you kept all your passwords on one computer, only to have its harddrive fail! Offline safes, on the other hand, aren't hosted online or communicate via a browser, and so some argue are more secure from hackers.


## Security of Password Safes

The security of the safe is only as good as the master password used to encrypt it, so be sure to make it a good one. Use my [previous guide](https://blog.flyingfortressit.ca/posts/passwords-1.html) for help in choosing a strong one. If someone can guess this password, they'll have everything!

In fact, when I first started using password safes, it bothered me a little that I know had put all my passwords in one place. If a hacker could get access to my safe or vault, he or she would have **all** of my passwords for **all** of my accounts! 

The concern is not entirely unfounded. However, you have to keep in mind **how** an attacker might gain access to my vault. He or she would need both the vault (stored either online or on my harddrive) and my encryption key. The only reliable way to get both of those things is to compromise my local PC. He or she would then make a copy of my vault, and perhaps use keyboard logging to steal my master password. This seems quite conceivable, which would suggest that password safes are actually **less** secure than just remembering passwords instead, but remember: if an attacker gains access to your local computer, he or she will be able to get your passwords and account information anyway, with or without a password safe, either by stealing browser tokens or using a key logger. It may just take him or her a bit a longer. So it doesn't really reduce your security.

Some people also worry that online password safes may be compromised by a hacker attacking the online side of the password safe. Through the website, for instance, an attacker may gain access to the safes and account information stored there. We have seen attackers do just that on many high-profile sites, including [LinkedIn](https://leakedsource.ru/blog/linkedin) and [MySpace](https://leakedsource.ru/blog/myspace).

However, it's not enough to just obtain a copy of the vault. Remember that it is stored encrypted, and the designers of online password safes have done their homework. The encryption used by online password safes is considered very strong; it is inconceivable that someone would be able to break the encryption, provided a good master password was used.

![Inconceivable](https://i.imgflip.com/1unr3b.jpg)

On top of that, the operators of the online passwords don't store (a usable form of) your master password anywhere. Even if an attacker compromised Lastpass.com or Dashlane.com from top to bottom, he or she would not get a copy of your master password, and so your safe would be... uh... safe. For login purposes, they do keep a copy of your master password in a hashed or encrypted format, but it can't be used for unencrypting your safe, and it is equally difficult to get the plain version of the master password from its hashed form.

Additionally, online password services have the option to secure your account with multi-factor authentication (MFA). MFA is the topic for my next article, so I won't delve into it too much, but it does provide an additional layer of security to protect your online password safe account.

I mentioned earlier that using a browser extension for a password safe includes the ability to auto-login to websites, but this has security implications. Basically, if an attacker can convince your browser that it is the login portal of another website you have an account for, he or she can trick your password manager to give him or her your login credentials. And so we don't recommend enabling this features, especially for sensitive websites or accounts.

Ultimately, what's more concerning than everything I've discussed here is an attacker obtaining a password for one account (say, from your Facebook) and using it to gain access to another account (say, GMail or your bank). Password re-use is a much bigger problem than the concerns around password safes, so we feel that the tradeoff is well worth the relatively minor concerns around password safes.


## Conclusion

Password safes allow users to keep very strong, unique passwords for every single website or account they have, while reducing the mental load of having to remember so many damn passwords. For this reason, I highly recommend that everyone start using a good password manager right away, today, this very moment. Choose one of the ones I listed above, and get to it. It only takes a few minutes to set up, and most of the online ones can even learn your passwords as you use them!


