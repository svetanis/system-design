# Design a File Storage Service Like Dropbox
Dropbox is a file hosting service that offers cloud storage, 
file synchronization, personal cloud, and client software.

## Functional Requirements
1. Users can upload files to remote storage
2. Users can download files from remote storage
3. Users can automatically sync files across devices

## Non-Functional Requirements
1. high availability >> strong consistency
2. low latency for upload and download large files up to 50G
3. low latency for file sync (< 1min) changes should be picked up quickly
4. fault tolerant upload - recover files when corrupted or interrupted
5. system should scale for 100M DAU

## Core Entities
1. Client
2. File
3. File Metadata
4. Directory

## API Design
```java
1. upload file
	POST /files -> fileId + pre-signed url
	body : {
		name : "",
		type : "",
		size : long
		metadata ...
	}
	
2. upload file
	POST /files/{pre-signed url}
	body : {
		file : bytes
	}
	
3. download file
	GET /files/{fileId} -> File + FileMetadata
	
4. sync file
	GET /files/{fileId}/changes -> FileMetadata[]
```

## [High Level Design](https://github.com/svetanis/system-design/blob/main/file-storage/high-level-design.png)

## [NotebookLM Slides](https://github.com/svetanis/system-design/blob/main/file-storage/slides.pdf)

## [NotebookLM Diagram](https://github.com/svetanis/system-design/blob/main/file-storage/diagram.png)
