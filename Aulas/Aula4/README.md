# **Aula: CSS Grid e Design Responsivo**

## **📌 Introdução**

Vamos aprender sobre **CSS Grid**, uma ferramenta poderosa para criar layouts modernos na web. 

Já aconteceu de você tentar alinhar elementos em um site e nada ficar no lugar certo? Ou já tentou usar `float` e `position` e ficou frustrado? O **CSS Grid** veio para resolver esse problema e permitir que a gente crie layouts organizados e flexíveis de forma muito mais fácil! 😃

------

## **🔹 5.1. Introdução a Grids**

O **CSS Grid** é um sistema baseado em **linhas e colunas** que nos permite organizar os elementos de um site de forma estruturada.

### 🏗️ **O que é Grid?**

Imagine uma folha quadriculada. Agora, pense que cada quadrado pode conter um elemento do seu site, como um menu, um texto ou uma imagem. O CSS Grid funciona assim!

📌 **Por que usar Grid?**
 ✅ Facilita a organização dos elementos da página
 ✅ Torna o site responsivo de forma mais simples
 ✅ Substitui métodos antigos como `float` e `flexbox` em layouts mais complexos

------

## **🔹 5.2. Propriedades Gerais dos Grids**

Agora que já entendemos o conceito, vamos colocar a mão no código!

### **Propriedades do Contêiner (Pai)**

O primeiro passo para criar um **Grid** é transformar um elemento em um "contêiner de grid" com a propriedade `display: grid;`.

```css
.container {
  display: grid;
}
```

### **📏 Criando Colunas e Linhas**

Podemos definir o número de colunas e linhas usando:

```css
.container {
  display: grid;
  grid-template-columns: 100px 200px 100px; /* 3 colunas */
  grid-template-rows: 150px 150px; /* 2 linhas */
}
```

### **📌 grid-template-columns e grid-template-rows**

Usamos essas propriedades para definir **quantas colunas e linhas** teremos e seus tamanhos.

```css
.container {
  display: grid;
  grid-template-columns: 1fr 2fr 1fr; /* A segunda coluna será duas vezes maior que as outras */
  grid-template-rows: auto;
}
```

------

### **📌 grid-template-areas**

Podemos nomear áreas do grid para organizar os elementos.

```css
.container {
  display: grid;
  grid-template-areas:
    "header header"
    "menu content"
    "footer footer";
}
```

Agora, no CSS dos itens, usamos `grid-area`:

```css
.header { grid-area: header; }
.menu { grid-area: menu; }
.content { grid-area: content; }
.footer { grid-area: footer; }
```

------

### **📌 Espaçamento entre os elementos (column-gap e row-gap)**

Podemos definir o espaço entre as colunas e as linhas usando `column-gap` e `row-gap`.

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  column-gap: 20px; /* Espaço entre as colunas */
  row-gap: 10px; /* Espaço entre as linhas */
}
```

------

## **🔹 5.3. CSS Grids - Flexibilização de Itens**

Os itens dentro do grid podem ser manipulados individualmente.

```css
.item1 {
  grid-column: 1 / 3; /* Ocupa da primeira até a terceira coluna */
  grid-row: 1 / 2; /* Ocupa a primeira linha */
}
```

### **Áreas da Grade**

É possível combinar `grid-template-areas` com `grid-column` e `grid-row` para mais controle.

```css
.container {
  display: grid;
  grid-template-columns: 1fr 2fr;
  grid-template-rows: auto;
  grid-template-areas:
    "header header"
    "menu content"
    "footer footer";
}
.header { grid-area: header; }
.menu { grid-area: menu; }
.content { grid-area: content; }
.footer { grid-area: footer; }
```

------

## **🔹 5.4. Distribuição dos Elementos em Grids**

Podemos alinhar os itens dentro do grid com `justify-items` e `align-items`:

```css
.container {
  display: grid;
  justify-items: center; /* Centraliza horizontalmente */
  align-items: center; /* Centraliza verticalmente */
}
```

📌 Para alinhar os itens em relação ao contêiner:

```css
.container {
  display: grid;
  justify-content: space-between; /* Distribui os itens horizontalmente */
  align-content: center; /* Alinha os itens verticalmente */
}
```

------

## **🔹 5.5. Design Responsivo**

📌 **O que é design responsivo?**
 É a capacidade de um site **se adaptar** a diferentes tamanhos de tela.

💡 **Por que é importante?**

- A maioria dos acessos à internet vem de celulares 📱
- Sites responsivos são mais fáceis de usar
- O Google prioriza sites responsivos no ranking de buscas

------

## **🔹 5.6. Mobile First**

O conceito de **Mobile First** significa que primeiro criamos o layout para telas menores e depois ajustamos para telas maiores.

📌 **Exemplo prático de Mobile First**

```css
.container {
  display: grid;
  grid-template-columns: 1fr; /* Começamos com uma única coluna */
}

