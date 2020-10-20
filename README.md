# meeting-search PROJECT

## Project setup - How to Run the Project
```
cd location/of/choice
git clone https://github.com/danielv7/meeting-search.git
npm install
npm run serve
```
### Project Features I Implemented

- The feature I choose to implement was allowing the user to interact with the search results. I gave the user the option to either delete a search result or pin/un-pin a result. If a user pinned a result it would automatically move the pinned result to the top of the list and if un-pined it would move down accordingly. I also added basic formatting features to format dates, emails, and phone numbers in a more user-friendly way.

### My approach to the product, design decisions and tradeoffs I made

- I approached the project with the user in mind, asking myself how would the user want to interact and visualize the product. Based on the size of the project I decided not to use Vue Router or Vuex. The main decision for not using Vue Router was because of the size, if I had to navigate to any additional pages/routes I would have; looking back I should have implemented the router to make the project more scalable and/or adding additional features. I decided not to use Vuex (React's Redux) for simplicity.  because of the limited data from the "backend" I was using (5 JSON files). I added the 5 JSON files to the assets folder and imported them individually to the main component. I thought about copying over the 5 JSON files into something called [JSONPlaceholder](https://jsonplaceholder.typicode.com/), this would allow me to make fake API calls that would give me real responses. This way I would use the Fetch API to make a GET request when fetching the data anytime a new search parameter was selected and a DELETE request when a result wanted to be deleted from the results. I would have used both async/await and try/catch blocks to do so. I would also add a loading icon in the user interface to let the user know data was being fetched on the backend. As of now none of the search results persist so if you made a search and reloaded the page it would disappear one possible way I would fix this if needed would be with client-side caching. I used Primitive UI for the CSS styling which was for simplicity and saving time. All I did was in the index.html file I imported a simple link tag. If I had more I would enhance the styling by creating a more uniform output of the results as the button's current vary on size.


## Author

- Daniel Vaughan

## Notes

- Estimate time spent on project 5 hours





### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

### Compiles and hot-reloads for development
```
npm run serve
```
### Compiles and minifies for production
```
npm run build
```
### Lints and fixes files
```
npm run lint
```