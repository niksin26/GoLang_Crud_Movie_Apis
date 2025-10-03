# GoLang CRUD Movie APIs

A simple RESTful API built with Go (Golang) for managing a movie collection. This project demonstrates basic CRUD (Create, Read, Update, Delete) operations using the Gorilla Mux router.

## 🚀 Features

- **GET** all movies
- **GET** a single movie by ID
- **POST** a new movie
- **PUT** (update) an existing movie
- **DELETE** a movie

## 📋 Prerequisites

- Go 1.25.1 or higher
- Git

## 🛠️ Installation

1. Clone the repository:
```bash
git clone git@github.com-personal:niksin26/GoLang_Crud_Movie_Apis.git
cd GoLang_Crud_Movie_Apis
```

2. Install dependencies:
```bash
go mod download
```

3. Run the application:
```bash
go run main.go
```

The server will start on port 8000 with the message:
```
Starting server at port 8000
```

## 📁 Project Structure

```
GoLang_Crud_Movie_Apis/
├── main.go       # Main application file with all API handlers
├── go.mod        # Go module file
├── go.sum        # Go module checksums
└── README.md     # Project documentation
```

## 🔗 API Endpoints

### Base URL
```
http://localhost:8000
```

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/movies` | Get all movies |
| GET | `/movies/{id}` | Get a specific movie by ID |
| POST | `/movies` | Create a new movie |
| PUT | `/movies/{id}` | Update an existing movie |
| DELETE | `/movies/{id}` | Delete a movie |

## 📝 API Documentation

### 1. Get All Movies
**Endpoint:** `GET /movies`

**Response:**
```json
[
  {
    "id": "1",
    "isbn": "123456",
    "title": "Movie One",
    "director": {
      "firstname": "John",
      "lastname": "Doe"
    }
  },
  {
    "id": "2",
    "isbn": "123457",
    "title": "Movie Two",
    "director": {
      "firstname": "Nikhil",
      "lastname": "Kumar"
    }
  }
]
```

**Screenshot:**
![Get All Movies](images/get-all-movies.png)

### 2. Get Movie by ID
**Endpoint:** `GET /movies/{id}`

**Example:** `GET /movies/1`

**Response:**
```json
{
  "id": "1",
  "isbn": "123456",
  "title": "Movie One",
  "director": {
    "firstname": "John",
    "lastname": "Doe"
  }
}
```

### 3. Create a New Movie
**Endpoint:** `POST /movies`

**Request Body:**
```json
{
  "isbn": "123458",
  "title": "New Movie",
  "director": {
    "firstname": "Jane",
    "lastname": "Smith"
  }
}
```

**Response:**
```json
{
  "id": "random_generated_id",
  "isbn": "123458",
  "title": "New Movie",
  "director": {
    "firstname": "Jane",
    "lastname": "Smith"
  }
}
```

### 4. Update a Movie
**Endpoint:** `PUT /movies/{id}`

**Example:** `PUT /movies/1`

**Request Body:**
```json
{
  "isbn": "123456",
  "title": "Updated Movie Title",
  "director": {
    "firstname": "John",
    "lastname": "Updated"
  }
}
```

**Response:** Returns the updated movie object

### 5. Delete a Movie
**Endpoint:** `DELETE /movies/{id}`

**Example:** `DELETE /movies/1`

**Response:** Returns the remaining movies list

## 💻 Testing with cURL

### Get all movies
```bash
curl http://localhost:8000/movies
```

### Get a specific movie
```bash
curl http://localhost:8000/movies/1
```

### Create a new movie
```bash
curl -X POST http://localhost:8000/movies \
  -H "Content-Type: application/json" \
  -d '{
    "isbn": "123458",
    "title": "Inception",
    "director": {
      "firstname": "Christopher",
      "lastname": "Nolan"
    }
  }'
```

### Update a movie
```bash
curl -X PUT http://localhost:8000/movies/1 \
  -H "Content-Type: application/json" \
  -d '{
    "isbn": "123456",
    "title": "The Matrix",
    "director": {
      "firstname": "Lana",
      "lastname": "Wachowski"
    }
  }'
```

### Delete a movie
```bash
curl -X DELETE http://localhost:8000/movies/1
```

## 🗃️ Data Models

### Movie Structure
```go
type Movie struct {
    ID       string    `json:"id"`
    Isbn     string    `json:"isbn"`
    Title    string    `json:"title"`
    Director *Director `json:"director"`
}
```

### Director Structure
```go
type Director struct {
    FirstName string `json:"firstname"`
    LastName  string `json:"lastname"`
}
```

## ⚠️ Important Notes

- This is a simple demonstration API that stores data in memory
- Data is not persisted and will be lost when the server restarts
- The API initializes with 2 sample movies on startup
- Movie IDs are randomly generated for new movies

## 🔧 Dependencies

- [Gorilla Mux](https://github.com/gorilla/mux) v1.8.1 - HTTP router and URL matcher

## 📄 License

This project is open source and available for educational purposes.

## 👤 Author

Nikhil Kumar Singh

## 🤝 Contributing

Feel free to fork this project and submit pull requests with improvements.

## 📞 Support

For any questions or issues, please create an issue in the GitHub repository.
