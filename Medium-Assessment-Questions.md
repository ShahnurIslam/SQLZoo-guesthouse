Link to ERM: http://sqlzoo.net/wiki/Guest_House
###6.Ruth Cadbury. Show the total amount payable by guest Ruth Cadbury for her room bookings. You should JOIN to the rate table using room_type_requested and occupants.
```SQL
SELECT SUM(nights*amount) AS "TTL Amount payable"
FROM booking 
JOIN guest ON guest_id = guest.id
JOIN rate ON room_type_requested = room_type
  AND occupancy = occupants
 WHERE first_name = 'Ruth' 
        AND last_name = 'Cadbury'
 
 ```
