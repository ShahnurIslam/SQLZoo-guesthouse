#1.Guest 1183. Give the booking_date and the number of nights for guest 1183
```SQL
SELECT booking_date, nights
  FROM booking WHERE guest_id = '1183'
```
#2.When do they get here? List the arrival time and the first and last names for all guests due to arrive on 2016-11-05, order the output by time of arrival.

```SQL
SELECT arrival_time, first_name, last_name 
  FROM booking b
  JOIN guest g
    ON b.guest_id = g.id
  WHERE booking_date = '2016-11-05'
ORDER BY 1 ASC
```
