# Apresentação

- **Projeto:** Desafio final do curso de JavaScript — uma Landing Page de Banda.
- **Contexto:** Material desenvolvido para demonstrar consumo de APIs públicas, manipulação do DOM e integrações com JavaScrpit puro.
- **Objetivo:** Criar uma página responsiva que carregue músicas, imagens, notícias e datas de turnê dinamicamente.
- **Requisitos do desafio:** Para concluir este desafio, cumpra os seguintes requisitos ([texto original com referências](https://app.notesnook.com/notebooks/691c9346d200264f47d3494e)). 

  - Personalizar a Learning Page para uma banda de sua preferência.
  - Utilizar no mínimo dois eventos distintos.
  - Realizar consulta em API.
  - Utilizar no mínimo duas Web APIs.
  - Realizar alteração no DOM.
  - Use modulação para melhor organização (ponto extra).

  

# Recursos / APIs sugeridas

- **JSONPlaceholder (Dados fictícios — datas da turnê / notícias)**:
	- O que faz: API para testes que retorna `users`, `posts`, `todos`, etc.
	- Uso no projeto: usar `https://jsonplaceholder.typicode.com/users` para simular locais e datas da turnê (pegar campos como `name` e `address.city`).
	- Exemplo (JS):

```javascript
fetch('https://jsonplaceholder.typicode.com/users')
	.then(res => res.json())
	.then(data => {
		// Exemplo: pega os 3 primeiros usuários como "datas da turnê"
		const shows = data.slice(0, 3);
		console.log(shows);
	});
```

- **iTunes Search API (Música real — capas e previews)**:
	- O que faz: Retorna faixas, capas de álbuns e `previewUrl` (30s) sem necessidade de chave.
	- Uso no projeto: preencher a seção `#music` e tocar `previewUrl` no player de áudio.
	- Exemplo (JS):

```javascript
fetch('https://itunes.apple.com/search?term=coldplay&entity=song&limit=5')
	.then(res => res.json())
	.then(data => {
		// Exemplo: capa e preview
		console.log(data.results[0].artworkUrl100);
		console.log(data.results[0].previewUrl);
	});
```

- **Lorem Picsum (Imagens aleatórias / galeria / hero)**:
	- O que faz: Fornece imagens de alta qualidade para usar como placeholders reais.
	- Uso no projeto: imagens para o `hero`, galeria ou cards.
	- Uso direto em HTML:

```html
<img src="https://picsum.photos/800/400" alt="Foto Aleatória">
```

- **httpbin (Testar formulário / newsletter)**:
	- O que faz: O endpoint `/post` devolve os dados que você enviou — útil para testar envio de formulários sem backend.
	- Uso no projeto: enviar o formulário de newsletter para `https://httpbin.org/post` e verificar a resposta.
	- Exemplo (JS):

```javascript
const dados = { email: 'usuario@teste.com' };
fetch('https://httpbin.org/post', {
	method: 'POST',
	body: JSON.stringify(dados),
	headers: { 'Content-Type': 'application/json' }
})
	.then(res => res.json())
	.then(response => console.log('Servidor recebeu:', response.json));
```

**Recomendação para o exercício**

- Use a **iTunes Search API** para fazer a seção `#music` funcionar com prévias de áudio reais (`previewUrl`).
- Use **JSONPlaceholder** para gerar dinamicamente a lista de datas da turnê ao invés de deixá-la fixa no HTML.






