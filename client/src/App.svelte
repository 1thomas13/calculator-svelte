<script>
// @ts-nocheck
  import Button from "./components/Button.svelte"
  import History from "./components/History.svelte";

  const OPERATORS = ["/", "*", "-", "+", ".", "%"]
  let result = "0"
  let lastOperation = "0"
  let history = []
  let renderHistory = false

  const changeDisplay = async (value) => {
    if(value === "="){
      try {
        lastOperation = result
        const total = String(eval(result))

        history = [ { operation: result, total }, ...history]
        result = total

        return result
      } catch (error) {
        return result = "error"
      }
    } 
    
    if (result === '0' || result === 'error' || result === undefined) result = ""
    if (value === "CE") return result = "0"
    if (value === "C" || value === "←") return result = result.slice(0, -1)
    if (result === '0' || result === 'err') result = ""

    const valueIsOperator = OPERATORS.some(character => character === value)
    const lastCharacterIsOperator = OPERATORS.some( character => character === result.charAt(result.length-1))

    if (lastCharacterIsOperator && valueIsOperator) return  result 
    
    result = result + value
  }
 
  const viewHistory = async () => { renderHistory = true }

</script>
<div>

  <button on:click={ viewHistory }>View history</button>
  {#if renderHistory === true}
    <History history={ history } />
  {/if}
  <main class="calculator">
    <div class="display">
      <span>{lastOperation}</span>
      {result}
    </div>
    <div class="buttons">
      <Button changeDisplay={changeDisplay} > CE </Button>
      <Button changeDisplay={changeDisplay}> C </Button>
      <Button changeDisplay={changeDisplay}> % </Button>
      <Button changeDisplay={changeDisplay}> / </Button>
      <Button changeDisplay={changeDisplay}> 7 </Button>
      <Button changeDisplay={changeDisplay}> 8 </Button>
      <Button changeDisplay={changeDisplay}> 9 </Button>
      <Button changeDisplay={changeDisplay}> * </Button>
      <Button changeDisplay={changeDisplay}> 4 </Button>
      <Button changeDisplay={changeDisplay}> 5 </Button>
      <Button changeDisplay={changeDisplay}> 6 </Button>
      <Button changeDisplay={changeDisplay}> - </Button>
      <Button changeDisplay={changeDisplay}> 1 </Button>
      <Button changeDisplay={changeDisplay}> 2 </Button>
      <Button changeDisplay={changeDisplay}> 3 </Button>
      <Button changeDisplay={changeDisplay}> + </Button>
      <Button changeDisplay={changeDisplay}> 0 </Button>
      <Button changeDisplay={changeDisplay}> . </Button>
      <Button changeDisplay={changeDisplay}> ← </Button>
      <Button changeDisplay={changeDisplay}> = </Button>
    </div>
  </main>
</div>


<style>
  .display {
    text-align: right;
    height: 70px;
   
    background: #fff;
    font-size: 25px;
    border-radius: 10px;
    background: #faf3fa;
    color: #000;
    padding:  15px;
    font-size: xx-large;
    overflow-x: auto;
    overflow-y: hidden;
    max-width: 330px;
    display: flex;
    flex-direction: column;
  }

  span {
      font-size: 13px;
    }

  .calculator {
   background-color: #fff;
   border-radius: 10px;
   padding-bottom: 10px;
   box-shadow: 3px 2px 25px 10px rgba(0,0,0,0.2);
  -webkit-box-shadow: 3px 2px 25px 10px rgba(0,0,0,0.2);
  -moz-box-shadow: 3px 2px 25px 10px rgba(0,0,0,0.2);
    width: fit-content;
    margin: auto;
  }

  .buttons {
    display: grid;
    flex-wrap: wrap;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    margin: 15px;
  }

  button {
    margin-bottom: 10px;
    cursor: pointer;
    text-transform: uppercase;
    color: #000;
    background-color: #fff;
    border-style: solid;
    border-width: 2px 2px 2px 2px;
    border-radius: 40px 40px 40px 40px;
    padding: 16px 24px;
    transition: 0.2s;
    box-shadow: -2px -1px 8px 0px #ffffff, 2px 1px 8px 0px rgb(95 157 231 / 48%);
  }

  button:hover {
    background-color: #E5EDF5;
  }

</style>
