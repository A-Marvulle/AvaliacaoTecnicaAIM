# AVALIAÇÃO TÉCNICA

1- Ao invés da mensagem de porcentagem de desconto no PIX, informar o desconto em REAL da diferença entre o preço de antes e o atual da página do produto (Lembre-se que deverá ser aplicado valores reais da página do produto, ou seja, é preciso que a diferença dos valores seja automática e não manualmente inserida).

2- Esconder o botão de "Adicionar a Sacola" e alterar a cor do botão "Comprar".

Durante o scroll da página, é exibida uma caixa de informações flutuante com preços e botões de compra:

3- Aplicar a mesma alteração do ponto 1 nesta caixa flutuante.

4- Alterar o botão "Adicionar à Sacola" pelo de "Comprar". O botão deverá ter a cor nova e também a mesma funcionalidade do botão comprar original.

[Imagem do Teste](https://drive.google.com/file/d/1pAt08bk-WybeuUDW2S48YeE73e-KLmIc/view)

# Resposta

```
// Sumir com o botão de Carrinho
document.querySelector("div.sc-dhKdcB.kbCiGN > div:nth-child(2) > button").style.display = 'none';

// Trocar cor do botão
document.querySelector("div.sc-dhKdcB.kbCiGN > div:nth-child(1) > button").style.backgroundColor = "rgb(0, 134, 255)";

// Preço original
const originalPriceElement = document.querySelector('div.sc-dcJsrY.bCfntu > div > div > div > p.sc-kpDqfm.gBEKKZ.sc-gEkIjz.hhsvJQ');
const originalPrice = parseFloat(originalPriceElement.innerText.replace('R$', '').replace('.', '').replace(',', '.'));

// Preço novo
const newPriceElement = document.querySelector('div.sc-dcJsrY.bCfntu > div:nth-child(1) > div > div > div > p');
const newPrice = parseFloat(newPriceElement.innerText.replace('R$', '').replace('.', '').replace(',', '.'));

// Desconto
const discountElement = document.querySelector('div.sc-dcJsrY.bCfntu > div:nth-child(1) > div > div > span');
const discountValue = originalPrice - newPrice;
const discountValueFormatted = discountValue.toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' });

// Alterar desconto
discountElement.innerHTML = discountValueFormatted + " de <b>desconto</b>";

// Função para verificar se um elemento está visível
function isElementVisible(element) {
    return element && element.offsetParent !== null;
}

// Barra
const visibleElement = document.querySelector("div.sc-bguTAn.SeUWX > div.sc-dhKdcB.gpBqsH");
const hiddenElement = document.querySelector("div.sc-bguTAn.jhTCbe > div.sc-dhKdcB.gpBqsH");

if (isElementVisible(visibleElement)) {
    // Alterar usando query do visível
    document.querySelector("div.sc-bguTAn.SeUWX > div.sc-dhKdcB.gpBqsH > div.sc-fqkvVR.dQuACk.sc-BGXOW.duTIoJ > button").style.backgroundColor = "rgb(0, 134, 255)";
    document.querySelector("div.sc-bguTAn.SeUWX > div.sc-dhKdcB.gpBqsH > div.sc-fqkvVR.dQuACk.sc-BGXOW.duTIoJ > button > label").innerText = " Comprar";
    const discount = document.querySelector('div.sc-bguTAn.SeUWX > div.sc-dhKdcB.gpBqsH > div.sc-fqkvVR.dQuACk.sc-hKosrt.jOZUKx > div > div > small');
    discount.style.color = "rgb(89, 192, 11)";
    discount.innerHTML = "(" + discountValueFormatted + " de <b>desconto</b>)";
} else if (isElementVisible(hiddenElement)) {
    // Alterar usando query do oculto
    document.querySelector("div.sc-bguTAn.jhTCbe > div.sc-dhKdcB.gpBqsH > div.sc-fqkvVR.dQuACk.sc-BGXOW.duTIoJ > button").style.backgroundColor = "rgb(0, 134, 255)";
    document.querySelector("div.sc-bguTAn.jhTCbe > div.sc-dhKdcB.gpBqsH > div.sc-fqkvVR.dQuACk.sc-BGXOW.duTIoJ > button > label").innerText = " Comprar";
    const discount = document.querySelector('div.sc-bguTAn.jhTCbe > div.sc-dhKdcB.gpBqsH > div.sc-fqkvVR.dQuACk.sc-hKosrt.jOZUKx > div > div > small');
    discount.style.color = "rgb(89, 192, 11)";
    discount.innerHTML = "(" + discountValueFormatted + " de <b>desconto</b>)";
}
```

## Exemplos
- [PS5](https://www.magazineluiza.com.br/console-sony-playstation-5-standard-edition-825gb-ps5/p/hcb4a552ed/ga/gps5/)
- [Lava e Seca](https://www.magazineluiza.com.br/lava-e-seca-lg-12kg-smart-vc4-cv5012pc4-com-inteligencia-atificial-agua-quente-e-fria-prata/p/238058200/ed/ela1/)
- [Celular](https://www.magazineluiza.com.br/smartphone-samsung-galaxy-a05-128gb-preto-4g-octa-core-4gb-ram-67-cam-dupla-selfie-8mp/p/238036500/te/ga05/)
