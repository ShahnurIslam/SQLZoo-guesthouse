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
###7.Including Extras. Calculate the total bill for booking 5128 including extras


###8.Edinburgh Residents. For every guest who has the word “Edinburgh” in their address show the total number of nights booked. Be sure to include 0 for those guests who have never had a booking. Show last name, first name, address and number of nights. Order by last name then first name.

```SQL
-- Use a left join to include all guests from the guest table and we use the COALESCE function to change Nulls into 0
SELECT  last_name, first_name, address, COALESCE(SUM(nights),0) AS "nights" FROM guest g
LEFT JOIN booking b on g.id = b.guest_id
WHERE address LIKE '%Edinburgh%'
GROUP BY 1,2,3
ORDER BY 1,2
```