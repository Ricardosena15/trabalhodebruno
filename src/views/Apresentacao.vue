<template>
  <div class="apresentacao">

    <!-- TOPO -->
    <header class="topo">
        <button class="btn-voltar" @click="voltar">
        Voltar
        </button>
      <h1> Arena Fute-Tênis</h1>
      <p>Projeto de aplicação da matemática no esporte</p>

      <div class="acoes">
        <button @click="abrirModal"> Sobre o Fute-Tênis</button>
        <button @click="abrirIntro"> Introdução</button>
        <button @click="proximoSlide"> Próximo</button>
      </div>
    </header>

    <!-- QUADRA -->
    <section class="quadra-section">
      <h2> Representação da Quadra</h2>

      <div class="quadra-container">
        <div class="quadra">
          <div class="rede"></div>

          <!-- LINHAS -->
          <div class="linha horizontal"></div>
          <div class="linha vertical"></div>

          <!-- BOLINHA -->
          <div class="bola"></div>
        </div>

        <div class="medidas-horizontal">6m</div>
        <div class="medidas-vertical">3m</div>
      </div>
    </section>

    <!-- CÁLCULO -->
    <section class="calculo">
      <h2> Cálculo da Área</h2>
      <p class="formula">
        {{ textoCalculo }}
      </p>
    </section>

    <!-- GRID -->
    <div class="grid">
      <div class="box">
        <h2> Medidas</h2>
        <p>6m × 3m</p>
      </div>

      <div class="box">
        <h2> Área</h2>
        <p class="numero">18 m²</p>
      </div>

      <div class="box">
        <h2> Perímetro</h2>
        <p class="numero">18 m</p>
      </div>

      <div class="box destaque">
        <h2> Solução</h2>
        <p>Criar a Arena Fute-Tênis.</p>
      </div>

      <div class="box inovacao">
        <h2> Inovação</h2>
        <ul>
          <li>Design moderno</li>
          <li>Cores vibrantes</li>
          <li>Quadra otimizada</li>
        </ul>
      </div>
    </div>

    <!-- MODAL -->
    <div v-if="modal" class="modal">
  <div class="modal-content">

    <button class="fechar" @click="modal = false">✖</button>

    <h2> Fute-Tênis</h2>

    <p class="descricao">
      O fute-tênis é um esporte que combina elementos do futebol e do tênis. 
      Ele é jogado em uma quadra dividida por uma rede, onde os jogadores utilizam pés, cabeça e corpo para passar a bola ao adversário.
    </p>

    <div class="info">

      <div class="item">
        <span> Origem</span>
        <p>
          Surgiu no Brasil, nas praias do Rio de Janeiro, como uma adaptação do futebol em espaços menores.
        </p>
      </div>

      <div class="item">
        <span> Objetivo</span>
        <p>
          Fazer a bola passar por cima da rede e cair na quadra adversária sem que o oponente consiga devolver.
        </p>
      </div>

      <div class="item">
        <span> Jogadores</span>
        <p>
          Pode ser jogado em partidas de 1x1 (individual) ou 2x2 (duplas).
        </p>
      </div>

      <div class="item">
        <span> Quadra</span>
        <p>
          Geralmente possui dimensões reduzidas. No projeto: 6m de comprimento por 3m de largura.
        </p>
      </div>

      <div class="item">
        <span> Regras básicas</span>
        <p>
          Cada jogador pode dar até 3 toques na bola antes de enviá-la ao outro lado.
        </p>
      </div>

      <div class="item">
        <span> Benefícios</span>
        <p>
          Desenvolve coordenação motora, equilíbrio, agilidade e trabalho em equipe.
        </p>
      </div>

      <div class="item">
        <span> Popularidade</span>
        <p>
          Muito praticado no Brasil e em crescimento em outros países como esporte recreativo e competitivo.
        </p>
      </div>

    </div>

    <button class="btn-fechar" @click="modal = false">
      Fechar
    </button>

  </div>
</div>

    <!-- MODAL INTRODUÇÃO -->
<div v-if="intro" class="modal">
  <div class="modal-content">

    <button class="fechar" @click="intro = false">✖</button>

    <h2> Introdução do Projeto</h2>

    <p class="descricao">
      Este projeto propõe a criação de uma quadra de fute-tênis dentro da escola, 
      utilizando conceitos matemáticos para planejar e organizar o espaço de forma eficiente.
    </p>

    <div class="info">

      <div class="item">
        <span> Solução</span>
        <p>
          Criar uma quadra compacta de 6m x 3m, aproveitando melhor o espaço disponível.
        </p>
      </div>

      <div class="item">
        <span> Aplicação da Matemática</span>
        <p>
          Foram utilizados cálculos de área e perímetro para definir o tamanho ideal da quadra 
          e a quantidade de material necessário.
        </p>
      </div>

      <div class="item">
        <span> Impacto na Escola</span>
        <p>
          A quadra proporcionará mais opções de lazer, incentivo ao esporte e melhoria na convivência entre os alunos.
        </p>
      </div>

      <div class="item">
        <span> Viabilidade</span>
        <p>
          O projeto é de baixo custo e pode ser implementado em espaços já existentes dentro da escola.
        </p>
      </div>

    </div>

    <button class="btn-fechar" @click="intro = false">
      Fechar
    </button>

  </div>