/* Para telas maiores que 768px, usamos duas colunas */
@media (min-width: 768px) {
  .container {
    grid-template-columns: 1fr 1fr;
  }
}
```

📌 **Outro exemplo aplicando Media Query para mudar o layout em telas grandes**

```css
@media (min-width: 1024px) {
  .container {
    grid-template-columns: repeat(3, 1fr);
  }
}
```

Isso significa que:
 ✅ **Em celulares**, os itens ficam em uma única coluna
 ✅ **Em tablets**, usamos duas colunas
 ✅ **Em computadores**, usamos três colunas

------

## **📌 Conclusão** 🎉

 ✅ O que é CSS Grid e como usá-lo
 ✅ Como criar colunas, linhas e espaçamentos
 ✅ Como distribuir os elementos corretamente
 ✅ Como fazer **design responsivo**
 ✅ Como aplicar **Mobile First**

Agora é hora de praticar! Tente criar um layout simples e testar diferentes tamanhos de tela.



# 📌 **Media Queries no CSS**

Agora vamos focar em **Media Queries**, que são fundamentais para criar um design responsivo. 

------

## **🔹 O que são Media Queries?**

As **Media Queries** permitem que o CSS **adapte o estilo do site de acordo com o tamanho da tela**. Isso significa que podemos ter um layout diferente para celular, tablet e computador, tudo dentro do mesmo código.

💡 **Como funciona?**
 Elas funcionam como uma **condição no CSS**. Se a condição for atendida (por exemplo, se a tela for menor que 600px), um conjunto de estilos será aplicado.

------

## **🔹 Sintaxe Básica de Media Queries**

A estrutura de uma Media Query é assim:

```css
@media (condição) {
  /* CSS que será aplicado quando a condição for atendida */
}
```

📌 **Exemplo básico**
 Mudando a cor do fundo para azul **quando a tela for menor que 600px**:

```css
@media (max-width: 600px) {
  body {
    background-color: blue;
  }
}
```

Se a tela tiver **menos de 600 pixels**, o fundo do site ficará azul. Se for maior, ele não muda.

------

## **🔹 Como Usar Media Queries para um Layout Responsivo?**

### **📌 Exemplo Prático 1 - Layout Diferente para Celular, Tablet e PC**

Aqui vamos criar um **layout flexível** que muda dependendo do tamanho da tela.

```css
.container {
  display: grid;
  grid-template-columns: 1fr; /* Começa com uma coluna única (mobile) */
  gap: 20px;
}

/* Para tablets (largura mínima de 768px) */
@media (min-width: 768px) {
  .container {
    grid-template-columns: 1fr 1fr; /* Duas colunas */
  }
}

/* Para computadores (largura mínima de 1024px) */
@media (min-width: 1024px) {
  .container {
    grid-template-columns: 1fr 1fr 1fr; /* Três colunas */
  }
}
```

🔹 **O que acontece aqui?**
 ✅ **Em celulares**, os itens aparecem um abaixo do outro (coluna única).
 ✅ **Em tablets**, os itens aparecem em **duas colunas**.
 ✅ **Em computadores**, os itens aparecem em **três colunas**.

------

### **📌 Exemplo Prático 2 - Alterando o Tamanho da Fonte**

Podemos usar Media Queries para alterar a fonte e melhorar a legibilidade em telas grandes.

```css
body {
  font-size: 16px;
}

/* Para telas maiores que 768px */
@media (min-width: 768px) {
  body {
    font-size: 18px;
  }
}

