+++
title = "Calendar and Tasks Clients on Linux"
date = 2026-02-04
+++
## Why
I've been looking for good to-do & calendar app(s) for over a year now. 

Before I started self hosting my calendar and to-dos, I used Google Calendar and Tasks. These worked perfectly for my use case. I created a different list for each of my classes, and tasks with due dates showed up on my calendar. 

Last year, I decided I wanted to start moving away from exclusively using Google services, and I started using Proton Calendar. Proton didn't have anything like Tasks at the time (although it seems to be [highly requested](https://protonmail.uservoice.com/forums/284483-proton-mail-calendar/suggestions/7158378-proton-tasks-to-do-list) and [potentially in progress](https://proton.me/blog/proton-mail-calendar-roadmap), as of me writing this, they still don't) so I started writing my to-do list on paper, thinking this was a perfect time to start being more analog.

It didn't work out very well. I'm used to features like recurring tasks and sync over multiple devices, which a paper notebook doesn't have. I would forget to write tasks down and forget to bring my notebook with me. By the end of last semester, I knew I needed to go back to digital tasks.

On iOS, the Calendar and Reminders apps sync perfectly with CalDAV and have all of the features I want (although subtasks apparently [don't work properly](https://help.nextcloud.com/t/sub-tasks-in-apple-reminders/167668), I don't use them.) The UI looks great too, and the apps are intuitive to use.

When I'm being productive, getting tasks done, I tend to be on my laptop. I also tend to put my phone away so I don't get distracted, so I need access to my tasks and calendar on my laptop too. For a while, I used the Nextcloud web client to manage my tasks and calendar, which works fine and has all of the features I need. However, I personally dislike having extra browser tabs open, and the website can take a while to load, so I decided to look for Calendar and Tasks clients.
## What I Wanted
- Loads reasonably fast
- Looks nice
- Both calendars and tasks in one application
- (Optional but highly preferred) "All tasks" view (or equivalent) groups tasks by which list they're in, and labels this information prominently. Extra points for also color coding tasks based on list.
- (Probably impossible to find) A calendar/tasks widget to put on my desktop so I can view upcoming events easily
## The Search Begins!
### [KOrganizer](https://apps.kde.org/korganizer/)/[Kontact](https://apps.kde.org/kontact/)
I use KDE Plasma, so this was already installed on my laptop. KOrganizer has calendar and to-do lists, while Kontact (which incorporates KOrganizer) adds mail, contacts, and RSS feeds, basically making it a personal start page. Since I don't need the extra features of Kontact, I'll focus on KOrganizer, though I will mention that somehow the colors I set for different calendars on Nextcloud worked automatically on KOrganizer but not Kontact.

I was able to add my calendar account pretty easily, and both my calendars and tasks lists synced over. It doesn't have the tasks view I wanted, and it doesn't look as modern as some of the other options on this list, but it works and satisfies most of my requirements.
### [Merkuro](https://apps.kde.org/merkuro/)
Merkuro (formerly Kalendar?) is also by KDE. It has similar functions to KOrganizer, but with a refreshed UI.

I reeeeally wanted this to work! I installed it, my calendar and tasks were already synced (probably because I set up my Nextcloud account with KOrganizer) and I immediately loved how the UI looked. Tasks still weren't grouped the way I wanted (at least by default; it's possible there was a setting somewhere I didn't see) but they were at least color coded by list. 

Unfortunately, when I tried to make a task, the application crashed. I tried reopening and making another task, and the same thing happened. I uninstalled and reinstalled, same issue still. Over the half dozen times I tried to make a task while troubleshooting, I only got to the task creation screen once, and I was so surprised I exited out by accident. I never made it back.

I probably could have gone further in finding the exact error that occurred and searching for a fix online, but I decided to move on.
### [GNOME Calendar](https://apps.gnome.org/Calendar/)
As far as I can tell, this one is only a calendar, no to-do lists. I initially installed it via the Fedora repo, and while the app looked really nice, I couldn't figure out how to add my Nextcloud account. Clicking on any of the settings options did nothing. I gave up and uninstalled it.

I later went back and tried the Flatpak version. I'm not sure what I did between my first try and my second one, but my calendar was actually synced already. The settings options still did nothing.

Unfortunately, not having the due dates of my to-do items on my calendar is a deal breaker. The UI of this calendar is really nice though.
### [Thunderbird](https://www.thunderbird.net/)
Thunderbird is best known as an email client, but it also has calendar and task features. Since I didn't want to use Thunderbird for emails, I found the setup to be slightly confusing. I eventually found out how to add my Nextcloud account for calendars and tasks only, and everything synced over well. 

I only used this briefly, so I don't remember my exact experiences well. I didn't like the tasks UI and didn't need the email client aspect, so I moved on.
### [Evolution](https://gitlab.gnome.org/GNOME/evolution)
Similar to Thunderbird, this is also an email client with calendars and tasks. I backed out of the email setup, then started adding my calendars and tasks lists. I say "started" because I seemingly had to add them one at a time. It's possible that there was an option to add every calendar and list at once, but it wasn't obvious to me anywhere on the UI or during the calendar adding process.

Each time I wanted to add a new calendar or task list, I would have to paste my Nextcloud URL, type in my long username and password, and then manually select a single calendar or list. This wasn't so bad for my calendars, because I only have two, but I have a task list for every class I'm taking and a few extras.

Halfway through adding my lists, I decided to give up so I could finish tasks on them instead. (Or procrastinate by writing this)
### [cfait](https://codeberg.org/trougnouf/cfait)
This one is interesting because it offers both a TUI and a GUI. It's also only for tasks, so I would need a separate app for viewing my calendar.

I installed it through cargo and tried both the TUI and GUI. After logging in to my Nextcloud, I spent some time on the TUI trying to get used to the keybinds. While I'm fine with using the terminal for some tasks, and even prefer it in some cases, I'm just too used to clicking on to-do boxes. Given a little more time, I probably could have adapted to the TUI, but I really wanted to try the GUI.

The GUI was almost perfect. The task view color codes tasks based on which list they're from, and the UI looks great with many color scheme options. There was no way to maximize the window, though. Even when I increased the size of the window to fill my monitor screen, it went back to the default size the next time the application was reopened.

I really want my calendar and tasks to be accessible from the same application, but if I changed my mind, I might come back to this.
## The Winner Is...
... none of the above?

In the end, I went back to using Nextcloud Web's Calendar and Tasks pages. UI and reliability matter the most to me, and although KOrganizer came close, the way it showed task lists made it difficult for me to tell which task belonged to which list at a glance.

I might look back into Merkuro in the future. Hopefully it works by then, or I at least have more time to troubleshoot.

I'm also sort of tempted to write my own client, though I haven't looked into how CalDAV works at all. Maybe next break!

If anyone has any other recommendations, please reach out to me on Matrix!