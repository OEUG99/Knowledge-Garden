- The pg library uses the Pool class to manage connections to the PostgreSQL database.
	- ```js
	  const { Pool } = require('pg');
	  
	  const pool = new Pool({
	    user: 'myuser',
	    host: 'localhost',
	    database: 'mydatabase',
	    password: 'mypassword',
	    port: 5432,
	  });
	  ```
- You can run queries using the `pool.query` method.
	- ```js
	  
	  pool.query('SELECT * FROM users', (err, res) => {
	    if (err) {
	      console.error('Error executing query', err.stack);
	    } else {
	      console.log('Query result:', res.rows);
	    }
	  });
	  ```
- Parameterized queries help prevent SQL injection by using placeholders for values.
	- ```js
	  const text = 'INSERT INTO users(name, email) VALUES($1, $2) RETURNING *';
	  const values = ['John Doe', 'john.doe@example.com'];
	  
	  pool.query(text, values, (err, res) => {
	    if (err) {
	      console.error('Error executing query', err.stack);
	    } else {
	      console.log('Inserted row:', res.rows[0]);
	    }
	  });
	  ```
- Using async/await for better readability and asynchronous control flow.
	- ```js
	  const insertUser = async (name, email) => {
	    const text = 'INSERT INTO users(name, email) VALUES($1, $2) RETURNING *';
	    const values = [name, email];
	  
	    try {
	      const res = await pool.query(text, values);
	      console.log('Inserted row:', res.rows[0]);
	    } catch (err) {
	      console.error('Error executing query', err.stack);
	    }
	  };
	  ```
	-