<script>
    import * as d3 from "d3"
  
    let numbers = [10, 25, 33, 62, 75, 100]
  
    function arcGenerator({startAngle, endAngle, innerRadius, outerRadius}) {
      return d3.arc()({
        startAngle,
        endAngle,
        innerRadius,
        outerRadius,
      })
    }
  </script>
  
  <main> 
    <div class="contenedor_maestro">
      <h3 class="headline">Visualización de Baterías</h3>
  
      <!-- Contenedor para los arcos -->
      <div class="baterias_container">
        {#each numbers as n}
          <div class="baterias_wrapper">
            <svg width="200" height="200">
              <!-- ARCO GRIS -->
              <path
                d={arcGenerator({
                  startAngle: 0,
                  endAngle: 2 * Math.PI,
                  innerRadius: 80,
                  outerRadius: 100,
                })}
                fill="#ccc"
                transform="translate(100, 100)"
              />
              <!-- ARCOS CON COLORES -->
              {#if n === 10}
                <path
                  d={arcGenerator({
                    startAngle: 0,
                    endAngle: (n / 100) * 2 * Math.PI,
                    innerRadius: 80,
                    outerRadius: 100,
                  })}
                  fill="red"
                  transform="translate(100, 100)"
                />
                <image
                  href="./images/rayorojo.svg"
                  width="140"
                  height="140"
                  x="30"  
                  y="30"  
                />
              {:else if n === 25 || n === 33}
                <path
                  d={arcGenerator({
                    startAngle: 0,
                    endAngle: (n / 100) * 2 * Math.PI,
                    innerRadius: 80,
                    outerRadius: 100,
                  })}
                  fill="orange"
                  transform="translate(100, 100)"
                />
                <image
                  href="./images/rayonaranja.svg"
                  width="140"
                  height="140"
                  x="30"  
                  y="30"  
                />
              {:else}
                <path
                  d={arcGenerator({
                    startAngle: 0,
                    endAngle: (n / 100) * 2 * Math.PI,
                    innerRadius: 80,
                    outerRadius: 100,
                  })}
                  fill="green"
                  transform="translate(100, 100)"
                />
                <image
                  href="./images/rayoverde.svg"
                  width="140"
                  height="140"
                  x="30"  
                  y="30"  
                />
              {/if}
            </svg>
            <p class="number">{n}</p>
          </div>
        {/each}
      </div>
    </div>  
  </main>
  
  <style>
  
    .contenedor_maestro {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      margin-top: -300px; /* Desplazamiento hacia arriba */
    }
  
    .baterias_container {
      display: flex;
      gap: 20px;
    }
  
    .number {
      text-align: center;
      margin-top: 10px;
    }
  
    .headline {
      margin-top: 100px; /* Agrega la unidad de medida, por ejemplo, píxeles */
      font-size: 50px;
      text-align: center;
    }
  </style>
  