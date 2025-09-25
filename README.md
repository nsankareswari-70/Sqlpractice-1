### Sqlpractice-1
Database:Northwind    
website: https://www.sql-practice.com/

Queries with Answers:
```
1. Show the category_name and description from the categories table sorted by category_name.
 select category_name,description from categories order by category_name;
```
```
2. Show all the contact_name, address, city of all customers which are not from 'Germany', 'Mexico', 'Spain'
 select contact_name,address,city from customers where country not in('Germany','Mexico','Spain');
```
```
3. Show order_date, shipped_date, customer_id, Freight of all orders placed on 2018 Feb 26
 select order_date,shipped_date,customer_id,freight from orders where order_date='2018-02-26';
```
```
4. Show the employee_id, order_id, customer_id, required_date, shipped_date from all orders shipped later than the required date   
 select employee_id,order_id,customer_id,required_date,shipped_date from orders where shipped_date>required_date;
```
```
5. Show all the even numbered Order_id from the orders table
 select order_id from orders where order_id%2=0;
```
```
6. Show the city, company_name, contact_name of all customers from cities which contains the letter 'L' in the city name, sorted by contact_name
 select city,company_name,contact_name from customers where city like '%L%' order by contact_name;
```
```
7. Show the company_name, contact_name, fax number of all customers that has a fax number. (not null)
  select company_name,contact_name,fax from customers where fax is not null;
```
```
8. Show the first_name, last_name. hire_date of the most recently hired employee.
 select first_name,last_name,hire_date from employees where hire_date=
(select max(hire_date) from employees);
 ```
```
9. Show the average unit price rounded to 2 decimal places, the total units in stock, total discontinued products from the products table.
select round(avg(unit_price),2) as average_price,sum(units_in_stock) as total_stock,sum(discontinued) as total_discontinued from products;
```
```
Database : Hospital
1.Show first name, last name, and gender of patients whose gender is 'M'
  select first_name,last_name,gender from patients where gender='M';select first_name,last_name,gender from patients where gender='M';
```
```
2. Show first name and last name of patients who does not have allergies. (null)
   select first_name,last_name from patients where allergies is null;
```
```
3. Show first name of patients that start with the letter 'C'
   select first_name from patients where first_name like 'C%';
```
```
4. Show first name and last name of patients that weight within the range of 100 to 120 (inclusive)
   select first_name,last_name from patients where weight between 100 and 120;
```
```
5. Update the patients table for the allergies column. If the patient's allergies is null then replace it with 'NKA'
   update patients set allergies='NKA' where allergies is null;
```
```
6. Show first name and last name concatinated into one column to show their full name.
   select concat(first_name,' ',last_name)as Full_name from patients;
```
```
7. Show first name, last name, and the full province name of each patient.
   select first_name,last_name,province_name from patients p join province_names pn on p.province_id=pn.province_id;
```
```
8. Show how many patients have a birth_date with 2010 as the birth year.
   select count(*) as Total_patients from patients where year(birth_date)=2010;
```
```
9. Show the first_name, last_name, and height of the patient with the greatest height.
select first_name,last_name,height from patients where height=
(select max(height) from patients);
```
```
10. Show all columns for patients who have one of the following patient_ids:
1,45,534,879,1000
select * from patients where patient_id in(1,45,534,879,1000);
```
```
11. Show the total number of admissions
select count(*) as Total_Admissions from admissions;
```
```
12. Show all the columns from admissions where the patient was admitted and discharged on the same day.
  select * from admissions where admission_date=discharge_date;
```
```
13. Show the patient id and the total number of admissions for patient_id 579.
select patient_id,count(*) as Total_admissions from admissions where patient_id=579;
```
```
14. Based on the cities that our patients live in, show unique cities that are in province_id 'NS'.
select distinct city as unique_cities from patients where province_id='NS';
```
```
15. Write a query to find the first_name, last name and birth date of patients who has height greater than 160 and weight greater than 70
select first_name,last_name,birth_date from patients where height>160 and weight>70;
```
```
16. Write a query to find list of patients first_name, last_name, and allergies where allergies are not null and are from the city of 'Hamilton'
select first_name,last_name,allergies from patients where allergies is not null and city='Hamilton';
```
```
Show unique birth years from patients and order them by ascending.
select distinct year(birth_date)as Dby from patients order by Dby;
```
```
Show unique first names from the patients table which only occurs once in the list.

For example, if two or more people are named 'John' in the first_name column then don't include their name in the output list. If only 1 person is named 'Leo' then include them in the output.
select first_name   from patients group by first_name having count(*)=1;
select first_name from(select first_name,count(*) as occur from patients group by first_name)where occur=1;
```

