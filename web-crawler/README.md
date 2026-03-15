# Design a Web Crawler
A web crawler is a program that automatically traverses the web by downloading web pages
and following links from one page to another. It is used to index the web for search engines,
collect data for research, or monitor websites

## Functional Requirements
1. Crawl the web starting from a given set of seed URLs.
2. Extract text data from each web page and store the text for later processing.

## Non-Functional Requirements
1. Fault tolerance to handle failures gracefully
and resume crawling without loosing progress
2. Politeness to adhere to robot.txt and not overload websites
3. Efficiency to crawl the web in 5 days
4. Scalability to crawl 10B web pages

## System Interface
```java
Input: Seed Urls ---> Output: HTML -> Text Data
```
## Data Flow
1. Take seed URL from frontier and request IP from DNS
2. Fetch HTML from external server using IP
3. Extract text data from HTML
4. Apply hash function and create checksum
5. Store text to db if not already present
6. Extract any linked URLs from HTML and 
add them to list of URLs to Crawl
7. Repeat steps 1-6 until all URLs have been crawled

## [High Level Design](https://github.com/svetanis/system-design/blob/main/web-crawler/high-level-design.png)

## [NotebookLM Slides](https://github.com/svetanis/system-design/blob/main/web-crawler/slides.pdf)

## [NotebookLM Diagram](https://github.com/svetanis/system-design/blob/main/web-crawler/diagram.png)
