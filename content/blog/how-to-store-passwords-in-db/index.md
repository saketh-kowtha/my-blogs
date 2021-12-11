---
id: 918494
title: How to store passwords in db?
published_at: 2021-12-06T09:37:29.950Z
tag_list: webdev,beginners,security,database
---

Hello All,

Hope all are doing good in this pandemic time.

This article is about hashing passwords before writing in storage.

Now a days every one are adding authentication for their apps and i heard some of the apps are storing password with out hashing.

### Why we need to hash the passwords

#### Reason 1

You are using a mobile / web app called _Abc_ assume if the Abc app's database got compromised your username and password will be in the hackers hand. If abc app has any sensitive or confidential information of yours then hacker able to access that because hacker has your credentials.

#### Reason 2

Almost 50% of the people will use same password for all their logins. So if attacker got your password he/she can try that over other apps.

### Solution!!!

For the above 2 problems user cannot do anything from his/her side. But developer can do it i.e hashing a password.

We can use irreversible hashing technique and we can hash user password and we can store that hashed password in the database.

#### How can we validate user if we don't have a plain password?

Simple when ever user try to login. Hash the password which was entered by user and compare that hash with the password which we saved during the time of registration or signup.

So no one don't know what is the actual password except the user.Even if database compromised it is impossible to generate actual one because we are using one-way hash function which cannot be reversed.

#### Adding Salt

For more security we can hash user's password with unique random string i.e salt. So if multiple users are using same password then it looks different in database because salts are unique and we can store that salts in db. We can use those salts at the time of login to validate user.

You can now extend your support by buying me a Coffee.

<a href="https://www.buymeacoffee.com/sakethk" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-blue.png" alt="Buy Me A Coffee" style="height: 30px !important;width: 60px !important;" ></a>
