# Task Description :

CREATE TABLE accounts
(
account_number int, 
group_name varchar(28),
country varchar(5),
account_status varchar(8),
registration_date_utc datetime,
upfront_price int, 
unlock_price int,
product_name varchar(25));
   
INSERT INTO accounts
    (account_number, group_name, country, account_status, registration_date_utc, upfront_price, unlock_price, product_name)
VALUES
    (3311339, 'Radio SHS 60 Easy Buy Siaya', 'Kenya', 'UNLOCKED', '2017-04-01 03:41:44', 2600, 12750, 'Sun King Home 60 Easy Buy'),
    (1417336, 'Pro Easy Buy Kisumu', 'Kenya', 'ENABLED', '2017-04-01 04:31:10', 1195, 4695, 'Sun King Pro Easy Buy'),
    (2990935, 'SHS 60 Easy Buy Kakamega', 'Kenya', 'DISABLED', '2017-04-01 04:54:17', 1600, 11750, 'Sun King Home 60 Easy Buy'),
    (2692440, 'SHS 60 Easy Buy Eldoret', 'Kenya', 'UNLOCKED', '2017-04-01 05:15:24', 1600, 11750, 'Sun King Home 60 Easy Buy'),
    (2733848, 'SHS 60 Easy Buy Kitui', 'Kenya', 'ENABLED', '2017-04-01 05:22:16', 1600, 11750,  'Sun King Home 60 Easy Buy'),
    (3866241, 'SHS 60 Easy Buy Eldoret', 'Kenya', 'DISABLED', '2017-04-01 05:48:31', 1600, 11750, 'Sun King Home 60 Easy Buy'),
    (1143437, 'Pro Easy Buy Kapsabet', 'Kenya', 'UNLOCKED', '2017-04-01 06:11:52', 1195, 4695, 'Sun King Pro Easy Buy'),
    (3241841, 'SHS 60 Easy Buy Eldoret', 'Kenya', 'DISABLED', '2017-04-01 06:13:57', 1600, 11750, 'Sun King Home 60 Easy Buy'),
    (32513806,'SHS 60 Easy Buy Kisumu', 'Kenya', 'UNLOCKED', '2017-04-01 06:16:05', 1600, 11750, 'Sun King Home 60 Easy Buy'),
    (1498930, 'Pro Easy Buy Eldoret', 'Kenya', 'UNLOCKED', '2017-04-01 06:19:02', 1195, 4695, 'Sun King Pro Easy Buy'),
    (2983633, 'SHS 60 Easy Buy Kakamega', 'Kenya', 'UNLOCKED', '2017-04-01 06:38:53', 1600, 11750, 'Sun King Home 60 Easy Buy'),
    (3310638, 'SHS 60 Easy Buy Homa Bay', 'Kenya', 'UNLOCKED', '2017-04-01 07:40:54', 1600, 11750, 'Sun King Home 60 Easy Buy'),
    (1420231, 'Pro Easy Buy Kakamega', 'Kenya', 'UNLOCKED', '2017-04-01 07:50:59', 1195, 4695, 'Sun King Pro Easy Buy'),
    (3231743, 'SHS 60 Easy Buy Kapsabet', 'Kenya', 'UNLOCKED', '2017-04-01 07:51:10', 1600, 11750, 'Sun King Home 60 Easy Buy'),
    (3240645, 'SHS 60 Easy Buy Kakamega', 'Kenya', 'UNLOCKED', '2017-04-01 08:07:40', 1600, 11750, 'Sun King Home 60 Easy Buy'),
    (3477742, 'SHS 60 Easy Buy Bungoma', 'Kenya', 'UNLOCKED', '2017-04-01 08:22:40', 1600, 11750, 'Sun King Home 60 Easy Buy'),
    (3822343, 'SHS 60 Easy Buy Eldoret', 'Kenya', 'UNLOCKED', '2017-04-01 08:54:02', 1600, 11750, 'Sun King Home 60 Easy Buy')
    
    
CREATE TABLE payments
(payment_id varchar(9),
transaction_date datetime,
account_number int,
group_name varchar(28), 
amount int, 
down_payment varchar(1));
   
INSERT INTO payments
    (payment_id, transaction_date, account_number, group_name, amount, down_payment)
