# Wire-e-commerce structure.
wire-app/
│
├── backend/
│   ├── config/
│   │   └── db.js
│   ├── controllers/
│   │   ├── productController.js
│   │   └── userController.js
│   ├── models/
│   │   ├── Product.js
│   │   └── User.js
│   ├── routes/
│   │   ├── productRoutes.js
│   │   └── userRoutes.js
│   ├── middleware/
│   │   ├── authMiddleware.js
│   │   └── errorMiddleware.js
│   ├── utils/
│   │   └── generateToken.js
│   ├── tests/
│   │   └── sample.test.js
│   ├── server.js
│   └── .env
│
├── frontend/
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── assets/
│   │   ├── components/
│   │   │   └── Navbar.jsx
│   │   ├── pages/
│   │   │   ├── Home.jsx
│   │   │   └── Product.jsx
│   │   ├── services/
│   │   │   └── api.js
│   │   ├── context/
│   │   │   └── AuthContext.js
│   │   ├── utils/
│   │   │   └── formatPrice.js
│   │   ├── App.js
│   │   ├── index.js
│   │   └── styles/
│   │       └── main.css
│
├── docker/
│   ├── backend.Dockerfile
│   ├── frontend.Dockerfile
│   └── docker-compose.yml
│
├── docs/
│   └── explanation.md
│
├── .gitignore
├── README.md
├── package.json
└── Jenkinsfile

ecommerce-app/
│
├── backend/
│   ├── config/
│   │   └── db.js            # MongoDB connection setup
│   ├── controllers/
│   │   ├── productController.js  # CRUD logic for products
│   │   └── userController.js     # User auth and management
│   ├── models/
│   │   ├── Product.js       # Product schema
│   │   └── User.js          # User schema
│   ├── routes/
│   │   ├── productRoutes.js # Product API routes
│   │   └── userRoutes.js    # User API routes
│   ├── middleware/
│   │   ├── authMiddleware.js    # JWT auth middleware
│   │   └── errorMiddleware.js  # Error handling middleware
│   ├── utils/
│   │   └── generateToken.js    # JWT token generation
│   ├── tests/
│   │   └── sample.test.js
│   ├── server.js              # Express app setup
│   └── .env
│
├── frontend/
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── assets/
│   │   ├── components/
│   │   │   └── Navbar.jsx
│   │   ├── pages/
│   │   │   ├── Home.jsx        # Homepage component
│   │   │   └── Product.jsx     # Product detail page
│   │   ├── services/
│   │   │   └── api.js          # Axios instance
│   │   ├── context/
│   │   │   └── AuthContext.js  # Context for user state
│   │   ├── utils/
│   │   │   └── formatPrice.js
│   │   ├── App.js              # App routes
│   │   ├── index.js            # React entry point
│   │   └── styles/
│   │       └── main.css
│
├── docker/
│   ├── backend.Dockerfile
│   │   # Backend Dockerfile content
│   │   FROM node:18-alpine
│   │   WORKDIR /app
│   │   COPY backend/package*.json ./
│   │   RUN npm install
│   │   COPY backend/ .
│   │   EXPOSE 5000
│   │   CMD ["node", "server.js"]
│   ├── frontend.Dockerfile
│   │   # Frontend Dockerfile content
│   │   FROM node:18-alpine
│   │   WORKDIR /app
│   │   COPY frontend/package*.json ./
│   │   RUN npm install
│   │   COPY frontend/ .
│   │   EXPOSE 3000
│   │   CMD ["npm", "start"]
│   └── docker-compose.yml
│       # Docker Compose setup
│       version: '3.8'
│       services:
│         backend:
│           build:
│             context: .
│             dockerfile: docker/backend.Dockerfile
│           ports:
│             - "5000:5000"
│           volumes:
│             - ./backend:/app
│           environment:
│             - MONGO_URI=mongodb://mongo:27017/ecommerce
│           depends_on:
│             - mongo
│
│         frontend:
│           build:
│             context: .
│             dockerfile: docker/frontend.Dockerfile
│           ports:
│             - "3000:3000"
│           volumes:
│             - ./frontend:/app
│           stdin_open: true
│           tty: true
│
│         mongo:
│           image: mongo
│           restart: always
│           ports:
│             - "27017:27017"
│
├── docs/
│   └── explanation.md
│
├── .gitignore
├── README.md
├── package.json
└── Jenkinsfile
