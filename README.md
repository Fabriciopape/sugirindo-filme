let filmes = [
  { nome: "O Incrível Hulk", idade: 12, categorias: ["Ação", "Fantasia", "Ficção Científica"] },
  { nome: "A Múmia", idade: 12, categorias: ["Terror", "Suspense", "Ação"] },
  { nome: "O Espetacular Homem-Aranha", idade: 10, categorias: ["Ação", "Super-Herói", "Ficção Científica"] },
  { nome: "Venom", idade: 14, categorias: ["Ação", "Ficção Científica"] },
  { nome: "It - A Coisa", idade: 16, categorias: ["Terror", "Mistério"] }
];

let idadeSelecionada;
let slider;

function setup() {
  createCanvas(800, 600);
  background(255);
  
  // Cria um slider para selecionar a idade
  slider = createSlider(0, 18, 12);
  slider.position(20, 20);
  slider.style('width', '200px');
}

function draw() {
  background(255);
  
  // Atualiza a idade selecionada com o valor do slider
  idadeSelecionada = slider.value();
  
  // Exibe a idade selecionada
  fill(0);
  textSize(16);
  text(`Idade Selecionada: ${idadeSelecionada}`, 20, 50);
  
  let offsetY = 100; // Espaçamento vertical entre os filmes
  let offsetX = 200; // Espaçamento horizontal entre os filmes e categorias
  let yOffset = 0; // Para controlar a posição Y dos filmes exibidos

  for (let i = 0; i < filmes.length; i++) {
    let filme = filmes[i];

    // Verifica se o filme é apropriado para a idade selecionada
    if (filme.idade <= idadeSelecionada) {
      let x = width / 4; // Posição X dos filmes
      let y = offsetY + yOffset * 100; // Posição Y dos filmes

      // Desenhar retângulo para o filme
      fill(200);
      rect(x - 50, y - 20, 100, 40);
      fill(0);
      text(filme.nome, x, y);

      // Desenhar categorias
      for (let j = 0; j < filme.categorias.length; j++) {
        let categoriaX = x + offsetX; // Posição X das categorias
        let categoriaY = y - 20 + j * 30; // Posição Y das categorias

        // Desenhar linha do filme para a categoria
        stroke(0);
        line(x, y, categoriaX - 50, categoriaY);

        // Desenhar retângulo para a categoria
        fill(150);
        rect(categoriaX - 50, categoriaY - 15, 100, 30);
        fill(0);
        text(filme.categorias[j], categoriaX, categoriaY);
      }
      
      yOffset++; // Incrementa a posição Y para o próximo filme exibido
    }
  }
}
