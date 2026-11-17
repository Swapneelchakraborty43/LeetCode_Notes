
1. What is apache camel and what is its use in SB?
- Apache Camel is an integration framework that helps connect different systems and services using standard enterprise integration patterns. In a Spring Boot microservices application, we use it to handle routing, transformation, and communication between services through clear routes instead of hard-coding the calls everywhere.”


2. What is the difference between Direct and SEDA endpoints in Apache Camel?
- Direct endpoint is synchronous and runs in the same thread, so the message goes immediately to the next step without queuing. Seda, on the other hand is asynchronous, using an in-memory queue, so the messages are processed by another consumer thread. In short, direct is instant and same-thread, while Seda puts the message in a queue and processes it asynchronously.


3. Internal working of HashMap?
- HashMap uses an array of buckets. It takes the key, runs a hash function, and finds the bucket. If two keys land in the same bucket, it checks with equals. If keys are really the same, it updates the value. If not, it chains the entries, and in Java 8, it can switch from a list to a red-black tree to keep things fast.

4. Camel use in project?
- We used Camel to manage integration flows between our messaging system and downstream services. Messages came from our queue, a Camel route picked them up, we transformed the payload, called a few REST services to enrich data, and finally sent a clean SMS request to the aggregator.” Then add one more line on error handling, like: “We also used Camel’s onException with retry policies to handle failures cleanly.” That'll sound confident but not too long.

5. Writing test cases for camel route?
“I'd use Camel Test support with Mock endpoints, like sending a test message into a direct start route, then asserting what arrives at a mock endpoint

6. 

7. What is the difference between PUT and PATCH in REST APIs?

- PUT is used to replace the entire resource. For example, if we have a customer record, and we send a PUT request, we usually send the full set of fields, like name, email and address, and it replaces the old resource. PATCH, on the other hand, is for updating only specific fields. For example, if we only want to update the address, we send just the new address in the PATCH request and keep the other fields unchanged.
- PUT equals full update, PATCH equals partial update.


