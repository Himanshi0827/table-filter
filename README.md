
### Task Report:
### Filter Table Application with Search API
### Implement a search component that filters a list of items based on user input.

# 1. Task Description
Create a search functionality with three types of filters and searches:
- ** Basic Search **: Filters based on the first name using a local dataset.
- DataTable Search: Filters data by `first_name`, `last_name`, and `email` from a local dataset.
- API Search: Filters data fetched from an external API with search criteria based on `first_name`, `last_name`, and `email`. The backend serves a REST API to perform these queries using Express.

The application includes tab navigation to toggle between these different types of search functionalities.
# 2. Task Output Screenshot
<img width="524" alt="image" src="https://github.com/user-attachments/assets/f39cba96-665d-4fad-9e28-bb307afed317">






# 3. Widgets/Algorithm Used in Task

- useState Hook: 
  - Manages the state of the search query (`query`).
  - Handles the active tab's state for tab switching (`setActiveTab`).

- useEffect Hook:
  - For API Search, used to trigger the API call when the search query changes or is empty.
  - Fetches data from the API endpoint (`localhost:5000?q=${query}`) and updates the result.

- Input Field (`<input>`): 
  - Captures the user’s search query. It is common to all three types of searches (basic, datatable, and API).

- Button Widget:
  - Used to create navigation buttons for switching between different search types (Basic Search, DataTable Search, and API Search).

- Table Component: 
  - Used to render filtered results in a tabular format for the DataTable Search and API Search.

- Array Filter Algorithm:
  - In Frontend: Filters the local dataset by searching across multiple fields (`first_name`, `last_name`, and `email`) using the `Array.filter()` method.
  - In Backend (API Search): Similar logic is implemented in the backend to filter data from a predefined dataset (`Users`) and return a maximum of 10 results.

  Search Algorithm Logic (both frontend and backend):
  - The algorithm iterates over the data.
  - For each data item, it checks if the query exists in any of the specified keys (`first_name`, `last_name`, or `email`) using `Array.some()`.
  - The search is case-insensitive, converting both the query and data to lowercase before comparing.
  
- Axios Library:
  - Used for making API calls from the frontend to the backend, fetching filtered results dynamically.

- Express.js:
  - Backend server serves the filtered data based on the user's search query by exposing a simple API endpoint.

  Backend Search Algorithm (in `server.js`):
  js
  const search = (data) => {
    return data.filter((item) =>
      keys.some((key) => item[key].toLowerCase().includes(q))
    );
  };
  
  - This backend algorithm matches the query with any of the `first_name`, `last_name`, or `email` fields and returns up to 10 results for efficiency.

- CORS Middleware:
  - Ensures cross-origin communication between the frontend React app and the backend Express API.

