<script lang="ts">
  import { onMount } from 'svelte';

  // State para o acordeão
  let activeFaq = $state<number | null>(null);

  const faqs = [
    { question: 'Como funciona a criação do site?', answer: 'Desenhamos uma estrutura focada em conversão e velocidade. Todo o desenvolvimento é feito em plataformas de alta performance para garantir que seus clientes não fiquem esperando.' },
    { question: 'O que inclui a gestão de Google Ads?', answer: 'Configuramos as campanhas do zero com base em um método validado. Analisamos palavras-chave, criamos os anúncios e otimizamos diariamente o seu investimento.' },
    { question: 'Em quanto tempo vejo resultados?', answer: 'A partir do momento em que o site e as campanhas estão no ar, o tráfego já começa a chegar. Os primeiros contatos podem ocorrer já nas primeiras semanas.' }
  ];

  function toggleFaq(index: number) {
    if (activeFaq === index) {
      activeFaq = null;
    } else {
      activeFaq = index;
    }
  }
</script>

<div class="bg-grid"></div>
<div class="bg-glow"></div>

<header class="header">
  <div class="container header-inner">
    <div class="brand">
      <span class="brand-name">HelpDev</span>
    </div>
    <nav class="nav">
      <a href="#diagnostico" class="nav-link">Diagnóstico</a>
      <a href="https://wa.me/5583986476062" target="_blank" rel="noopener noreferrer" class="nav-link btn-tech" style="padding: 8px 16px; font-size: 0.9rem;">WhatsApp</a>
    </nav>
  </div>
</header>

<main>
  <!-- Hero Section -->
  <section class="hero">
    <div class="hero-particles"></div>
    <div class="container hero-content">
      <div class="hero-eyebrow">
        <strong>HelpDev</strong>
        <span class="eyebrow-line"></span>
        <span>Agência de Performance</span>
      </div>
      
      <h1 class="hero-title">
        <span class="line">Desenvolvemos</span>
        <span class="line">seu site <em>&amp;</em></span>
        <span class="line">criamos seus</span>
        <span class="line highlight">anúncios no Google.</span>
      </h1>
      
      <p class="hero-subtitle">
        Estrutura feita pra converter e campanha configurada com método. Diagnóstico em 2 minutos.
      </p>
      
      <div class="hero-cta">
        <a href="#diagnostico" class="btn-tech primary">FAZER DIAGNÓSTICO RÁPIDO</a>
      </div>
    </div>
  </section>

  <!-- Terminal / Services Showcase -->
  <section class="services" id="servicos">
    <div class="container">
      <div class="section-header">
        <span class="eyebrow">Nossos Serviços</span>
        <h2>Tudo que você precisa em um só lugar.</h2>
        <p class="section-sub">Sites de alta conversão integrados à inteligência de anúncios.</p>
      </div>

      <div class="terminal">
        <div class="terminal-header">
          <span class="dot red"></span>
          <span class="dot yellow"></span>
          <span class="dot green"></span>
          <span class="title">~/helpdev/servicos</span>
        </div>
        <div class="terminal-body">
          <div class="sidebar">
            <ul>
              <li class="active">▸ landing_pages.ts</li>
              <li>▸ google_ads.ts</li>
              <li>▸ automacoes_ia.ts</li>
            </ul>
          </div>
          <div class="code-area">
            <pre><code><span class="comment">// Desenvolvimento de Landing Pages focadas em conversão</span>
<span class="keyword">const</span> <span class="variable">landingPage</span> = &lcub;
  <span class="property">velocidade</span>: <span class="string">"Alta"</span>,
  <span class="property">copywriting</span>: <span class="string">"Persuasivo"</span>,
  <span class="property">design</span>: <span class="string">"Focado na ação"</span>,
  <span class="function">iniciar</span>() &lcub;
    <span class="keyword">return</span> <span class="string">"Mais leads para o seu comercial"</span>;
  &rcub;
&rcub;;

