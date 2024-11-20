# Company Stuff
1. [Seafood UAT](https://pmtfresh-uat.primesupermarket.com/login.php)
1. [Fresh UAT](https://pmtseafood-uat.primesupermarket.com/login.php)
1. `PMT`: Prime Mart Trading
1. `MSOH`: Min stock at hand
1. `PLU`: Price Lookup (barcode, etc.)
1. `Eleap`: Weighing system, weigh food, get barcode.
1. `IBT`: Price Prime sells to supermarkets.
1. `RSP`: Recommended Selling Price.
1. `UOM`: Unit Of Measurement
1. `Sage`: Database for fresh goods like fruits & vegs
1. `Navision`: Database for other goods (like pencils, etc.)
1. `MAHOTA Food`, `Prime Online`, `Prime Mahota`: Not related to Prime
1. `Sync`: Since the 3 companys above are ordering from Prime as well, need to sync with other companies.
1. `MOQ`: Minimum Order Quantity.
1. `PO` / `PU`: `PO` is list of things buyers bought from outside vendors / `PU` is list of things prime sell to supermarket.
1. `Special Pricing`: Top priority for pricing. For giving discounts to certain customers.
1. `DO`: Delivery Order generated when customer recieves the product.
1. `12:00 - 14:00 & 16:00 - 17:00`: Same day delivery.
1. `00:00 - 10:00 & 12:00 - 14:00 & 16:00 - 17:00`: Next day delivery.
1. `Add on` & `Declaring stock balance` & `Force allocation`: Ordering for seafood.
1. `Normal Ordering` & `Standing Order` & `Allocation Order`: Ordering for fresh.
    1. `Normal Order` is similar to `Add On`, but diff cuz outlet has to select individually and "add to cart". 
    1.  Buyer can `allocate` to Outlet. Outlet can reject allocation order. 
    1. `Standing Order` can be set based on customer behaviour, e.g. every monday, etc.
1. `Block Normal Order`: If don't have stock, can block the order so customer don't order the product.
1. `Cutoff Time`: Did by intern. Can set num of days to block order. During block days, cannot order. Used for standing order.
1. Must set delivery time for customer in pmt fresh when creating it.

1. `Account`: Knows how much PMT buys from Supermarket (IBT)
1. `PSM Account`: Can't know how much PMT buys from Supermarket (IBT)
1. `Con job`: Setup certain time, certain code to be ran.