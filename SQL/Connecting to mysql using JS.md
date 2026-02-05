***

Run these mysql queries for access in database:
```sql
-- Create a user that JS can use
CREATE USER 'hacker22'@'localhost' IDENTIFIED BY 'iseeyou';

-- Give this user permission to use your coffee database
GRANT ALL PRIVILEGES ON nc_coffee.* TO 'hacker22'@'localhost';

-- Apply changes
FLUSH PRIVILEGES;
```

Code 

```js
const mysql = require("mysql2");
const connection = mysql.createConnection({
  host: "localhost",
  user: "hacker22",
  password: "iseeyou",
  database: "nc_coffee",
});

connection.connect((err) => {
  if (err) throw err;
  console.log("Connected to the database!");
});

connection.query("SELECT * FROM user", (err, results) => {
  if (err) throw err;
  console.table(results); // This prints your data in a nice table in the terminal
});

connection.end();
```