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
test").
***
## To Do:
- Just download some CSVs of the data you expect to scrape to get started on algorithms
    - thebaseballcube has some detailed splits and play-by-play info
        - e.g. http://www.thebaseballcube.com/players/profile.asp?Y=2017&ID=146981&View=SplitsP
            - Chris Sale 2017 pitching splits
            - Includes info on count, outs, baserunners,etc.
        - e.g. http://www.thebaseballcube.com/players/profile.asp?Y=2017&ID=146981&View=LogP
            - Chris Sale 2017 pitching game logs
            - Include pitches thrown in each PA, balls/strikes, contact, play result, etc.
        - Maybe automate scraping from here instead of fangraphs
    - BrooksBaseball has some great pitch info too, with pitchfx tracking
        - http://www.brooksbaseball.net/tabs.php?player=519242&p_hand=-1&tto=-1&ppos=-1&cn=200&compType=none&risp=0&1b=0&2b=0&3b=0&rType=perc&gFilt=regular&time=month&minmax=ci&var=usage&s_type=2&startDate=01/01/2017&endDate=01/01/2018&balls=-1&strikes=-1&b_hand=-1
        - pitch usage tables sortable by baserunners, pitch type, and count type (even, full, batter ahead, etc.)
        - pitch outcomes by count
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
                