/* Para telas maiores que 1024px */
@media (min-width: 1024px) {
  body {
    font-size: 20px;
  }
}
```

🔹 **O que acontece?**
 ✅ **No celular**, a fonte será **16px**.
 ✅ **No tablet**, a fonte será **18px**.
 ✅ **No computador**, a fonte será **20px**.

Isso melhora a leitura do site em dispositivos diferentes!

------

### **📌 Exemplo Prático 3 - Alterando um Menu para Mobile**

Normalmente, em computadores o menu é **horizontal**, mas em celulares ele precisa ser **vertical** para caber na tela. Vamos criar essa adaptação com Media Queries.

```css
.menu {
  display: flex;
  justify-content: space-around;
  background-color: #333;
  padding: 10px;
}

.menu a {
  color: white;
  text-decoration: none;
  padding: 10px;
}

/* Para telas menores que 768px */
@media (max-width: 768px) {
  .menu {
    flex-direction: column; /* Deixa o menu na vertical */
    align-items: center;
  }
}
```

🔹 **O que acontece?**
 ✅ **Em telas grandes**, o menu fica **na horizontal**.
 ✅ **Em telas pequenas**, ele vira **vertical** e centralizado.

------

### **📌 Exemplo Prático 4 - Mobile First: Começando pelo Celular**

O conceito de **Mobile First** significa que começamos escrevendo o CSS para celulares e, depois, adicionamos estilos para telas maiores.

```css
.container {
  display: grid;
  grid-template-columns: 1fr; /* Começamos com 1 coluna */
  gap: 20px;
}

/* Para telas maiores que 600px (tablet) */
@media (min-width: 600px) {
  .container {
    grid-template-columns: repeat(2, 1fr); /* Duas colunas */
  }
}

/* Para telas maiores que 1024px (computador) */
@media (min-width: 1024px) {
  .container {
    grid-template-columns: repeat(3, 1fr); /* Três colunas */
  }
}
```

🔹 **Por que usar Mobile First?**
 ✅ Sites carregam mais rápido em celulares 📱
 ✅ Melhor adaptação para diferentes dispositivos
 ✅ Melhor experiência para usuários

------

## **🔹 Resumo Rápido**

✅ **Media Queries permitem mudar o CSS com base no tamanho da tela**
 ✅ **Usamos `max-width` para telas menores e `min-width` para telas maiores**
 ✅ **O Mobile First começa com estilos para celular e adiciona regras para telas maiores**

------

# **📌 Exemplos Práticos com HTML + CSS**

------

## **📌 Exemplo 1: Criando um Layout Responsivo com CSS Grid**

Neste exemplo, vamos criar um layout básico com **CSS Grid**, que se ajusta automaticamente em diferentes tamanhos de tela.

### **📄 Código Completo (HTML + CSS)**

```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Grid Responsivo</title>
    <style>
        /* Estilos gerais */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f5f5f5;
        }

        .container {
            display: grid;
            grid-template-columns: 1fr; /* Começa com uma única coluna */
            gap: 20px;
            padding: 20px;
        }

        .box {
            background-color: #007bff;
            color: white;
            padding: 20px;
            text-align: center;
            border-radius: 8px;
        }

        /* Layout para tablets (largura mínima de 600px) */
        @media (min-width: 600px) {
            .container {
                grid-template-columns: 1fr 1fr; /* Duas colunas */
            }
        }

        /* Layout para computadores (largura mínima de 1024px) */
        @media (min-width: 1024px) {
            .container {
                grid-template-columns: 1fr 1fr 1fr; /* Três colunas */
            }
        }
    </style>
</head>
<body>

    <div class="container">
        <div class="box">Caixa 1</div>
        <div class="box">Caixa 2</div>
        <div class="box">Caixa 3</div>
        <div class="box">Caixa 4</div>
    </div>

</body>
</html>
```

🔹 **O que esse código faz?**
 ✅ Em **celulares**, os itens ficam em uma única coluna.
 ✅ Em **tablets (600px ou mais)**, os itens são organizados em **duas colunas**.
 ✅ Em **computadores (1024px ou mais)**, os itens são organizados em **três colunas**.

------

## **📌 Exemplo 2: Criando um Menu Responsivo com Media Queries**

Agora, vamos criar um **menu responsivo**. Em telas grandes, ele fica na **horizontal**, e em telas pequenas (celulares), ele vira **vertical**.

### **📄 Código Completo (HTML + CSS)**

```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Menu Responsivo</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
        }

        .menu {
            display: flex;
            justify-content: space-around;
            background-color: #333;
            padding: 10px;
        }

        .menu a {
            color: white;
            text-decoration: none;
            padding: 10px;
        }

        /* Quando a tela for menor que 768px (celulares), o menu fica vertical */
        @media (max-width: 768px) {
            .menu {
                flex-direction: column;
                align-items: center;
            }
        }
    </style>
