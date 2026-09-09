# Calculadora do Retiro

Página única em HTML, CSS e JavaScript que calcula o valor total do retiro com base na quantidade de participantes informada.

Sem backend, sem build, sem dependências além de uma fonte do Google Fonts — é só abrir o arquivo `index.html` no navegador ou publicar como estático (ex: GitHub Pages).

## Como funciona

O usuário informa três quantidades:

- **Adultos**
- **Adolescentes (12 anos ou mais)** — pagam como adulto
- **Menores de 12 anos** — não pagam quarto, mas pagam ônibus e inscrição

Com base nisso, a página calcula automaticamente:

| Item | Regra |
|---|---|
| Quarto | Só adultos e adolescentes. Valor por pessoa varia pela quantidade de pagantes (faixas) |
| Ônibus | Todo mundo paga (adultos, adolescentes e crianças), valor fixo por pessoa |
| Inscrição | Todo mundo paga, valor fixo por pessoa |
| Salão | Por família — cada 2 adultos contam como 1 família |

O total e o valor médio por pessoa são atualizados em tempo real conforme os contadores mudam.

## Valores atuais

Os valores estão fixos diretamente no código, no início do bloco `<script>` do `index.html`:

```js
const RATES = {
  bus: 240.00,
  inscricao: 70.00,
  salao: 321.20
};

const ROOM_TIERS = [
  { min: 1, max: 2, valor: 2133.81 },
  { min: 1, max: 3, valor: 1991.43 },
  { min: 1, max: 4, valor: 1896.61 }
];
```

- `RATES.bus` — valor da poltrona do ônibus, por pessoa
- `RATES.inscricao` — valor da inscrição, por pessoa
- `RATES.salao` — valor do salão, por família (2 adultos = 1 família)
- `ROOM_TIERS` — faixas de valor do quarto por pessoa, conforme o total de pagantes (adultos + adolescentes). Grupos acima da maior faixa cadastrada usam o valor da última faixa.

Para atualizar preços, edite essas constantes e publique de novo — não há painel de configuração na interface.

## Publicar no GitHub Pages

1. Suba o arquivo como `index.html` na raiz do repositório.
2. No repositório, vá em **Settings > Pages**.
3. Em **Branch**, selecione `main` e a pasta `/ (root)`, depois clique em **Save**.
4. O link fica disponível em `https://seu-usuario.github.io/nome-do-repositorio/` após um ou dois minutos.
