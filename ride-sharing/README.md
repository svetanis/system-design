# Design a Ride-Sharing Service Like Uber 
Uber is a Ride-Sharing platform that connects passengers with drivers
who offer transportation services in personal vehicles. It allows
users to book rides on-demand from their smartphones, matching them
with a nearby driver who will take them from their location to their
desired destination. When the system finds a match, it sends an update
to the driver asking them to accept or decline the ride.

## Functional Requirements
1. Riders should be able to input a start location and a destination and get a fare estimate
2. Riders should be able to request a ride based on the estimated fare
3. Drivers should be able to accept/decline a request and navigate to pickup/drop-off

## Non-Functional Requirements
1. prioritize low latency ride matching (<1min)
2. prioritize strong consistency in ride matching to present driver's overbooking
3. highly available outside the matching
4. be able to handle high throughput during peak hours (up to 100K requests from same location)
5. System Scale: 100M DAU, 15M rides per day

## API Design
```java
1. request a fare
POST /ride/fare-estimation
	body : {
		pickupLocation : "",
		destination : ""
	} -> Fare[]
	
2. request a ride
POST /ride/request
	header : JWT
	body : {
		fareId : ""
	} -> Ride{}
	
3. update driver location
POST /drivers/location -> 200 OK | Failure
	body : {
		latitude
		longitude
	}
4. accept ride
PATCH /ride/driver/accept -> Ride
	body : {
		rideId : ""
		accept/deny
	}
5. update status
PATCH /ride/driver/update
	body : {
		rideId : ""
		status : "pickedUp" | "droppedOff"
	} -> lat/long | null
```

## [High Level Design](https://github.com/svetanis/system-design/blob/main/ride-sharing/high-level-design.png)

## [NotebookLM Slides](https://github.com/svetanis/system-design/blob/main/ride-sharing/slides.pdf)

## [NotebookLM Diagram](https://github.com/svetanis/system-design/blob/main/ride-sharing/diagram.png)
