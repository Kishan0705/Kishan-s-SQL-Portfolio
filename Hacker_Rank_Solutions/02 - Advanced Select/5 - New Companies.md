## Q - Amber's conglomerate corporation just acquired some new companies.

- write a query to print the company_code, founder name, total number of lead managers, total number of senior managers, total number of managers, and total number of employees. Order your output by ascending company_code.

- Note:

- The tables may contain duplicate records.
- The company_code is string, so the sorting should not be numeric. For example, if the company_codes are C_1, C_2, and C_10, then the ascending company_codes will be C_1, C_10, and C_2.

  ```sql
  SELECT 
    c.company_code,
    c.founder,
    COUNT(DISTINCT l.lead_manager_code) AS lead_manager,
    COUNT(DISTINCT s.senior_manager_code) AS Senior_Manager,
    COUNT(DISTINCT m.manager_code) AS Manager,
    COUNT(DISTINCT e.employee_code) AS Employees
  FROM 
      Company c
  JOIN 
      Lead_Manager l ON c.company_code = l.company_code
  JOIN 
      Senior_Manager s ON s.company_code = c.company_code
  JOIN 
      Manager m ON m.company_code = c.company_code
  JOIN 
      Employee e ON e.company_code = c.company_code
  GROUP BY 
      c.company_code,
      c.founder
  ORDER BY 
      c.company_code ASC;
