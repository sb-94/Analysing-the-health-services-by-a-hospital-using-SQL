# Analysing-the-health-services-by-a-hospital-using-SQL
/* Display the records where the employee has resigned */
  SELECT emp_id, CONCAT(fname,' ',lname) AS name, date_of_resign
  FROM hospital_analysis.employee
  WHERE NULLIF(date_of_resign,' ') IS NOT NULL;
  ![Screenshot (41)](https://user-images.githubusercontent.com/117995417/210268479-23891331-01b6-4e9d-91ca-db8ac427d56c.png)
 
  
/* Find the number of males and females in each employee type category */
   SELECT emp_type, sex, count(emp_id)
   FROM hospital_analysis.employee
   GROUP BY emp_type,sex;
   ![Screenshot (42)](https://user-images.githubusercontent.com/117995417/210268636-c43e887c-b55e-48c7-9242-7ef5dbe180e5.png)

   
/* List the top 5 treatments with the highest fee amount */
   SELECT treatment_name, fees
   FROM hospital_analysis.treatments
   ORDER BY fees DESC
   LIMIT 5;
   ![Screenshot (43)](https://user-images.githubusercontent.com/117995417/210268745-dfe2fa63-469d-430e-a92b-93ad84dad960.png)

   
/* List the dept_name and the fees spent in that dept */
   SELECT d.dep_name, t.fees
   FROM hospital_analysis.department d
   JOIN hospital_analysis.treatments t
   ON d.dep_no = t.dep_no;
   ![Screenshot (46)](https://user-images.githubusercontent.com/117995417/210268818-94ea5972-81cf-4d5f-8289-5ded63153df6.png)

   
/* List the top 3 departments in terms of fees spent*/
   SELECT dep_name, SUM(t.fees) AS total_fees
   FROM hospital_analysis.department AS d
   JOIN hospital_analysis.treatments AS t 
   ON d.dep_no = t.dep_no
   GROUP BY d.dep_name
   ORDER BY t.fees DESC 
   LIMIT 3;
   ![Screenshot (47)](https://user-images.githubusercontent.com/117995417/210268870-5a3904a7-4c96-488a-afbf-4f28f3fe78ef.png)

