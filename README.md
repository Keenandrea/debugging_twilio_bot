# debugging_twilio_bot
A README illustrating my attempts to locate bugs in Twilio Customer Satisfaction Bot

## Attempt 1
Give the bot an existential crisis:
![existential crisis 1](https://github.com/Keenandrea/debugging_twilio_bot/blob/master/debug1.PNG)
![existential crisis 2](https://github.com/Keenandrea/debugging_twilio_bot/blob/master/debug2.PNG)

## Attempt 2
Give the bot gibberish
![gibberish 1](https://github.com/Keenandrea/debugging_twilio_bot/blob/master/debug3.PNG)

## Attempt 3
Comply with bots demands
![compliance 1](https://github.com/Keenandrea/debugging_twilio_bot/blob/master/debug4.PNG)

## Attempt 4
Resopond with out-of-bounds integer for survey response satisfaction
![oob int 1](https://github.com/Keenandrea/debugging_twilio_bot/blob/master/debug5.PNG)

## Debug Conclusion
The bot has sustained **Attempt 1**, no more crashing into an existential crisis than any self-satisfied person.

**Attempt 2**, in which I respond with gibberish, the bot is aware that what I am telling it is nonsense.

However, during **Attempt 3**, the bot believes my compliance as a service response. It makes sense. Given that my response was __Ok__, which sits in for a natural response to any question asked on behalf of any service. The bug here is in the context. I was saying __Ok__ to signify my compliance to the bot asking me to repeat what gibberish I has said beforehand, not as a response to the customer service.

With **Attempt 4**, once my satisfaction response was recieved, the bot then asked me to how likely I was to recommend the platform service. The correct response, on my part, was a number [1 to 10]. I responded with 25. Still, the number was logged.

## Solutions
Each message I send the bot is a string of characters. Perhaps checking that string with a RegEx to make sure there are no special characters in a long series, then responding to the user with a message clearly expressing the user's mistake.

Using context-aware message parsing to sift through the ambiguities of the language.

Initiating a simple conditional statement to keep the bound of user recommendation response between [1 -10], sending an error message from the bot if the user enters a number outside of those specific bounds.
