---
layout: page
title: "Q130307: How to Use Null Values in Visual FoxPro"
permalink: /kb/130/Q130307/
---

## Q130307: How to Use Null Values in Visual FoxPro

{% raw %}

	Article: Q130307
	Product(s): Microsoft FoxPro
	Version(s): 3.0,5.0,6.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Microsoft Visual FoxPro version 3.0 supports null data values. Versions of
	FoxPro prior to version 3.0 did not directly support null data values. This
	article describes the general rules Visual FoxPro follows for handling null
	values (represented as .NULL.) when they passed to Visual FoxPro commands or
	functions.
	
	MORE INFORMATION
	================
	
	Use a null value (.NULL.) value when a value is missing, irrelevant, or unknown.
	In previous versions of FoxPro, values that were unknown or missing were usually
	represented by spaces or zeroes, which could have been misinterpreted. With
	Visual FoxPro, you can now store a null value in a field.
	
	It is important to note that a null value (.NULL.) in Visual FoxPro is not the
	same as an empty, blank, or zero value. Null represents the absence of a value,
	so null is never equal to, greater than, or less than another value, null or
	non-null. Visual FoxPro support for null values complies with the ANSI standards
	and affects any area of the product where values and expressions are used.
	
	General Rules for Null Values
	-----------------------------
	
	Here are the general rules for null values passed to Visual FoxPro commands or
	functions:
	
	- Commands generate an error when passed a null.
	
	- Functions that accept null values return .NULL. as a result.
	
	- Functions expecting a numeric value will generate an error if supplied with a
	  null.
	
	- ISBLANK(), ISDIGIT(), ISLOWER(), ISUPPER(), ISALPHA(), and EMPTY() each
	  return false (.F.) when passed a null value.
	
	- ISNULL() returns true (.T.) when passed a null value.
	
	- The commands INSERT SQL and SELECT SQL process null values through the IS
	  NULL and IS NOT NULL clauses.
	
	- SQL Aggregate functions, such as MAX(), MIN(), and SUM() ignore all null
	  values in the aggregate.
	
	- Visual FoxPro aggregate functions propagate .NULL. if all supplied values are
	  null values, otherwise, any null value is ignored.
	
	The remainder of this article gives more information and examples for these
	general rules.
	
	Commands Generate an Error When Passed a Null
	---------------------------------------------
	
	A Visual FoxPro command is a statement that results in an action. Examples of
	commands are USE, BROWSE, and DELETE. For example, the USE command returns an
	error for this code:
	
	     STORE .NULL. TO nWorkArea
	     USE mytable IN (nWorkArea)
	
	The IN clause of the USE command is expecting a numeric or alpha value, when
	passed a .NULL. the error "Table Number is Invalid." is generated.
	
	The NVL() function may be used to remove null values from calculations or
	operations where null values are not supported or are not relevant.
	
	     STORE .NULL. TO nWorkArea
	     USE mytable IN NVL(nWorkArea,0)
	
	This would open mytable in the first available workarea. Please see the Help file
	or Visual FoxPro documentation for more information about the NVL() function.
	
	Functions that Accept Null Values Return .NULL. as a Result
	-----------------------------------------------------------
	
	A Visual FoxPro function is a routine that performs a specific task and takes
	zero or more arguments. Examples of functions include ISBLANK(), UPPER(), and
	SUBSTR(). Most Visual FoxPro functions allow a null value to be passed as an
	argument without generating an error, however a .NULL. is returned from the
	function. In other words, when you pass a null value to a function, the result
	is always null. This is also how null values are treated in mathematical
	equations. For example a null value added to 500 equals null, and a null value
	multiplied by zero equals null (not zero).
	
	The following example code returns .NULL.:
	
	     cLastName = "Johnson"
	     nBegin = 5
	     nExtract = .NULL.
	     ?SUBSTR(cLastName,nBegin,nExtract)
	
	The exceptions to this rule are the ISBLANK(), ISDIGIT(), ISLOWER(), ISUPPER(),
	ISALPHA(), and EMPTY() functions - each of which return a .F. value. The
	ISNULL() function returns a .T. value.
	
	INSERT SQL and SELECT SQL Process Null Values by Using New Clauses
	------------------------------------------------------------------
	
	Two new clauses (IS NULL and IS NOT NULL) handle nulls in the INSERT and SELECT
	SQL commands. For example, to locate all records in a table where cLastName is
	not null, use this command:
	
	     SELECT cLastName FROM mytable WHERE cLastName IS NOT NULL
	
	To locate null values, use the IS NULL clause.
	
	SQL Aggregate Functions Ignore Null Values
	------------------------------------------
	
	An aggregate function is a function that performs a numeric operation such as
	addition, minimum, maximum, or average on a group (aggregate) of values.
	Examples of aggregate functions include MAX(), MIN(), and SUM().
	
	The SELECT SQL command, for example, can use aggregate functions to retrieve
	numeric values from tables. For example, the following SELECT command returns
	the maximum value from a field named nYTDSales:
	
	     SELECT MAX(nYTDSales) from mytable
	
	Any SQL aggregate function performed on a field that contains .NULL. values
	ignores the .NULL. values, returning a result that treat the null valuses as if
	they do not exist (are not part of the aggregate).
	
	For more information about the .NULL. value and the functions described above,
	search for topics in the Visual FoxPro Help file.
	
	Additional query words: VFoxWin
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP500 kbVFP600
	Version           : :3.0,5.0,6.0
	
	=============================================================================
	

{% endraw %}
