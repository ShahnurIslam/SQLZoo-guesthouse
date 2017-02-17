Link to ERM: http://sqlzoo.net/wiki/Guest_House

###1.Guest 1183. Give the booking_date and the number of nights for guest 1183
```SQL
SELECT booking_date, nights
  FROM booking WHERE guest_id = '1183'
```
###2.When do they get here? List the arrival time and the first and last names for all guests due to arrive on 2016-11-05, order the output by time of arrival.

```SQL
SELECT arrival_time, first_name, last_name 
  FROM booking b
  JOIN guest g
    ON b.guest_id = g.id
  WHERE booking_date = '2016-11-05'
ORDER BY 1 ASC -- rather than writing the actual column name, you can order by column number
```
###3.Look up daily rates. Give the daily rate that should be paid for bookings with ids 5152, 5165, 5154 and 5295. Include booking id, room type, number of occupants and the amount.

```SQL
SELECT booking_id, room_type_requested, occupants, amount
  FROM booking b 
  JOIN rate r 
    ON b.room_type_requested = r.room_type 
      AND b.occupants = r.occupancy
 WHERE booking_ID IN(5152,5165,5154,5295)
```
###4.Who’s in 101? Find who is staying in room 101 on 2016-12-03, include first name, last name and address.
```SQL
SELECT first_name, last_name, address 
  FROM booking b 
  JOIN guest g 
    ON b.guest_id = g.id
 WHERE room_no =101 
  AND booking_date = '2016-12-03'
```

###5.How many bookings, how many nights? For guests 1185 and 1270 show the number of bookings made and the total number nights. Your output should include the guest id and the total number of bookings and the total number of nights.
```SQL
SELECT guest_id, COUNT(*) AS "Total Bookings", SUM(nights) AS "Total Nights" -- I find adding aliases makes tables make more sense
FROM booking
WHERE guest_id IN(1185,1270)
GROUP BY 1 
```
