<script setup>
import { ref } from 'vue'

const menuAberto = ref(false)
const lgpdAceita = ref(false)

const areas = [
  {
    numero: '01',
    titulo: 'Cultura e tradição',
    descricao: 'Conheça as histórias, os saberes e as manifestações culturais da nossa região.',
    simbolo: '✳'
  },
  {
    numero: '02',
    titulo: 'Pessoas e comunidades',
    descricao: 'Conecte pessoas, iniciativas e comunidades que fazem o Nordeste crescer.',
    simbolo: '♧'
  },
  {
    numero: '03',
    titulo: 'Empreendedorismo local',
    descricao: 'Descubra produtores, pequenos negócios e talentos da nossa terra.',
    simbolo: '◇'
  }
]
</script>

<template>
  <div class="pagina">
    <header class="cabecalho">
      <a class="marca" href="#" aria-label="Raízes do Nordeste, início">
        <span class="marca-simbolo">R<span>.</span></span>
        <span class="marca-texto">
          <strong>Raízes do Nordeste</strong>
          <small>NOSSA TERRA, NOSSO FUTURO</small>
        </span>
      </a>

      <button
        class="botao-menu"
        @click="menuAberto = !menuAberto"
        :aria-expanded="menuAberto"
        aria-label="Abrir ou fechar menu"
      >
        {{ menuAberto ? 'Fechar ×' : 'Menu ☰' }}
      </button>

      <nav class="navegacao" :class="{ 'navegacao-aberta': menuAberto }">
        <a href="#sobre" @click="menuAberto = false">Sobre a rede</a>
        <a href="#areas" @click="menuAberto = false">Nossas áreas</a>
        <a href="#contato" @click="menuAberto = false">Contato</a>
        <a class="link-destaque" href="#areas" @click="menuAberto = false">
          Explorar a rede ↗
        </a>
      </nav>
    </header>

    <main>
      <section class="hero" id="sobre">
        <div class="hero-texto">
          <span class="etiqueta">
            <span class="ponto"></span>
            UMA REDE FEITA DE HISTÓRIAS REAIS
          </span>

          <h1>
            Nossas raízes.<br />
            <span>Nossas possibilidades.</span>
          </h1>

          <p class="introducao">
            Um espaço para conectar pessoas, valorizar a cultura
            e fortalecer iniciativas que transformam o Nordeste.
          </p>

          <div class="hero-acoes">
            <a class="botao-principal" href="#areas">
              Conheça a rede <span>↗</span>
            </a>
            <a class="botao-secundario" href="#contato">
              Nossa proposta
            </a>
          </div>

          <div class="assinatura">
            <span class="assinatura-linha"></span>
            <p>Do nosso território, para o nosso futuro.</p>
          </div>
        </div>

        <div class="hero-arte" aria-label="Ilustração inspirada na paisagem do sertão">
          <div class="sol"></div>
          <div class="morro morro-fundo"></div>
          <div class="morro morro-meio"></div>
          <div class="morro morro-frente"></div>

          <div class="cacto cacto-esquerda">
            <span></span>
          </div>
          <div class="cacto cacto-direita">
            <span></span>
          </div>

          <div class="arte-legenda">
            <span>01 / 09</span>
            <span>Território e pertencimento</span>
          </div>

          <span class="arte-decoracao">RAÍZES VIVAS</span>
        </div>
      </section>

      <section class="manifesto">
        <span class="manifesto-numero">01 — NOSSO PROPÓSITO</span>
        <p>
          O Nordeste não é apenas um lugar no mapa.
          <strong>É conhecimento, criatividade, trabalho e futuro.</strong>
        </p>
      </section>

      <section class="areas" id="areas">
        <div class="secao-cabecalho">
          <div>
            <span class="etiqueta">O QUE NOS CONECTA</span>
            <h2>Uma rede de muitas riquezas.</h2>
          </div>
          <p>
            Diferentes histórias, talentos e iniciativas.
            Um território que cresce quando suas pessoas se conectam.
          </p>
        </div>

        <div class="cartoes">
          <article
            class="cartao"
            v-for="area in areas"
            :key="area.numero"
          >
            <div class="cartao-topo">
              <span>{{ area.numero }}</span>
              <span class="cartao-simbolo">{{ area.simbolo }}</span>
            </div>

            <h3>{{ area.titulo }}</h3>
            <p>{{ area.descricao }}</p>
            <a href="#contato" class="cartao-link">
              Saber mais <span>↗</span>
            </a>
          </article>
        </div>
      </section>

      <section class="convite" id="contato">
        <div>
          <span class="etiqueta etiqueta-clara">O FUTURO É CONSTRUÍDO EM REDE</span>
          <h2>Vamos fortalecer nossas raízes?</h2>
          <p>
            Esta é a primeira etapa de uma plataforma criada para
            aproximar pessoas e iniciativas do Nordeste.
          </p>
        </div>
        <a class="botao-convite" href="mailto:contato@rede-raizes.org">
          Entre em contato ↗
        </a>
      </section>
    </main>

    <footer class="rodape">
      <a class="rodape-marca" href="#">Raízes do Nordeste.</a>
      <p>Feito para valorizar o que é nosso.</p>
      <span>© 2026 · Projeto em construção</span>
    </footer>

    <!-- Banner informativo de privacidade e LGPD -->
    <div
      v-if="!lgpdAceita"
      class="banner-lgpd"
      role="status"
      aria-label="Aviso de privacidade"
    >
      <div class="banner-lgpd-texto">
        <strong>🔒 Sua privacidade importa</strong>
        <p>
          A Rede Raízes do Nordeste respeita a Lei Geral de Proteção de Dados
          (Lei nº 13.709/2018). As informações pessoais devem ser tratadas com
          transparência, segurança e para finalidades informadas. Você pode
          consultar seus direitos e as informações sobre o uso dos dados.
        </p>
      </div>

      <button
        class="banner-lgpd-botao"
        @click="lgpdAceita = true"
        aria-label="Fechar aviso de privacidade"
      >
        Entendi
      </button>
    </div>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700&family=Playfair+Display:wght@500;600;700&display=swap');

