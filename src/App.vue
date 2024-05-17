<template>
  <div class="Padrre">
    <div class="Hijo">
      <div
        class="modal fade"
        id="exampleModal"
        tabindex="-1"
        aria-labelledby="exampleModalLabel"
        aria-hidden="true"
      >
        <div class="modal-dialog">
          <div class="modal-content">
            <div class="modal-header">
              <h1 class="modal-title fs-5" id="exampleModalLabel">
                Formulario
              </h1>
              <button
                type="button"
                class="btn-close"
                data-bs-dismiss="modal"
                aria-label="Close"
              ></button>
            </div>
            <div class="modal-body">
              <div class="divForm1">
                <div class="divName divInput">
                  <label for="name">Digite el nombre del producto</label>
                  <input type="text" id="name" v-model="nombre" />
                </div>
                <div class="divPrice divInput">
                  <label for="lastName">Digite el precio</label>
                  <input type="text" id="precio" v-model.number="precio" />
                </div>
                <div class="divCost divInput">
                  <label for="birthdate">Digite el costo</label>
                  <input type="text" id="costo" v-model.number="costo" />
                </div>
                <div class="divInput">
                  <label for="birthdate">Digite el nombre del proveedor</label>
                  <input type="text" id="proveedor" v-model="proveedor" />
                </div>
              </div>

              <div class="divForm2"></div>
              <div class="modal-footer">
                <div class="divButton divInput">
                  <button @click="validacion()">Agregar</button>
                </div>
                <button
                  type="button"
                  class="btn btn-secondary"
                  data-bs-dismiss="modal"
                >
                  Close
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
      <button
          type="button"
          class="btnmodalAGG btn btn-primary"
          data-bs-toggle="modal"
          data-bs-target="#exampleModal"
        >
          Agregar Productos
        </button>
      <div class="divTable">
        
        <div class="TablaPRODS">
          <table>
          <thead>
            <tr>
              <th>Producto</th>
              <th>Precio</th>
              <th>Costo</th>
              <th>Cantidad</th>
              <th>Proveedor</th>
              <th>+/- cantidad</th>
              <th>Ganancias</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(producto, i) in productos" :key="i">
              <td>{{ producto.nombre }}</td>
              <td>{{ producto.precio }}</td>
              <td>{{ producto.costo }}</td>
              <td>{{ producto.cantidad }}</td>
              <td>{{ producto.proveedor }}</td>
              <td>
                <div>
                  <button @click="aumentarCant(producto)">
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      x="0px"
                      y="0px"
                      width="50"
                      height="48"
                      viewBox="0 0 48 48"
                    >
                      <path
                        fill="#4caf50"
                        d="M44,24c0,11.045-8.955,20-20,20S4,35.045,4,24S12.955,4,24,4S44,12.955,44,24z"
                      ></path>
                      <path fill="#fff" d="M21,14h6v20h-6V14z"></path>
                      <path fill="#fff" d="M14,21h20v6H14V21z"></path>
                    </svg>
                  </button>
                  <button @click="disminuirCant(producto)">
                    <img
                      src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAwCAYAAABXAvmHAAAACXBIWXMAAAsTAAALEwEAmpwYAAACb0lEQVR4nO1ZzW7TQBBeAeXAEcqJwluAyokXqFQ8mxV/99xbdSaBi29t7xQVxCMg4ADlwgv0StU+ANAT/RG0O1bSi6tJqiAajO2s43WQP2mkSLbj71uPZ78ZK1WjRg1nxMZcjMzSXavxmQV8y0A7DHhogU4k5DcDbssxOYcDmo3D8ILyjWh+8SYDrVqgXdYU5wmr8TtrXOGAZkonfmSeXmdNryxgNy/xISGAXQu0fvRocboU8sfQesxAB67EhwP3owY9HBvxuNmcYqDXxROn80/kpdyrWPJz4RUG/DRu8vw7NuSeBa58qeTjs/gcm/Cys4Ay0oYT04nWncgfN/CJL/J8FhHgg5HI/7rfvsZAe74FMNDBSCVW6rx38nqQSi/ykQ9opohNqjgB2I1M61Z2AUCrvknzUOBKJvJisvo+xTdhOp9Gu2IaUwWIq/RNlpPC0J1UAT2765uoTnoKrXYGAfQu6Q9ONndKCU4SoPFNqgBpPKoqgAG3MghItsr+BdBeegr9o/77FmA1df5/ATzpKcST/hLbSS+jtsobmcZWegoFNOubKCdF0L6d0czRt8qtPuDXzNO83sSsAqT5j8DlTOQr2dBo6rBZuKHyQCYC1RGAz1Ve/DQLVyvR1GvcH3luKrNK3wKiBhrlAplVeksdwDXlCulDrab3HlLnY3wvvOQsYDDc1bRRGnmgD4UNdwcims2pMiqTBVwrbOX/BplVjqU6Af5wfmHzzE1l3NfbYFxXXFNH6ryUbVU2ZHcU2zGKd+pfg8u5d9hxQEyWDJ1kbiOeXRoP6ez6H/Cw2+vygL7IMbHE4ior8Zm1Rg01+TgFI5yW29LO/hIAAAAASUVORK5CYII="
                    />
                  </button>
                </div>
              </td>
              <td>{{ producto.ganancias }}</td>
            </tr>
          </tbody>
        </table>
        </div>
        

        <div class="Totales">
          <h3>
            Total de ganancias:
            {{ totalGanancias }}
          </h3>

          <h3>
            Total de precios:
            {{ totalPrecios }}
          </h3>

          <h3>
            Total de costos:
            {{ totalCostos }}
          </h3>
        </div>
      </div>
    </div>
  </div>
