# facebook-pixel-vtex-gtm

Configuration Facebook pixel and events, VTEX IO with Google Tag Manager

# Variables

## variables GTM

click classes:

---

- Grupo: variables incorporadas
- Tipo: Variable de capa de datos
- nome da variable:gtm.elementClasses

---

**productName**

- Grupo: variables definidas por usuario
- Tipo: Variable de capa de datos
- Nombre de variable: productName

---

**pageCategory**

- Grupo: variables definidas por usuario
- Tipo: Variable de capa de datos
- Nombre de variable: pageCategory

**productId**

- Grupo: variables definidas por usuario
- Tipo: Variable de capa de datos
- Nombre de variable: productId

---

**productPriceTo**

- Grupo: variables definidas por usuario
- Tipo: Variable de capa de datos
- Nombre de variable: productPriceTo

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
- TIpo: Javascript personalizado

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

## Accionadores GTM

---

**addToCart**

- TIpo: Clique - todos os elementos
- disparar:
  Click classes - Corresponde a RegEx `buy-button|buy-button-ref`

---

**checkout - payment**

- Tipo: Evento Personalizado
- Nome do evento: payment
- disparar: Todos os eventos personalizados

---

**checkout - profile**

- Tipo: Evento Personalizado
- Nome do evento: profile
- disparar:
  Todos os eventos personalizados

---

**checkout - shipping**

- Tipo: Evento Personalizado
- Nome do evento: shipping
- disparar:
  Todos os eventos personalizados

---

**checkout - email**

- Tipo: Evento Personalizado
- Nome do evento: email
- disparar:
  Todos os eventos personalizados

---

**orderPlaced Trigger**

- Tipo: Evento Personalizado
- Nome do evento: orderPlaced
- disparar:
  Todos os eventos personalizados

---

**pg Busca**

- TIpo: Exibição de página
- disparado em: Algumas exibições de página
- disparar:
  - pageCategory corresponde a RegEx `InternalSiteSearch`

---

**pg Geral**

- TIpo: Exibição de página
- disparado em: Algumas exibições de página
- disparar:
  - pageCategory corresponde a RegEx `Department|Category|Home|InternalSiteSearch`

---

**pg Others**

- TIpo: Evento personalizado
- Nome do evento: otherView
- disparar:
  Todos os eventos personalizados

---

**pg Produto**

- TIpo: Exibição de página
- disparado em: Algumas exibições de página
- disparar:
  - pageCategory corresponde a RegEx `Product`

---

## tags do GTM

**FB - Pixel**

- HTML personalizado

  ```html
  <!-- Facebook Pixel Code -->
  <script>
    !(function (f, b, e, v, n, t, s) {
      if (f.fbq) return;
      n = f.fbq = function () {
        n.callMethod
          ? n.callMethod.apply(n, arguments)
          : n.queue.push(arguments);
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
    fbq("init", "000000000000000000000"); // Insert your pixel ID here.
    fbq("track", "PageView");
  </script>

  <noscript
    ><img
      height="1"
      width="1"
      style="display:none"
      src="https://www.facebook.com/tr?id=000000000000000000000&ev=PageView&noscript=1"
  /></noscript>
  <!-- DO NOT MODIFY -->
  <!-- End Facebook Pixel Code -->
  ```

- Acionamento:
  - All Pages

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
- Acionamento:
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
- Acionamento:
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
- Acionamento:
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
- Acionamento:
  - checkout - shipping

---

**FB - Order Placed**

- HTML personalizado

````html
<!-- Facebook Conversion Code for Conclusões de compra - Loungerie -->
‪
<script>
  (function () {
    var \_fbq = window.\_fbq || (window.\_fbq = []);
    if (!\_fbq.loaded) {
    var fbds = document.createElement('script');
    fbds.async = true;
    fbds.src = '//connect.facebook.net/en_US/fbds.js';
    var s = document.getElementsByTagName('script')[0];
    s.parentNode.insertBefore(fbds, s);
    \_fbq.loaded = true;
    }
    })();
    window.\_fbq = window.\_fbq || [];
    window.\_fbq.push(['track', '{{transactionId}}', { 'value': '{{transactionTotal}}', 'currency': 'USD' }]);
</script>
<noscript
  ><img
    height="1"
    width="1"
    alt=""
    style="display:none"
    src="https://www.facebook.com/tr?ev={{transactionId}}&cd[value]={{transactionTotal}}&cd[currency]=USD&noscript=1"
/></noscript>
``` - Sequencia de Tags: Disparar tag antes: FB - Pixel - Acionamento: -
orderPlaced Trigger --- **FB - Other** - HTML personalizado ```html
<script>
  fbq("track", "Other");
</script>
````

- Sequencia de Tags:
  Disparar tag antes: FB - Pixel
- Acionamento:
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
- Acionamento:
  - OrderPlaced Trigger

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
- Acionamento:
  - Pg Busca

---

**FB - ViewContent Product**

- HTML personalizado

```html
<script>
  var precoFinal = parseFloat({{productPriceTo}}).toFixed(2);fbq('track', 'ViewContent', {value: precoFinal,	currency: 'BRL',content_name: '{{productName}}',content_ids: {{productSkuIds}},content_type: 'product'});
</script>
```

- Sequencia de Tags:
  Disparar tag antes: FB - Pixel
- Acionamento:
  - Pg Produto
