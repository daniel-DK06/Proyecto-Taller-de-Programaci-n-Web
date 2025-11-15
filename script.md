document.addEventListener('DOMContentLoaded', () => {
    const botonesComprar = document.querySelectorAll('.btn-comprar');

    botonesComprar.forEach((button) => {
        button.addEventListener('click', (event) => {

            const nombreProducto = event.target.getAttribute('data-nombre');
            const precioProducto = event.target.getAttribute('data-precio');

            let respuesta = confirm(`¿Estás seguro de que deseas comprar el producto: ${nombreProducto}?`);

            if (respuesta) {


                console.log(`✅ Producto '${nombreProducto}' confirmado.`); 

                const productoSeleccionado = {
                    nombre: nombreProducto,
                    precio: parseFloat(precioProducto),
                    cantidad: 1
                };

                localStorage.setItem('productoPedido', JSON.stringify(productoSeleccionado));

                window.location.href = 'pago.html';

            } else {

                console.log("❌ Compra cancelada por el usuario.");
                
                event.preventDefault(); 
            }
        });
    });
});
