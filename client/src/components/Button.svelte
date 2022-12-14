<script>
// @ts-nocheck

  export let changeDisplay


</script>
  
<button on:click={ (e) => changeDisplay(e.target.innerText) }>
  <slot></slot>
</button>

<style>
  button {
    border-radius: 1000000px;
    border: none;
    width: 80px;
    height: 80px;
    text-align: center;
    font-size: 20px;
    cursor: pointer;
    background: #fcf1fc;
    color: black;
    margin: 2px;
  }

  button:hover{
   transition: 0.2s;
   background: #f3f3f3;
  }

  button:active{
   transition: 0.2s;
   background: #ddd;
 }
</style>