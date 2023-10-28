# Sorteio de Amigo Secreto Alura

Práitica de lógica de programação através deste desafio de um aplicativo de sorteio de amigo secreto

## 🚀 Funcionalidades

- Sorteio de amigo secreto
- Função para garantir que a pessoa não retire seu próprio nome como amigo secreto
- Função otimizada de embaralhamento da lista de pessoas

## 🛠 Tecnologia aplicada

Javascript, HTML, CSS...

## 🕹 Uso/Exemplos

#### Função de embaralhamento da lista de amigos

```javascript
function embaralhaAmigos(arr) {
  for (let i = arr.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [arr[i], arr[j]] = [arr[j], arr[i]];
  }
}
```

#### Função para realizar o sorteio

```javascript
function realizaSorteio() {
  arrAmigosSorteados.length = 0;

  const arrAmigosEmbaralhados = arrAmigosIncluidos.slice();
  embaralhaAmigos(arrAmigosEmbaralhados);
  console.log(`Embaralhamento n: ${contador}`, arrAmigosEmbaralhados);

  // Verifica se o amigo tirou ele mesmo e retorna o status falso ou verdadeiro
  for (let i = 0; i < arrAmigosIncluidos.length; i++) {
    if (arrAmigosEmbaralhados[i] == arrAmigosIncluidos[i]) {
      return false;
    }
    // Se não tiver erro, adiciona na lista de sorteados
    arrAmigosSorteados.push(arrAmigosEmbaralhados[i]);
  }
  return true;
}
```

#### Função final de sortear

```javascript
function sortear() {
  // Limpa lista de sorteios
  elemListaSorteio.innerHTML = "";

  const sorteioBemSucedido = realizaSorteio();

  if (sorteioBemSucedido) {
    arrAmigosIncluidos.forEach((item, i) => {
      elemListaSorteio.innerHTML += `${item} --> ${arrAmigosSorteados[i]}<br>`;
    });
    console.log("Amigos sorteados", arrAmigosSorteados);
    contador = 1;
  } else {
    contador += 1;
    sortear();
  }
}
```

## Autores

- [@michelsandre](https://www.github.com/michelsandre)
