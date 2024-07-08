# Feedback App Client

This is the frontend application for the Feedback App, built with Vue 2. It allows users to submit feedback ratings from 1 to 5.

## Features

- Submit feedback ratings using a 5-star rating system.
- Displays numbers below the stars.
- Modern styled submit button.
- Responsive design.

## Prerequisites

- Node.js and npm installed.

## Installation

1. Clone the repository:

   ```sh
   git clone https://github.com/yudi-prasetyo/feedback_form_client.git
   ```

2. Navigate to the project directory:

   ```sh
   cd feedback_form_client
   ```

3. Install the dependencies:

   ```sh
   npm install
   ```

## Usage

1. Start the development server:

   ```sh
   npm run serve
   ```

2. Open your browser and navigate to `http://localhost:8080`.

## Project Structure

```
feedback-app-client/
├── node_modules/
├── public/
│   └── index.html
├── src/
│   ├── assets/
│   ├── components/
│   │   └── FeedbackForm.vue
│   ├── App.vue
│   ├── main.js
├── .gitignore
├── babel.config.js
├── package.json
├── README.md
└── vue.config.js
```

## Dependencies

- [Vue.js](https://vuejs.org/) - The Progressive JavaScript Framework.
- [Axios](https://github.com/axios/axios) - Promise based HTTP client for the browser and node.js.
- [Font Awesome](https://fontawesome.com/) - The web's most popular icon set and toolkit.