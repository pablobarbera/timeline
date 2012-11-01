Twitter Election Timeline
=============

Source code to build the website at [www.pablobarbera.com/timeline](http://www.pablobarbera.com/timeline).

Summary of .R files
-------

* `functions.R` includes all the functions that are necessary to run the other two R files.
* `get_tweets.R` captures all tweets mentioning the strings `obama' or `romney' in intervals of 1 hour, transforms them from JSON into a dataframe, and stores them in a mySQL database on localhost.
* `summary_data.R` queries the SQL server for a summary of the number of tweets every minute, cleans and organizes these data, and exports it to a .csv file that will be uploaded to the server.

Notes
-------

* All times are EST.
* The estimated average tweets per minute (TPM) are lower than the real TPM during moments of high activity, such as the debates or the conventions. This is due to the limitations of the Streaming API. (Only around 1% of all tweets can be captured at any given time, and therefore when tweets mentioning Obama or Romney constitute more than this proportion, not all of them can be extracted with the public streaming API.)
* The smoothing parameter computes rolling averages over periods of 10 minutes.