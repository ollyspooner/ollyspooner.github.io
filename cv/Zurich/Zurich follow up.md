# Zurich follow up

Hi Renita,
Thank you for the opportunity for a role within your team at Zurich. It was great to meet you, Benjamin and Daniel, and to learn a it more about how you approach Mendix and development at a different scale and sector to the one in which I have worked so far.

During the technical test I feel that I sent myself down a bit of a rabbit hole, which meant that I didn't manage to get a working application. I was not please with this outcome, so I tried it again and this time completed it in under 15 minutes (see test output from the Swagger page attached). In addition to the validation discussed, I also would add a uniqueness constraint to the ISBN attribute to prevent duplicate records being added.

```bash
// Get all books

curl -X 'GET' \
  'http://localhost:8080/rest/bookrepo/v1/book' \
  -H 'accept: application/json'

  [
  {
    "Title": "The Adventures of Huckleberry Finn",
    "Author": "Mark Twain",
    "Publisher": "Penguin Printing",
    "ISBN": "0984509784156",
    "DatePublished": "1970-03-08T00:00:00.000Z",
    "MSRP": 13.5
  }
]

// Add book

curl -X 'POST' \
  'http://localhost:8080/rest/bookrepo/v1/book' \
  -H 'accept: */*' \
  -H 'Content-Type: application/json' \
  -d '{
  "Title": "The Shining",
  "Author": "Stephen King",
  "Publisher": "Anchor",
  "ISBN": "0345806786",
  "DatePublished": "2013-08-27",
  "MSRP": 9.57
}'

// (no reponse body)

// Get book by ISBN

curl -X 'GET' \
  'http://localhost:8080/rest/bookrepo/v1/book/0345806786' \
  -H 'accept: application/json'

  {
  "Title": "The Shining",
  "Author": "Stephen King",
  "Publisher": "Anchor",
  "ISBN": "0345806786",
  "DatePublished": "2013-08-27T00:00:00.000Z",
  "MSRP": 9.57
}

// Get all books again

curl -X 'GET' \
  'http://localhost:8080/rest/bookrepo/v1/book' \
  -H 'accept: application/json'

[
  {
    "Title": "The Adventures of Huckleberry Finn",
    "Author": "Mark Twain",
    "Publisher": "Penguin Printing",
    "ISBN": "0984509784156",
    "DatePublished": "1970-03-08T00:00:00.000Z",
    "MSRP": 13.5
  },
  {
    "Title": "The Shining",
    "Author": "Stephen King",
    "Publisher": "Anchor",
    "ISBN": "0345806786",
    "DatePublished": "2013-08-27T00:00:00.000Z",
    "MSRP": 9.57
  }
]