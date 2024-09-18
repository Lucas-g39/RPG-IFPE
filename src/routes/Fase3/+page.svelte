<script lang="ts">
    import "../../styles/gameplay.css";

    let player = {
    hp: 100,
    defesa: 8,
    ataque: 18,
    remedios: 5,
    cura: 20
  };

  let boss = {
    hp: 500,
    defesa: 15,
    ataque: 20
  };

  let turnoDoJogador = true;

  function atacar() {
    if (turnoDoJogador) {
      let dano = player.ataque - boss.defesa;
      boss.hp = Math.max(boss.hp - dano, 0);
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
      let dano = boss.ataque - player.defesa;
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
    } else if (boss.hp <= 0) {

      turnoDoJogador = false;
      setTimeout(() => {
        window.location.href = '/Fim';
      },);
    }
  }
  </script>
  
  <main class="container">
    <div class="box2">
      <div class="Boss">
      <h2 class="Boss">HP: {boss.hp}/500</h2>
      </div>
    </div>
    
    <div class="box">
      <div class="heroi">
        <h2 class="Heroi">{player.hp}/100 :HP</h2>
        <h3 class="Heroi">{player.remedios} :REMEDIOS</h3>
      </div>
    </div>
    
    <button class="Butaoataque" on:click={atacar} disabled={!turnoDoJogador || player.hp <= 0 || boss.hp <= 0}>
      ATACAR
    </button>
    <button class="Butaoremedio" on:click={curar} disabled={!turnoDoJogador || player.hp <= 0 || boss.hp <= 0}>
      CURA
    </button>
    
    <img class="Boss-imagem" src="/images/boss.png" alt="imagem"/>
    <img class="player-imagem" src="/images/player.png" alt="imagem"/>
  </main>