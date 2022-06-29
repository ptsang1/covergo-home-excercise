# Here is my solution

- I chose Vue 3 as the framework supporting me to finish the homework although I was just familiar with it in one day instead of the React.

- As the following requirements, there are 4 pages in the app. So I create the _Routes_ folder that includes the 2 files helping me manage routing in the app.

  ```text
  Routes
  │   paths.js
  │   Routes.vue
  ```

  - Where:
    - paths.js: In this file, I define and export all the routes in the app, specifically there are 4 routes in the app.
    - Routes.vue: This is a component help me manage what the view should be rendered.

- Each page in the requirements is corresponding to each file in the view folders.

  ```text
  views
  │   Page1.vue
  │   Page2.vue
  |   Page2Error.vue
  |   Page3.vue
  ```

  - Where:
    - Page1: This is the first page as well as the default page when there is nothing page found.
    - Page2: The page collects user input and saves it to the local storage if the data is valid else redirects to the Page2Error.
    - Page2Error: The page is redirected from the Page2 when the user input is invalid.
    - Page3: Get the data is stored in the local storage and show it on the webpage.