</div>

  </div>
</template>

<script setup>
import { ref, onMounted } from "vue"
import { useRouter } from "vue-router"

const modal = ref(false)
const intro = ref(false)
const router = useRouter()
const textoCalculo = ref("")

const abrirModal = () => {
  modal.value = true
}

const abrirIntro = () => {
  intro.value = true
}

const proximoSlide = () => {
  window.scrollBy({ top: 500, behavior: "smooth" })
}

const voltar = () => {
  router.back("/")
}

/* ANIMAÇÃO DO TEXTO */
onMounted(() => {
  const texto = "Área = base × altura = 6 × 3 = 18 m²"
  let i = 0

  const escrever = () => {
    if (i < texto.length) {
      textoCalculo.value += texto[i]
      i++
      setTimeout(escrever, 50)
    }
  }

  escrever()
})
</script>

<style scoped>
.apresentacao {
  min-height: 100vh;
  font-family: 'Poppins', sans-serif;
  background: linear-gradient(135deg, #0b1c2c, #1a2f45, #243b55);
  color: #f1f1f1;
  padding: 40px;
}

/* TOPO */
.topo {
  text-align: center;
  margin-bottom: 30px;
}

.topo h1 {
  font-size: 2.6rem;
  font-weight: 700;
}

.topo p {
  color: rgba(255,255,255,0.65);
}

/* BOTÕES */
.acoes {
  margin-top: 20px;
}

.acoes button {
  margin: 6px;
  padding: 12px 22px;
  border: none;
  border-radius: 12px;
  background: linear-gradient(135deg, #00c853, #00e676);
  color: white;
  cursor: pointer;
  transition: all 0.3s ease;
}

.acoes button:hover {
  transform: translateY(-3px);
  box-shadow: 0 10px 25px rgba(0,200,83,0.4);
}

/* CONTAINER DA QUADRA */
.quadra-container {
  position: relative;
  width: fit-content;
  margin: 30px auto;
}

/* QUADRA */
.quadra {
  width: 400px;
  height: 200px;
  background: radial-gradient(circle, #00e676, #009624);
  border: 4px solid white;
  border-radius: 14px;
  position: relative;
  box-shadow: 0 20px 50px rgba(0,0,0,0.6);
}

/* REDE */
.rede {
  position: absolute;
  left: 50%;
  width: 3px;
  height: 100%;
  background: repeating-linear-gradient(
    to bottom,
    white,
    white 5px,
    transparent 5px,
    transparent 10px
  );
  transform: translateX(-50%);
}

/* LINHAS */
.linha {
  position: absolute;
  background: white;
}

/* BOLA */
.bola {
  width: 14px;
  height: 14px;
  background: white;
  border-radius: 50%;
  position: absolute;
  box-shadow: 0 0 10px white;
  animation: mover 2s infinite alternate ease-in-out;
}

@keyframes mover {
  0% { left: 10%; top: 65%; }
  100% { left: 80%; top: 35%; }
}

/* MEDIDAS */
.medidas-horizontal {
  position: absolute;
  bottom: -25px;
  left: 50%;
  transform: translateX(-50%);
}

.medidas-vertical {
  position: absolute;
  left: -25px;
  top: 50%;
  transform: translateY(-50%) rotate(-90deg);
  font-weight: 500;
}

/* GRID */
.grid {
  margin-top: 60px;
  display: grid;
  gap: 25px;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
}

/* CARDS */
.box {
  position: relative;
  background: linear-gradient(145deg, rgba(255,255,255,0.05), rgba(255,255,255,0.02));
  padding: 28px;
  border-radius: 18px;

  backdrop-filter: blur(14px);
  border: 1px solid rgba(255,255,255,0.08);

  transition: all 0.35s ease;
  overflow: hidden;
}

/* BORDA BRILHANTE ANIMADA */
.box::before {
  content: "";
  position: absolute;
  inset: 0;
  border-radius: 18px;
  padding: 1px;
  background: linear-gradient(120deg, transparent, #00e676, transparent);
  -webkit-mask: 
    linear-gradient(#000 0 0) content-box, 
    linear-gradient(#000 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  opacity: 0;
  transition: 0.4s;
}

/* GLOW INTERNO */
.box::after {
  content: "";
  position: absolute;
  width: 200px;
  height: 200px;
  background: radial-gradient(circle, rgba(0,230,118,0.15), transparent);
  top: -50px;
  left: -50px;
  opacity: 0;
  transition: 0.4s;
}

/* HOVER */
.box:hover {
  transform: translateY(-10px) scale(1.03);
  box-shadow: 0 20px 40px rgba(0,0,0,0.5);
  border-color: rgba(0,230,118,0.3);
}

.box:hover::before {
  opacity: 1;
}

.box:hover::after {
  opacity: 1;
}

/* TÍTULO */
.box h2 {
  font-size: 1.3rem;
  font-weight: 600;
  margin-bottom: 10px;
}

/* TEXTO */
.box p {
  font-size: 0.95rem;
  color: rgba(255,255,255,0.75);
  line-height: 1.4;
}

/* NÚMEROS */
.numero {
  font-size: 2.4rem;
  color: #00e676;
  font-weight: 700;
  letter-spacing: 1px;
}

/* DESTAQUE MAIS BONITO */
.destaque {
  background: linear-gradient(145deg, rgba(0,200,83,0.15), rgba(0,200,83,0.05));
  border: 1px solid rgba(0,230,118,0.4);
}

/* INOVAÇÃO PREMIUM */
.inovacao {
  background: linear-gradient(135deg, #00c853, #009624);
  color: white;
}

.inovacao li {
  margin-bottom: 6px;
  font-size: 0.9rem;
}

/* CALCULO */
.calculo {
  text-align: center;
  margin-top: 30px;
}

.formula {
  font-size: 1.3rem;
  color: #00e676;
}

/* MODAL */
/* FUNDO */
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.85);
  backdrop-filter: blur(8px);

  display: flex;
  align-items: center;
  justify-content: center;

  padding: 20px; /* evita colar nas bordas */
  z-index: 999;

  animation: fadeIn 0.3s ease;
}

/* CAIXA */
.modal-content {
  position: relative;
  background: linear-gradient(180deg, #1b1b1b, #0f0f0f);
  padding: 30px;
  border-radius: 20px;

  max-width: 450px;
  width: 100%;
  max-height: 90vh; /* 🔥 IMPORTANTE */
  overflow-y: auto; /* 🔥 SCROLL */

  box-shadow: 0 25px 60px rgba(0,0,0,0.8);
  border: 1px solid rgba(255,255,255,0.08);

  animation: subir 0.4s ease;
}

/* SCROLL BONITO */
.modal-content::-webkit-scrollbar {
  width: 6px;
}

.modal-content::-webkit-scrollbar-thumb {
  background: #00e676;
  border-radius: 10px;
}

/* BOTÃO X */
.fechar {
  position: absolute;
  top: 12px;
  right: 12px;
  background: rgba(255,255,255,0.05);
  border: none;
  color: #aaa;
  width: 32px;
  height: 32px;
  border-radius: 50%;
  cursor: pointer;
  transition: 0.3s;
}

.fechar:hover {
  color: #fff;
  background: rgba(255,255,255,0.15);
  transform: scale(1.1);
}

/* TÍTULO */
.modal-content h2 {
  text-align: center;
  margin-bottom: 10px;
  font-size: 1.5rem;
}

/* DESCRIÇÃO */
.descricao {
  text-align: center;
  font-size: 0.95rem;
  color: rgba(255,255,255,0.7);
  margin-bottom: 20px;
  line-height: 1.4;
}

/* GRID INFO */
.info {
  display: grid;
  gap: 12px;
  margin-bottom: 20px;
}

/* ITENS */
.item {
  background: rgba(255,255,255,0.05);
  padding: 14px;
  border-radius: 12px;
  border: 1px solid rgba(255,255,255,0.05);
  transition: 0.3s;
}

.item:hover {
  background: rgba(255,255,255,0.08);
  transform: translateY(-2px);
}

/* TITULO ITEM */
.item span {
  display: block;
  font-weight: 600;
  color: #00e676;
  font-size: 0.9rem;
  margin-bottom: 4px;
}

/* TEXTO ITEM */
.item p {
  font-size: 0.85rem;
  color: rgba(255,255,255,0.7);
  line-height: 1.3;
}

/* BOTÃO FINAL */
.btn-fechar {
  width: 100%;
  padding: 12px;
  border-radius: 12px;
  border: none;
  background: linear-gradient(135deg, #00c853, #00e676);
  color: white;
  font-weight: 600;
  cursor: pointer;
  transition: 0.3s;
}

.btn-fechar:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 25px rgba(0,200,83,0.4);
}

/* ANIMAÇÕES */
@keyframes fadeIn {
  from { opacity: 0 }
  to { opacity: 1 }
}

@keyframes subir {
  from {
    transform: translateY(40px) scale(0.95);
    opacity: 0;
  }
  to {
    transform: translateY(0) scale(1);
    opacity: 1;
  }
}
.btn-voltar {
  position: absolute;
  left: 40px;
  top: 40px;

  padding: 10px 18px;
  border-radius: 12px;
  border: none;

  background: rgba(255,255,255,0.08);
  color: white;
  font-size: 0.9rem;

  backdrop-filter: blur(10px);
  border: 1px solid rgba(255,255,255,0.1);

  cursor: pointer;
  transition: 0.3s;
}

/* hover bonito */
.btn-voltar:hover {
  background: rgba(0,230,118,0.15);
  border-color: rgba(0,230,118,0.4);
  transform: translateY(-2px);
}
</style>