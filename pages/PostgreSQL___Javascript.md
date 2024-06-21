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
- Transactions ensure a series of database operations either all succeed or all fail.
	- ```js
	  const performTransaction = async () => {
	    const client = await pool.connect();
	    try {
	      await client.query('BEGIN');
	      const res1 = await client.query('INSERT INTO users(name, email) VALUES($1, $2) RETURNING *', ['John Doe', 'john.doe@example.com']);
	      const res2 = await client.query('INSERT INTO users(name, email) VALUES($1, $2) RETURNING *', ['Jane Doe', 'jane.doe@example.com']);
	      await client.query('COMMIT');
	      console.log('Transaction successful:', res1.rows[0], res2.rows[0]);
	    } catch (err) {
	      await client.query('ROLLBACK');
	      console.error('Transaction error:', err.stack);
	    } finally {
	      client.release();
	    }
	  };
	  ```
	-