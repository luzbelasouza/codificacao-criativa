# 🎨 ARTCODE-01

## 📌 Descrição
Peça inicial do projeto **Codificação Criativa**.  
Explora a construção de padrões geométricos aleatórios usando triângulos em uma grade.

---

<div style="display: flex; gap: 30px; align-items: flex-start;">
  <div style="flex: 1; min-width: 300px;">

```javascript
let nb = 25; //quantidade de linhas
let dim = 10; //posição das linhas
let margin = 20; //tamanho da margem
let x,y;

function setup() {
  createCanvas(550, 550); 
  dim = (width-2*margin)/nb;
  noLoop();
}

function draw() {
  background(255);
    for (let j=0; j<nb; j=j+1){
    for (let i=0; i<nb; i=i+1){
      x = margin + i*dim;
      y = margin + j*dim;
      
      noFill ();
      //stroke(220); 
      //rect (x,y,dim,dim);
     noStroke();
      fill(0);
      let rnd = int (random(0,4));
      if (rnd==0){
         triangle(x+dim, y, x+dim, y+dim, x, y+dim);
      }
      else if (rnd==1){
        triangle(x,y,x+dim, y,x,y+dim);
      }
      else if (rnd==2){
        triangle(x,y,x+dim, y+dim, x,y+dim);
      }
      else {
        triangle(x,y,x+dim, y,x+dim, y+dim);
      }
    }
  }
}

function keyPressed (){
  redraw();
  //permite mudar o padrão pressionando qualquer tecla
}
```

  </div>
  <div style="flex: 1; min-width: 200px;">
    <img src="art0001.png" alt="Prévia da peça" width="200" />
  </div>
</div>

---

## 📖 Metodologia
- **Conceito:** explorar variação aleatória em uma grade geométrica.  
- **Processo:** uso de `random()` para criar triângulos orientados de diferentes formas.  
- **Objetivo:** introduzir aleatoriedade como elemento estético fundamental.  
