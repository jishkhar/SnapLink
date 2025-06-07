# URL Shortener

A simple and efficient URL shortening service built with Node.js, Express, and MongoDB. This application allows users to create shortened versions of long URLs and tracks click analytics.

## Features

- **URL Shortening**: Convert long URLs into short, manageable links
- **Click Tracking**: Monitor how many times each shortened URL has been accessed
- **Web Interface**: Clean web interface to create and view shortened URLs
- **Automatic Redirects**: Seamlessly redirect users from short URLs to original destinations
- **MongoDB Storage**: Persistent storage of URLs and analytics

## Technology Stack

- **Backend**: Node.js with Express.js
- **Database**: MongoDB with Mongoose ODM
- **View Engine**: EJS for server-side rendering
- **URL Generation**: ShortID for creating unique short codes

## Prerequisites

Before running this application, make sure you have the following installed:

- Node.js (v12 or higher)
- MongoDB (running locally or accessible remotely)
- npm (Node Package Manager)

## Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd url-shortener
   ```

2. **Install dependencies**
   ```bash
   npm install express mongoose ejs shortid
   ```

3. **Start MongoDB**
   Make sure MongoDB is running on your local machine:
   ```bash
   mongod
   ```

4. **Run the application**
   ```bash
   node server.js
   ```

5. **Access the application**
   Open your browser and navigate to `http://localhost:5000`

## Usage

### Creating Short URLs

1. Visit the home page at `http://localhost:5000`
2. Enter the full URL you want to shorten in the input field
3. Click submit to generate a shortened URL
4. The shortened URL will appear in the list below

### Accessing Short URLs

- Click on any shortened URL to be redirected to the original destination
- Each click is automatically tracked and the counter increments

### API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | Display home page with URL list |
| POST | `/shortUrls` | Create a new shortened URL |
| GET | `/:shortUrl` | Redirect to original URL and increment click counter |

## Database Schema

The application uses a MongoDB collection with the following schema:

```javascript
{
  full: String,     // Original full URL (required)
  short: String,    // Generated short code (required, auto-generated)
  clicks: Number    // Click counter (required, default: 0)
}
```

## File Structure

```
url-shortener/
├── models/
│   └── shortUrl.js     # Mongoose schema definition
├── views/
│   └── index.ejs       # Main page template (not included)
├── server.js           # Main application server
└── README.md           # This file
```

## Environment Variables

The application supports the following environment variables:

- `PORT`: Server port (default: 5000)
- `MONGODB_URI`: MongoDB connection string (default: mongodb://localhost/urlShortener)

## Development

To run the application in development mode:

```bash
# Install nodemon for auto-restart
npm install -g nodemon

# Run with nodemon
nodemon server.js
```

## Deployment

For production deployment:

1. Set the `PORT` environment variable
2. Configure MongoDB connection string
3. Use a process manager like PM2:
   ```bash
   npm install -g pm2
   pm2 start server.js --name "url-shortener"
   ```

## Future Enhancements

- User authentication and personal URL management
- Custom short URL aliases
- Expiration dates for URLs
- Advanced analytics and reporting
- Rate limiting and spam protection
- API key authentication for programmatic access

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Create a Pull Request

## License

This project is open source and available under the [MIT License](LICENSE).

## Support

If you encounter any issues or have questions, please create an issue in the repository or contact the maintainers.
