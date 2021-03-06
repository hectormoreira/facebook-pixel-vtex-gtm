# facebook-pixel-vtex-gtm

Configuracion de Facebook Pixel y eventos, VTEX IO con Google Tag Manager

Documentación: [Setting up Google Tag Manager
](https://developers.vtex.com/vtex-developer-docs/docs/vtex-io-documentation-setting-up-google-tag-manager)

# Variables

## variables GTM

---

**productName**

- Grupo: variables definidas por usuario
- Tipo: Variable de capa de datos
- Nombre de variable: ecommerce.detail.products.0.name

---

**categoryName**

- Grupo: variables definidas por usuario
- Tipo: Variable de capa de datos
- Nombre de variable: page

**productId**

- Grupo: variables definidas por usuario
- Tipo: Variable de capa de datos
- Nombre de variable: ecommerce.detail.products.0.id

---

**productPriceTo**

- Grupo: variables definidas por usuario
- Tipo: Variable de capa de datos
- Nombre de variable: ecommerce.detail.products.0.price

---

**transactionId**

- Grupo: variables definidas por usuario
- Tipo: Variable de capa de datos
- Nombre de variable: transactionId

---

**transactionTotal**

- Grupo: variables definidas por usuario
- Tipo: Variable de capa de datos
- Nombre de variable: transactionTotal

---

**ProductsOrderId**

- Grupo: variables definidas por usuario
- Tipo: Javascript personalizado

```js
function() { var arr = {{transactionProducts}}, len = arr.length, i = -1, res =
[]; while (++i < len) {res[i] = arr[i].id;}; return res; }
```

---

**orderFormProducts**

- Grupo: variables definidas por usuario
- Tipo: Variable de capa de datos
- orderFormProducts

---

**orderFormProductsIds**

- Grupo: variables definidas por usuario
- Tipo: Javascript Personalizado

```js
function() { var arr = {{orderFormProducts}}, len = arr.length, i = -1, res =
[]; while (++i < len) {res[i] = arr[i].sku;}; return res; }
```

---

**orderFormProductsValue**

- Grupo: variables definidas por usuario
- Tipo: Javascript Personalizado

```js
function() { var arr = {{orderFormProducts}}, len = arr.length, i = -1, subtotal
= 0; while (++i < len) {if(arr[i].sellingPrice != undefined) subtotal +=
arr[i].sellingPrice;}; return subtotal; }
```

---

**orderFormItems**

- Grupo: variables definidas por usuario
- javascript personalizado

```js
function() { var arr = {{orderFormProducts}}, len = arr.length, i = -1, res =
[]; while (++i < len) { res[i] = arr[i].sku; res[i] = {'id':
arr[i].sku,'quantity':arr[i].quantity,'item_price':parseFloat(arr[i].sellingPrice).toFixed(2)}
}; return res; }
```

**ProductsCartId**

- Grupo: variables definidas por usuario
- Tipo: Javascript personalizado

```js
function() { var arr = {{orderFormProducts}}, len = arr.length, i = -1, res =
[]; while (++i < len) {res[i] = arr[i].id;}; return res; }
```

---

**visitorContactInfoEmail**

- Grupo: variables definidas por usuario
- Variable de capa de datos
- visitorContactInfo.0

---

**shelfProductIds**

- Grupo: variables definidas por usuario
- variable de capa de datos
- shelfProductIds

---

**siteSearchTerm**

- Grupo: variables definidas por usuario
- variable de capa de datos
- siteSearchTerm

---

**skuStocks**

- Grupo: variables definidas por usuario
- variable de capa de datos
- skuStocks

---

**productSkuIds**

- Grupo: variables definidas por usuario
- javascript personalizado

```js
function(){return Object.keys({{skuStocks}});}
```

---

**transactionProducts**

- Grupo: variables definidas por usuario
- variable de capa de datos
- transactionProducts

---

**transactionProductsIds**

- Grupo: variables definidas por usuario
- javascript personalizado

```js
function() { var arr = {{transactionProducts}}, len = arr.length, i = -1, res =
[]; while (++i < len) {res[i] = arr[i].sku;}; return res; }
```

---

**transactionProductsItems**

- Grupo: variables definidas por usuario
- javascript personalizado

```js
function() { var arr = {{transactionProducts}}, len = arr.length, i = -1, res =
[]; while (++i < len) { res[i] = arr[i].sku; res[i] = {'id':
arr[i].sku,'quantity':arr[i].quantity,'item_price':parseFloat(arr[i].sellingPrice).toFixed(2)}
}; return res; }
```

---

## Triggers GTM

---

**addToCart**

- Tipo: Evento personalizado
- Nombre del evento: addToCart
- disparar: Todos los eventos personalizados

---

**checkout - payment**

- Tipo: Evento Personalizado
- Nombre del evento: payment
- disparar: Todos los eventos personalizados

---

**checkout - profile**

- Tipo: Evento Personalizado
- Nombre del evento: profile
- disparar:
  Todos los eventos personalizados

---

**checkout - shipping**

- Tipo: Evento Personalizado
- Nombre del evento: shipping
- disparar:
  Todos los eventos personalizados

---

**checkout - email**

- Tipo: Evento Personalizado
- Nombre del evento: email
- disparar:
  Todos los eventos personalizados

---

**orderPlaced Trigger**

- Tipo: Evento Personalizado
- Nombre del evento: orderPlaced
- disparar:
  Todos los eventos personalizados

---

**VTEX - Busca**

- Tipo: Evento personalizado
- Nombre del evento: internalSiteSearchView
- disparar:
  Todos los eventos personalizados

---

**VTEX - Categorias**

- Tipo: Evento personalizado
- Nombre del evento: RegEx `departmentView|categoryView` 
- disparar:
  Todos los eventos personalizados

---

**VTEX - PageView**

- Tipo: Evento personalizado
- Nombre del evento: pageView
- disparar:
  Todos los eventos personalizados

---

**VTEX - Producto**

- Tipo: Evento personalizado
- Nombre del evento: productDetail
- disparar:
  Todos los eventos personalizados

---

## tags GTM

**FB - Pixel**

- HTML personalizado

```html
<!-- Facebook Pixel Code -->
<script>
  !function(f,b,e,v,n,t,s)
  {if(f.fbq)return;n=f.fbq=function(){n.callMethod?
  n.callMethod.apply(n,arguments):n.queue.push(arguments)};
  if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
  n.queue=[];t=b.createElement(e);t.async=!0;
  t.src=v;s=b.getElementsByTagName(e)[0];
  s.parentNode.insertBefore(t,s)}(window, document,'script',
  'https://connect.facebook.net/en_US/fbevents.js');
  fbq('init', '{your-pixel-id-goes-here}');
  fbq('track', 'PageView');
</script>
<noscript>
  <img height="1" width="1" style="display:none" 
       src="https://www.facebook.com/tr?id={your-pixel-id-goes-here}&ev=PageView&noscript=1"/>
</noscript>
<!-- End Facebook Pixel Code -->
```

- Accionamiento:
  - VTEX - PageView

---

**FB - PageView**

- HTML personalizado

```html
<script>
  fbq("track", "PageView");
</script>
```

- Sequencia de Tags:
  Disparar tag antes: FB - Pixel
- Accionamiento:
  - VTEX - PageVIew

---

**FB - AddPaymentInfo**

- HTML personalizado

```html
<script>
  fbq("track", "AddPaymentInfo");
</script>
```

- Sequencia de Tags:
  Disparar tag antes: FB - Pixel
- Accionamiento:
  - checkout - payment

---

**FB - AddToCart**

- HTML personalizado

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

- Sequencia de Tags:
  Disparar tag antes: FB - Pixel
- Accionamiento:
  - addToCart
  - checkout - cart

---

**FB - checkout inicio**

- HTML personalizado

```html
<script>
  fbq("track", "InitiateCheckout");
</script>
```

- Opções de disparo da tag
  - Uma vez por página
- Sequencia de Tags:
  Disparar tag antes: FB - Pixel
- Accionamiento:
  - checkout - profile
  - checkout - email

---

**FB - CompleteRegistration**

- HTML personalizado

```html
<script>
  fbq("track", "CompleteRegistration");
</script>
```

- Sequencia de Tags:
  Disparar tag antes: FB - Pixel
- Accionamiento:
  - checkout - shipping

---

**FB - Order Placed**

- HTML personalizado

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

- Sequencia de Tags: Disparar tag antes: FB - Pixel
- Accionamiento: - orderPlaced Trigger 

---

**FB - Other** 

- HTML personalizado
```html
<script>
  fbq("track", "Other");
</script>
````
- Sequencia de Tags:
  Disparar tag antes: FB - Pixel
- Accionamiento:
  - Pg Others

---

**FB - Purchase**

- HTML personalizado

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

- Sequencia de Tags:
  Disparar tag antes: FB - Pixel
- Accionamiento:
  - VTEX - OrderPlaced

---

**FB - Search**

- HTML personalizado

```html
<script>
  fbq("track", "Search", {
    search_string: "{{siteSearchTerm}}",
    content_category: "Product Search",
    content_ids: "{{shelfProductIds}}",
  });
</script>
```

- Sequencia de Tags:
  Disparar tag antes: FB - Pixel
- Accionamiento:
  - Pg Busca

---

**FB - ViewContent Product**

- HTML personalizado

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

- Sequencia de Tags:
  Disparar tag antes: FB - Pixel
- Accionamiento:
  - VTEX - Producto
