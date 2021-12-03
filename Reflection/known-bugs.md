# Bug Documentation

This documentation lists known bugs/TODO fixes for our Tune Tip application:

- Currently we do allow the user to send duplicate music entries into the recommendation service. This would ideally by fixed to make sure the inputs going into recommendation service are all unique.
  
- We do not catch/plan for time out errors as well as we should for the app, we would need to do more exception handling in that regard. Especially when developing locally and it takes a long time to get responses.

- The model itself is not consistently/constantly learning. We are giving back a recommendation based on the song title and artist. So, if we send the model the same song and track title, we will keep getting back the same recommendation. An example of this would be if I send the model the song Barracuda by Heart the model will currently always send back the recommendation Two Tickets to Paradise by Eddie Money. Realistically the user would be able to like/dislike the recommendation and allow the model to constantly throw different recommendations even if it’s receiving the same song information.

- The model can/will recommend songs that are already on our playlist. We would ideally check for this before returning the input back to the user.

- Finding a more compatible data set to train the model on. Currently if the user decides to add a track to their playlist from the recommendation page, we do not give back the album information. We would find a way to return the album as well so the data can line up. The album is 'null' for all recommendations added on the account screen.