VALUES
    ('PA685882', '2017-04-22 08:33:10',  3311339, 'Radio SHS 60 Easy Buy Siaya', 100, 'f'),
    ('PA1072129', '2017-06-13 17:13:42', 3311339, 'Radio SHS 60 Easy Buy Siaya', 100, 'f'),
    ('PA1123806', '2017-06-19 17:04:07', 3311339, 'Radio SHS 60 Easy Buy Siaya', 50, 'f'),
    ('PA1360329', '2017-07-13 18:25:52', 3311339, 'Radio SHS 60 Easy Buy Siaya', 50, 'f'),
    ('PA1403215', '2017-07-17 18:13:10', 3311339, 'Radio SHS 60 Easy Buy Siaya', 100, 'f'),
    ('PA2000354', '2017-08-30 18:54:44', 3311339, 'Radio SHS 60 Easy Buy Siaya', 50, 'f'),
    ('PA2092940', '2017-09-05 17:03:24', 3311339, 'Radio SHS 60 Easy Buy Siaya', 100, 'f'),
    ('PA2312120', '2017-09-18 16:03:54', 3311339, 'Radio SHS 60 Easy Buy Siaya', 50, 'f'),
    ('PA1553076', '2017-07-30 16:50:45', 2990935, 'SHS 60 Easy Buy Kakamega', 70, 'f'),
    ('PA2172469', '2017-09-10 16:15:35', 2990935, 'SHS 60 Easy Buy Kakamega', 50, 'f'),
    ('PA566919', '2017-04-01 05:22:16',  2733848, 'SHS 60 Easy Buy Kitui', 1650, 't'),
    ('PA1392738', '2017-07-17 06:38:04', 2733848, 'SHS 60 Easy Buy Kitui', 50, 'f'),
    ('PA1421230', '2017-07-19 15:43:42', 2733848, 'SHS 60 Easy Buy Kitui', 50, 'f'),
    ('PA1616542', '2017-08-04 14:30:19', 2733848, 'SHS 60 Easy Buy Kitui', 50, 'f'),
    ('PA1671189', '2017-08-08 14:53:01', 2733848, 'SHS 60 Easy Buy Kitui', 100, 'f'),
    ('PA733906', '2017-04-29 17:14:40',  1143437, 'Pro Easy Buy Kapsabet', 75, 'f'),
    ('PA1097075', '2017-06-16 16:24:35', 1143437, 'Pro Easy Buy Kapsabet', 100, 'f'),
    ('PA1480639', '2017-07-24 16:59:27', 3310638, 'SHS 60 Easy Buy Homa Bay', 100, 'f'),
    ('PA1592349', '2017-08-02 16:22:36', 3310638, 'SHS 60 Easy Buy Homa Bay', 100, 'f'),
    ('PA605714', '2017-04-08 11:33:36',  1420231, 'Pro Easy Buy Kakamega', 450, 'f'),
    ('PA1296011', '2017-07-07 17:35:33', 3231743, 'SHS 60 Easy Buy Kapsabet', 50, 'f'),
    ('PA1930767', '2017-08-26 15:20:44', 3231743, 'SHS 60 Easy Buy Kapsabet', 50, 'f'),
    ('PA2489852', '2017-09-27 17:13:26', 3231743, 'SHS 60 Easy Buy Kapsabet', 50, 'f'),
    ('PA2530419', '2017-09-29 17:26:14', 3231743, 'SHS 60 Easy Buy Kapsabet', 50, 'f'),
    ('PA746761', '2017-05-01 17:41:31',  3477742, 'SHS 60 Easy Buy Bungoma', 200, 'f'),
    ('PA784063', '2017-05-07 13:31:15',  3477742, 'SHS 60 Easy Buy Bungoma', 100, 'f'),
    ('PA965171', '2017-05-31 17:56:39',  3477742, 'SHS 60 Easy Buy Bungoma', 50, 'f')
    ;

### -- /TASK 1. Write a query to list count of unique accounts by group_name/

### -- /TASK 2. accounts table has the amount to be paid to unlock every
### -- account (unlock_price). And payments table has the amount
### -- paid by the accounts in every installment. Write a query to
### -- get percentage of total amount paid out of the
### -- total unlock_price amount for every type of
### -- product(product_name). There is a one to many relationship
### -- between accounts and payments /

### -- /TASK 3. Write a query to calculate the cumulative amount paid with every payment 
### -- by the accounts along with the %age of the total amount paid i.e 
### -- (cumulative amount/unlock_price) by the accounts till date  /
