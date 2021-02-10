# Express REST Guest List API (in-memory)

A simple, naïve, in-memory RESTful guest list API in Express.

## Installation

```terminal
git clone https://github.com/Thoud/express-guest-list-api
cd express-guest-list-api
yarn
yarn start
```

## Usage

### Base URL

```js
const baseUrl = 'http://localhost:5000';
```

### Getting event details (aka GET /event)

```js
const response = await fetch(`${baseUrl}/event`);
const eventDetails = await response.json();
```

### Updating event details (aka PATCH /modEvent)

```js
const response = await fetch(`${baseUrl}/modEvent`, {
  method: 'PATCH',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({ date: '01.01.2021' }),
});
const updatedEventDetails = await response.json();
```

### Getting all guests (aka GET /)

```js
const response = await fetch(`${baseUrl}/`);
const allGuests = await response.json();
```

### Creating a new guest (aka POST /)

```js
const response = await fetch(`${baseUrl}/`, {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({ firstName: 'John', lastName: 'Doe' }),
});
const createdGuest = await response.json();
```

### Updating a guest (aka PATCH /:id)

```js
const response = await fetch(`${baseUrl}/1`, {
  method: 'PATCH',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({ attending: true }),
});
const updatedGuest = await response.json();
```

### Deleting a guest (aka DELETE /:id)

```js
const response = await fetch(`${baseUrl}/1`, { method: 'DELETE' });
const deletedGuest = await response.json();
```

## Deploying to Heroku

Create a Heroku account at [Heroku - Sign up](https://signup.heroku.com/),
and then use this repository to deploy the express app.
