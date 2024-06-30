# Election-Analysis-Kalvium-
This project leverages R for web scraping, while Power BI is used to create interactive dashboards. The combination provides a comprehensive approach to analyze and present voting patterns, demographic insights, and election trends.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
R language is used for creating the script for web scraper.
The code for web scrapper:
#required libraries

library(rvest)
library(httr)
library(tidyverse)

# Define the target URL

url <- "https://results.eci.gov.in/PcResultGenJune2024/index.htm"

# Set the user agent to mimic a browser

response <- GET(url, add_headers('User-Agent' = 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.124 Safari/537.36'))

# Check the status of the response

status_code(response)

# If the status is 200, proceed with scraping

if (status_code(response) == 200) {
  # Read the HTML content of the webpage
  
  webpage <- content(response, as = "text")
  webpage <- read_html(webpage)
  
  # Use CSS selectors to extract the data you want
  
  party <- html_nodes(webpage, "tr > :nth-child(1)") %>% html_text()
  
  
  
  
  
  # Check the number of columns of data per scrape match
  
  length(titles)
  
  # Combine the extracted data into a data frame
  
  data <- data.frame(
    party = party
    )
  
  # View the scraped data
  view(data)
  write.table(data, file = "scraped_data.txt", sep = "\t", row.names = FALSE, quote = FALSE)
} else {
  print("Failed to retrieve the webpage.")
}
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

