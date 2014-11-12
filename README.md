smoke_signal_backend
====================


### What is Smoke Signal?

Smoke Signal (name pending) does several things:
1. Records state (can setup multiple variables)
  * Boolean values (can label the value, assign meaning to true/false)
  * A string value
  * An integer
  * You can come up with more...
2. Shares state with others (Think of being able to send a URL to someone else and them load the state into their app)
3. Allows you to read/write the others state variables
4. Notifies you (and those that it is shared with) when state changes
  * On every change
  * On every change from false -> true
  * When so-and-so updates the value
  * Value goes from non-zero to 0 and gets 0 n times in a row
5. Could do other unique things like: reset this value to X every week on Monday at midnight.
6. Track the history of the state variable (who changed it, when it changed)

### A few use cases
------------------------
#### Everyday home use (A)

I (Matt W.) have a flag system for whose dog(s) are out mounted on the fence that my neighbor and I share. It works great when you have shoes on and it's not raining. You walk outside and put up the flag. The issue is that I have to walk over to the window and look if his dogs are back inside (essentially polling) rather than being notified that he put his flag down. So, in *Smoke Signal* I would set up a state variable that would be labeled "Matt's Dog Is Out" w/ true being labeled "Yes" and false "No". I would then send that state variable ID via some means to my neighbor. He would then get the app and plug in the ID. It would now show on his app all the time. He then sets up an alert for whenever I change the value of "Matt's Dog Is Out". He would do the same for his dog's with me.

#### Everday home use (B)

Set up a state variable for the # of rolls of toilet paper in your house. Whenever you change a roll, decrement the counter. Whenever you buy toilet paper increment the count by N rolls. Alert yourself whenever it gets below X. Share it with everyone that lives in your house.


#### Monitoring

On several of my server platforms I log status messages to HipChat. This is great for having a *free* log of server performance and is super easy to implement in any backend platform. Because I currently don't have a way to send myself a notification from HipChat "Processes Running: 1" turns to "Processes Running: 0" I have to use the Twilio API to send myself a text message. I would love to be able to set up a state variable in *Smoke Signal* and hit an API endpoint  (POST /api/v1/state/123123459 w/ 1 nominally and 0 in error condition) and have an alert triggered to me. This could occur whenever the value changes from 1 to 0 or whenever we go from 1 to 0 and stays that way for X updates or Y minutes.


#### Weird/Fun Games

I'm sure that we could come up with some fun games to play where the realtime nature of the state variable could yield interesting dynamics. Maybe you all have ideas?


#### More Ideas?
