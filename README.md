# Spotify-Discover-Weekly-Tracker
Tracks user's Spotify Discover Weekly by importing data into Google Sheets every week <p>
[presentation](https://github.com/almostelle/Spotify-Discover-Weekly-Tracker/blob/b9cf8fd73813726f11ad4ef8e29f7fe566293ad1/13%20Weeks%20of%20%20Spotify%20Discover%20Weeklys.pdf) </p>
### Why I chose to track and rate my Discover Weekly Songs
In 2021 and 2022, I found that I was consistently dissapointed in Spotify's reccomendation of 30 songs in my Discover Weekly playlist. I decided to evaluate all of the weekly playlists to see if a pattern would appear pertaining to what genres Spotify would reccomend and the ratio of like to disliked songs.
The goal was that by the end of the year, I would like about 30% of the songs in each Discover Weekly playlist

### Method
In this study, I documented 3 months of data. That's 13 weeks with 13 different playlists - a total of 390 songs. <p>
**Categories and Rating Metrics** </p>
* Liked - generally liked but did not add to a playlist
* Added - songs I added to a playlist called "New: Jan - Mar"
* Disliked - songs I listened to *all the way through* but disliked
* Skipped - songs that, for one reason or another, I did not listen to all the way through
* If I did not have a specific reation to a song, it would be counted as "neutral"
I could rate them on initial reactions, but I tried to give each item on the list at least two listens. <p>

**Method and Tools** </p>
I knew that I did NOT want to type out 20 songs and artist names every single week, so I need to find a way to automate the insertion of the data in to my Google Sheet. Since Spotify has Web API, I used an API connector extension through Google Sheets. Further, since I knew that the playlists are updated every week, Monday, at 12 AM CT for me, I could trigger the API to update the sheet's information around the same hour Spotify would update.
The API connector used code andSpotify's API to connect my specific Discover Weekly linked to my account, pull whatever information I designated, and populate the spreadsheet with the info.

The biggest problem was that even thogh I could set up the tables where the information would populate, I would still have to copy and paste the info into those tables. The solution was to give every cell a formula that would only populate the cell with the track / artist name when the reference date of the table and the reference date taken from the API connector matched. (See Google Sheets Fomulas code for more info)
This task meant creating three sheets tha would communacate with each other:
* Formatted tables - where the information from the API would populate to. These tables were separated into weeks (Week 1, Week 2, etc). This sheet is where I could rate and view the songs in a easy-to-read format
* Dates -  A two column reference table of dates and weeks. One column would list the week number (Week 1, Week 2, etc) just as the ttiles of the tables were listed. The other column would list the date in YYYY-MM-DD format
* API Reference - This is where the API would output the called infomation from my Discover Weekly playlists. A column would have the datetime the song infomation was added. Other columns contained track name, artist name, and album name

Everyweek, the API would fill its reference table. If the datetime in that table matched the date in the Dates table, it woudl also match the week number to the week number in the formatted tables sheet. Each cell in the formatted tables sheet was set to query the information from the API reference table if the date criteria was met.

### Results
After 13 weeks of listening to songs and tracking reactions I concluded that I liked 35 / 390 songs and added 16 / 390; I skipped 13/390 and disliked 16/390. I ranked weeks on best to least, determined by how many songs I liked or added and skipped or disliked. In conclusion, most of the songs I did not like fell under a specific genre (Broadway, Musical) and there were many songs / artsists I have listened to at least once before. Since my main objective for listening to Discover Weekly is to "Discover" new songs I liked, I couted that as a failure. <p>
**Next Steps** <p>
In the next trial (quarter of the year) I will:
* Add drop-down data validations instead of having to type "liked", "disliked", etc
* try to automate the copying of text through the spreadsheet
* Activiely LIKE (press the like button) and DISLIKE (press the dislike button) in Spotify to help the algorithm learn about my personal listening habits.

### [Feel free to try this method yourself with my premade tables](https://docs.google.com/spreadsheets/d/1DKOiEoxP1mnbhCGh99Hg7Pj68CPWGca5LtmEo1YOz1s/edit?usp=sharing)
[Steps for replication](https://github.com/almostelle/Spotify-Discover-Weekly-Tracker/blob/b9cf8fd73813726f11ad4ef8e29f7fe566293ad1/Replicate%20Spreadsheet)