<span class="comment">// Gestão de tráfego com método validado</span>
<span class="keyword">await</span> GoogleAds.<span class="function">otimizarCampanhas</span>(landingPage);
            </code></pre>
            <div class="terminal-prompt">
              <span class="prompt-arrow">›</span>
              <span class="command">helpdev start --performance</span>
              <span class="cursor">_</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- FAQ Section -->
  <section class="faq" id="faq">
    <div class="container">
      <div class="section-header">
        <span class="eyebrow">Dúvidas frequentes</span>
        <h2>O que você precisa saber</h2>
      </div>

      <div class="faq-list">
        {#each faqs as faq, i}
          <div class="faq-item {activeFaq === i ? 'active' : ''}">
            <button class="faq-question" aria-expanded={activeFaq === i} onclick={() => toggleFaq(i)}>
              {faq.question}
              <span class="faq-icon">{activeFaq === i ? '−' : '+'}</span>
            </button>
            {#if activeFaq === i}
              <div class="faq-answer">
                <p>{faq.answer}</p>
              </div>
            {/if}
          </div>
        {/each}
      </div>
    </div>
  </section>

  <!-- Footer CTA -->
  <section class="cta-bottom" id="diagnostico">
    <div class="container">
      <div class="cta-card">
        <h2>Pronto para escalar?</h2>
        <p>Faça um diagnóstico rápido e descubra como podemos ajudar seu negócio.</p>
        <a href="https://wa.me/5583986476062" target="_blank" rel="noopener noreferrer" class="btn-tech primary">FALAR COM ESPECIALISTA</a>
      </div>
    </div>
  </section>
</main>

<style>
  /* Header */
  .header {
    position: fixed;
    top: 0;
    width: 100%;
    background: rgba(0, 0, 0, 0.7);
    backdrop-filter: blur(10px);
    z-index: 100;
    border-bottom: 1px solid rgba(255, 255, 255, 0.05);
  }

  .header-inner {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 70px;
  }

  .brand-name {
    font-size: 1.5rem;
    font-weight: 700;
    letter-spacing: 1px;
  }

  .brand-name em {
    color: var(--accent-color);
    font-style: normal;
  }

  .nav {
    display: flex;
    align-items: center;
    gap: 30px;
  }

  .nav-link {
    font-weight: 500;
    transition: color 0.2s;
  }
  
  .nav-link:hover {
    color: var(--accent-color);
  }

  /* Hero */
  .hero {
    position: relative;
    padding-top: 180px;
    padding-bottom: 120px;
    text-align: center;
  }

  .hero-eyebrow {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 12px;
    margin-bottom: 24px;
    font-size: 0.9rem;
    color: #888;
    text-transform: uppercase;
    letter-spacing: 1px;
  }

  .eyebrow-line {
    width: 40px;
    height: 1px;
    background: rgba(255, 255, 255, 0.3);
  }

  .hero-title {
    font-size: 4.5rem;
    font-weight: 800;
    line-height: 1.1;
    margin-bottom: 30px;
    display: flex;
    flex-direction: column;
  }

  .hero-title em {
    color: var(--accent-color);
    font-style: normal;
  }

  .hero-title .highlight {
    background: -webkit-linear-gradient(0deg, #fff, #888);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  .hero-subtitle {
    font-size: 1.25rem;
    color: #aaa;
    max-width: 600px;
    margin: 0 auto 40px;
  }

  /* Terminal */
  .terminal {
    background: #0d0d0d;
    border: 1px solid rgba(255,255,255,0.1);
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 20px 40px rgba(0,0,0,0.5);
    max-width: 900px;
    margin: 0 auto;
  }

  .terminal-header {
    background: #1a1a1a;
    padding: 12px 16px;
    display: flex;
    align-items: center;
    border-bottom: 1px solid rgba(255,255,255,0.05);
  }

  .terminal-header .dot {
    width: 12px;
    height: 12px;
    border-radius: 50%;
    margin-right: 8px;
  }

  .dot.red { background: #ff5f56; }
  .dot.yellow { background: #ffbd2e; }
  .dot.green { background: #27c93f; }

  .terminal-header .title {
    margin-left: 20px;
    font-family: monospace;
    font-size: 0.85rem;
    color: #888;
  }

  .terminal-body {
    display: flex;
  }

  .sidebar {
    width: 250px;
    background: #111;
    padding: 20px;
    border-right: 1px solid rgba(255,255,255,0.05);
  }

  .sidebar ul {
    list-style: none;
  }

  .sidebar li {
    font-family: monospace;
    font-size: 0.9rem;
    color: #666;
    margin-bottom: 10px;
    cursor: pointer;
  }

  .sidebar li.active {
    color: var(--accent-color);
  }

  .code-area {
    padding: 24px;
    flex: 1;
    font-family: monospace;
    font-size: 0.95rem;
    background: #0d0d0d;
  }

  .code-area pre {
    margin: 0;
    color: #e6e6e6;
  }

  .comment { color: #6a9955; }
  .keyword { color: #569cd6; }
  .variable { color: #4fc1ff; }
  .property { color: #9cdcfe; }
  .string { color: #ce9178; }
  .function { color: #dcdcaa; }

  .terminal-prompt {
    margin-top: 20px;
    color: #ccc;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .prompt-arrow {
    color: var(--accent-color);
    font-weight: bold;
  }

  .cursor {
    animation: blink 1s step-end infinite;
    color: #fff;
  }

  @keyframes blink {
    50% { opacity: 0; }
  }

  /* FAQ */
  .faq-list {
    max-width: 700px;
    margin: 0 auto;
  }

  .faq-item {
    border-bottom: 1px solid rgba(255,255,255,0.1);
  }

  .faq-question {
    width: 100%;
    text-align: left;
    background: none;
    border: none;
    color: #fff;
    font-size: 1.1rem;
    font-weight: 500;
    padding: 24px 0;
    cursor: pointer;
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-family: inherit;
  }

  .faq-icon {
    color: var(--accent-color);
    font-size: 1.5rem;
    font-weight: 300;
  }

  .faq-answer {
    padding-bottom: 24px;
    color: #aaa;
    line-height: 1.7;
  }

  /* CTA Bottom */
  .cta-card {
    background: rgba(20, 20, 20, 0.8);
    border: 1px solid rgba(255,255,255,0.1);
    border-radius: 12px;
    padding: 60px;
    text-align: center;
    max-width: 800px;
    margin: 0 auto;
  }

  .cta-card h2 {
    font-size: 2.5rem;
    margin-bottom: 16px;
  }

  .cta-card p {
    color: #aaa;
    font-size: 1.1rem;
    margin-bottom: 30px;
  }

  /* Responsive */
  @media (max-width: 768px) {
    .hero-title { font-size: 2.5rem; }
    .terminal-body { flex-direction: column; }
    .sidebar { width: 100%; border-right: none; border-bottom: 1px solid rgba(255,255,255,0.05); }
    .nav { display: none; } /* Simplified for mobile */
  }
</style>
