<script lang="ts">
    import "../../styles/gameplay.css";

    let player = {
    hp: 100,
    defesa: 2,
    ataque: 10,
    remedios: 3,
    cura: 10
  };

  let vilao2 = {
    hp: 200,
    defesa: 2,
    ataque: 8
  };

  let turnoDoJogador = true;

  function atacar() {
    if (turnoDoJogador) {
      let dano = player.ataque - vilao2.defesa;
      vilao2.hp = Math.max(vilao2.hp - dano, 0);
      checarFimDeJogo();
      turnoDoJogador = false;
      setTimeout(turnoDoVilao, 500); 
    }
  }


  function curar() {
    if (turnoDoJogador && player.remedios > 0) {
      player.hp = Math.min(player.hp + player.cura, 100);
      player.remedios--;
      checarFimDeJogo();
      turnoDoJogador = false;
      setTimeout(turnoDoVilao, 500);
    }
  }


  function turnoDoVilao() {
    if (!turnoDoJogador) {
      let dano = vilao2.ataque - player.defesa;
      player.hp = Math.max(player.hp - dano, 0);
      checarFimDeJogo();
      turnoDoJogador = true;
    }
  }

  function checarFimDeJogo() {
    if (player.hp <= 0) {
      turnoDoJogador = false;
      setTimeout(() => {
        window.location.href = '/Derrota';
      });
    } else if (vilao2.hp <= 0) {

      turnoDoJogador = false;
      setTimeout(() => {
        window.location.href = '/Dialogo3';
      },);
    }
  }

  </script>
  
  <main class="container">
    <div class="box2">
      <div class="vilao">
      <h2 class="Vilao">HP: {vilao2.hp}/200</h2>
      </div>
    </div>
    
    <div class="box">
      <div class="heroi">
        <h2 class="Heroi">{player.hp}/100 :HP</h2>
        <h3 class="Heroi">{player.remedios} :REMEDIOS</h3>
      </div>
    </div>
    
    <button class="Butaoataque" on:click={atacar} disabled={!turnoDoJogador || player.hp <= 0 || vilao2.hp <= 0}>
      ATACAR
    </button>
    <button class="Butaoremedio" on:click={curar} disabled={!turnoDoJogador || player.hp <= 0 || vilao2.hp <= 0}>
      CURA
    </button>
    
    <img class="inimigo2-imagem" src="/images/inimigo2.png" alt="imagem"/>
    <img class="player-imagem" src="/images/player.png" alt="imagem"/>
  </main>