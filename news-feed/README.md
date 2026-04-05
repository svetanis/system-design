# Design Facebook's News Feed
Facebook is a social network which pioneered the News Feed, 
a product which shows recent stories from users in your social graph.

## Functional Requirements
1. Users should be able to create posts
2. Users should be able to friend/follow people 
(these are uni-directional follow relationships)
3. Users should be able to view of posts from people they follow,
in chronoligical order
4. Users should be able to page through their feed

## Non-Functional Requirements
1. prefer high availability over strong consistency 
   eventual consistency ok : post visible in < 1min
2. low latency for posting and viewing posts (< 500ms)
3. system should be scalable to support 2B users

## API Design
```java
1. create post 
POST /posts
	body : {
		content : ""
	}
	
2. view posts -> Post[], nextCursor 
GET /feed?cursor={cursor}&limit={limit}

3. follow other users -> 200 OK
PUT /users/{id}/followers
	body : {
		follower : ""
	}
```

## [High Level Design](https://github.com/svetanis/system-design/blob/main/news-feed/high-level-design.png)

## [NotebookLM Slides](https://github.com/svetanis/system-design/blob/main/news-feed/slides.pdf)

## [NotebookLM Diagram](https://github.com/svetanis/system-design/blob/main/news-feed/diagram.png)
