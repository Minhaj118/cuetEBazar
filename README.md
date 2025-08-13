# CUET Marketplace

A digital marketplace built with the MERN stack specifically for CUET students to buy and sell products within the campus community.

## Features

### For Buyers
- Browse all available products
- Filter products by category, price range, and search terms
- View detailed product information including seller contact
- Clean, responsive interface for easy browsing

### For Sellers
- Post products for sale with detailed descriptions
- Manage product listings (view, edit, delete)
- Update product status (available, pending, sold)
- Track all your listings in one dashboard

### General Features
- User authentication (register/login)
- Student ID verification for CUET community
- Responsive design for mobile and desktop
- Clean, modern interface

## Technologies Used

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - Database
- **Mongoose** - MongoDB object modeling
- **JWT** - Authentication
- **bcryptjs** - Password hashing

### Frontend
- **React.js** - UI library
- **React Router** - Navigation
- **Axios** - HTTP client
- **Context API** - State management

## Project Structure

```
cuet-marketplace/
├── server.js                 # Backend entry point
├── package.json             # Backend dependencies
├── models/                  # Database models
│   ├── User.js             # User model
│   └── Product.js          # Product model
├── routes/                  # API routes
│   ├── auth.js             # Authentication routes
│   └── products.js         # Product routes
├── middleware/              # Custom middleware
│   └── auth.js             # JWT authentication middleware
└── client/                  # React frontend
    ├── package.json        # Frontend dependencies
    ├── public/             # Static files
    ├── src/
    │   ├── App.js          # Main app component
    │   ├── App.css         # Global styles
    │   ├── context/        # React context
    │   │   └── AuthContext.js
    │   ├── components/     # Reusable components
    │   │   ├── Navbar.js
    │   │   ├── ProductCard.js
    │   │   └── PrivateRoute.js
    │   └── pages/          # Page components
    │       ├── Home.js
    │       ├── Login.js
    │       ├── Register.js
    │       ├── BuyerDashboard.js
    │       ├── SellerDashboard.js
    │       ├── AddProduct.js
    │       └── ProductDetails.js
```

## Installation & Setup

### Prerequisites
- Node.js (v14 or higher)
- MongoDB installed locally or MongoDB Atlas account
- Git

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/cuet-marketplace.git
cd cuet-marketplace
```

### 2. Backend Setup
```bash
# Install backend dependencies
npm install

# Create .env file
touch .env
```

Add the following to your `.env` file:
```
NODE_ENV=development
PORT=5000
MONGODB_URI=mongodb://localhost:27017/cuet-marketplace
JWT_SECRET=your-super-secret-jwt-key
```

### 3. Frontend Setup
```bash
# Navigate to client directory
cd client

# Install frontend dependencies
npm install
```

### 4. Run the Application

#### Development Mode (Backend and Frontend separately):
```bash
# Terminal 1 - Run backend
npm run server

# Terminal 2 - Run frontend
cd client
npm start
```

#### Or run both concurrently:
```bash
# Install concurrently globally (optional)
npm install -g concurrently

# Run both backend and frontend
npm run dev
```

## API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user

### Products
- `GET /api/products` - Get all products with filters
- `GET /api/products/:id` - Get product by ID
- `POST /api/products` - Create new product (protected)
- `GET /api/products/seller/my-products` - Get seller's products (protected)
- `PUT /api/products/:id` - Update product (protected)
- `DELETE /api/products/:id` - Delete product (protected)

## Database Models

### User Model
```javascript
{
  name: String,
  email: String (unique),
  password: String (hashed),
  studentId: String (unique),
  phone: String,
  userType: String (buyer/seller/both),
  createdAt: Date
}
```

### Product Model
```javascript
{
  title: String,
  description: String,
  price: Number,
  category: String,
  condition: String,
  images: [String],
  seller: ObjectId (ref: User),
  status: String (available/sold/pending),
  createdAt: Date
}
```

## Key Features Implementation

### Authentication Flow
1. User registers with CUET student ID verification
2. Password is hashed using bcryptjs
3. JWT token generated for authentication
4. Protected routes require valid JWT token

### Product Management
1. Sellers can create, read, update, delete their products
2. Buyers can view all available products with filtering
3. Products are categorized and searchable
4. Status tracking (available, pending, sold)

### Security Features
- Password hashing with bcryptjs
- JWT token authentication
- Protected API routes
- CORS configuration
- Input validation

## Deployment

### Environment Variables for Production
```
NODE_ENV=production
PORT=5000
MONGODB_URI=your-mongodb-atlas-connection-string
JWT_SECRET=your-super-secret-jwt-key
```

### Build for Production
```bash
# Build the React frontend
cd client
npm run build

# The build files will be served by Express in production
```

## Future Enhancements

- [ ] Image upload functionality with Cloudinary
- [ ] Real-time chat between buyers and sellers
- [ ] Email notifications for product interactions
- [ ] Advanced search and filtering options
- [ ] User ratings and reviews system
- [ ] Product wishlist functionality
- [ ] Admin panel for managing users and products
- [ ] Mobile app using React Native

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

If you encounter any issues or have questions, please:
1. Check the existing [Issues](https://github.com/yourusername/cuet-marketplace/issues)
2. Create a new issue if your problem isn't already reported
3. Contact the development team

## Acknowledgments

- CUET community for inspiration
- MERN stack documentation and tutorials
- Open source libraries used in this project
