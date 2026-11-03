<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#52613b">
<meta name="description" content="Cotiza tu pedido de Yura Snacks y compártelo por WhatsApp.">
<title>Cotizador | Yura Snacks</title>
<style>
:root{
  --green:#52613b;--green-dark:#35452d;--green-soft:#e8eddf;
  --cream:#f7f3e9;--paper:#fffefa;--cocoa:#684735;
  --text:#283126;--muted:#778071;--line:#e7e2d7;
  --gold:#d9b66c;--shadow:0 22px 60px rgba(49,61,39,.12);
}
*{box-sizing:border-box}
body{
  margin:0;min-height:100vh;padding:38px 18px;
  font-family:Inter,ui-sans-serif,system-ui,-apple-system,"Segoe UI",sans-serif;
  color:var(--text);
  background:
    radial-gradient(circle at 12% 8%,rgba(217,182,108,.16),transparent 26%),
    radial-gradient(circle at 90% 88%,rgba(82,97,59,.12),transparent 28%),
    var(--cream);
}
.page{width:min(100%,760px);margin:0 auto}
.header{text-align:center;margin:0 auto 26px}
.logo{
  width:58px;height:58px;border-radius:20px;margin:0 auto 13px;
  display:grid;place-items:center;background:var(--green);color:#fff;
  font-size:27px;box-shadow:0 10px 25px rgba(82,97,59,.22)
}
.kicker{font-size:.72rem;letter-spacing:.18em;text-transform:uppercase;font-weight:850;color:var(--green)}
h1{font-family:Georgia,serif;font-size:clamp(2rem,6vw,2.8rem);line-height:1.05;letter-spacing:-.045em;color:var(--green-dark);margin:8px 0}
.subtitle{color:var(--muted);margin:0;font-size:.98rem}
.card{
  background:rgba(255,254,250,.96);border:1px solid rgba(255,255,255,.9);
  border-radius:28px;padding:clamp(22px,5vw,36px);box-shadow:var(--shadow)
}
.section-title{display:flex;align-items:center;gap:10px;margin:0 0 19px;font-size:1rem;color:var(--green-dark)}
.section-title span{width:28px;height:28px;border-radius:9px;background:var(--green-soft);display:grid;place-items:center}
.field{margin-bottom:21px}
label{display:block;font-weight:780;font-size:.88rem;margin-bottom:8px;color:var(--green-dark)}
.hint{font-size:.78rem;color:var(--muted);margin:-2px 0 9px}
select,input{
  width:100%;min-height:52px;border:1px solid var(--line);border-radius:14px;
  background:#fff;padding:0 15px;color:var(--text);font:inherit;outline:none;
  transition:border .2s,box-shadow .2s
}
select:focus,input:focus{border-color:var(--green);box-shadow:0 0 0 4px rgba(82,97,59,.11)}
.quantity-row{display:grid;grid-template-columns:1fr 150px;gap:16px;align-items:end}
.quantity-control{display:flex;align-items:center;border:1px solid var(--line);border-radius:14px;background:#fff;overflow:hidden}
.quantity-control button{width:45px;height:52px;border:0;background:#f4f2e9;color:var(--green);font-size:1.35rem;cursor:pointer}
.quantity-control input{border:0;border-radius:0;text-align:center;min-width:0;padding:0 5px;box-shadow:none!important}
.delivery-note{
  display:flex;gap:12px;align-items:flex-start;background:#f3ecdc;border-radius:16px;
  padding:15px 16px;color:#64533c;font-size:.86rem;margin:8px 0 23px
}
.delivery-note .emoji{font-size:1.25rem}
.summary{background:#f7f8f2;border:1px solid #e8ecdf;border-radius:18px;padding:18px;margin:4px 0 22px}
.summary-head{display:flex;justify-content:space-between;align-items:center;margin-bottom:12px}
.summary-head strong{color:var(--green-dark)}
.summary-line{display:flex;justify-content:space-between;gap:12px;color:var(--muted);font-size:.88rem;padding:5px 0}
.summary-total{display:flex;justify-content:space-between;align-items:center;border-top:1px solid #dfe5d5;margin-top:10px;padding-top:14px;font-weight:850;color:var(--green-dark)}
.total{font-size:1.65rem;color:var(--green)}
.primary{
  display:flex;justify-content:center;align-items:center;gap:10px;width:100%;min-height:56px;
  border:0;border-radius:15px;background:var(--green);color:#fff;font-size:1rem;font-weight:850;
  cursor:pointer;transition:.2s;box-shadow:0 10px 22px rgba(82,97,59,.2)
}
.primary:hover{background:var(--green-dark);transform:translateY(-1px)}
.primary:disabled{opacity:.5;cursor:not-allowed;transform:none}
.secondary{display:none;margin-top:12px;width:100%;min-height:50px;border:1px solid var(--line);border-radius:14px;background:#fff;color:var(--green-dark);font-weight:750;cursor:pointer}
.secondary.show{display:block}
.foot{text-align:center;color:var(--muted);font-size:.77rem;margin:18px 0 0}
.foot strong{color:var(--green)}
.toast{display:none;margin-top:13px;padding:12px;border-radius:12px;background:#fbeee7;color:#814a31;font-size:.85rem}
.toast.show{display:block}
@media(max-width:520px){
 body{padding:25px 13px}.card{border-radius:23px}.quantity-row{grid-template-columns:1fr 125px}
}
</style>
</head>
<body>
<main class="page">
  <header class="header">
    <div class="logo" aria-hidden="true">🌿</div>
    <div class="kicker">Hecho para acompañar tu día</div>
    <h1>Cotizador Yura Snacks</h1>
    <p class="subtitle">Arma tu pedido y compártelo fácilmente por WhatsApp.</p>
  </header>

  <section class="card" aria-label="Cotizador de pedidos">
    <h2 class="section-title"><span>🛍️</span> Personaliza tu pedido</h2>

    <div class="field">
      <label for="product">Producto</label>
      <select id="product">
        <option value="Barra de kiwicha y cacao" data-price="8">Barra de kiwicha y cacao — S/ 8.00</option>
      </select>
    </div>

    <div class="quantity-row">
      <div class="field" style="margin-bottom:0">
        <label for="quantity">Cantidad</label>
        <p class="hint">Número de barras</p>
      </div>
      <div class="field" style="margin-bottom:0">
        <div class="quantity-control">
          <button type="button" id="minus" aria-label="Disminuir cantidad">−</button>
          <input id="quantity" type="number" min="1" max="99" value="1" inputmode="numeric">
          <button type="button" id="plus" aria-label="Aumentar cantidad">+</button>
        </div>
      </div>
    </div>

    <div class="field" style="margin-top:23px">
      <label for="delivery">¿Cómo deseas recibir tu pedido?</label>
      <select id="delivery">
        <option value="pickup">Recojo en punto de venta — Sin costo</option>
        <option value="delivery">Delivery en Lima — S/ 5.00 por pedido</option>
      </select>
    </div>

    <div class="delivery-note" id="deliveryNote">
      <span class="emoji">📍</span>
      <span>El recojo en punto de venta no tiene costo. Coordina el horario por WhatsApp.</span>
    </div>

    <div class="summary" aria-live="polite">
      <div class="summary-head"><strong>Resumen de tu pedido</strong><span>🧾</span></div>
      <div class="summary-line"><span id="summaryProduct">Barra de kiwicha y cacao × 1</span><strong id="subtotal">S/ 8.00</strong></div>
      <div class="summary-line"><span>Entrega</span><strong id="shipping">S/ 0.00</strong></div>
      <div class="summary-total"><span>Total estimado</span><span class="total" id="total">S/ 8.00</span></div>
    </div>

    <button class="primary" type="button" id="calculate">Calcular mi pedido <span>→</span></button>
    <button class="secondary" type="button" id="send">Enviar pedido por WhatsApp</button>
    <div class="toast" id="toast" role="alert"></div>
  </section>

  <p class="foot">🌾 <strong>Yura Snacks</strong> · Gracias por elegir ingredientes con identidad andina.</p>
</main>

<script>
  // CONFIGURA AQUÍ tu WhatsApp: código de país + número, solo dígitos.
  // Ejemplo de formato para Perú: 51 seguido de tu número.
  const WHATSAPP_NUMBER = "51XXXXXXXXX";
  const DELIVERY_FEE = 5;

  const product = document.getElementById("product");
  const quantity = document.getElementById("quantity");
  const delivery = document.getElementById("delivery");
  const deliveryNote = document.getElementById("deliveryNote");
  const sendButton = document.getElementById("send");
  const toast = document.getElementById("toast");

  let currentTotal = 0;

  const money = value => "S/ " + value.toFixed(2);

  function getQuantity() {
    let value = Number.parseInt(quantity.value, 10);
    if (!Number.isFinite(value) || value < 1) value = 1;
    if (value > 99) value = 99;
    quantity.value = value;
    return value;
  }

  function calculateOrder() {
    const selected = product.options[product.selectedIndex];
    const name = selected.value;
    const price = Number(selected.dataset.price);
    const count = getQuantity();
    const subtotal = price * count;
    const shipping = delivery.value === "delivery" ? DELIVERY_FEE : 0;
    currentTotal = subtotal + shipping;

    document.getElementById("summaryProduct").textContent = name + " × " + count;
    document.getElementById("subtotal").textContent = money(subtotal);
    document.getElementById("shipping").textContent = money(shipping);
    document.getElementById("total").textContent = money(currentTotal);

    deliveryNote.innerHTML = delivery.value === "delivery"
      ? '<span class="emoji">🚚</span><span>El delivery en Lima tiene un costo fijo de <strong>S/ 5.00</strong> por pedido.</span>'
      : '<span class="emoji">📍</span><span>El recojo en punto de venta no tiene costo. Coordina el horario por WhatsApp.</span>';

    sendButton.classList.add("show");
    toast.classList.remove("show");
  }

  document.getElementById("minus").addEventListener("click", () => {
    quantity.value = Math.max(1, getQuantity() - 1);
    calculateOrder();
  });

  document.getElementById("plus").addEventListener("click", () => {
    quantity.value = Math.min(99, getQuantity() + 1);
    calculateOrder();
  });

  [product, quantity, delivery].forEach(element => {
    element.addEventListener("change", calculateOrder);
    element.addEventListener("input", calculateOrder);
  });

  document.getElementById("calculate").addEventListener("click", calculateOrder);

  sendButton.addEventListener("click", () => {
    if (WHATSAPP_NUMBER.includes("X")) {
      toast.textContent = "Antes de enviar, coloca tu número de WhatsApp en la variable WHATSAPP_NUMBER del código.";
      toast.classList.add("show");
      return;
    }

    const selected = product.options[product.selectedIndex];
    const count = getQuantity();
    const shippingText = delivery.value === "delivery"
      ? "Delivery en Lima: S/ 5.00"
      : "Recojo en punto de venta: sin costo";

    const message =
      "¡Hola, Yura Snacks! Quiero realizar este pedido:%0A" +
      "Producto: " + selected.value + "%0A" +
      "Cantidad: " + count + "%0A" +
      shippingText + "%0A" +
      "Total estimado: " + money(currentTotal);

    window.open("https://wa.me/" + WHATSAPP_NUMBER + "?text=" + encodeURIComponent(message), "_blank");
  });

  calculateOrder();
</script>
</body>
</html>
