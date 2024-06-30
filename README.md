
# 2024 Election Analysis 

This project leverages R for web scraping, while Power BI is used to create interactive dashboards. The combination provides a comprehensive approach to analyze and present voting patterns, demographic insights, and election trends.



## Required Libraries in R

Install rvest

```bash
  install.packages("rvest")
```
Install httr

```bash
  install.packages("httr")
```
Install tidyverse

```bash
  install.packages("tidyverse")
```
## Required Tool
Download "Selector Gadget" extension in Chrome to easily navigate html code.


```bash
  SelectorGadget
```
Download PowerBI 

```bash
  PowerBI
```


    
    
## code

To deploy this project run

```bash
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



```
## File

Access Scraped Data

```bash
  open scraped_data.txt
```
Clean and Import the data in PowerBI

Selector Gadget Demo:


![selectorgadget](https://github.com/rr1028/Election-Analysis-Kalvium-/assets/104455207/371872c9-602a-49b6-b994-34c06399fbe0)

Output File:

![fileoutput](https://github.com/rr1028/Election-Analysis-Kalvium-/assets/104455207/c4047169-e025-4bbb-aafc-4984a274d9c7)


# Key Insights for Analysis:

## 1.Seats won by different parties in different states

## 2.% seats won by each party

## 3.State vs Union territory 

## 4.The voting trend in south 

## 5.The voting trend in north 

## 6.The voting trend in northeast 

## 7.Party trend followed by Voters

## 8.Performance 2019 vs 2024(voters)

## 9.Performance 2019 vs 2024 parties

## 10.Alliance Performance 2024


# PowerBI
```bash
Election 2024 overall data:
```
![election2024](https://github.com/rr1028/Election-Analysis-Kalvium-/assets/104455207/6f2a5b21-3c2a-46b9-8bda-1c29b6b07f73)
```bash
click on any state to view its distribution of parties:
```
![election2024stateview](https://github.com/rr1028/Election-Analysis-Kalvium-/assets/104455207/4ef35f18-4760-4682-b517-0c200de5ceb7)
```bash
State and UT:
```
![states and ut](https://github.com/rr1028/Election-Analysis-Kalvium-/assets/104455207/61e05be8-ee9d-4697-83ae-f13d7460e10f)

```bash
click on any state to view its distribution of parties:
```
UT view

![ut view](https://github.com/rr1028/Election-Analysis-Kalvium-/assets/104455207/07bde456-57c6-4c1e-a182-5200751e8160)

State View

![state view](https://github.com/rr1028/Election-Analysis-Kalvium-/assets/104455207/b1d0cefc-a7a5-442c-8e79-e74f4671bdca)

```bash
Party trend followed by Voters
```
![partytrend](https://github.com/rr1028/Election-Analysis-Kalvium-/assets/104455207/bf5e4e31-f782-4b34-bdbf-b0dd54b7fb32)

```bash
The voting trend in south
```
![south trend](https://github.com/rr1028/Election-Analysis-Kalvium-/assets/104455207/f1dcef99-f111-459b-84a5-5070cae5234e)

```bash
The voting trend in north
```
![northtrend](https://github.com/rr1028/Election-Analysis-Kalvium-/assets/104455207/4ee09aa5-41b2-454c-a28c-303e6cfb3b30)

```bash
The voting trend in northeast
```
![northeasttrend](https://github.com/rr1028/Election-Analysis-Kalvium-/assets/104455207/fac1fc8e-6150-48e5-9a02-25b56470819f)

```bash
Performance 2019 vs 2024(voters)
```
![2019vs2024](https://github.com/rr1028/Election-Analysis-Kalvium-/assets/104455207/566b9fad-8332-43c2-83fb-8ee744bbbc42)

```bash
Performance 2019 vs 2024(party)
```
![partyperformance](https://github.com/rr1028/Election-Analysis-Kalvium-/assets/104455207/da90fc7e-4425-4983-b938-d9c6b6b2a338)

```bash
Alliance Performance 2024
```
![allianceper](https://github.com/rr1028/Election-Analysis-Kalvium-/assets/104455207/807339b7-3816-4cc8-bd8b-d0ece89fa90a)

## Open Dashboard for an interactive experience.

```bash
Election Analysis Dashboard.pbix
```


# THANK YOU!
























