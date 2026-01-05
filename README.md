<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Pañalera J&J - Catálogo Oficial</title>
    <link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;700;800;900&family=Quicksand:wght@500;700&display=swap" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/PapaParse/5.3.2/papaparse.min.js"></script>

    <style>
        :root { --primary: #007bff; --success: #25D366; --bg: #f7f9fc; --white: #ffffff; --red: #dc3545; --dark: #2c3e50; }
        * { box-sizing: border-box; -webkit-tap-highlight-color: transparent; }
        body { margin: 0; font-family: 'Quicksand', sans-serif; background-color: var(--bg); padding-bottom: 90px; overflow-x: hidden; }
        
        /* BARRA SUPERIOR MOTO */
        .top-bar { background: #f8d7da; height: 40px; overflow: hidden; position: relative; display: flex; align-items: center; border-bottom: 1px solid #f5c6cb; }
        .moto-repartidor { position: absolute; white-space: nowrap; font-weight: 900; color: var(--red); font-size: 14px; animation: motoMove 15s linear infinite; }
        @keyframes motoMove { from { left: -100%; } to { left: 100%; } }

        /* HEADER */
        header { background: var(--white); padding: 10px 20px; display: flex; align-items: center; justify-content: space-between; position: sticky; top: 0; z-index: 1000; box-shadow: 0 2px 10px rgba(0,0,0,0.1); gap: 15px; }
        .header-title { font-family: 'Nunito', sans-serif; font-size: 24px; font-weight: 900; color: var(--primary); text-transform: uppercase; cursor: pointer; }
        .search-container { flex-grow: 1; max-width: 600px; }
        .search-container input { width: 100%; padding: 10px 15px; border: 2.5px solid #000; border-radius: 25px; outline: none; font-weight: 800; font-family: 'Quicksand'; }
        .cart-trigger { background: var(--primary); border: none; color: white; padding: 10px 15px; border-radius: 20px; font-weight: 800; cursor: pointer; }

        /* CINTA CATEGORÍAS */
        .cinta-categorias { width: 100%; height: 2cm; background-color: var(--primary); display: flex; align-items: center; justify-content: center; gap: 30px; overflow-x: auto; padding: 0 20px; white-space: nowrap; }
        .cinta-categorias span { color: white; font-weight: 900; text-transform: uppercase; cursor: pointer; font-size: 14px; }

        /* SECCIÓN OFERTAS DINÁMICAS (HOME) */
        #home-ofertas { max-width: 800px; margin: 20px auto; height: 350px; position: relative; display: flex; align-items: center; justify-content: center; }
        .oferta-slide { position: absolute; width: 100%; opacity: 0; transition: opacity 0.8s ease-in-out; text-align: center; display: flex; flex-direction: column; align-items: center; }
        .oferta-slide.active { opacity: 1; z-index: 10; }
        .oferta-img { height: 220px; object-fit: contain; margin-bottom: 10px; }
        
        /* CARTEL DE PRECIO LLAMATIVO */
        .precio-tag { background: var(--red); color: white; padding: 10px 25px; border-radius: 50px; font-size: 32px; font-weight: 900; box-shadow: 0 4px 15px rgba(220, 53, 69, 0.4); transform: rotate(-3deg); margin-top: 10px; }
        .oferta-nombre { font-size: 20px; font-weight: 900; color: var(--dark); margin: 0; }

        /* CINTAS DE INFORMACIÓN */
        .cinta-titulo-info { width: 100%; background: var(--primary); color: white; height: 1.2cm; display: flex; align-items: center; justify-content: center; font-weight: 900; text-transform: uppercase; letter-spacing: 2px; margin-top: 40px; }
        .cinta-info-detalle { background: var(--dark); color: white; padding: 25px 0; display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); text-align: center; }
        .info-col { padding: 15px; border-right: 1px solid #455a64; }
        .info-col:last-child { border-right: none; }
        .info-col h5 { margin: 0 0 8px; color: #ffccbc; font-weight: 900; text-transform: uppercase; }
        .info-col p { margin: 0; font-size: 13px; font-weight: 700; line-height: 1.5; }

        /* CATÁLOGO (OCULTO EN HOME) */
        .catalogo { display: none; grid-template-columns: repeat(auto-fill, minmax(220px, 1fr)); gap: 15px; padding: 15px; max-width: 1200px; margin: 0 auto; }
        .producto { background: white; border-radius: 15px; padding: 15px; border: 1px solid #eee; text-align: center; display: flex; flex-direction: column; min-height: 420px; box-shadow: 0 2px 5px rgba(0,0,0,0.05); }
        .img-box { height: 180px; display: flex; align-items: center; justify-content: center; }
        .img-box img { max-width: 100%; max-height: 100%; object-fit: contain; }

        /* MODALES */
        .modal-jj { display:none; position:fixed; top:0; left:0; width:100%; height:100dvh; background:rgba(0,0,0,0.8); z-index:10000; justify-content:center; align-items:center; }
        .modal-jj-content { background:white; padding:25px; border-radius:15px; width:92%; max-width:450px; text-align: center; }
        .input-jj { width: 100%; padding: 12px; margin-top: 10px; border: 2.2px solid #000; border-radius: 12px; font-weight: 800; }
    </style>
</head>
<body>

<div class="top-bar">
    <div class="moto-repartidor">🛵📦 ¡ENVÍOS EN EL DÍA! Recibimos pedidos hasta las 13hs de Lunes a Viernes 📦🛵</div>
</div>

<header>
    <div class="header-title" onclick="resetPagina()">PAÑALERA J&J</div>
    <div class="search-container">
        <input type="text" id="buscador" onkeyup="filtrar()" placeholder="🔍 ¿Qué estás buscando?">
    </div>
    <button class="cart-trigger" onclick="abrirCarrito()">🛒 (<span id="cartCount">0</span>)</button>
</header>

<nav class="cinta-categorias">
    <span onclick="seleccionarCategoria('PAÑALES')">PAÑALES</span>
    <span onclick="seleccionarCategoria('LECHES INFANTILES')">LECHES</span>
    <span onclick="seleccionarCategoria('ALIMENTACION')">ALIMENTACIÓN</span>
    <span onclick="seleccionarCategoria('ARTICULOS DE BAÑO')">BAÑO</span>
    <span onclick="seleccionarCategoria('MATERNIDAD')">MATERNIDAD</span>
    <span onclick="seleccionarCategoria('LACTANCIA')">LACTANCIA</span>
    <span onclick="seleccionarCategoria('ADULTOS')">ADULTOS</span>
</nav>

<div id="home-ofertas">
    <p id="loading-home">Cargando ofertas destacadas...</p>
</div>

<div id="catalogo" class="catalogo"></div>

<div class="cinta-titulo-info">Información</div>
<section class="cinta-info-detalle">
    <div class="info-col">
        <h5>💳 Medios de Pago</h5>
        <p>Efectivo, Transferencia,<br>Débito y Cuenta DNI</p>
    </div>
    <div class="info-col">
        <h5>🚚 Envíos y Reparto</h5>
        <p>Lunes a Sábados.<br>CABA y Gran Buenos Aires</p>
    </div>
    <div class="info-col">
        <h5>🕒 Horarios</h5>
        <p>Lun-Sáb: 09:00 a 20:30<br>Dom: 10:00 a 13:00</p>
    </div>
    <div class="info-col">
        <h5>📍 Ubicación</h5>
        <p>Craviotto 2240, Quilmes</p>
        <button onclick="window.open('https://www.google.com/maps?q=Craviotto+2240,+Quilmes')" style="background:var(--success); color:white; border:none; padding:5px 10px; border-radius:5px; margin-top:8px; cursor:pointer; font-weight:bold; font-size:11px;">COMO LLEGAR</button>
    </div>
</section>

<div id="modalCart" class="modal-jj"><div class="modal-jj-content"><h2 style="margin-top:0; font-weight:900;">🛍️ Mi Pedido</h2><div id="cartItems" style="text-align:left;"></div><div style="display:flex; justify-content:space-between; font-weight:900; font-size:20px; margin-top:15px; border-top:2px solid #eee; padding-top:10px;"><span>TOTAL:</span><span id="cartTotal">$0</span></div><button onclick="irAFinalizar()" style="background:var(--success); color:white; border:none; padding:15px; border-radius:50px; font-weight:900; width:100%; margin-top:15px; cursor:pointer;">CONTINUAR</button><button onclick="cerrarCarrito()" style="width:100%; border:none; background:none; color:gray; margin-top:10px; cursor:pointer;">Cerrar</button></div></div>

<div id="modalFinal" class="modal-jj"><div class="modal-jj-content"><h3 style="margin-top:0; font-weight:900;">Finalizar Pedido</h3><input type="text" id="nomJJ" class="input-jj" placeholder="Nombre y Apellido"><input type="tel" id="telJJ" class="input-jj" placeholder="WhatsApp"><select id="zonaJJ" class="input-jj" onchange="actualizarTotalFinal()"><option value="0">🏠 Retiro por Local - GRATIS</option><option value="3700">Envío Quilmes ($3.700)</option><option value="4200">Envío Zona Sur ($4.200)</option><option value="4800">Envío CABA ($4.800)</option><option value="5700">Envío La Plata ($5.700)</option><option value="6200">Envío Zona Norte/Oeste ($6.200)</option></select><div id="divDir" style="display:none;"><input type="text" id="calleJJ" class="input-jj" placeholder="Calle y número"><input type="text" id="entreJJ" class="input-jj" placeholder="Entre calles (OBLIGATORIO)" style="border-color:orange;"><input type="text" id="locJJ" class="input-jj" placeholder="Localidad"></div><div id="resumenFinal" style="margin-top:15px; padding:15px; background:#e3f2fd; border-radius:15px; font-weight:900;">TOTAL: <span id="totalConEnvio">$0</span></div><button onclick="enviarWhatsApp()" style="background:var(--success); color:white; border:none; padding:15px; border-radius:50px; font-weight:900; width:100%; margin-top:15px; cursor:pointer;">PEDIR POR WHATSAPP ✅</button></div></div>

<script>
const LINK_EXCEL = 'https://docs.google.com/spreadsheets/d/e/2PACX-1vStiiqXwfXZUBNq_1y15bpdQXZFax-_1xxuuNDn6aTl4QRcyHpAj-7duQmh4SNgz5VMBJa__bm9EQJH/pub?gid=0&single=true&output=csv';
let productos = [];
let carrito = [];
let currentIndex = 0;

function normalizar(t) { return t.normalize("NFD").replace(/[\u0300-\u036f]/g, "").toLowerCase(); }

function limpiarPrecio(val) {
    if (!val) return 0;
    let str = String(val).replace(/\$/g, '').replace(/\s/g, '').replace(/\./g, '').trim();
    return parseInt(str) || 0;
}

function cargar() {
    Papa.parse(LINK_EXCEL, {
        download: true, header: true,
        transformHeader: h => h.toLowerCase().trim().replace(/\s+/g, ''),
        complete: function(r) {
            productos = r.data.map((p, i) => ({
                id: i,
                nombre: p.nombre || p.articulo || "Producto",
                categoria: (p.categoria || "VARIOS").toUpperCase().trim(),
                marca: p.marca || "",
                imagen: p.imagen || p.foto || p.url || "",
                p1: limpiarPrecio(p.precio1), p2: limpiarPrecio(p.precio2), p3: limpiarPrecio(p.precio3), p4: limpiarPrecio(p.precio4),
                oferta: String(p.oferta).toLowerCase() === 'true' || String(p.destacado).toLowerCase() === 'true'
            })).filter(p => p.p1 > 0);
            
            iniciarHome();
        }
    });
}

function iniciarHome() {
    const container = document.getElementById('home-ofertas');
    const destacados = productos.filter(p => p.oferta).slice(0, 5);
    
    if (destacados.length === 0) {
        container.innerHTML = "<p>¡Bienvenidos a Pañalera J&J!</p>";
        return;
    }

    container.innerHTML = destacados.map((p, i) => `
        <div class="oferta-slide ${i === 0 ? 'active' : ''}" id="slide-${i}">
            <h4 class="oferta-nombre">${p.nombre}</h4>
            <img src="${p.imagen}" class="oferta-img" onerror="this.src='https://via.placeholder.com/300'">
            <div class="precio-tag">$${p.p1.toLocaleString('es-AR')}</div>
            <button onclick="agregar(${p.id}, true)" style="background:var(--success); color:white; border:none; padding:10px 20px; border-radius:20px; font-weight:bold; margin-top:15px; cursor:pointer;">¡LO QUIERO! 🛒</button>
        </div>
    `).join('');

    setInterval(() => {
        document.getElementById(`slide-${currentIndex}`).classList.remove('active');
        currentIndex = (currentIndex + 1) % destacados.length;
        document.getElementById(`slide-${currentIndex}`).classList.add('active');
    }, 2000);
}

function filtrar() {
    const bus = normalizar(document.getElementById('buscador').value);
    const cat = document.getElementById('filtroCategoria') ? document.getElementById('filtroCategoria').value : 'TODOS';
    const isSearching = bus.length > 0;
    
    document.getElementById('home-ofertas').style.display = isSearching ? 'none' : 'flex';
    document.getElementById('catalogo').style.display = isSearching ? 'grid' : 'none';

    if (isSearching) {
        let html = "";
        productos.forEach(p => {
            const textoProd = normalizar(p.nombre + " " + p.marca + " " + p.categoria);
            if (textoProd.includes(bus)) {
                html += `
                <div class="producto">
                    <div class="img-box"><img src="${p.imagen}" onerror="this.src='https://via.placeholder.com/200'"></div>
                    <div style="color:var(--primary); font-size:12px; font-weight:900;">${p.marca}</div>
                    <div style="font-weight:900; height:40px; overflow:hidden; margin-bottom:10px;">${p.nombre}</div>
                    <div style="margin-top:auto;">
                        <select id="sel-${p.id}" style="width:100%; padding:8px; border-radius:10px; margin-bottom:8px; font-weight:bold;">
                            <option value="${p.p1}|1 und">precio x 1 und: $${p.p1.toLocaleString('es-AR')}</option>
                            ${p.p2 > 0 ? `<option value="${p.p2}|2 und">precio x 2 und: $${p.p2.toLocaleString('es-AR')}</option>` : ''}
                        </select>
                        <button class="btn-green" style="padding:10px; margin:0; background:var(--success); color:white; border:none; width:100%; border-radius:10px; cursor:pointer; font-weight:bold;" onclick="agregar(${p.id})">AÑADIR 🛒</button>
                    </div>
                </div>`;
            }
        });
        document.getElementById('catalogo').innerHTML = html || "<p style='grid-column:1/-1;'>Sin resultados</p>";
    }
}

function seleccionarCategoria(c) {
    document.getElementById('buscador').value = c;
    filtrar();
    window.scrollTo({ top: 0, behavior: 'smooth' });
}

function resetPagina() { location.reload(); }

function agregar(id, deHome = false) {
    const p = productos.find(x => x.id === id);
    let precio = p.p1;
    let label = "1 und";
    if (!deHome) {
        const val = document.getElementById(`sel-${id}`).value.split('|');
        precio = parseInt(val[0]);
        label = val[1];
    }
    carrito.push({ nom: p.nombre, pre: precio, lab: label });
    document.getElementById('cartCount').innerText = carrito.length;
    actualizarCartUI();
    abrirCarrito();
}

function actualizarCartUI() {
    const cont = document.getElementById('cartItems');
    let t = 0; cont.innerHTML = "";
    carrito.forEach((item, i) => {
        t += item.pre;
        cont.innerHTML += `<div style="display:flex; justify-content:space-between; margin-bottom:10px; border-bottom:1px solid #eee; padding-bottom:5px;"><div><b>${item.nom}</b><br>$${item.pre.toLocaleString('es-AR')}</div><button onclick="carrito.splice(${i},1); actualizarCartUI(); document.getElementById('cartCount').innerText = carrito.length;" style="border:none; color:red; background:none; font-size:20px; cursor:pointer;">✕</button></div>`;
    });
    document.getElementById('cartTotal').innerText = "$" + t.toLocaleString('es-AR');
}

function abrirCarrito() { document.getElementById('modalCart').style.display = 'flex'; }
function cerrarCarrito() { document.getElementById('modalCart').style.display = 'none'; }
function irAFinalizar() { if(carrito.length===0) return; cerrarCarrito(); document.getElementById('modalFinal').style.display = 'flex'; actualizarTotalFinal(); }
function actualizarTotalFinal() { const envio = parseInt(document.getElementById('zonaJJ').value); const sub = carrito.reduce((s, i) => s + i.pre, 0); document.getElementById('divDir').style.display = envio > 0 ? 'block' : 'none'; document.getElementById('totalConEnvio').innerText = "$" + (sub + envio).toLocaleString('es-AR'); }
function enviarWhatsApp() { const nom = document.getElementById('nomJJ').value; const tel = document.getElementById('telJJ').value; const zona = document.getElementById('zonaJJ').options[document.getElementById('zonaJJ').selectedIndex].text; if(!nom || !tel) return alert("Completa tus datos."); let m = `¡Hola J&J! Mi pedido:\n\n`; carrito.forEach(i => m += `▪️ ${i.nom} ($${i.pre.toLocaleString('es-AR')})\n`); m += `\n👤 Cliente: ${nom}\n🏠 Entrega: ${zona}`; window.open(`https://wa.me/5491159362317?text=${encodeURIComponent(m)}`); }

window.onload = cargar;
</script>
</body>
</html>
