### Friday January 29th 2021

I set up the api key secrets.

A helper function will check the R environment variables for a key named "VRD_API".  
If the variable doesn't exist it will remind to user to set it and how to do that.  
With the error message `You must set your VRD_API with Sys.setenv(VRD_API = 'your_api_key_here')`.

I chose to use the R system env for a couple reasons. First, I dont want to store the secrets in plain text in side a file.  
And since our end goal is to upload this package to CRAN I think having a `secrets.txt` that is read is more difficult to set up compared to Sys.setenv().

Currently I have to set the api key every time I refresh my RStudio, so Im working on a permanent solutinon.

Also I set up an api call function `get_recall_by_number()` to test the api key getter function as well as making sure this first api call works.

Commits for this:
https://github.com/WraySmith/caRecall/pull/1/commits


### Sunday January 31st 2021

I gave PR review for https://github.com/WraySmith/caRecall/pull/4
Checked for code accuracy and style adherence.


### Monday Febuary 1st 2021

I gave PR review for https://github.com/WraySmith/caRecall/pull/10
Checked for code accuracy and stile adherence.
We talked about our naming convention, we decided to go with shorter funciton names at the cost of not always having them contain a verb.
I found a flaw in our code. Our api response wasnt being checked for error codes in the right spot which lead to difficult to debug responses for a 403 error code.

