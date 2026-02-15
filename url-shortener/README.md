# URL Shortener

## Functional Requirements
1. Users should be able to submit a long URL and receive a shortened version
2. Users can optionally provide a custom alias and/or expiration for the shortened URL
3. Users should be able to access the original URL by using the shortened URL

## Non-Functional Requirements
1. high availability, eventual consistency for url shortening
2. low latency on redirects (<200ms)
3. system scale to support 100M DAU and 1B urls
4. short urls should be unique

## Core Entities
1. Long (Original) Url
2. Short Url
3. User

## API Design
```java
// 1. shorten a URL
POST /api/v1/tiny-url/shorten -> shortUrl
(user auth details in header)
{
	originalUrl,
	alias ?,
	expiration-time ?
}

// 2. redirection
GET /api/v1/tiny-url/{short-url} -> HTTP 302 redirect to original url
```

## [High Level Design](https://github.com/svetanis/system-design/blob/main/url-shortener/high-level-design.png)

## [NotebookLM Slides](https://github.com/svetanis/system-design/blob/main/url-shortener/slides.pdf)

## [NotebookLM Diagram](https://github.com/svetanis/system-design/blob/main/url-shortener/diagram.png)
