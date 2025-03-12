<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Registro de Vehículos</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            padding: 20px;
            background-color: #f4f4f4;
        }
        .container {
            max-width: 500px;
            margin: auto;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        input, select, button {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            background-color: #28a745;
            color: white;
            cursor: pointer;
        }
        button:hover {
            background-color: #218838;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }
        th, td {
            border: 1px solid #ddd;
            padding: 8px;
            text-align: center;
        }
        th {
            background-color: #007bff;
            color: white;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>Registro de Vehículos</h2>
    <form id="carForm">
        <label>Modelo del carro:</label>
        <input type="text" id="modelo" required>

        <label>Año:</label>
        <input type="number" id="anio" min="1900" max="2025" required>

        <label>Kilometraje:</label>
        <input type="number" id="kilometraje" required>

        <label>Tipo de combustible:</label>
        <select id="combustible" required>
            <option value="Gasolina">Gasolina</option>
            <option value="Diésel">Diésel</option>
            <option value="Eléctrico">Eléctrico</option>
            <option value="Híbrido">Híbrido</option>
        </select>

        <button type="button" onclick="agregarVehiculo()">Agregar</button>
    </form>

    <h3>Lista de Vehículos</h3>
    <table>
        <thead>
            <tr>
                <th>Modelo</th>
                <th>Año</th>
                <th>Kilometraje</th>
                <th>Combustible</th>
                <th>Eliminar</th>
            </tr>
        </thead>
        <tbody id="listaVehiculos"></tbody>
    </table>
</div>

<script>
    function agregarVehiculo() {
        let modelo = document.getElementById("modelo").value;
        let anio = document.getElementById("anio").value;
        let kilometraje = document.getElementById("kilometraje").value;
        let combustible = document.getElementById("combustible").value;

        if (modelo && anio && kilometraje && combustible) {
            let tabla = document.getElementById("listaVehiculos");
            let fila = tabla.insertRow();
            fila.insertCell(0).textContent = modelo;
            fila.insertCell(1).textContent = anio;
            fila.insertCell(2).textContent = kilometraje;
            fila.insertCell(3).textContent = combustible;
            
            let botonEliminar = document.createElement("button");
            botonEliminar.textContent = "❌";
            botonEliminar.style.background = "red";
            botonEliminar.style.color = "white";
            botonEliminar.style.border = "none";
            botonEliminar.style.padding = "5px";
            botonEliminar.style.cursor = "pointer";
            botonEliminar.onclick = function () {
                fila.remove();
            };

            fila.insertCell(4).appendChild(botonEliminar);

            document.getElementById("carForm").reset();
        } else {
            alert("Por favor, completa todos los campos.");
        }
    }
</script>

</body>
</html>
