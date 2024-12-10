# Waste Management Software

this project is waste management software that helps companies do their jobs.

### System users requirements(users of the system)

User one (shaqale)
-------------

1- lacag kasoo ururiyo
2- diwan geliyo macmiilka / update ku samee xogta
3- cabasho inuu so gudbiyo
4- update information kisa ku sameeyo / change password

User Two (manager/admin)
---------------

1- diwangeliyo macamisha / update and delete
2- diwan shaqalaha / change password
3- shaqada todobadka = shaqada bishan todobad walba la qabanayo salasa - 10 xashiish/shaqalaha
4- shaqoyinka hore = shaqoyinka hore loo qabto.
5- shaqada lacag ururinta : month
6- report / month , yearly 
7- amaahda  = ururka ama xafada dadka dagan amahaha meel lagu soo ban dhigo. 
8- cabashada 
9- information / change password. 
10- urur : ururka loo shaqeeynayo xafadaha ah wataan (inta xafadood ee loo shaqeeyay magacantoda iyo numberkoda iyo totalka guud ee xafada).###  

## Database Design

this project contains 10 tables , database is named wastemng

## Main Tables

1. Admin Table

2. Employee Table

3. Login Table

4. Employee_Salary Table

5. District(Xafadaha Magacantoda) Tabale

6. Customer_Registeration Table

7. WeekWork Table

8. Complain Table

9. Money Collection Table

10. Dept Table

### Each Table Schema Design

1- admin

- adminid
- adminname
- adminemail
- adminphone

2- employees

- empid
- empname
- empohone
- empaddress
- empcity
- empemail

3- login

- userid

- username

- useremail

- userrole

4- employee_salary

- id 

- date

- empname

- empid

- amount

- paymentstatus

5- district(xafado)

- id
- xafadaid
- xafada magaceda

6- customers_registeration

- customerid
- customername
- customerphone
- districtname
- date

7- weekwork

- id

- weekname

- date

- work

- workstatus (completed, pending)

8- complain

- id
- subject
- clientname
- complaindescription

9- moneycollection

- id
- customername
- districtname
- moneyamount
- paymentstatus
- deptid

10- dept

- id

- date

- deptamount

- customername

- customerid

- customerphone

- customerdistrictname 

- deptamount

# Features

- import and export in excel format

- report generation and ability to print it

- pagination on tables and ability to search by name or id

- language support (english / somali) ability to switch languages for particular user