</template>


<style>
body {
  width: 100%;
  font-family: "Kanit", sans-serif;
  margin: 0;
  padding: 0;
  background-color: black !important;
}

h3 {
  color: white;
}

.Padrre {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100vw;
}

.btnmodalAGG {
  position: fixed;
  top: 0;
  right: 0;
}
.Hijo {
  display: flex;
  justify-content: center;
  align-items: center;
}

.divForm {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-right: 20px;
}

.divForm1 {
  display: flex;
  flex-direction: column;
  justify-content: left;
  align-items: center;
  border: 3px solid#45a049;
  color: black;
  background-color: white;
  border-radius: 5px;
}

.divForm2 {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.divInput {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin: 10px;
}

.divInput input:hover {
  background-color: #45a049;
  box-shadow: 2px 2px 2px 2px #8ee992;
}

.divForm1:hover {
  box-shadow: 4px 4px 4px 4px #45a049;
}

.divTable {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 90vw;
}

.TablaPRODS{
  justify-content: center;
  margin: 0 auto;
  width: 100%;
  padding: 20px;
  border: 3px solid #45a049;
  color: white;
  background-color: #45a049;
  border-radius: 5px;
}

.Totales{
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  padding: 20px;
  border: 3px solid #45a049;
  color: white;
  background-color: #45a049;
  border-radius: 5px;
  display: flex;
  justify-content: space-around;
}

.btn {
  background-color: #4caf50;
  color: white;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
}

#app{
  width: 100%;
  margin: 0;
  padding: 0;
}

.btn:hover {
  background-color: #45a049;
}

table {
  border-collapse: collapse;
  width: 100%;
}

th {
  background-color: #4caf50;
  color: white;
}

th,
td {
  color: white;
  border: 1px solid #ddd;
  text-align: left;
  padding: 8px;
}
</style>



<script setup>
import { ref, computed } from "vue";

const nombre = ref("");
const precio = ref(0);
const costo = ref(0);
const proveedor = ref("");
const productos = ref([]);

const totalGanancias = computed(() => {
  return productos.value.reduce((acc, producto) => acc + producto.ganancias, 0);
});

const totalPrecios = computed(() => {
  return productos.value.reduce(
    (acc, producto) => acc + producto.precio * producto.cantidad,
    0
  );
});

const totalCostos = computed(() => {
  return productos.value.reduce(
    (acc, producto) => acc + producto.costo * producto.cantidad,
    0
  );
});

const validacion = () => {
  if (
    nombre.value === "" ||
    precio.value === 0 ||
    costo.value === 0 ||
    proveedor.value === ""
  ) {
    Swal.fire({
      title: "ALERTAA!",
      text: "Llene todos los campos con cariño",
      icon: "error",
    });
  } else {
    productos.value.push({
      nombre: nombre.value,
      precio: precio.value,
      costo: costo.value,
      cantidad: 0,
      proveedor: proveedor.value,
      ganancias: 0,
    });
    nombre.value = "";
    precio.value = 0;
    costo.value = 0;
    proveedor.value = "";
  }
};

const aumentarCant = (producto) => {
  producto.cantidad++;
  producto.ganancias =
    producto.precio * producto.cantidad - producto.costo * producto.cantidad;
};

const disminuirCant = (producto) => {
  if (producto.cantidad > 0) {
    producto.cantidad--;
    producto.ganancias =
      producto.precio * producto.cantidad - producto.costo * producto.cantidad;
  }
};
</script>