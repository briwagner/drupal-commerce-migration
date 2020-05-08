# Basic Commerce Migrate

This Drupal module is a demo of making basic migrations with Commerce entities: products, variations, attributes.

A more detailed example is here: https://github.com/mglaman/commerce_examples

## Migration Sequencing

If you're migrating interconnected data, you have to decide what to migrate first. I find it confusing that other Commerce migrations choose to migrate product variations before products. I think that's because previous version of Commerce required you to add the variation before the product. As of spring 2020 that is not the case. On the default product form, you can choose to create the product with no variations. Or you can create the product and add variations. There is no form to add a variation, outside of the parent product. A product with no active variation is visible, but it will not have the add-to-cart button.

This module assumes we first migrate products with a unique product-number. Then we migrate variations, which look up the parent product from that product-number.

## Usage

The three json files in the attributes/ directory should be copied to the root of the site's public folder. These are the data files that are consumed by the migration tasks.

After installing the module, the default product should include a new field: Product number. Edit the product form to show or edit this field.

Navigate to the migration group page: admin/structure/migrate/manage/basic_commerce/migrations

Run the "Get product variations" to perform all three migrations. You can choose to run the produts or attributes individually.

Confirm the three products are created. The first product should have four variations created with it.