# Analysing-the-health-services-by-a-hospital-using-SQL
/* Display the records where the employee has resigned */
  SELECT emp_id, CONCAT(fname,' ',lname) AS name, date_of_resign
  FROM hospital_analysis.employee
  WHERE NULLIF(date_of_resign,' ') IS NOT NULL;
  
/* Find the number of males and females in each employee type category */
   SELECT emp_type, sex, count(emp_id)
   FROM hospital_analysis.employee
   GROUP BY emp_type,sex;
   
/* List the top 5 treatments with the highest fee amount */
   SELECT treatment_name, fees
   FROM hospital_analysis.treatments
   ORDER BY fees DESC
   LIMIT 5;
   
/* List the dept_name and the fees spent in that dept */
   SELECT d.dept_name, t.fees
   FROM hospital_analysis.department AS d
   INNER JOIN hospital_analysis.treaments AS t
   ON d.dep_id = t.dep_no
   GROUP BY dept_id ASC;
   
/* List the top 3 departments in terms of fees spent*/
   SELECT dept_name, SUM(t.fees) AS total_fees
   FROM hospital_analysis.department AS d
   JOIN hospital_analysis.treatments AS t 
   ON d.dept_id = t.dept_no
   GROUP BY d.dept_name
   ORDER BY t.fees DESC 
   LIMIT 3;
