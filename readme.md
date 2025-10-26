# Azalea Jewelry Theme Enhancements

This project contains custom Shopify Liquid blocks tailored for the Azalea Jewelry storefront.

## Key Blocks

- **Shop by Style Scroll (`blocks/ai_gen_block_5e6fc84.liquid`)**
  - Renders a metaobject-driven carousel of styles.
  - Supports asynchronous selection with history state updates and custom events.

- **Product Showcase (`blocks/ai_gen_block_936a851.liquid`)**
  - Displays collection products with featured-image thumbnails and swatch interactions.
  - Filters cards in-place based on the selected style without reloading the page.

## Development Notes

- Style data originates from `shop.metaobjects.custom.values`.
- Product cards rely on `product.featured_image` for visuals and `product.metafields.custom.custom` for style metadata.
- Filtering communication occurs through the `style:filter` custom event dispatched by the scroll block and handled by the showcase block.

## Getting Started

1. Ensure collection products have the required `custom` metafield populated with a style metaobject reference.
2. Populate style metaobjects with `style` and `image` fields.
3. Add both blocks to the desired template within the theme editor.

For further modifications, review the corresponding Liquid files within the `blocks/` directory.
