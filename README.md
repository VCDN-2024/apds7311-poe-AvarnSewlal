# **International Payments Portal (Employee & Customer Portal)**

## **Overview**

This application is a secure **International Payments Portal** designed for employees and customers. The system allows employees to perform international payments, while customers can securely make payments through their respective portals.

The application includes several key security measures such as **password hashing**, **input validation**, and **SSL encryption** to ensure secure and robust functionality. The application is also integrated with **CircleCI** and **SonarQube** for continuous integration and code quality monitoring.

## **Key Features**

- **No Registration Process**: Users (both customers and employees) are pre-created and no registration process is allowed.
- **Password Security**: Passwords are hashed and salted using **bcrypt** for secure storage.
- **Whitelist Input Validation**: User inputs (e.g., full name, ID number, account number) are validated with **RegEx patterns** to prevent invalid or malicious data.
- **SSL Encryption**: All traffic is served over HTTPS to protect sensitive data.
- **Security Protections**: Protection against common attacks like XSS, CSRF, and SQL Injection.
- **CI/CD Pipeline**: Continuous integration and deployment via **CircleCI** and automated code quality checks using **SonarQube**.

## **Pre-registered Users and Employees**

### **Pre-registered Users:**

1. **Name**: John Doe  
   **ID Number**: 1234567890  
   **Account Number**: 1234  
   **Password**: password123 (hashed)

2. **Name**: Alice Johnson  
   **ID Number**: 2345678901  
   **Account Number**: 5678  
   **Password**: alicePassword (hashed)

3. **Name**: Bob Smith  
   **ID Number**: 3456789012  
   **Account Number**: 9012  
   **Password**: bobPassword (hashed)

### **Pre-registered Employees:**

1. **Name**: Jane Smith  
   **ID Number**: 9876543210  
   **Account Number**: 5678  
   **Password**: employeePass (hashed)

2. **Name**: Michael Brown  
   **ID Number**: 8765432109  
   **Account Number**: 1357  
   **Password**: michaelPass (hashed)

3. **Name**: Sara Lee  
   **ID Number**: 7654321098  
   **Account Number**: 2468  
   **Password**: saraPass (hashed)

---

## **Technologies Used**

- **Frontend**: React.js (`my-app`)
- **Backend**: Node.js with Express.js
- **Security**: bcrypt (password hashing), SSL, RegEx input validation
- **CI/CD**: CircleCI, SonarQube
- **Version Control**: Git, GitHub

## **Project Structure**

```bash
/
├── /backend
│   ├── /controllers        # Controllers for handling login and payment
│   ├── /middleware         # Security middleware
│   ├── /models             # Models (static users)
│   ├── /routes             # API routes (login, payment)
│   ├── server.js           # Entry point for the backend
│   ├── .env                # Environment variables
│   └── package.json        # Backend dependencies
│
├── /my-app                 # Frontend (React)
│   ├── /src
│   │   ├── /components     # React components (LoginForm, PaymentForm, etc.)
│   │   ├── /styles         # CSS/SCSS files for styling
│   │   ├── App.js          # Main React component
│   │   └── index.js        # React entry point
│   ├── package.json        # Frontend dependencies
│   └── README.md           # Frontend documentation
│
├── .gitignore              # Git ignore file
└── README.md               # Project documentation
```

## **Security Features**

### 1. **Password Hashing and Salting**

Password security is ensured by hashing and salting using **bcrypt**. This prevents the retrieval of original passwords in case of a data breach.

### 2. **Input Validation with RegEx**

All user inputs (like full name, ID number, account number) are validated using **RegEx** to ensure only valid data is accepted, preventing malicious or malformed inputs.

### 3. **SSL Encryption**

The backend serves all traffic over **HTTPS** to secure communication between the frontend and the backend.

### 4. **Protection Against Attacks**

- **Cross-Site Scripting (XSS)**: User inputs are sanitized to prevent malicious scripts.
- **Cross-Site Request Forgery (CSRF)**: Tokens are used to prevent unauthorized actions.
- **SQL Injection**: All inputs are validated and sanitized to prevent harmful SQL queries.

### 5. **CI/CD Pipeline (CircleCI and SonarQube)**

- **CircleCI**: Automates the build, test, and deployment process.
- **SonarQube**: Analyzes the code for hotspots and code smells to maintain high-quality code.

## **Installation and Setup**

### 1. **Clone the Repository**

Clone the repository to your local machine:

```bash
git clone https://github.com/yourusername/international-payments-portal.git
cd international-payments-portal
```

