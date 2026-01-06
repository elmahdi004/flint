# Environment Variables Required for Flint Commerce

Create a `.env` file in the `server` folder with the following variables:

## 🔴 REQUIRED Variables (Must Have)

### 1. Database Configuration
```env
MONGO_URL=your_mongodb_connection_string
```
- **Description**: MongoDB connection string (MongoDB Atlas or local MongoDB)
- **Example**: `mongodb+srv://username:password@cluster.mongodb.net/dbname?retryWrites=true&w=majority`

### 2. JWT Authentication
```env
JWT_SECRET_KEY=your_jwt_secret_key_here
```
- **Description**: Secret key for signing JWT tokens
- **Example**: Generate a random string: `openssl rand -base64 32`

### 3. Password Hashing
```env
HASH_SALT=10
```
- **Description**: Number of salt rounds for bcrypt password hashing
- **Recommended**: `10` (default value)

### 4. Cloudinary Configuration (Required for Image Uploads)
```env
CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret
```
- **Description**: Cloudinary credentials for image uploads
- **How to get**: 
  1. Go to https://cloudinary.com/
  2. Sign up or log in
  3. Go to Dashboard
  4. Copy your Cloud Name, API Key, and API Secret

## 🟡 OPTIONAL Variables (Recommended)

### 5. Server Port
```env
PORT=5000
```
- **Description**: Port number for the server
- **Default**: `5000` (if not set)

### 6. Email Configuration (For Order Notifications)
```env
EMAIL_USER=your_email@gmail.com
EMAIL_PASS=your_email_app_password
STORE_OWNER_EMAIL=store_owner@example.com
```
- **Description**: Email configuration for sending order notifications
- **Note**: For Gmail, you need to use an "App Password" instead of your regular password
- **How to get Gmail App Password**:
  1. Go to Google Account settings
  2. Security → 2-Step Verification → App passwords
  3. Generate a new app password for "Mail"

---

## 📝 Complete .env File Template

Copy this template and fill in your values:

```env
# ============================================
# REQUIRED VARIABLES
# ============================================

# Database
MONGO_URL=mongodb+srv://username:password@cluster.mongodb.net/dbname?retryWrites=true&w=majority

# JWT Secret (Generate a secure random string)
JWT_SECRET_KEY=your_super_secret_jwt_key_here_change_this

# Password Hashing
HASH_SALT=10

# Cloudinary (Required for product image uploads)
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# ============================================
# OPTIONAL VARIABLES
# ============================================

# Server Port (defaults to 5000 if not set)
PORT=5000

# Email Configuration (Optional - for order notifications)
EMAIL_USER=your_email@gmail.com
EMAIL_PASS=your_app_password
STORE_OWNER_EMAIL=store_owner@example.com
```

---

## ⚠️ Important Notes

1. **Never commit your `.env` file to Git** - It contains sensitive information
2. Make sure `.env` is in your `.gitignore` file
3. The `.env` file should be in the `server` folder (same level as `index.js`)
4. Restart your server after creating/updating the `.env` file

---

## 🔍 Quick Check

After creating your `.env` file, verify it's being loaded:
- The server should connect to MongoDB without errors
- Cloudinary should show "✅ Cloudinary configured successfully" message
- If you see warnings about missing variables, check your `.env` file spelling

