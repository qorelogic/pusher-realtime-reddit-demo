# Realtime Reddit API Demo

This example shows you how to use the [Pusher-powered](http://pusher.com) Realtime Reddit API, allowing you to subscribe to a live feed for any subreddit.


## API overview

Here is an overview of the API:

- The Pusher application key for the Realtime Reddit API is `50ed18dd967b455393ed`
- Each subreddit publishes to a Pusher channel using the name of the subreddit in lowercase and without the "/r/" prefix (eg. "askreddit")
- New stories are published using the `new-listing` event
- Stories are formatted using the standard [Reddit API JSON structure](https://github.com/reddit/reddit/wiki/JSON#link-implements-votable--created)


## Using the API

The Realtime Reddit API has been built with simplicity in mind. All you need to do is subscribe to any subreddit using [one of Pusher's free platform libraries](http://pusher.com/docs/libraries) and decide what you want to do with each story.

Here's an example that subscribes to the "/r/AskReddit" subreddit using JavaScript and outputs each new story to the browser console:

```
// Include the Pusher JavaScript library
<script src="http://js.pusher.com/2.2/pusher.min.js"></script>

<script>
  // Open a Pusher connection to the Realtime Reddit API
  var pusher = new Pusher("50ed18dd967b455393ed");

  // Subscribe to the /r/AskReddit subreddit (lowercase)
  var subredditChannel = pusher.subscribe("askreddit");

  // Listen for new stories
  subredditChannel.bind("new-listing", function(listing) {
    // Output listing to the browser console
    console.log(listing);
  };
</script>
```