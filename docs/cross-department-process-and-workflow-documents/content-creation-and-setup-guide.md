# How To Add A New Brand Show

1. Add a new config value under config/railcontent.php, key 'cataloguesMetadata'. 
   Copy existing one and modify it, add correct data. The key is the content row 'type', usually a slug of the title.
2. Add a new config value under config/railcontent.php, key 'showTypes'. Add the same slug value for the show
   as used in the key from the previous step.
3. Adding a show to musora center for CMS editing is a whole different and complicated process. Docs coming soon...
   
Example commit: [https://github.com/railroadmedia/drumeo/commit/904970b906f63fdc93bee0de3be981fdd0f6d92d](https://github.com/railroadmedia/drumeo/commit/904970b906f63fdc93bee0de3be981fdd0f6d92d)

# How To Add A New Digital Product

This is for linking a digital product that must enable access to specific members' area content.

1. The product and content must already be created. You will need the product SKU and top level content slug.
   For example the pianote product with SKU 'classical-piano' unlocks the content pack with the slug 
   'victoria-theodore-teaches-classical-piano'.
3. A railcontent_permissions table row is always required for a new pack/digital product. There is no UI for this yet.
   Make a new row for a permission which represents this product and content. Use the relevant name and brand for the data.
2. Note: changes are required in both the musora repo and relevant brand repo since the syncing needs to work for orders
   on either platform.
   
### Pianote & Others

1. app/Maps/ProductAccessMap.php -> add product SKU to packProductIds() function array.
2. config/event-data-synchronizer.php -> add product SKU to customer_io_pack_skus_to_sync_ownership array.
2. config/event-data-synchronizer.php -> add product SKU to customer_io_pack_sku_to_purchase_event_name array. 
   Add a customer.io event name, either as requested by the marketing team or just the same as the sku.
3. config/event-data-synchronizer.php -> add product SKU to ecommerce_product_sku_to_content_permission_name_map 
   array as the key, the value should be the relevant 'railcontent_permissions' row 'name' column.

Now in the musora repo:

2. config/event-data-synchronizer.php -> add product SKU to customer_io_pack_skus_to_sync_ownership array.
2. config/event-data-synchronizer.php -> add product SKU to customer_io_pack_sku_to_purchase_event_name array.
   Add a customer.io event name, either as requested by the marketing team or just the same as the sku.
3. config/event-data-synchronizer.php -> add product SKU to ecommerce_product_sku_to_content_permission_name_map
   array as the key, the value should be the relevant 'railcontent_permissions' row 'name' column.
   

Test ordering this product on your local machine to make sure the product is added and accessible.
Push and deploy both repos.