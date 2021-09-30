# Code Challenge Practice

### Overview
We are going to create a E-Commerce backend. This backend will consist of a cart that we can select items to be added to the cart. Once all of the items are selected, then we want to checkout, which will mark the cart completed.

### Note:
This sounds like a lot. But we are only focused on the backend. Not the front end side of this. You can use postman to send the requests.

### Models
* Cart
  * has many cart_items
  * has many items through cart_items
  * has a completed boolean

* CartItem
  * belongs to Cart
  * belongs to Item
  * has a quantity

* Item
  * has many cart_items
  * has many carts through cart_items
  * has a name

### Current Cart
* You should have a current_cart method built in the application_controller.rb file. This method should:
  * Check if there are any carts created previously, if not then return a new saved cart with completed as false.
  * Check if the last cart was completed or not. If it was completed, then create a new cart with completed as false.
  * Otherwise return the last cart that was created.

### Requests
* CartsController
  * `GET /carts` - Returns all of the carts that have been created.
  * `PATCH /checkout` - Updates a cart to be completed. Returns an error that the cart has been completed with a bad_request status if already completed previously.
* ItemsController
  * `GET /items` - Returns all of the items that have been created.
  * `GET /carts/:cart_id/items` - Returns all of the items that are currently in that cart.
  * `POST /items` - Creates an item, should only need a name.
* CartItems Controller
  * `POST /cart_items` - This is the equivilent of adding an item to the current cart. To be able to create a cart_item, you will need to send an `item_id` and a `cart_id`.


NOTE: No other routes / requests should exist.