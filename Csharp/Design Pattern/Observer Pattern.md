#Events #Delegates #Observer #subject 


The #ObserverPattern is an event- driven approach that allows you to execute logic when something else is your game happens. 

It typically works by allowing #observers, such as other #scripts, to #subscribe one or more of their functions to a #subject's event.

The purpose of this is to avoid tight coupling between  scripts, as it allows a class to anonymously respond to events when they happen.

This works because the <b> observer </b> manages it own connection to the <b> subject </b>, which is usually the only class that's class that's able to call the event.


This means that, if either one is missing, so long as the observer pattern is being used correctly , nothing breaks, because neither of the scripts is dependent on the other.


In Unity, the observer pattern is implemented with #Delegates , which are variables that can store one or more functions.