### 2. **Install Backend Dependencies**

Navigate to the `backend` directory and install the necessary dependencies:

```bash
cd backend
npm install
```

### 3. **Install Frontend Dependencies**

Navigate to the `my-app` directory and install the necessary dependencies:

```bash
cd ../my-app
npm install
```

### 4. **Set Up Environment Variables**

Create a `.env` file in the **backend** directory to store environment variables, such as JWT secret and port:

```plaintext
JWT_SECRET=your-secret-key
PORT=5000
```

### 5. **Running the Application**

To run the backend and frontend simultaneously:

#### **Start the Backend**

Navigate to the **backend** folder and start the backend server:

```bash
cd backend
npm start
```

This will start the backend server on `http://localhost:5000`. Ensure SSL (HTTPS) is configured in your backend.

#### **Start the Frontend (my-app)**

Navigate to the **my-app** folder and start the frontend React application:

```bash
cd ../my-app
npm start
```

This will start the React development server on `http://localhost:3000`.

### 6. **Production Build**

To prepare the frontend for production, build the React app and deploy it:

#### **Build Frontend**

```bash
cd my-app
npm run build
```

This will create a production-ready build in the `my-app/build` folder.

#### **Deploy Backend**

Make sure your backend is configured to serve the built React app and handle SSL encryption for production.

## **What the Application Does**

### **Login Process**

- Employees and customers log in with a **full name**, **ID number**, **account number**, and **password**.
- Employees gain additional privileges to access the payment management system, while customers can make international payments.

### **Payment Process (For Employees)**

After logging in, employees can access the payment management system to perform secure international transactions.

### **Input Validation**

All inputs (such as full name, ID number, etc.) are validated using **RegEx** to ensure the data conforms to the expected format. Invalid inputs are rejected, and error messages are shown.

### **CircleCI and SonarQube Integration**

- **CircleCI** automates the build, test, and deployment process, ensuring fast feedback on every code change.
- **SonarQube** analyzes the code for quality issues such as bugs, vulnerabilities, and code smells.

## SSL Configuration

In order for the SSL to work correctly in your application, you need to ensure that the paths to the SSL certificate (`server.crt`) and key (`server.key`) are correctly specified in your server configuration.

### Step 1: Locate the SSL Certificate and Key

Make sure you have the following files in your project:

- **SSL Certificate**: `server.crt`
- **SSL Key**: `server.key`

### Step 2: Update the SSL Path in Configuration

In your backend configuration, you will need to update the paths to reflect where your certificate files are stored.

For example, in your server configuration file (typically `server.js` or similar), you should find code similar to this:

```javascript
const fs = require('fs');
const path = require('path');

// Update these paths to match the location of your server.crt and server.key
const sslCertPath = path.join(__dirname, 'src', 'backend', 'ssl', 'server.crt');
const sslKeyPath = path.join(__dirname, 'src', 'backend', 'ssl', 'server.key');

// Use the updated paths in your SSL configuration
https.createServer({
  key: fs.readFileSync(sslKeyPath),
  cert: fs.readFileSync(sslCertPath)
}, app).listen(443);
```

### Step 3: Update the File Paths

If you have placed the SSL certificate files elsewhere, make sure to update the `sslCertPath` and `sslKeyPath` with the correct paths to your `server.crt` and `server.key` files.

For example, if your certificate files are in the following directory:

- **SSL Certificate**: `C:/Users/Avarn/Downloads/APDS Part 3/APDS Part 3/APDS Part 2/my-app/src/backend/ssl/server.crt`
- **SSL Key**: `C:/Users/Avarn/Downloads/APDS Part 3/APDS Part 3/APDS Part 2/my-app/src/backend/ssl/server.key`

Update the paths in your configuration like this:

```javascript
const sslCertPath = 'C:/Users/Avarn/Downloads/APDS Part 3/APDS Part 3/APDS Part 2/my-app/src/backend/ssl/server.crt';
const sslKeyPath = 'C:/Users/Avarn/Downloads/APDS Part 3/APDS Part 3/APDS Part 2/my-app/src/backend/ssl/server.key';
```

### Step 4: Restart the Server

After updating the paths, restart your server to apply the changes.

## **Contributing**

If you'd like to contribute to this project:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-name`).
3. Commit your changes (`git commit -am 'Add new feature'`).
4. Push to the branch (`git push origin feature-name`).
5. Create a pull request.

## **License**

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

### **Conclusion**
