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

### Wednesday Febuary 3rd 2021

I created the PR https://github.com/WraySmith/caRecall/pull/11
Setup CI/CD for projects with the framework of automated testing. This is important going forward to make sure pushes dont break the code. Ran into an issue using ubuntu for github actions, it said invalid SSL certificate. This isnt an issue now since I switched it to MacOS, but will be solved when we move our project to CRAN. Right now our tests ignore some important bits, but in my next PR I'll address this and make the tests more comprehensive.


### Thursday Febuary 4th 2021
Merged In https://github.com/WraySmith/caRecall/pull/11/files after some changes.
Gave code review on https://github.com/WraySmith/caRecall/pull/12.


### Friday Febuary 5th 2021
Gave code review for https://github.com/WraySmith/caRecall/pull/17 to help clarify teammate's code
Gave code review for https://github.com/WraySmith/caRecall/pull/20/files to help check for code and style consistency
We did a feature branch PR to main https://github.com/WraySmith/caRecall/pull/21, I double checked that everything was in order.
I began working on my portion of the unit tests: https://github.com/WraySmith/caRecall/pull/28 Unit tests are important so we know if we break something or if the api some how changes. I had lots of api calls in my tests and since Im not super knowledgable of dependancy injection or other testing techniques I was breaking the CI/CD pipeline with 429 (too many api requests). So I worked over the next couple days to make my tests smarter and remove the redundant ones.


### Saturday Febuary 6th 2021
We had a group call to discuss time lines and progress, we deemed that we were on schedule.
Reviewed https://github.com/WraySmith/caRecall/pull/26 and https://github.com/WraySmith/caRecall/pull/27

### Sunday Febuary 7th 2021
Continued working on https://github.com/WraySmith/caRecall/pull/28

### Monday Febuary 8th 2021
Merged https://github.com/WraySmith/caRecall/pull/28 (my unit tests) after cleaning it up. We also changed out CI/CD to only use one opperating system on push/pull tests, with the option to trigger tests on MacOS, windows, and linux manually if needed. We have ~95% code coverage now.

### Tuesday Febuary 9th 2021
Working on cleaning up the documentaion with https://github.com/WraySmith/caRecall/pull/34/files. Working adding examples and fixing typos. This is an important piece if we want to have our project hosted on CRAN.


### Wednesday Febuary 10th 2021
Continued working on roxygen documentation https://github.com/WraySmith/caRecall/pull/34/files. I am adding a details section so the doc's pdf will be top quality.
Added a spell check package also for automated proofreading.

### Friday Febuary 12th 2021
I wrote a small function to test the validity of the URL for our APIs. https://github.com/WraySmith/caRecall/pull/39.
The function checks to see if the limit of reponses is greater than 0. It also checks that the year range is valid (start_year <= end_year), and has 6 unit tests.
