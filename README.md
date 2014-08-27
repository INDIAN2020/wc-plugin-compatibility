# WooCommerce 2.2 Compatibility Utility Class

The purpose of this class is to provide a single point of compatibility functions for dealing with supporting multiple versions of WooCommerce (currently 2.1.x and 2.2)

## How to Use

The recommended procedure is to include this class in any plugin that you want to add WooCommerce cross-compatibility to, renaming the file/class, replacing "my plugin" with the name of the plugin in which this is included, so as to avoid clashes between plugins.

Over time it's expected that methods will be removed as compatibility for older versions of WooCommerce is dropped.

The class also provides a convenient reference of methods, constants, etc, that need to be modified within a plugin for WooCommerce cross-compatibility.

## Changelog

**2.0 - 2014.08.27**
* Feature - Added 2.2 compatibility methods
* Misc - Dropped 2.0.x compatibility methods

**1.1 - 2014.01.22**

* Feature - Added a bunch of new compatibility methods
* Fix - Fixed get_order_custom_field() method

**1.0 - 2014.01.17**

* Initial release

## Compatibility Issues

### Fixed

* `new WC_Order()` is deprecated in favor of `wc_get_order()`
* `get_product()` is soft-deprecated in favor of `wc_get_product()`
* Order Status is no longer a taxonomy (`shop_order_status`), rather the `post_status` is used. While there is backwards compat in 2.2 core for this, you can use the `backport_order_status_query_args()` method as a one line method to make 2.2-compatible queries backwards compat to 2.1. It's easy to then remove the single line once you can target 2.2+.
* `WC_Order()` introduced new methods in 2.2, `get_user_id()` and `get_user()` which are backported to 2.1 with `get_order_user_id()` and `get_order_user()`
* `WC_Order_Item_Meta::get_formatted()` was added in 2.2 and backported to 2.1 with `get_formatted_item_meta()`
* The log file path has changed from `wp-content/woocommerce/logs/` in WC 2.1 to one level above the webroot in WC 2.2 and `wc_get_log_file_path()` was introduced to get the fully-qualified log path. This is backported.
