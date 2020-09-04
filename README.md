# WhichPitch
***
### Project Author: Sam Unger
### GitHub: [Author Page](https://github.com/ungersk1998)
### Version: Still in Early Development
***
## Project Description
WhichPitch is a Python project with the goal of predicting the best pitch to throw in any given baseball situation. This 
project will be built incrementally, starting with minimal features and situations and (hopefully) expanding to account
for every baseball situation. Predictors will include pitcher and batter histories, number of outs, men on base, and runs
scored. Output will be pitch type and location (e.g. slider low and away). Pitch predictions will be considered satisfactory 
if they show success under cross-validation and make sense to a person with good baseball knowledge (a.k.a. "pass the eye 
test"). Note again that the goal of this project is to decide the *best* pitch to throw, not necesarily what pitch a batter
should expect (given pitch usage histories, for example), although intelligent support for pitch choice based on previous
pitch usage may be considered at some point in development.
***
## To Do:
- Choose/design best pitch algorithm from currently scrapable data
    - Remember original plan to choose objective function by current situation
    - Compare generated best pitch suggestions to pitch usage histories from Brooks BB
    - Need to adjust pitch selector function params for cleanliness and control
        - Make it possible to enter all game state params as single dict
        - Allow user to specify history combination method in function call
        - Allow user to specify other params for internal functions in function call
        - Maybe just allow user to call function with no inputs to trigger interactive input questionnaire

- thebaseballcube has some detailed splits and play-by-play info
    - e.g. http://www.thebaseballcube.com/players/profile.asp?Y=2017&ID=146981&View=SplitsP
        - Chris Sale 2017 pitching splits
        - Includes info on count, outs, baserunners,etc.
    - e.g. http://www.thebaseballcube.com/players/profile.asp?Y=2017&ID=146981&View=LogP
        - Chris Sale 2017 pitching game logs
        - Include pitches thrown in each PA, balls/strikes, contact, play result, etc.
- Webscraping Support for FanGraphs
    - Use requests, BeautifulSoup libraries, maybe re (regular expressions), too
    - Create functional interface to accept URL query params and find desired webpage (2ish main ones)
        - Pitching Splits/Play Log
            - e.g. Chris Sale Pitching Play Log base URL: fangraphs.com/players/chris-sale/10603/play-log?
            - Query params: position=P, season=2017
            - Want to be able to input pitcher name and season and return play log df
        - Batter Splits
            - e.g. Aaron Judge Batting Splits Tool base URL: fangraphs.com/players/aaron-judge/15640/splits-tool?
            - Query Params: splitArr=&splitArrPitch=&position=B&autoPt=false&splitTeams=false&statType=player&
                statgroup=1&startDate=2002-01-01&endDate=2019-11-01&players=&filter=&groupBy=season&sort=-1,1
            - Important splits for now:
                - vs RHP
                - Situation (outs,runners)
                - Count
                - Pitch type
            - Want to be able to input batter name, season, and desired splits to return df
                
