
# Avisos Recebedoria - Site para GitHub Pages

Este é um site estático (HTML/CSS/JS) que funciona com Firestore (Firebase) e serve como quadro de avisos.

## Estrutura
- `index.html` - página principal
- `styles.css` - estilos
- `app.js` - script auxiliar
- `README.md` - este arquivo

## Configuração do Firebase
O projeto já contém a configuração que você forneceu. No Firestore, espera-se:
- Coleção `usuarios` com documentos que contenham campo `email` igual a `<matricula>@movebuss.local`
- Coleção `avisos` com documentos contendo:
  - `title` (string)
  - `createdAt` (timestamp)
  - `items` (array de objetos `{ text: string, completed: boolean }`)

Exemplo de documento `avisos/mylist`:
```
{
  "title": "Lista 1",
  "createdAt": Timestamp,
  "items": [
    {"text":"Aviso A","completed":false},
    {"text":"Aviso B","completed":true}
  ]
}
```

## Login admin
- Para ser considerado admin, a matrícula deve estar em: `6266, 70029, 4144, 5354`
- A verificação também checa se existe um usuário na coleção `usuarios` com o e-mail `<matricula>@movebuss.local`
- O login é feito no painel (botão **Admin** no canto superior esquerdo)

## Funcionalidades
- Usuários normais: ao abrir o site, podem ver os avisos; dando um duplo clique no painel abre a 'tela preta' com tabela dos avisos. Eles não podem editar ou baixar listas.
- Admins: conseguem criar listas, editar itens, marcar itens como cumpridos (isso atualiza o Firestore), excluir listas e baixar JSON da lista.
- Painel flutuante, arrastável e "fixável".

## Como publicar
- Faça fork / crie um repositório no GitHub e ative **GitHub Pages** apontando para a branch `main` ou `gh-pages` com `/` root.
- Faça commit dos arquivos e acesse a página gerada pelo GitHub Pages.

## Observações
- A autenticação aqui é simples (apenas valida matrícula e existência no Firestore) — se desejar autenticação real, integramos Firebase Auth (pode ser solicitado).
- Ajustes visuais e traduções podem ser feitos editando `styles.css` e `index.html`.
