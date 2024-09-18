<script lang="ts">
    import "../../styles/dialogo.css";
    import { goto } from "$app/navigation";

    let dialogos = [
        "Bom dia à todos, aqui e o seu amigo matinal, V , falando diretamente da maior, melhor e mais antiga radio do Japao, a maravilhosa NHK. Hoje e um dia muito especial, estamos na reta final do ano, falta pouco mais de uma semana para encerrarmos mais um ciclo terrestre... Infelizmente ja fazem quase 2 anos que estamos enfrentando um momento dificil, mas desejo que pocamos comemorar com nossos entes queridos e lembrar com carinho de quem infelizmente perdemos...",
        " V , Nao sei porque coloquei nessa radio, nem gosto dela. Sempre achei ela muito sensacionalista! ",
        "[*MUDANDO DE ESTACAO*]",
        " V, Agora sim! A radio local sempre tocando coisa boa, sempre escutava com...",
        "[*BATIDA NA PORTA*]",
        "E AI, V , TAMO QUASE ATRASADO, VAI DEMORAR MAIS?",
        "Ihhh, acabei me distraindo e o Samuel ja chegou. ESPERA AI QUE JA TO DESCENDO, SO VOU COLOCAR A MASCARA, NAO DESLIGA A MOTO!!"
    ];

    let dialogoAtual = 0;

    function proximoDialogo() {
        if (dialogoAtual < dialogos.length - 1) {
            dialogoAtual++;
        } else {
            goto("/");
        }
    }
</script>

<div class="container">
  <div class="dialog-box">
    <p>{dialogos[dialogoAtual]}</p>
    <button on:click={proximoDialogo}>
        {dialogoAtual < dialogos.length - 1 ? "⬇" : "⮕"}
    </button>
  </div>
</div>