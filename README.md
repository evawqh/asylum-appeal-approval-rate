# cjs-databases-project-asylum-database
 This program scrapes Lexis Nexis and creates a database of over 600 asylum cases heard in the 2nd Circuit Immigration Court, with approvals, denials, corresponding to countries of origin and key terms used in trial.

To use this code, one needs to have a login for Lexis Nexis and be able to put in the credentials manually. The code does the rest.

It advance searches for cases containing the word 'asylum' AND categorized under 'asylum and refugees'. One can choose the time range they're hoping to look at.

After the search results are narrowed down, as shown below:

<img width="790" alt="asylum" src="https://user-images.githubusercontent.com/116761533/213279728-910eac71-8c5c-45bb-a5ef-460171c19381.png">

I used [Playwright](https://github.com/RayzaOliveira/web-scraping-with-playwright) (a web scraping tool similar to Selenium) to click into each case, go into different pages, etc. 

Within each case, I use [BeautifulSoup](https://beautiful-soup-4.readthedocs.io/en/latest/) (which turned out to more reliably get content but unfortunately cannot interact with the site itself) to scrape for the case title, core terms, and the judge's written opinion.

<img width="774" alt="Screenshot 2023-01-13 at 2 47 17 PM" src="https://user-images.githubusercontent.com/116761533/213279808-d12060f9-5970-414b-8072-992cd9d266a3.png">

While the case title and core terms are directly put into the database, opinions are usually pages long. I therefore decided to use Regular Expression (Regex) to find out whether the particular case is denied or granted and the asylum seeker(s)' nationality, which are then also added into the database.
