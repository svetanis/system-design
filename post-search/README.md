# Design Facebook's Post Search
Facebook is a social media platform that allows users to share their posts with their friends. 
The search functionality allows them to find a specific post by keyword, with sort options.

## Functional Requirements
1. Users should be able to create and like posts
2. Users should be able to search posts by keyword
3. Users should be able to get search results sorted by recency or like count

## Non-Functional Requirements
1. prefer high availability over strong consistency 
(eventual consistency ok) 
2. low latency search (< 500ms)
3. index posts within 1 min of creation
3. system scale: support 1B DAU and 1T posts

## System Interface
```java
1. create post 
POST /posts
	body : {
		text : ""
	}
	
2. like post 
POST /posts/{postId}/likes
	body : {
		like : boolean
	}
	
3. search posts
GET /posts?key={keyword}&sortBy={like|TIME}&cursor={cursor}&pageSize={10}&pageToken={token}
--> Post[], nextPageToken={token}
```

## [High Level Design](https://github.com/svetanis/system-design/blob/main/post-search/high-level-design.png)

## [NotebookLM Slides](https://github.com/svetanis/system-design/blob/main/post-search/slides.pdf)

## [NotebookLM Diagram](https://github.com/svetanis/system-design/blob/main/post-search/diagram.png)
