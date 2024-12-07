# .env Files

## Installation of Python Dotenv Module

Install the Python Dotenv library by running the following command in your terminal or integrated terminal within your Python IDE.

pip install python-dotenv
### .env file

```
SECRET_KEY=mysecretkey  
DATABASE_URL=postgres://user:password@localhost/db  
API_KEY=your-api-key  
DEBUG=True
```
### File Structure

![ok](https://media.geeksforgeeks.org/wp-content/uploads/20240313112706/ok.png)

## Accessing Keys

```python
# Import the necessary module
from dotenv import load_dotenv
import os

# Load environment variables from the .env file (if present)
load_dotenv()

# Access environment variables as if they came from the actual environment
SECRET_KEY = os.getenv('SECRET_KEY')
```