:root {
  font-family: 'DM Sans', sans-serif;
  color: #233c30;
  background: #faf8f1;
  font-synthesis: none;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-optical-sizing: auto;
  scroll-behavior: smooth;
}

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  min-width: 320px;
}

a {
  color: inherit;
  text-decoration: none;
}

button {
  font: inherit;
}

.pagina {
  width: 100%;
  overflow: hidden;
}

.cabecalho {
  min-height: 88px;
  padding: 18px 7%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 28px;
  background: #faf8f1;
  border-bottom: 1px solid #e9e6db;
}

.marca {
  display: flex;
  align-items: center;
  gap: 12px;
}

.marca-simbolo {
  font-family: 'Playfair Display', serif;
  font-size: 38px;
  font-weight: 700;
  color: #2c6549;
}

.marca-simbolo span {
  color: #c67d4b;
}

.marca-texto {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.marca-texto strong {
  font-size: 16px;
}

.marca-texto small {
  font-size: 9px;
  letter-spacing: 1.5px;
  color: #8a8979;
}

.navegacao {
  display: flex;
  align-items: center;
  gap: 30px;
  font-size: 13px;
  font-weight: 500;
}

.navegacao a:not(.link-destaque):hover,
.rodape a:hover {
  color: #b96d40;
}

.link-destaque {
  background: #285d43;
  color: white;
  padding: 13px 18px;
  border-radius: 3px;
}

.botao-menu {
  display: none;
  border: 1px solid #d8d9cb;
  background: transparent;
  padding: 10px 13px;
  border-radius: 4px;
  color: #233c30;
}

.hero {
  display: grid;
  grid-template-columns: 1fr 0.88fr;
  gap: 5%;
  align-items: center;
  padding: 78px 7% 82px;
}

.hero-texto {
  max-width: 620px;
}

.etiqueta {
  display: inline-flex;
  align-items: center;
  gap: 9px;
  font-size: 10px;
  letter-spacing: 1.6px;
  font-weight: 700;
  color: #8e6745;
}

.ponto {
  width: 7px;
  height: 7px;
  border-radius: 50%;
  background: #c77c4b;
}

h1,
h2,
h3,
p {
  margin-top: 0;
}

.hero h1 {
  margin: 26px 0 22px;
  font-family: 'Playfair Display', serif;
  font-size: clamp(39px, 4.3vw, 63px);
  font-weight: 500;
  line-height: 1.13;
  letter-spacing: -1.8px;
}

.hero h1 span {
  color: #59805b;
  font-style: italic;
}

.introducao {
  max-width: 460px;
  color: #747467;
  font-size: 15px;
  line-height: 1.9;
}

.hero-acoes {
  display: flex;
  align-items: center;
  gap: 24px;
  flex-wrap: wrap;
  margin-top: 30px;
}

.botao-principal {
  display: inline-flex;
  gap: 24px;
  align-items: center;
  background: #285d43;
  color: white;
  padding: 16px 20px;
  font-size: 13px;
  border-radius: 3px;
  transition: background 0.2s;
}

.botao-principal:hover,
.link-destaque:hover {
  background: #19452f;
}

.botao-principal span,
.cartao-link span {
  font-size: 18px;
}

.botao-secundario {
  font-size: 13px;
  border-bottom: 1px solid #c8bba5;
  padding-bottom: 5px;
}

.assinatura {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-top: 47px;
}

.assinatura-linha {
  width: 34px;
  height: 1px;
  background: #c77c4b;
}

.assinatura p {
  margin: 0;
  color: #8a8979;
  font-size: 11px;
}

.hero-arte {
  position: relative;
  min-height: 420px;
  overflow: hidden;
  background: linear-gradient(180deg, #e9dfc6 0%, #f0c58c 68%, #c58d5d 100%);
}

.sol {
  position: absolute;
  top: 57px;
  right: 20%;
  width: 106px;
  height: 106px;
  background: #f8e8b6;
  border-radius: 50%;
}

.morro {
  position: absolute;
  width: 130%;
  left: -15%;
  border-radius: 50% 50% 0 0;
}

.morro-fundo {
  height: 180px;
  bottom: 100px;
  background: #c99a70;
  transform: rotate(-9deg);
}

.morro-meio {
  height: 180px;
  bottom: 35px;
  left: -35%;
  background: #a56f4e;
  transform: rotate(10deg);
}

.morro-frente {
  height: 160px;
  bottom: -75px;
  background: #52684a;
  transform: rotate(-7deg);
}

.cacto {
  position: absolute;
  z-index: 2;
  bottom: 56px;
  width: 15px;
  height: 105px;
  background: #365b40;
  border-radius: 12px 12px 3px 3px;
}

.cacto::before,
.cacto::after,
.cacto span {
  content: '';
  position: absolute;
  width: 23px;
  height: 45px;
  border: 9px solid #365b40;
  border-bottom: 0;
  border-radius: 20px 20px 0 0;
}

.cacto::before {
  top: 28px;
  left: -19px;
  height: 28px;
  transform: rotate(-10deg);
}

.cacto::after {
  top: 43px;
  right: -20px;
  height: 32px;
  transform: rotate(9deg);
}

.cacto span {
  display: none;
}

.cacto-esquerda {
  left: 15%;
}

.cacto-direita {
  right: 16%;
  transform: scale(0.7);
  transform-origin: bottom;
}

.arte-legenda {
  position: absolute;
  z-index: 3;
  bottom: 18px;
  left: 20px;
  right: 20px;
  display: flex;
  justify-content: space-between;
  gap: 10px;
  color: #fff7e6;
  font-size: 10px;
  letter-spacing: 0.7px;
}

.arte-decoracao {
  position: absolute;
  z-index: 2;
  top: 20px;
  left: 20px;
  font-size: 9px;
  letter-spacing: 2px;
  color: #725e46;
}

.manifesto {
  background: #eee8d9;
  padding: 43px 7%;
  display: grid;
  grid-template-columns: 200px 1fr;
  gap: 35px;
  align-items: start;
}

.manifesto-numero {
  color: #8e6745;
  font-size: 10px;
  letter-spacing: 1.5px;
  font-weight: 700;
  padding-top: 8px;
}

.manifesto p {
  max-width: 720px;
  margin: 0;
  font-family: 'Playfair Display', serif;
  font-size: clamp(21px, 2.5vw, 31px);
  line-height: 1.5;
}

.manifesto strong {
  color: #59805b;
  font-weight: 600;
}

.areas {
  padding: 90px 7%;
}

.secao-cabecalho {
  display: flex;
  align-items: end;
  justify-content: space-between;
  gap: 40px;
  margin-bottom: 38px;
}

.secao-cabecalho h2,
.convite h2 {
  font-family: 'Playfair Display', serif;
  font-size: clamp(30px, 3vw, 42px);
  font-weight: 500;
  line-height: 1.2;
  margin: 16px 0 0;
  letter-spacing: -0.7px;
}

.secao-cabecalho > p {
  max-width: 340px;
  margin-bottom: 3px;
  font-size: 13px;
  line-height: 1.8;
  color: #747467;
}

.cartoes {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  border-top: 1px solid #dedbce;
  border-bottom: 1px solid #dedbce;
}

.cartao {
  padding: 27px 26px 30px 0;
}

.cartao + .cartao {
  padding-left: 26px;
  border-left: 1px solid #dedbce;
}

.cartao-topo {
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: #999583;
  font-size: 11px;
}

.cartao-simbolo {
  color: #64805b;
  font-size: 27px;
}

.cartao h3 {
  margin: 35px 0 12px;
  font-family: 'Playfair Display', serif;
  font-size: 22px;
  font-weight: 600;
}

.cartao > p {
  min-height: 66px;
  margin-bottom: 25px;
  color: #747467;
  font-size: 12px;
  line-height: 1.8;
}

.cartao-link {
  display: inline-flex;
  align-items: center;
  gap: 12px;
  color: #37694b;
  font-size: 12px;
  font-weight: 700;
}

.convite {
  margin: 0 7% 70px;
  padding: 47px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 30px;
  background: #28533d;
  color: #faf8f1;
}

.etiqueta-clara {
  color: #e4bd8c;
}

.convite h2 {
  max-width: 560px;
  margin: 17px 0 12px;
}

.convite p {
  max-width: 510px;
  margin-bottom: 0;
  color: #d4ddcf;
  font-size: 13px;
  line-height: 1.8;
}

.botao-convite {
  flex-shrink: 0;
  padding: 16px 20px;
  background: #f1e8d6;
  color: #28533d;
  font-size: 12px;
  font-weight: 700;
  border-radius: 3px;
}

.rodape {
  padding: 28px 7%;
  border-top: 1px solid #e9e6db;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 20px;
  flex-wrap: wrap;
}

.rodape-marca {
  font-family: 'Playfair Display', serif;
  font-weight: 700;
  font-size: 15px;
}

.rodape p,
.rodape > span {
  margin: 0;
  color: #858475;
  font-size: 11px;
}

@media (max-width: 760px) {
  .cabecalho {
    min-height: 76px;
    padding: 14px 5%;
    flex-wrap: wrap;
  }

  .marca-simbolo {
    font-size: 32px;
  }

  .marca-texto strong {
    font-size: 14px;
  }

  .marca-texto small {
    font-size: 8px;
  }

  .botao-menu {
    display: block;
    cursor: pointer;
  }

  .navegacao {
    display: none;
    width: 100%;
    flex-direction: column;
    align-items: stretch;
    gap: 0;
    padding: 8px 0;
  }

  .navegacao-aberta {
    display: flex;
  }

  .navegacao a {
    padding: 14px 8px;
  }

  .navegacao .link-destaque {
    text-align: center;
    margin-top: 8px;
  }

  .hero {
    grid-template-columns: 1fr;
    gap: 40px;
    padding: 55px 5% 60px;
  }

  .hero h1 {
    font-size: clamp(38px, 10vw, 54px);
  }

  .hero-arte {
    min-height: 330px;
  }

  .manifesto {
    grid-template-columns: 1fr;
    gap: 17px;
    padding: 35px 5%;
  }

  .areas {
    padding: 60px 5%;
  }

  .secao-cabecalho {
    flex-direction: column;
    align-items: start;
    gap: 18px;
  }

  .cartoes {
    grid-template-columns: 1fr;
  }

  .cartao,
  .cartao + .cartao {
    padding: 25px 0;
    border-left: 0;
  }

  .cartao + .cartao {
    border-top: 1px solid #dedbce;
  }

  .cartao h3 {
    margin-top: 22px;
  }

  .cartao > p {
    min-height: 0;
  }

  .convite {
    margin: 0 5% 45px;
    padding: 30px 24px;
    flex-direction: column;
    align-items: start;
  }

  .rodape {
    padding: 25px 5%;
    flex-direction: column;
    align-items: start;
    gap: 12px;
  }
}

/* Banner informativo de privacidade LGPD — adicionado sem alterar o estilo existente */
.banner-lgpd {
  position: fixed;
  z-index: 1000;
  bottom: 20px;
  left: 7%;
  right: 7%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 24px;
  padding: 22px 26px;
  background: #28533d;
  color: #faf8f1;
  border: 1px solid #59805b;
  border-radius: 4px;
  box-shadow: 0 8px 25px rgba(35, 60, 48, 0.2);
}

.banner-lgpd-texto {
  flex: 1;
}

.banner-lgpd-texto strong {
  display: block;
  margin-bottom: 8px;
  font-size: 14px;
}

.banner-lgpd-texto p {
  margin: 0;
  color: #e4e8dc;
  font-size: 12px;
  line-height: 1.7;
}

.banner-lgpd-botao {
  flex-shrink: 0;
  padding: 12px 20px;
  background: #f1e8d6;
  color: #28533d;
  border: none;
  border-radius: 3px;
  font: inherit;
  font-size: 12px;
  font-weight: 700;
  cursor: pointer;
}

.banner-lgpd-botao:hover {
  background: #ffffff;
}

@media (max-width: 760px) {
  .banner-lgpd {
    left: 5%;
    right: 5%;
    bottom: 12px;
    flex-direction: column;
    align-items: stretch;
    gap: 16px;
    padding: 20px;
    max-height: 80vh;
    overflow-y: auto;
  }

  .banner-lgpd-botao {
    width: 100%;
  }
}
</style>