</head>
<body>

    <nav class="menu">
        <a href="#">Início</a>
        <a href="#">Sobre</a>
        <a href="#">Serviços</a>
        <a href="#">Contato</a>
    </nav>

</body>
</html>
```

🔹 **O que esse código faz?**
 ✅ **Em telas grandes**, o menu fica **horizontal**.
 ✅ **Em telas pequenas**, o menu vira **vertical** e fica centralizado.

------

## **📌 Exemplo 3: Criando um Layout Mobile First**

Agora, vamos criar um layout seguindo o **conceito de Mobile First**. Ou seja, começamos pelo layout para celulares e depois adicionamos regras para telas maiores.

### **📄 Código Completo (HTML + CSS)**

```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mobile First</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
        }

        .container {
            display: grid;
            grid-template-columns: 1fr; /* Inicia com 1 coluna */
            gap: 20px;
            padding: 20px;
        }

        .box {
            background-color: #28a745;
            color: white;
            padding: 20px;
            text-align: center;
            border-radius: 8px;
        }

        /* Para telas maiores que 600px (tablet) */
        @media (min-width: 600px) {
            .container {
                grid-template-columns: repeat(2, 1fr); /* Duas colunas */
            }
        }

        /* Para telas maiores que 1024px (computador) */
        @media (min-width: 1024px) {
            .container {
                grid-template-columns: repeat(3, 1fr); /* Três colunas */
            }
        }
    </style>
</head>
<body>

    <div class="container">
        <div class="box">Caixa 1</div>
        <div class="box">Caixa 2</div>
        <div class="box">Caixa 3</div>
        <div class="box">Caixa 4</div>
    </div>

</body>
</html>
```

🔹 **O que acontece nesse código?**
 ✅ **Em celulares**, os itens ficam **em uma única coluna**.
 ✅ **Em tablets (600px ou mais)**, os itens aparecem em **duas colunas**.
 ✅ **Em computadores (1024px ou mais)**, os itens aparecem em **três colunas**.

## 

📌 **O que aprendemos?**
 ✅ Como usar **CSS Grid** para organizar elementos
 ✅ Como aplicar **Media Queries** para tornar um site **responsivo**
 ✅ Como criar um **menu responsivo** que muda dependendo do tamanho da tela
 ✅ Como aplicar o conceito de **Mobile First** para melhorar a experiência no celular

Agora, copie e cole esses códigos no seu editor de texto favorito e teste no navegador! 🚀

# **📌 Usando "Áreas" do CSS Grid para Distribuir Seções HTML**

A técnica de **áreas no CSS Grid** permite **nomear partes do layout** e organizar os elementos de forma visual, sem precisar manipular `grid-column` e `grid-row` diretamente. Isso torna o código mais **legível e intuitivo**.

------

## **📌 O que é a técnica de "áreas" no CSS Grid?**

A ideia é definir um **layout nomeado**, onde cada área recebe um **identificador único**. Em vez de manipular cada elemento individualmente, usamos `grid-template-areas` para criar uma estrutura clara.

**🎯 Benefícios da técnica de áreas:** ✅ Código mais limpo e organizado
 ✅ Melhor visualização da estrutura da página
 ✅ Fácil manutenção e alteração

------

## **📌 Como funciona?**

1️⃣ **Criamos o HTML** e damos nomes às seções (exemplo: `header`, `menu`, `content`, `extra`, `footer`).
 2️⃣ **Definimos a grade no CSS** e usamos `grid-template-areas` para posicionar cada seção.
 3️⃣ **Aplicamos `grid-area` em cada elemento para que ele ocupe o espaço definido.**

------

## **📄 Código Completo (HTML + CSS)**

Aqui está um exemplo prático usando **áreas no CSS Grid**.

------

### **📄 Arquivo HTML: `index.html`**

```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Layout Responsivo com CSS Grid Áreas</title>
    <link rel="stylesheet" href="styles.css"> <!-- Importa o CSS -->
