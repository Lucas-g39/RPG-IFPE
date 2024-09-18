<script lang="ts">
    import "../../styles/introducao.css"
    import { onMount } from 'svelte';

    onMount(() => {
        document.body.style.display = 'none';
        document.body.offsetHeight;
        document.body.style.display = '';
    });
</script>

<div class="container">
    <h1>WARNING!!</h1>
    <h2>SUAS ESCOLHAS TEM CONSEQUÊNCIAS!</h2>
    <img class="jogar" src="/images/imagem.png" alt="foto"/>
    <h2>A narrativa vai se dar conforme suas escolhas. <br> Leia com calma e escolha o que mais te agradar.</h2>
    <h1 class="sobre" id="nomesobre">Sobre</h1>
    <img class="sobre" src="/images/logoIFPE.png" alt="logo IPFE"/>
    <p>
      Autores:<br> Filipe J. <br>Lionardo M. <br> Lucas G. <br> Pedro L. <br> Reynaldo S 
    </p>
</div>

<a class="introducao" id="botaovoltarmenu" href="/">VOLTAR</a>
<a class="introducao" id="botaodialogo" href="/Dialogo" >PULAR</a>