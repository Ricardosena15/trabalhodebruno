<template>
  <div class="home">
    <header class="hero">
      <div class="hero-content">
        <h1> Arena Fute-Tênis</h1>
        <p>Aplicação de Matemática na criação de uma quadra esportiva</p>
        <button @click="irParaApresentacao">Ver Projeto</button>
      </div>
    </header>

    <section class="info">
      <div class="card">
        <h2> Área</h2>
        <p>Calculamos o espaço necessário da quadra usando base × altura.</p>
      </div>

      <div class="card">
        <h2> Perímetro</h2>
        <p>Determinamos a quantidade de material para marcação da quadra.</p>
      </div>

      <div class="card">
        <h2> Objetivo</h2>
        <p>Organizar um espaço seguro e divertido para os alunos.</p>
      </div>
    </section>
  </div>
</template>

<script setup>
import { useRouter } from 'vue-router'
const router = useRouter()

const irParaApresentacao = () => {
  router.push('/apresentacao')
}
</script>

<style scoped>
.home {
  font-family: 'Poppins', sans-serif;
  color: #fff;
  background: radial-gradient(circle at top, #1b2a38, #0b1c2c);
  min-height: 100vh;
  overflow-x: hidden;
}

/* HERO */
.hero {
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 120px 20px;
  position: relative;
}

/* EFEITO DE LUZ */
.hero::before {
  content: "";
  position: absolute;
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, rgba(0,255,140,0.15), transparent);
  top: -100px;
  left: -100px;
}

.hero::after {
  content: "";
  position: absolute;
  width: 400px;
  height: 400px;
  background: radial-gradient(circle, rgba(0,255,140,0.1), transparent);
  bottom: -100px;
  right: -100px;
}

/* CONTEÚDO */
.hero-content {
  position: relative;
  backdrop-filter: blur(18px);
  background: rgba(255, 255, 255, 0.05);
  padding: 50px;
  border-radius: 24px;
  border: 1px solid rgba(255,255,255,0.1);
  box-shadow: 0 20px 60px rgba(0,0,0,0.6);
  animation: fadeUp 0.8s ease;
}

/* TEXTO */
.hero h1 {
  font-size: 3.2rem;
  margin-bottom: 10px;
  font-weight: 700;
  letter-spacing: 1px;
}

.hero p {
  font-size: 1.2rem;
  margin-bottom: 30px;
  color: rgba(255,255,255,0.75);
}

/* BOTÃO */
.hero button {
  padding: 14px 32px;
  border: none;
  background: linear-gradient(135deg, #00c853, #00e676);
  color: white;
  font-size: 1rem;
  border-radius: 14px;
  cursor: pointer;
  transition: all 0.3s ease;
  font-weight: 600;
  box-shadow: 0 10px 30px rgba(0,200,83,0.3);
}

.hero button:hover {
  transform: translateY(-4px) scale(1.05);
  box-shadow: 0 15px 40px rgba(0,200,83,0.6);
}

/* SEÇÃO INFO */
.info {
  display: flex;
  justify-content: center;
  gap: 30px;
  padding: 80px 20px;
  flex-wrap: wrap;
}

/* CARDS */
.card {
  background: rgba(255,255,255,0.06);
  padding: 30px;
  border-radius: 20px;
  width: 260px;
  text-align: center;
  backdrop-filter: blur(14px);
  border: 1px solid rgba(255,255,255,0.08);
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

/* LINHA ANIMADA */
.card::before {
  content: "";
  position: absolute;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, transparent, #00e676, transparent);
  top: 0;
  left: -100%;
  transition: 0.5s;
}

.card:hover::before {
  left: 100%;
}

/* TEXTO */
.card h2 {
  margin-bottom: 10px;
  font-size: 1.3rem;
}

.card p {
  color: rgba(255,255,255,0.75);
  font-size: 0.95rem;
}

/* HOVER */
.card:hover {
  transform: translateY(-12px) scale(1.04);
  box-shadow: 0 20px 40px rgba(0,0,0,0.5);
  border-color: rgba(0,230,118,0.4);
}

/* ANIMAÇÃO */
@keyframes fadeUp {
  from {
    opacity: 0;
    transform: translateY(40px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>