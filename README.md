# Date and Next Event Widget
This KWGT widget mimics the calendar functionality provided by Google's At A Glance widget, placing "event announcements" under the current date.

The most notable feature of this widget is the logic used to determine what event announcment is shown (and when it is shown). Specifically, the widget will display:

* A message if there are no events for the current day
* A countdown for events starting in the next 60 minutes
* The title of a "underway" event
* The title of an all-day event whenever an "underway" event or countdown announcement is _not_ being displayed (this assumes there is only one all-day event for the current day)
* The number of all-day events (if there is more than one all-day event on the current day)
* A message when there are no more events for the current day

Additionally, the widget contains logic for:
* gracefully handling back-to-back events, where the widget will effectively supress the countdown for the subsequent event until there is 10 minutes remaining, allowing the "underway" event to show for longer
* Trimming long event names (i.e., adding  ellipses).

## Examples
<img src="https://github.com/matthewkeating/KWGT-Date-and-Next-Event/assets/6810065/174c816e-8f93-48cf-a70b-af21b5305776" width="350"/><p/>
<img src="https://github.com/matthewkeating/KWGT-Date-and-Next-Event/assets/6810065/ef639614-5d94-4a95-97c3-a4b631247412" width="350"/><p/>
<img src="https://github.com/matthewkeating/KWGT-Date-and-Next-Event/assets/6810065/89119474-3ca6-459f-86c3-36ac1417500d" width="350"/>

## Note on the Formulas Used
I don't write alot of KWGT widgets... and I find the dearth of features in the language (and the lack of an editor) make it challegning to write readable code. I have included a formula file in this repo to better illustrate the logic and serve as a starting point for anyone who may want to make modifications.

## Considerations
### Birthdays
The widget has "hard coded" logic for handling events on a calendar called "Birthdays". This may (or may not) address, or serve as a work around for, [the issues some encounter with Google's Contacts Birthday calendar](https://www.reddit.com/r/kustom/comments/vyazjo/help_google_contacts_birthdays_not_visible_anymore/). The work around implemented in this widget is to have a calendar called "Birthdays" that contains all-day events for any birthday you want to "announce" on the widget. If you want to show birthdays on the widget, I would suggest testing with your calendar configuraiton and modifying the formula as needed.

### Trimming
Trimming event names is accomplished by using the `ell` conversion mode available through the [text converter function]([url]https://docs.kustom.rocks/docs/reference/functions/tc/). Since the font I use is variable width, the values set in the `tc` function cannot be universal. The values are good defaults for my configuration but YMMV. Consider testing and editing the values in the formula if the defaults don't work well for you.

### Events from Midnight to 1am
The above functional was tested during "daylight" hours. There may (or may not) be logic that prevents events starting between midnight and 1am from displaying properly. I may (or may not) decide to test this someday.
