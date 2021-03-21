# Authentication workflow for S3 Console

## Requirements

* Are there any regular types of message that are posted manually?
  * Looking for reviews: {{ PR }}
* Ask team members to find one or two automated messages that they’ve received in the past week or so that are critical to their job.
  * TBD
* Think beyond pure communication and embrace interactivity
* Think about the key hurdles that people face when using Slack in your team, and outline them.
  * Other messages might make LFR messages left ignored as they will be up in the page.
* Do you regularly use an external service while working?
  * Google calender, standuply, Jira.

## Design

* Pick entry points for interactions
  * /lfr {{ PR}}
  * Users will initiate workflow by using slash commands and not a shortcut neither the Block Kit components.
    * Limitations:
      * Slash Commands cannot be used in message threads. Consider using app shortcuts for this purpose instead.
    * HTTP POST command to the app

* Imagine user-app communication
  * How will user reach to a conclusion?
    * After entering a PR, the list of current PRs in the bucket will be posted.
    * [Incoming WebHooks](https://api.slack.com/start/planning/communicating#communicating-with-users__incoming-webhooks):
      * Good for periodic notifications
      * can only post to a single channel, which is specified when the app is installed.
      * On their own, incoming webhooks can’t receive responses to the messages they post or process responses from interactive elements like buttons.
      * probably best to think of incoming webhooks as one-way only communication flows that are simple to set up and used for posting notifications into your workspace.
      * Hence good for periodic PR needing reviews reminder
    * [chat.postMessage](https://api.slack.com/start/planning/communicating#communicating-with-users__chat.postmessage):
      * post into any channel it has access to, including threads to individual messages
      * compose sophisticated app-like interfaces using Slack's Block Kit UI framework (more on this a bit later), and
      * receive responses to build true interactivity into your app
    * [Formatting messages with Block Kit](https://api.slack.com/start/planning/communicating#communicating-with-users__formatting-messages-with-block-kit):
      * [sophisticated UI](https://api.slack.com/block-kit)
  * Choosing the right voice and tone for your app
    * Keep messages on point.
    * Make sure your meaning is clear.
    * Stay professional.
    * If you decide to give gender to your app (and it’s very easy not to), then be appropriate with the kind of things it says - make sure it doesn't use any stereotypes or generalizations.
    * Use contractions and conversational cadence: “You’ll be able to” rather than “You will” and that sort of thing.
    * A little goes a long way. We cannot say this enough.
    * Let’s talk about the actual words: Be brief
      * Nearly every word your app says should facilitate an interaction (courteous parts of speech, such as greetings, are also useful). Don’t add a joke or aside just to be glib.
      * Be clear
        * Don’t use jargon and slang in the important parts of message text
        * Avoid culturally specific references, like jokes from movies
        * Stick to common, simple words
        * Buttons labels should be clear and specific
        * Make buttons active-voice and reflect the user’s outcome (Save, Book Flight, Place Order)
        * Avoid vague, non-actionable text like Click here or Settings
        * Don’t replace words with emoji
      * Be empathetic
        * Use gender-neutral pronouns
        * Use a variety of emoji skin tones
        * Don’t use sexist, racist, or ableist language
        * Make an effort to trial your voice and tone with people from a diversity of backgrounds, in different settings (on mobile, with flaky wifi, etc.)
        * Don’t assume any level of technical fluency from your users, keep instructions clear and simple
        * Writing for a broad audience takes a bit of practice if you’re new to it, and it is usually easier if you have a diverse team of people working on your app from the start.
      * Spend time rewriting
        * Read your work out loud to yourself. Ah, you found a typo, didn’t you?
        * Find someone to read your script out loud with, to prototype the two-part interaction (Thanks to Erika Hall for this advice - abookapart.com/products/conversational-design). Where does it sound unnatural? Forced?
        * Rewrite as though you’re writing to a friend. Does that sound more natural or human?
        * Record yourself verbally explaining the concepts you’re trying to convey. This may help you find a more casual way of expressing your app’s message.
  * [Choosing the right APIs](https://api.slack.com/start/planning/choosing)
    * The Events API
      * [Socket Mode](https://api.slack.com/apis/connections/socket): If you don't wish to expose a public, static HTTP endpoint to communicate with Slack, Socket Mode can help.
    * The Web API
    * The Conversations API
    * Socket Mode
    * Real Time Messaging
  * [Understand your audience](https://api.slack.com/start/planning/guidelines)
    * Be upfront about communication
    * Avoiding large-group mentions
    * Keeping modals meaningful
    * Being considerate with messaging
      * Pick the right frequency of notifications
      * Match message types and channels
      * Make messages that notify actionable
      * Sending direct messages to users
      * Responding to users in channel
        * [Ephemeral messages](https://api.slack.com/messaging/managing#ephemeral)
        * [Plotting out interactive flows](https://api.slack.com/start/planning/triggers)
          * The flow of interactions
          * Origins for interaction
          * After-action report



### Basic Flow

### Technical Details

### API

### UI

### Upgrade/Downgrade

### Security

### Tests

### Documentation

## Open question