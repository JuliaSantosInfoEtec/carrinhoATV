# Projeto Carinho!

<p align="center">
  <img src="#>
</p>


// 
const produtos = [
    {
        id: "1",
        nome: "Informática para Internet: Interfaces Web II",
        prof: "Prof. Kelly",
        preco_de: 80,
        preco_por: 50,
        descricao: "O melhor curso de Javascript",
        imagem: "./assets/1.png",

    },
    {
        id: "2",
        nome: "Gestão de conteúdo Web II",
        prof: "Prof. Kelly",
        preco_de: 80,
        preco_por: 50,
        descricao: "O melhor curso de Javascript",
        imagem: "./assets/3.png",
    }
];

function renderizaProdutos() {
    //Está declarando uma variavel para armazenar o html gerado
    let html = "";
    for (let i = 0; i < produtos.length; i++) {
        html = html + criaProduto(produtos[i], i);
    }
    return html;
}

function criaProduto (produto, index) {
    return `
    <div class="curso"> 
    <img class='inicio' title="t" src="${produto.imagem}" />
    <div class="curso-info">
    <h4>${produto.nome}</h4>
    <p>${produto.prof}</p>
    <p>${produto.descricao}</p>
    </div>
    <div class="curso-preco">
    <span class="preco-de">R$${produto.preco_de}</span>
    <span class="preco-por">R$${produto.preco_por}</span>
    <button class="btncar btn-add" data-index="${index}"></button>
    </div>
    </div>
     `;
}

const container = document.querySelector("#container")
container.innerHTML= renderizaProdutos();

const carrinhoItens = {};

function renderizaCarrinho() {
    let html = '';
    for (let produtoId in carrinhoItens) {
        html = html + criaItemCarrinho (carrinhoItens[produtoId]);
    }
    document.querySelector('.carrinho_itens').innerHTML = html;

}

function criaItemCarrinho(produto) {
    return `
    <div class="carrinho_compra">
    <h4>${produto.nome}</h4>
    <p>Preço unidade: ${produto.preco_por}
    Quantidade: ${produto.quantidade}</p>
    <p>Valor: R$${produto.preco_por*produto.quantidade} </p>
    <button data-produto-id="${produto.id}" class="btn-remove">
    </button>
    </div>
    `;}

function criaCarrinhoTotal (){
    let total = 0;
    for (let produtoId in carrinhoItens) {
        total = total + carrinhoItens[produtoId].preco_por * carrinhoItens[produtoId].quantidade;
    }
    document.querySelector('.carrinho_total').innerHTML = `
    <h4> Total:<strong> R$${total} </strong></h4>
    <a href="#" target="_blank">
    <ion-icon name="card-outline"></ion-icon>
    <strong> Comprar Agora</strong>
    </a>
    `;}

    function adicionaItemNoCarrinho(produto) {
        if (!carrinhoItens[produto.id]) {
            carrinhoItens[produto.id] = produto;
            carrinhoItens[produto.id].quantidade = 0;
        }carrinhoItens[produto.id].quantidade++;
        renderizaCarrinho();
        criaCarrinhoTotal();
        }
    
        document.body.addEventListener('click', function (event) {
            const elemento = event.target;
            if(elemento.classList.contains('btn-add')) {
                const index = parseInt(elemento.getAttribute('data-index'), 10);
            const produto = produtos[index];

            adicionaItemNoCarrinho(produto);
                    }
            if (elemento.classList.contains('btn-remove')) {
                const produtoId = elemento.getAttribute('data-produto-id');
                if (carrinhoItens[produtoId].quantidade <= 1) {
                delete carrinhoItens[produtoId];
                }
                else {
                    --carrinhoItens[produtoId].quantidade;
                }
                renderizaCarrinho();
                criaCarrinhoTotal();
            }
        });

## O carinho deve ser controlado usando as seguintes técnicas:

1. **querySelector():** Este método é usado para selecionar um elemento específico pelo seu seletor CSS. No caso deste projeto, é usado para selecionar o elemento .curso e os elementos .carrinho_compra, .carrinho_total e .btn-remove.
2. **querySelectorAll():** Este método é usado para selecionar todos os elementos que correspondem a um seletor CSS. No caso deste projeto, é usado para selecionar todos os elementos .btn-add.
3. **addEventListener():** Este método é usado para adicionar um ouvinte de evento a um elemento. No caso deste projeto, é usado para adicionar um ouvinte de evento click aos elementos .btn-add e .btn-remove.
4. **Função renderizaProdutos():** Esta função é usada para renderizar uma lista de produtos na página. A função usa a estrutura de repetição for para percorrer o array de produtos e renderizar um elemento .curso para cada produto.
5. **Função renderizaProduto():** Esta função é usada para renderizar um único produto na página. A função recebe como argumento um objeto produto e retorna um elemento .curso com as informações do produto.
6. **Função renderizaCarrinho():** Esta função é usada para renderizar uma lista de itens de carrinho na página. A função usa a estrutura de repetição for para percorrer o objeto carrinhoItens e renderizar um elemento .carrinho_compra para cada item de carrinho.
7. **Função renderizaItemCarrinho():** Esta função é usada para renderizar um único item de carrinho na página. A função recebe como argumento um objeto item de carrinho e retorna um elemento `.carrinho
8.  **estrutura de repetição - For:**  Esta estrutura de repetição é usada para percorrer uma coleção de elementos. No caso deste projeto, é usada para percorrer o array de produtos e renderizar uma lista de itens de carrinho para cada produto.
9.  aaaaa
