[preview.html](https://github.com/user-attachments/files/28490931/preview.html)
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Innova Clean Remisiones V3</title>
<style>
body{font-family:Arial,sans-serif;background:#f2f2f2;margin:0;padding:15px}
.box{max-width:1200px;margin:auto;background:#fff;padding:20px;border-radius:10px}
input,select{width:100%;padding:10px;margin:4px 0;box-sizing:border-box}
table{width:100%;border-collapse:collapse}
th,td{border:1px solid #ddd;padding:8px}
th{background:#00A3D7;color:white}
button{padding:12px;margin:4px;border:none;border-radius:6px;cursor:pointer}
.total{font-size:30px;font-weight:bold;color:green}
</style>
</head>
<body>
<div class="box">
<h1>INNOVA CLEAN - REMISIONES V3</h1>

<p><b>Folio:</b> <span id="folio"></span></p>

<input id="cliente" placeholder="Cliente">
<input id="telefono" placeholder="Teléfono">
<input id="direccion" placeholder="Dirección">

<button onclick="guardarCliente()">Guardar Cliente</button>
<select id="clientes" onchange="cargarCliente()">
<option value="">Clientes guardados</option>
</select>

<hr>

<input id="buscar" placeholder="Buscar producto..." onkeyup="filtrarProductos()">
<select id="productos"></select>
<button onclick="agregarProductoCatalogo()">Agregar producto</button>

<table id="tabla">
<tr>
<th>Cant.</th><th>Producto</th><th>P.Unit</th><th>Importe</th><th>X</th>
</tr>
</table>

<p>Descuento:</p>
<input id="descuento" type="number" value="0" oninput="actualizar()">

<p class="total">TOTAL $<span id="total">0.00</span></p>

<button onclick="enviarWhatsapp()">Enviar WhatsApp</button>
<button onclick="window.print()">Imprimir</button>

</div>

<script>
const productos=[
"Cloro","Pino","Mas color","Downy","Salvo","Axion",
"Suave sol","Carisma suavizante","Carisma detergente",
"Zote","Roma","Insecticida","Detercon","Almorol",
"Desengrasante de motor"
];

let folio=parseInt(localStorage.getItem("folioInnovaV3")||"1");
document.getElementById("folio").innerText=String(folio).padStart(6,"0");

function cargarLista(){
let s=document.getElementById("productos");
s.innerHTML="";
productos.forEach(p=>{
let o=document.createElement("option");
o.text=p;
s.add(o);
});
}
cargarLista();

function filtrarProductos(){
let txt=document.getElementById("buscar").value.toLowerCase();
let s=document.getElementById("productos");
s.innerHTML="";
productos.filter(p=>p.toLowerCase().includes(txt)).forEach(p=>{
let o=document.createElement("option");
o.text=p;
s.add(o);
});
}

function agregarProductoCatalogo(){
let prod=document.getElementById("productos").value;
let t=document.getElementById("tabla");
let r=t.insertRow();
r.innerHTML=`
<td><input type="number" value="1" oninput="actualizar()"></td>
<td><input value="${prod}"></td>
<td><input type="number" value="0" oninput="actualizar()"></td>
<td>0.00</td>
<td><button onclick="this.parentNode.parentNode.remove();actualizar()">X</button></td>`;
actualizar();
}

function actualizar(){
let t=document.getElementById("tabla");
let subtotal=0;
for(let i=1;i<t.rows.length;i++){
let c=parseFloat(t.rows[i].cells[0].children[0].value)||0;
let p=parseFloat(t.rows[i].cells[2].children[0].value)||0;
let imp=c*p;
t.rows[i].cells[3].innerText=imp.toFixed(2);
subtotal+=imp;
}
let desc=parseFloat(document.getElementById("descuento").value)||0;
document.getElementById("total").innerText=(subtotal-desc).toFixed(2);
}

function guardarCliente(){
let data={
nombre:cliente.value,
telefono:telefono.value,
direccion:direccion.value
};
localStorage.setItem("cliente_"+data.nombre,JSON.stringify(data));
cargarClientes();
alert("Cliente guardado");
}

function cargarClientes(){
let s=document.getElementById("clientes");
s.innerHTML='<option value="">Clientes guardados</option>';
for(let k in localStorage){
if(k.startsWith("cliente_")){
let o=document.createElement("option");
o.value=k;
o.text=k.replace("cliente_","");
s.add(o);
}
}
}
cargarClientes();

function cargarCliente(){
let k=document.getElementById("clientes").value;
if(!k)return;
let d=JSON.parse(localStorage.getItem(k));
cliente.value=d.nombre;
telefono.value=d.telefono;
direccion.value=d.direccion;
}

function enviarWhatsapp(){
let texto="*INNOVA CLEAN*%0A";
texto+="Remisión "+document.getElementById("folio").innerText+"%0A";
texto+="Cliente: "+cliente.value+"%0A%0A";

let t=document.getElementById("tabla");
for(let i=1;i<t.rows.length;i++){
texto+=t.rows[i].cells[0].children[0].value+" x ";
texto+=t.rows[i].cells[1].children[0].value+" - $";
texto+=t.rows[i].cells[3].innerText+"%0A";
}

texto+="%0ATOTAL: $"+document.getElementById("total").innerText;
window.open("https://wa.me/?text="+texto,"_blank");
}
</script>
</body>
</html>
