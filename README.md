# MoviesDatabase API Documentation

## API Overview
The MoviesDatabase API is a comprehensive RESTful service that provides access to extensive movie data including titles, release information, cast details, ratings, and images. It enables developers to retrieve movie listings, search for specific films, filter by various criteria like year and genre, and access detailed metadata about movies through structured endpoints.

## Version
The current API version is 2.

## Available Endpoints

- **GET /titles** - Retrieve paginated list of movie titles with filtering options
- **GET /titles/{id}** - Get detailed information about a specific movie by ID
- **GET /titles/search/title/{title}** - Search for movies by title with exact or fuzzy matching
- **GET /titles/random** - Fetch random movie titles from the database
- **GET /titles/{id}/ratings** - Retrieve ratings information for a specific movie
- **GET /titles/{id}/actors** - Get cast and actor information for a specific movie

## Request and Response Format
{
  "page": 1,
  "next": "string",
  "entries": 10,
  "results": [
    {
      "id": "tt1234567",
      "primaryImage": {
        "url": "https://example.com/image.jpg",
        "caption": {
          "plainText": "Movie poster description"
        }
      },
      "titleText": {
        "text": "Movie Title"
      },
      "releaseYear": {
        "year": 2023
      },
      "releaseDate": {
        "day": 15,
        "month": 5,
        "year": 2023
      }
    }
  ]
}


### Request Format:
http
GET /titles?year=2023&genre=Action&limit=10&page=1
Headers:
  X-RapidAPI-Key: your-api-key-here
  X-RapidAPI-Host: moviesdatabase.p.rapidapi.com

Authentication
Authentication is handled through RapidAPI platform. All requests require:

X-RapidAPI-Key header containing your unique API key

X-RapidAPI-Host header set to moviesdatabase.p.rapidapi.com

API keys are obtained by registering on RapidAPI and subscribing to the MoviesDatabase API service.

Error Handling
Common HTTP Status Codes:
200 - Successful request

400 - Bad Request (invalid parameters or malformed request)

401 - Unauthorized (missing or invalid API key)

404 - Not Found (requested resource does not exist)

429 - Too Many Requests (rate limit exceeded)

500 - Internal Server Error (server-side issue)

Error Response Example:
json
{
  "message": "Invalid API key",
  "statusCode": 401
}
Usage Limits and Best Practices
Rate Limiting:
Free tier: 500 requests per month

Basic tier: 10,000 requests per month

Pro tier: 100,000 requests per month

Best Practices:
Implement proper error handling and user feedback for API failures

Use pagination parameters (limit and page) to manage large datasets

Cache responses when possible to reduce API calls

Validate all parameters before making requests

Monitor API usage to avoid exceeding rate limits

Use specific endpoints instead of filtering large result sets

Implement retry logic for transient failures with exponential backoff
