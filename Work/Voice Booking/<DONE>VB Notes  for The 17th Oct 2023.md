---
tags:
  - Introduction
  - tasks
  - VB
---
VB review Demo issues changes on staging and local


>[!Info]
>List of tasks
>
## VB-398 
\- ==11:20 - 11-40==

**Expected behavior**


Demo’s should always be able to be downloaded

**Actual behavior**

Currently for clients it’s not working. Also not for my colleagues.

When I tried to reproduce it works on my normal chrome (logged in), but it doesn’t work when I’m incognito.

**Steps to reproduce**

1. Go to [https://www.voicebooking.com/en/voiceactor-needed/british-voice-actor/james#](https://www.voicebooking.com/en/voiceactor-needed/british-voice-actor/james#)
    
2. Try to download the demo
    
3. Also try in incognito to make sure
    

[https://www.loom.com/share/17880876218c4ba691a554bbb9423b8f?sid=f1a094d5-e5ee-4718-95bb-ab9c1a733db6](https://www.loom.com/share/17880876218c4ba691a554bbb9423b8f?sid=f1a094d5-e5ee-4718-95bb-ab9c1a733db6)

[https://www.loom.com/share/2738a547921f414c8b3ef292ac42e09a?sid=5586c944-b8f3-4333-a9d6-5f0867c51b9b](https://www.loom.com/share/2738a547921f414c8b3ef292ac42e09a?sid=5586c944-b8f3-4333-a9d6-5f0867c51b9b)



***


## VB-390
[[VB390 notes]]


\- ==12:20 - 1 ==


- [x] add estimate 
- [x] change status



**Task**

Please create a new link in the 'account' menu and use the correct translations based on the language chosen.

**Acceptance criteria**

- The menu reflects the language chosen for the website
    
- The menu reflects the type of account 1) customers or 2) Voices / Employees / Editor
    
- Add new menu item for team members
    
- Add the icons to the menu
    

## Customers

|**EN / DU**|**NL**|**FR**|**Link**|
|---|---|---|---|---|
|My dashboard|**Mijn dashboard**|**Mon dashboard**|_Same_|[https://projectpages.voicebooking.com/client/dashboard](https://projectpages.voicebooking.com/client/dashboard)|
|Subscriptions|**Abonnementen**|**Abonnements**|_Same_|[https://projectpages.voicebooking.com/client/subscription](https://projectpages.voicebooking.com/client/subscription)|
|Invoices|**Facturen**|**Factures**|_Same_|[https://projectpages.voicebooking.com/client/invoices](https://projectpages.voicebooking.com/client/invoices)|
|~~Billing details~~|~~Facturatiegegevens~~|~~Détails de facturation~~|Skip|Probably not possible, as WP doesn’t know the company ID|
|**Teams**|**Teams**|**Equipes**|**NEW**|[https://projectpages.voicebooking.com/client/teams](https://projectpages.voicebooking.com/client/teams)|
|Manage profile|**Profiel beheren**|**Gérer le profil**|_Same_|[https://projectpages.voicebooking.com/client/settings](https://projectpages.voicebooking.com/client/settings)|
|Log out|Log uit|Se déconnecter|_Same_||

## Voices / Employee / Editor

|**EN / DU**|**NL**|**FR**|**Link**|
|---|---|---|---|---|
|Manage profile|**Profiel beheren**|**Gérer le profil**|_Same_|[https://projectpages.voicebooking.com/client/settings](https://projectpages.voicebooking.com/client/settings)|
|Log out|Log uit|Se déconnecter|_Same_||


[[]]
### File changes

functions.php
header.scss
Acf - 








***

