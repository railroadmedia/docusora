# Cart Sidebar Updates - Drumeo/Pianote Nov 2020

## New Marketing Sales Pages Requirements

### Shop Cards
Shop card partial includes now always need some JSON passed in. The SKU and the quantity that should be added 
when the customer clicks 'Add To Cart'.  

Example:  

```php
@include('drumshop.partials._drum-shop-card', [
    "sku" => "electrify-your-drumming",
    "itemURL" => "/drumshop/electrify-your-drumming/",
    "thumbnail" => "https://dpwjbsxqtam5n.cloudfront.net/drum-shop/electrify-your-drumming/card-thumb.jpg",
    "packLogo" => "https://dpwjbsxqtam5n.cloudfront.net/drum-shop/electrify-your-drumming/logo.png",
    "title" => "Electrify Your Drumming",
    "packAuthor" => "Michael Schack",
    "cardDescription" => "The ultimate guide to playing electronic dance music on the drums.",
    "fullPrice" => Prices::$eydFull,
    "price" => Prices::$eydRegular,
    "includedEdge" => true,
    "popularity" => "92",
    "category" => "lessons",

    "productJson" => '{"electrify-your-drumming": 1}', // must be added for dynamic add to cart to function
])
```

### Linking To Each Products Sales Page
Also, each product should have its 'sales page url' property set in Musora Center. This is where the user will go 
when they click a product thumbnail inside the cart sidebar.

See any Musora Center product edit page: 'Sales Page URL' field.

### Recommended Products
This is controlled inside the ecommerce.php file (in the laravel config folder) under the 'recommended_products' 
array key. The details are mostly self explanatory in the config file. Here is a more details description of how all 
that works: [https://github.com/railroadmedia/ecommerce/blob/2.4-/docs/recommended-products/cart.md](https://github.com/railroadmedia/ecommerce/blob/2.4-/docs/recommended-products/cart.md)

### Add To Cart Buttons
You can make any html element add items to the cart, including multiple items/bundles at the same time by setting the 
correct JSON data and classes on the HTML element (such as a button). You can also add promo codes and lock the cart 
much like with the normal checkout urls. Details for how to do that are here:
[https://github.com/railroadmedia/vuesora/blob/0.16-cart-sidebar/docs/components/CartSidebar.md](https://github.com/railroadmedia/vuesora/blob/0.16-cart-sidebar/docs/components/CartSidebar.md)

```
The vue component attaches events listeners to the html elements that exists on page load 
(not to the elements added later to DOM) and have vue-add-to-cart class.
```

## Technical Details

The cart sidebar is created and controlled by vuesora.