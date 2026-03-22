<script>
  let display = "0";
  let valorAnterior = 0;
  let operacaoAtiva = "";
  let limparProximo = false;

  function digitar(num) {
    if (display === "0" || limparProximo) {
      display = num.toString();
      limparProximo = false;
    } else {
      display += num.toString();
    }
  }

  function setOperacao(op) {
    valorAnterior = parseInt(display);
    operacaoAtiva = op;
    limparProximo = true; 
  }
	
  function calcular() {
    const valorAtual = parseInt(display);

    if (operacaoAtiva === "+"){ 
			display = (valorAnterior + valorAtual).toString();
		}else if (operacaoAtiva === "-"){ 
			display = (valorAnterior - valorAtual).toString();
		}else if (operacaoAtiva === "*"){ 
			display = (valorAnterior * valorAtual).toString();
		}else if (operacaoAtiva === "/"){
			display =  (valorAnterior / valorAtual).toString();
		}
    operacaoAtiva = "";
    limparProximo = true;
  }

  function limparTudo() {
    display = "0";
    valorAnterior = 0;
    operacaoAtiva = "";
    limparProximo = false;
  }
</script>

<main>
  <div class="calculadora">
    <div class="visor">{display}</div>
    
    <div class="grade">
      <button on:click={limparTudo} class="btn-clear">C</button>
      <button on:click={() => setOperacao("/")}>/</button>
      <button on:click={() => setOperacao("*")}>*</button>
      <button on:click={() => setOperacao("-")}>-</button>

      <button on:click={() => digitar(7)}>7</button>
      <button on:click={() => digitar(8)}>8</button>
      <button on:click={() => digitar(9)}>9</button>
      <button on:click={() => setOperacao("+")}>+</button>

      <button on:click={() => digitar(4)}>4</button>
      <button on:click={() => digitar(5)}>5</button>
      <button on:click={() => digitar(6)}>6</button>
      
      <button on:click={calcular} class="btn-igual">=</button>

      <button on:click={() => digitar(1)}>1</button>
      <button on:click={() => digitar(2)}>2</button>
      <button on:click={() => digitar(3)}>3</button>
      <button on:click={() => digitar(0)}>0</button>
    </div>
  </div>
</main>

<style>
  .calculadora { width: 250px; margin: 20px auto; background: #444; padding: 15px; border-radius: 12px; }
  .visor { background: #222; color: #fff; padding: 20px; text-align: right; font-size: 25px; margin-bottom: 10px; border-radius: 5px; overflow: hidden; }
  .grade { display: grid; grid-template-columns: repeat(4, 1fr); gap: 8px; }
  button { padding: 15px; border: none; border-radius: 6px; font-size: 20px; background: #666; color: fff; }
  button:hover { background: #888; }
  .btn-clear { background: #8B0000; }
  .btn-igual { background: #00008B; grid-row: span 2; }
</style>
