# 🎨 ARTCODE-02

## 📌 Descrição
Esta obra apresenta uma grade de círculos que **pulsam em movimento ondulatório**.  
A oscilação é gerada pela função **seno (sin)**, que altera o tamanho dos círculos ao longo do tempo, criando um efeito hipnótico e contínuo.  
O contraste entre o fundo preto e os círculos brancos reforça a estética minimalista, remetendo a padrões de energia, ondas e ritmos visuais.

---

## ✨ Interatividade
Nesta peça é possível **interagir pressionando qualquer tecla**.  
Quando isso acontece, uma imagem da obra é automaticamente salva no computador, permitindo ao espectador capturar sua própria versão da arte.

---

## 🎯 Propósito
- Explorar o conceito de **movimento oscilatório** aplicado a elementos gráficos simples.  
- Demonstrar como funções matemáticas podem gerar efeitos visuais orgânicos e dinâmicos.  
- Permitir que o público se torne coautor, registrando imagens únicas da peça em diferentes momentos.

---

## 🖼️ Imagem
![Prévia da peça](https://github.com/luzbelasouza/codificacao-criativa/blob/main/codex/art0002/art0002.png?raw=true)

---

## 🎮 Interatividade
[![Abrir no OpenProcessing](https://img.shields.io/badge/%F0%9F%8E%AE_Abrir_no_OpenProcessing-ff69b4?style=for-the-badge)](https://openprocessing.org/sketch/2565904)

---

## 📖 Metodologia
1. Definir uma grade de células (`nb x nb`) onde cada célula abriga um círculo.  
2. Usar a função **seno (sin)** combinada com `frameCount` para gerar pulsação constante.  
3. Incluir a função **dist()**, para que a velocidade/defasagem do movimento dependa da distância até o centro.  
4. Adicionar a função **keyPressed()**, que permite salvar imagens estáticas da peça durante a execução.  
5. Criar contraste estético: círculos brancos sobre fundo preto, reforçando o impacto visual.  

---

## 🔎 Code
```javascript
// ==============================
// ARTCODE-02
// ==============================
// Este sketch cria uma grade de círculos que "pulsam" (aumentam e diminuem de tamanho)
// O efeito é gerado pelo uso da função seno (sin), criando movimento em ondas
// ==============================

// Variáveis globais
let nb = 20;         // número de linhas e colunas da grade (a grade será nb x nb)
let dim = 0;         // tamanho de cada célula da grade (será calculado no setup)
let margin = 60;     // margem branca ao redor do desenho
let f = 0.25;        // fator que controla o tamanho dos círculos (será alterado no draw)
let frequence = 1.5; // velocidade da oscilação (quanto maior, mais rápido o movimento)
let x, y;            // coordenadas de cada célula (calculadas dentro dos loops)

function setup() {
  createCanvas(600, 600); // cria a tela 600x600 pixels
  // calcula o tamanho real de cada célula da grade
  dim = (width - 2 * margin) / nb; 
  angleMode(DEGREES); // muda o cálculo do seno/cosseno para graus (em vez de radianos)
}

function draw() {
  background(0); // fundo preto

  fill(255);     // cor branca para os círculos
  rectMode(CENTER); // caso use retângulos, eles serão desenhados pelo centro

  // dois loops aninhados para percorrer cada célula da grade
  for (let j = 0; j < nb; j = j + 1) {        // linhas (vertical)
    for (let i = 0; i < nb; i = i + 1) {      // colunas (horizontal)
      
      // calcula a posição x,y do centro de cada célula
      x = margin + dim/2 + i * dim;
      y = margin + dim/2 + j * dim;
      
      // calcula o fator de oscilação "f"
      // - sin() cria o movimento de onda
      // - frameCount faz o tempo avançar (animação)
      // - dist() faz com que a oscilação dependa da distância até o centro da tela
      f = sin(frequence * frameCount + 0.5 * dist(width/2, height/2, x, y));
      
      // desenha um círculo no centro da célula
      // o tamanho varia de acordo com "f"
      circle(x, y, f * dim); 
      
      // se quiser testar com quadrados, descomente a linha abaixo:
      // rect(x, y, 0.8 * dim, 0.8 * dim); 
    }
  }
}

function keyPressed() { 
  // ao pressionar qualquer tecla, salva uma imagem do frame atual
  // dica: pressione a tecla espaço para salvar um print da arte
  save("artcode-02.png"); 
}

