-- Create shipment
select * from event_audit ea where request_id = '90d6a937-a98e-4cce-a52a-33bcb92dfc09';

-- Asset assignment
select * from event_audit ea where request_id = '59f080d2-ad82-4910-ae8e-1e3b108c909c';

-- LO
SELECT * FROM event_audit ea WHERE request_id = '55ce4c93-869d-4f0b-bf3b-267bc7d6ac88';

-- Carrier Arrival
SELECT * FROM event_audit ea WHERE request_id = '8e2fcf60-c676-4012-a027-245b42bab1ab';

-- LO Departure Origin
SELECT * FROM event_audit ea WHERE request_id = '59ebf5de-9d2b-4223-ba93-e33d3c341c40';

-- Carrier Departure
SELECT * FROM event_audit ea WHERE request_id = '6411fe1e-7ee4-4135-bc3f-88ba217ad974';

-- LO Near Destination
SELECT * FROM event_audit ea WHERE request_id = '0dfd2ca0-90b2-4a46-b023-09de0a206104';

-- LO at Destination
SELECT * FROM event_audit ea WHERE request_id = '63c911b3-0ef0-4fe3-a138-f89db91f377f';

-- Carrier Arrival at Destination
SELECT * FROM event_audit ea WHERE request_id = 'b1485fa8-26da-473a-9b47-666c61958656';

-- LO Departing Destination
SELECT * FROM event_audit ea WHERE request_id = '0c75ddbe-e38c-4733-883e-c802fef914b9';

-- Carrier Departure from Destination
SELECT * FROM event_audit ea WHERE request_id = '47fa093c-eca8-418a-beb4-5b5ec664de4f';
 
