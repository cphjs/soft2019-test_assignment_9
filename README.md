# Info

[Assignment description](https://github.com/datsoftlyngby/soft2019spring-test/blob/master/Assignments/09%20Nonfunctional%20Testing%20Assignment.pdf)

[Assigment 8\(this is the code for the server that is tested\)](https://github.com/cphjs/soft2019-test_assignment_8)

The server can be run locally to run the tests, but for your convenience I set up a server to host that website http://134.209.201.127/ It will be taken down after the peer-review period ends.

# Solution

To have a site to test, I added some more features to the Marios pizza bar web solution from Assignment 8. Particularly, the index page can now return the current orders and available pizzas as a JSON response. As well as a new endpoint `/price`, used to retrieve the price of a pizza based on its name(this is used for the parameterized test).

The test plan consists of three thread groups, each solving one part of the assigment. The various reports(results tree, assertion result view, summary report and graph results) are part of the root and are shared amongst all thread groups.

The first thread group **10-group** makes a simple GET request to the index page and asserts that the HTTP return code is 200(meaning no errors) and that the pages HTML content contains a h3 element with the class `card-header` and text `New order`.

The second thread group is similar to the first except that it deals with JSON instead of HTML. It uses a **HTTP Header Manager** to send an `Accept` header to tell the server that it should return JSON. The `Response type is json` assertion validates that the server is indeed returning valid json. Afterwards I check that the returned json object contains arrays of orders and pizzas and that their elements contain a name attribute.

The last thread group contains a parameterized test. It takes a simple file(see `pizzaset.txt`) that contains the name of the pizza and the expected price. It uses the `/price` endpoint to query the price for a specific pizza and then compares the returned value to the one loaded from the csv file.
