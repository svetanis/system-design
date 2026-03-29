# Design a Ticket Booking Site Like Ticketmaster 
Ticketmaster is an online platform that allows users to purchase tickets 
for concerts, sporting events, theater, and other live entertainment

## Functional Requirements
1. Users should be able to view events
2. Users should be able to search for events
3. Users should be able to book tickets to events

## Non-Functional Requirements
1. Prefer strong consistency for booking tickets (no double booking)
2. Prefer high availability for view and search of events
3. Low latency search (<500ms)
4. Scalability to handle surges from popular events
5. System Scale: support 100M DAU and up to 100K events/day and 1M events at a time

## API Design
```java
1. search events
GET /events?term={term}&location={location}&start={startDate}&end={endDate}
	&page={1}&size={10} -> Partial<Event>[]
	
2. view event
GET /events/{eventId} -> Event{name, venue, time, performer, tickets[]}

3. book ticket -> bookingId + confirmation message
POST /events/{eventId}/booking
	header : JWT | sessionToken
	body : {
		ticketIds : string[]
		paymentDetails (stripe)
	}
```

## [High Level Design](https://github.com/svetanis/system-design/blob/main/ticket-booking/high-level-design.png)

## [NotebookLM Slides](https://github.com/svetanis/system-design/blob/main/ticket-booking/slides.pdf)

## [NotebookLM Diagram](https://github.com/svetanis/system-design/blob/main/ticket-booking/diagram.png)
