<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Carrito de Compras</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  
  <style>
    body {
      font-family: Arial, Helvetica, sans-serif;
      background: #f5f5f5;
      margin: 0;
      padding: 0;
    }

    .container {
      max-width: 1000px;
      margin: 40px auto;
      background: #fff;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }

    h1 {
      text-align: center;
      margin-bottom: 20px;
    }

    table {
      width: 100%;
      border-collapse: collapse;
    }

    th, td {
      padding: 12px;
      border-bottom: 1px solid #ddd;
      text-align: center;
    }

    th {
      background: #222;
      color: #fff;
    }

    img {
      width: 60px;
      border-radius: 6px;
    }

    button {
      padding: 8px 14px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-weight: bold;
    }

    .btn-delete {
      background: #dc3545;
      color: white;
    }

    .btn-buy {
      background: #28a745;
      color: white;
    }

    .btn-back {
      background: #007bff;
      color: white;
    }

    .total {
      text-align: right;
      font-size: 22px;
      margin-top: 15px;
      font-weight: bold;
    }

    .actions {
      display: flex;
      justify-content: space-between;
      margin-top: 25px;
      flex-wrap: wrap;
      gap: 10px;
    }
  </style>
</head>

<body>

  <div class="container">
    <h1>🛒 Mi Carrito</h1>

    <table>
      <thead>
        <tr>
          <th>Producto</th>
          <th>Precio</th>
          <th>Cantidad</th>
          <th>Subtotal</th>
          <th>Acción</th>
        </tr>
      </thead>
      <tbody id="cart-body">
      </tbody>
    </table>

    <div class="total">
      Total: $<span id="total">0</span>
    </div>

    <div class="actions">
      <button class="btn-back" onclick="volver()">← Seguir comprando</button>
      <button class="btn-buy" onclick="comprar()">Proceder con la compra</button>
    </div>
  </div>


  <script>
    let carrito = [
      { id: 1, nombre: "Zapatillas Nike", precio: 35000, cantidad: 1 },
      { id: 2, nombre: "Remera Adidas", precio: 12000, cantidad: 2 },
      { id: 3, nombre: "Gorra Puma", precio: 8000, cantidad: 1 }
    ];

    function renderCarrito() {
      const tbody = document.getElementById("cart-body");
      tbody.innerHTML = "";

      carrito.forEach((producto, index) => {
        let subtotal = producto.precio * producto.cantidad;

        tbody.innerHTML += `
          <tr>
            <td>${producto.nombre}</td>
            <td>$${producto.precio}</td>
            <td>${producto.cantidad}</td>
            <td>$${subtotal}</td>
            <td>
              <button class="btn-delete" onclick="eliminar(${index})">
                Eliminar
              </button>
            </td>
          </tr>
        `;
      });

      calcularTotal();
    }

    function calcularTotal() {
      let total = carrito.reduce((acc, prod) => {
        return acc + (prod.precio * prod.cantidad);
      }, 0);

      document.getElementById("total").textContent = total;
    }

    function eliminar(index) {
      carrito.splice(index, 1);
      renderCarrito();
    }

    function comprar() {
      window.location.href = "404.html";
    }

    function volver() {
      window.history.back();
    }

    renderCarrito();
  </script>

</body>
</html>
