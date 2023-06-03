WITH RECURSIVE employee_chain AS (
  SELECT
    ID,
    FIRSTNAME,
    LASTNAME,
    FIRSTNAME || ' ' || LASTNAME AS chain
  FROM ANALYTICS.EMPLOYEE 
  WHERE manager_id IS NULL
  UNION ALL
  SELECT
     m.id,
    m.FIRSTNAME,
    m.LASTNAME,
    chain || '->' || m.LASTNAME || ' ' || m.LASTNAME
  FROM employee_chain
  JOIN ANALYTICS.EMPLOYEE m
    ON m.manager_id = employee_chain.id
)
 
SELECT
  FirstName,
  LastName,
  chain
FROM employee_chain;
