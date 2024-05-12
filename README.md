I designed a web crawler using HTTP 1.1 protocol to retrieve hidden data from a fake social networking site using an
HTML parser, bread-first search algorithm and cookie management techniques.

High Level Approach:

Connection Management: The crawler uses HTTP/1.1 protocol by using the header Connection: Keep-Alive to improve efficiency and reduce the load on the server.
HTML Parsing: Utilizes HTMLParser from Python's standard library to extract necessary data from the HTML portion of the response from the server such as CSRF middleware token and the flags
Login Mechanism: Implements an HTTP GET and POST request to handle the login, extracting and using cookies (csrf token and sessionid) to correctly login
Crawling Strategy: Adopts a breadth-first search approach, storing URLs to visit in a list (all_pages) and tracking visited URLs (crawled_pages) to avoid loops and redundant visits
Error Handling: Includes logic to handle various HTTP status codes and server responses, ensuring robust crawling behavior.

Challenges faced:

Logging into Fakebook: This was the biggest challenge since sending the requests in the correct format took lot of research and testing to get it correct. Also it took time to read the response and try to figure out how to extract the csrfmiddlewaretoken from the HTML body of the response.
Session Management: Ensuring that the crawler maintains a valid session with cookie management was crucial since it took a while to figure out that new cookies were needed before crawling
Error Handling: Implementing comprehensive error handling to manage different HTTP responses and connection issues without crashing or stalling the crawler
Loop Prevention: Developing a mechanism to avoid infinite loops caused by circular links between pages was essential for efficient crawling.

List of interesting properties/features of the design:

HTML Parser to parse: Effectively extracts necessary data from HTML body, handling a variety of tag structures and attributes.
HTTP 1.1 with Connection: keep-alive that keeps persistent connection with the server and reduces the load on the server
Function for extracting the relevant cookies
Bread-first search strategy that stores all the URLs and keeps track of the URLs that get visited that prevents redundant visits


Overview of testing the code:

Used print statements both for the sending of the requests and the response from the server. This for example helped in detecting where the csrfmiddlewaretoken was by being able to identify the tag and its location within the HTML body.
