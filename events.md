# Events

## Facebook Pixel Code

```html
<!-- Facebook Pixel Code -->
<script type="text/javascript">
  !(function (f, b, e, v, n, t, s) {
    if (f.fbq) return;
    n = f.fbq = function () {
      n.callMethod ? n.callMethod.apply(n, arguments) : n.queue.push(arguments);
    };
    if (!f._fbq) f._fbq = n;
    n.push = n;
    n.loaded = !0;
    n.version = "2.0";
    n.queue = [];
    t = b.createElement(e);
    t.async = !0;
    t.src = v;
    s = b.getElementsByTagName(e)[0];
    s.parentNode.insertBefore(t, s);
  })(
    window,
    document,
    "script",
    "https://connect.facebook.net/en_US/fbevents.js"
  );
  fbq("init", "0000000000000000");
  fbq("track", "PageView");
</script>
<noscript
  ><img
    height="1"
    width="1"
    style="display:none"
    src="https://www.facebook.com/tr?id=0000000000000000&ev=PageView&noscript=1"
/></noscript>
<!-- End Facebook Pixel Code -->
```

## Pixel product page

```html
<!-- Pixel product page -->
<script>
  var precoFinal = parseFloat({{ productPriceTo }}).toFixed(2);
  fbq('track', 'ViewContent', {
      value: precoFinal,
      currency: 'USD',
      content_name: '{{productName}}',
      content_ids: {{ productSkuIds }},
      content_type: 'product'
  });
</script>
<!-- End Pixel product page -->
```

## Pixel category page

```html
<!-- Pixel category page -->
<script>
  fbq('track', 'ViewCategory', { content_name: {{ categoryName }} })
</script>
<!-- End Pixel category page -->
```

## AddTocart

```html
<!-- AddTocart  -->
<script type="text/javascript">
  var precoFinal = parseFloat({{orderFormProductsValue}}).toFixed(2);
  var content_ids = {{orderFormProductsIds}};
  if (!(precoFinal > 0)) {
      content_ids = [];
  }
  fbq('track', 'AddToCart', {
      content_ids: content_ids,
      content_type: 'product',
      value: precoFinal,
      currency: 'USD',
    	contents: {{orderFormItems}}
  });
</script>
<!-- End AddTocart  -->
```

## Purchase

```html
<!-- Purchase  -->
<script>
  fbq('track', 'Purchase', {
      value: {{transactionTotal}},
      currency: 'USD',
      content_type: 'product',
      content_ids: {{transactionProductsIds}},
    	contents: {{transactionProductsItems}}
  });
</script>
<!-- End Purchase  -->
```
