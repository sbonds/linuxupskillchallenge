# Day 0 - Creating Your Own Server - with a $5 Linode plan (FAILED)

* [Previous "Day 0" threads](https://www.reddit.com/r/linuxupskillchallenge/search/?q=Day%200&restrict_sr=1)

## Linode fails to work

Linode does not appear to accept many new subscribers. You may want to avoid this service.

## INTRO

First, you need a server. You can't really learn about administering a remote Linux server without having one of your own - so today we're going to buy one!

Through the magic of Linux and virtualization, it's now possible to get a small Internet server setup almost instantly - and at very low cost. Technically, what you'll be doing is creating and renting a VPS ("Virtual Private Server"). In a datacentre somewhere, a single physical server running Linux will be split into a dozen or more Virtual servers, using the KVM (Kernel-based Virtual Machine) feature that's been part of Linux since early 2007.

In addition to a hosting provider, we also need to choose which "flavour" of Linux to install on our server. If you're new to Linux then the range of "distributions" available can be confusing - but the latest LTS ("Long Term Support") version of Ubuntu Server is a popular choice, and what you'll need for this course.

These instructions will walk you through using Linode ([https://www.linode.com/](https://www.linode.com/)) as your VPS hosting provider. They are popular for small scale linux hosting, with simple uncluttered interface. Linode charges $5 (USD) per month for the minimal server that you'll be creating, equal to other providers. You will also see fewer attempts at marketing and upselling from Linode than other comparable providers. (Of course, if you have a strong reason to use another provider, then by all means do so, but be sure to choose Ubuntu Server 20.04)

## Signing up with Linode

Linode is friendlier about people using anti-spam services than other providers like Digital Ocean. For example, many people use the [https://sneakemail.com/](https://sneakemail.com/) service and Digital Ocean flat-out refuses to accept a registration which uses them. No problem, plenty of fish in the sea. People who prefer to avoid marketing spam can choose another provider easily enough and it says something about a company's stance on marketing spam when they make choices like this.

### First E-mail

You will get an activation E-mail which will direct you to a form where you must enter billing information, including address and credit card info. They will put a hold of $1.00 on your card.

### Second E-mail (longer delay)

This one takes longer to arrive. The $1.00 credit card hold appears nearly instantly.

## DENIED

Linode refused to sign me up.

```text
We appreciate your interest in Linode, however, your registration did not
meet the criteria we use to approve new accounts. As such, the account you
attempted to create has been canceled.

You are welcome to try signing up again - here are some best practices to keep
in mind if you do that:

    1. Make sure all of the information you enter at signup is accurate. The account
    name and address should correspond to the cardholder who is financially responsible
    for the account.

    2. If you used a VPN to create your account, try to sign up without a VPN. Some VPNs
    have a history of being used for fraudulent or illicit activity, which may have caused
    your account to be flagged as high risk.

    3. There is no restriction on the number of Linode accounts you may have. However, if
    we determine that you are creating multiple accounts in an attempt to bypass restrictions
    or limits on an existing account, we may prevent you from creating new accounts.

If you believe you have received this message in error, or if you any questions or concerns,
please contact us at support@linode.com. To ensure a prompt response please include:

    1. Your account's username or email address.
    2. The last six (6) digits of the payment card used.

If you do not receive a reply, this means the decision to cancel the account could not be overturned. We appreciate your understanding.
```

I E-mailed their support contact with the above info and mentioned that this wasn't enrolled via VPN, used a valid credit card, etc. They have not responded so I can only assume they do not wish to do business with me.

No problem. Moving on.
