- The url_for() function is very useful for dynamically building a URL for a specific function. The function accepts the name of a function as first argument, and one or more keyword arguments, each corresponding to the variable part of URL.

- The url_for() function is used to build a URL to a specific function. It takes the name of the function as the first argument and any number of keyword arguments that correspond to the variable parts of the URL.

## rules used in using url_for 
- The first argument is the name of the function you want to build a URL for. This is usually the name of a view function in your Flask application.
- The keyword arguments correspond to the variable parts of the URL. For example, if your URL has a variable part like /user/<username>, you would pass username as a keyword argument to url_for().
- The url_for() function will return the URL for the specified function, with the variable parts replaced by the values you provided in the keyword arguments.

- The url_for() function is useful for generating URLs dynamically, especially when you want to create links to different parts of your application without hardcoding the URLs.
- It helps to avoid issues with URL changes, as you can use the function name and keyword arguments instead of hardcoding the URL.