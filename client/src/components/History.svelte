<script>
  export let history = []
</script>

<div>
  {#if history.length === 0}
    <h4 >
      No se encontraron operaciones...
    </h4>
  {:else}
    <table>
      <thead>
      <tr>
        <th> Operacion </th>
        <th> Resultado </th>
      </tr>
      </thead>
      <tbody>
        {#each history as operation}
          <tr>     
            <td>{ operation.operation } </td>
            <td><span> { operation.total }</span></td>
          </tr>
        {/each}
      </tbody>
    </table>
  {/if}
</div>

<style>
  div {
    padding: 0;
    background: #f3f0fa;
    color: #222;
    border-radius: 20px;
    padding: 4px 24px 4px 4px;
    display: flex;
    margin: 10px auto;
    justify-content: space-evenly;
    box-shadow: 3px 2px 25px 10px rgba(0,0,0,0.2);
    -webkit-box-shadow: 3px 2px 25px 10px rgba(0,0,0,0.2);
    -moz-box-shadow: 3px 2px 25px 10px rgba(0,0,0,0.2);
    max-height: 50vh;
    overflow-y: auto;
    overflow-x: auto
  }

  table {
    border-collapse: separate;
    border-spacing: 0;
  }

  tbody tr:nth-child(odd) {
    background-color: #f1e6f8;
  }

  th, td {
    padding: 0.75rem;
    font-size: 0.9375rem;
  }

  th { 
    font-weight: 700;
    background: #f3f0fa;
    position: sticky;
    top: 0;
  }

  span {
    color: #000;
    font-weight: 300;
  }
</style>