</head>
<body>

    <header class="header">Cabeçalho</header>

    <div class="grid-container">
        <aside class="menu">Menu Lateral</aside>
        <main class="content">Conteúdo Principal</main>
        <aside class="extra">Seção Extra</aside>
    </div>

    <footer class="footer">Rodapé</footer>

</body>
</html>
```

------

### **📄 Arquivo CSS: `styles.css`**

```css
/* Reset padrão */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

/* Estilos gerais */
body {
    font-family: Arial, sans-serif;
    background-color: #f5f5f5;
    display: grid;
    grid-template-rows: auto 1fr auto; /* Cabeçalho (auto), Conteúdo (1fr), Rodapé (auto) */
    height: 100vh;
}

/* Estilos do Cabeçalho e Rodapé */
.header, .footer {
    background-color: #007bff;
    color: white;
    text-align: center;
    padding: 20px;
    font-size: 24px;
}

/* Estilos da Grade Principal */
.grid-container {
    display: grid;
    grid-template-areas: 
        "menu content"
        "menu extra";
    grid-template-columns: 1fr 3fr; /* O menu ocupa 1 parte, o conteúdo 3 partes */
    grid-template-rows: auto 1fr;
    gap: 10px;
    padding: 20px;
}

/* Aplicando as Áreas */
.menu {
    grid-area: menu;
    background-color: white;
    padding: 20px;
    font-size: 20px;
    border-radius: 8px;
    box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
}

.content {
    grid-area: content;
    background-color: white;
    padding: 20px;
    font-size: 20px;
    border-radius: 8px;
    box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
}

.extra {
    grid-area: extra;
    background-color: white;
    padding: 20px;
    font-size: 20px;
    border-radius: 8px;
    box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
}

/* Layout Responsivo */

/* 📌 Para tablets (600px a 1024px): Menu lateral e conteúdo em duas colunas */
@media (max-width: 1024px) {
    .grid-container {
        grid-template-areas:
            "menu content"
            "menu extra";
        grid-template-columns: 1fr 2fr;
    }
}

/* 📌 Para celulares (menores que 600px): Tudo empilhado */
@media (max-width: 600px) {
    .grid-container {
        grid-template-areas:
            "menu"
            "content"
            "extra";
        grid-template-columns: 1fr;
    }
}
```

------

## **📌 Explicação do Código**

### **🔹 Passo 1: Criamos o Layout no CSS**

Usamos `grid-template-areas` para definir o layout de forma **visual e organizada**.

```css
grid-template-areas: 
    "menu content"
    "menu extra";
```

- O **menu** ocupa a primeira coluna e se estende para duas linhas.
- O **conteúdo principal** ocupa a segunda coluna na **primeira linha**.
- A **seção extra** ocupa a segunda coluna na **segunda linha**.

------

### **🔹 Passo 2: Ligamos as áreas aos elementos**

Cada seção do HTML recebe um nome correspondente no CSS:

```css
.menu { grid-area: menu; }
.content { grid-area: content; }
.extra { grid-area: extra; }
```

Agora, o **CSS sabe onde posicionar cada item** no grid automaticamente.

------

### **🔹 Passo 3: Adaptamos para telas menores**

1️⃣ **Para tablets (600px a 1024px)** → O layout mantém **duas colunas**, mas reduz o tamanho do conteúdo.
 2️⃣ **Para celulares (< 600px)** → O layout **se adapta para uma única coluna**, empilhando os elementos.

```css
@media (max-width: 600px) {
    .grid-container {
        grid-template-areas:
            "menu"
            "content"
            "extra";
        grid-template-columns: 1fr;
    }
}
```

Agora, em telas pequenas, o layout muda automaticamente para **colunas únicas**, garantindo **boa usabilidade em dispositivos móveis**. 📱

------

## **📌 Testando o Código**

1️⃣ **Crie um arquivo `index.html` e cole o código HTML.**
 2️⃣ **Crie um arquivo `styles.css` e cole o código CSS.**
 3️⃣ **Abra o `index.html` no navegador** e redimensione a tela para ver o layout mudar automaticamente!

------

## **📌 Resumo do que aprendemos**

✅ O que são **áreas no CSS Grid** e como utilizá-las.
 ✅ Como distribuir seções de forma **visual e organizada**.
 ✅ Como criar um **layout responsivo** que se adapta automaticamente.
 ✅ Como usar **Media Queries** para garantir um **bom design para mobile**.

