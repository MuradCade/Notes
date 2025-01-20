
	
	
	
	admin {
		INTEGER id
		VARCHAR(50) admin_name
		VARCHAR(50) admin_email
		VARCHAR(50) admin_phone
	}

	employee {
		INTEGER id
		VARCHAR(50) empname
		VARCHAR(50) emp_phone
		VARCHAR(50) empaddress
		VARCHAR(50) empcity
		VARCHAR(50) empemail
		DATE begin_work
		DATE leave_work
	}

	Login {
		INTEGER userid
		VARCHAR(50) username
		VARCHAR(50) useremail
		VARCHAR(50) userrole
		TEXT(65535) password
	}

	salary {
		INTEGER id
		VARCHAR(50) name
		VARCHAR(50) userid
		TEXT(65535) amount
		TEXT(65535) paymentstatus
		VARCHAR(255) method
		DATE date
	}

	district {
		INTEGER id
		TEXT(65535) dis_name
	}

	customer {
		INTEGER id
		TEXT(65535) customername
		TEXT(65535) customerphone
		TEXT(65535) dis_name
		DATE register_date
	}

	weekwork {
		INTEGER id
		VARCHAR(50) weekname
		VARCHAR(255) started_date
		TEXT(65535) work_area
		TEXT(65535) work_assigned_to
		ENUM workstatus
		TEXT(65535) vechile_name
		TEXT(65535) vichel_total
		DATE end_date
		TIME start_time
		TIME end_time
	}

	Complain {
		INTEGER id
		TEXT(65535) subject
		TEXT(65535) description
		TEXT(65535) customername
		TEXT(65535) customer_phone
		TEXT(65535) destrictname
		TEXT(65535) emp_name
		DATE complain_date
	}

	money_collection {
		INTEGER id
		TEXT(65535) customername
		TEXT(65535) districtname
		TEXT(65535) empname
		TEXT(65535) money_amount
		ENUM payment_method
		TEXT(65535) week_name
		DATE payment_date
		ENUM payment_status
	}