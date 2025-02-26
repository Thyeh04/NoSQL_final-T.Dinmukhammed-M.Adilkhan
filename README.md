# 🌦️ Weather App

## 📌 Project Overview
Weather App is a web-based application that provides real-time weather updates for any city. Users can register, log in, and retrieve weather data while the app securely stores historical weather information in MongoDB.

## ✨ Features
- 🔑 **User Authentication**: Secure login and registration with JWT.
- 🌍 **Real-time Weather Data**: Fetches current weather using OpenWeather API.
- 🗄️ **Data Storage**: Saves weather information in MongoDB for historical tracking.
- 📊 **Statistics & History**: Provides weather analytics and historical trends.
- 🔒 **Security**: Authentication middleware protects API endpoints.

## 🛠️ Setup Instructions

### 📋 Prerequisites
Ensure you have the following installed:
- [Node.js](https://nodejs.org/) (Latest LTS version recommended)
- npm (comes with Node.js) or yarn
- MongoDB (local or cloud-based, e.g., MongoDB Atlas)

### 🚀 Installation
1. **Clone the repository**:
   ```sh
   git clone https://github.com/your-username/weather-app.git
   cd weather-app
   ```
2. **Install dependencies**:
   ```sh
   npm install
   ```
3. **Set up environment variables**:
   Create a `.env` file in the root directory and add:
   ```sh
   MONGO_URI=your_mongodb_connection_string
   JWT_SECRET=your_secret_key
   OPENWEATHER_API_KEY=your_api_key
   PORT=10000
   ```
4. **Start the server**:
   ```sh
   npm start
   ```
5. The server will run on `http://localhost:10000`

## 📡 API Documentation
### 🌐 Base URL
```
http://localhost:5000/api
```

### 🔑 Authentication Endpoints
#### ➤ Register User
```http
POST /auth/register
```
**Request Body:**
```json
{
  "username": "testuser",
  "password": "password123"
}
```
**Response:**
```json
{
  "message": "✅ User registered successfully"
}
```

#### ➤ Login User
```http
POST /auth/login
```
**Request Body:**
```json
{
  "username": "testuser",
  "password": "password123"
}
```
**Response:**
```json
{
  "token": "your_jwt_token"
}
```

### ☁️ Weather Endpoints
#### ➤ Get Current Weather
```http
GET /weather?city={city_name}
```
**Headers:**
```json
{
  "Authorization": "Bearer your_jwt_token"
}
```
**Response:**
```json
{
  "message": "✅ Данные успешно обновлены",
  "data": {
    "city": "New York",
    "temperature": 15.0,
    "humidity": 65,
    "wind_speed": 3.5
  }
}
```

#### ➤ Get Weather Metrics
```http
GET /weather/metrics?city={city_name}&field={temperature/humidity/wind_speed}
```
**Response:**
```json
{
  "avg": 14.5,
  "min": 10.0,
  "max": 18.0,
  "stdDev": 3.2
}
```

#### ➤ Get Weather History
```http
GET /weather/history?city={city_name}&field={temperature/humidity/wind_speed}
```
**Response:**
```json
[
  { "timestamp": "2024-02-25T12:00:00Z", "temperature": 14.0 },
  { "timestamp": "2024-02-24T12:00:00Z", "temperature": 13.5 }
]
```

## 👥 Contribution
Contributions are welcome! Feel free to fork this repository and submit pull requests with improvements.

## 📜 License
This project is licensed under the MIT License.

