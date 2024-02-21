---
layout: post
title:  Bypass Kobo e-reader account setup
date:   2024-02-21
categories: tips
---

After purchasing a Kobo e-reader, 
I encountered an obligatory step during the initial setup: the device requires you to log in to a Kobo account.
While this does provide access to a variety convenient features, it also means you must share some of your personal privacy with Kobo.
For those who prefer to have full control and wish to bypass the login process, there's no direct option to do so.
Fortunately, some users from abroad have found a workaround using SQL command to not only skip the login step but also disable Kobo Analytics Event, ensuring a greater degree of privacy.

<br/>

```sql
insert or replace into user
  (UserID, UserKey)
values
  ('-', '-');

drop index if exists analytics_events_timestamp;

create trigger if not exists delete_analytics
after insert on AnalyticsEvents begin
  delete from AnalyticsEvents;
end;
```
<br/>

[Ref: Setting up a Kobo without logging in](https://jacobalbano.com/2021/06/24/setting-up-a-kobo-without-logging-in/)
