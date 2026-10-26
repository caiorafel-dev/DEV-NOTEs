# 📝 HTML: Tabelas e Formulários — Notas de Estudo

> Anotações pessoais sobre as principais tags e atributos de **tabelas** e **formulários** em HTML5, com exemplos de código.

---

## 📑 Sumário

1. [Tabelas](#-tabelas)
   - [Tags](#tags-de-tabela)
   - [Atributos](#atributos-de-tabela)
   - [Atributos obsoletos](#atributos-obsoletos-de-tabela)
   - [Exemplo de código](#exemplo-de-tabela)
   - [Boas práticas](#boas-práticas-para-tabelas)
2. [Formulários](#-formulários)
   - [Tags](#tags-de-formulário)
   - [Atributos do `<form>`](#atributos-do-form)
   - [Tipos de `<input>`](#tipos-de-input)
   - [Atributos comuns dos campos](#atributos-comuns-dos-campos)
   - [Validação nativa](#validação-nativa)
   - [Atributos do `<button>`](#atributos-do-button)
   - [Exemplo de código](#exemplo-de-formulário)
   - [Boas práticas](#boas-práticas-para-formulários)
3. [Referências](#-referências)
4. [Autor](#-autor)

---

# 📊 Tabelas

Tabelas servem para apresentar **dados tabulares** (linhas e colunas). Não devem ser usadas para montar o layout da página.

## Tags de tabela

| Tag | Função |
|---|---|
| `<table>` | Container principal da tabela |
| `<caption>` | Título/legenda da tabela. Deve ser o primeiro filho do `<table>` |
| `<colgroup>` | Agrupa colunas para aplicar estilo a elas |
| `<col>` | Define uma coluna (ou várias, com `span`) dentro do `<colgroup>` |
| `<thead>` | Agrupa o cabeçalho da tabela |
| `<tbody>` | Agrupa o corpo (dados) da tabela |
| `<tfoot>` | Agrupa o rodapé (totais, resumos) |
| `<tr>` | Linha da tabela (*table row*) |
| `<th>` | Célula de cabeçalho (*table header*). Negrito e centralizada por padrão |
| `<td>` | Célula de dados (*table data*) |

## Atributos de tabela

| Atributo | Em qual tag | Função |
|---|---|---|
| `colspan` | `<th>`, `<td>` | Faz a célula ocupar várias **colunas** |
| `rowspan` | `<th>`, `<td>` | Faz a célula ocupar várias **linhas** |
| `scope` | `<th>` | Diz se o cabeçalho é de `col`, `row`, `colgroup` ou `rowgroup` (acessibilidade) |
| `headers` | `<th>`, `<td>` | Lista os `id` dos cabeçalhos relacionados à célula (tabelas complexas) |
| `abbr` | `<th>` | Versão abreviada do texto do cabeçalho |
| `span` | `<col>`, `<colgroup>` | Quantidade de colunas que o elemento abrange |
| `id` / `class` | qualquer | Identificação e estilização via CSS |

## Atributos obsoletos de tabela

Estes atributos existiam no HTML antigo e hoje devem ser substituídos por **CSS**:

| Obsoleto | Substituir por |
|---|---|
| `border` | `border` no CSS |
| `cellpadding` | `padding` nas células |
| `cellspacing` | `border-spacing` / `border-collapse` |
| `align`, `valign` | `text-align`, `vertical-align` |
| `bgcolor` | `background-color` |
| `width`, `height` | `width`, `height` no CSS |

## Exemplo de tabela

```html
<table>
  <caption>Catálogo de Livros</caption>

  <colgroup>
    <col style="width: 40%">
    <col style="width: 25%">
    <col style="width: 20%">
    <col style="width: 15%">
  </colgroup>

  <thead>
    <tr>
      <th scope="col">Title</th>
      <th scope="col">Author</th>
      <th scope="col">Genre</th>
      <th scope="col">Publication Year</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>Dom Casmurro</td>
      <td>Machado de Assis</td>
      <td>Romance</td>
      <td>1899</td>
    </tr>
    <tr>
      <td>O Cortiço</td>
      <td>Aluísio Azevedo</td>
      <td>Romance</td>
      <td>1890</td>
    </tr>
    <tr>
      <td>Vidas Secas</td>
      <td>Graciliano Ramos</td>
      <td>Romance</td>
      <td>1938</td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <td colspan="4">Total books = 3</td>
    </tr>
  </tfoot>
</table>
```

### Exemplo com `rowspan` e `colspan`

```html
<table>
  <caption>Horário de Aulas</caption>
  <thead>
    <tr>
      <th scope="col">Horário</th>
      <th scope="col">Segunda</th>
      <th scope="col">Terça</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">08h</th>
      <td rowspan="2">Cálculo (2 horas)</td>
      <td>HTML</td>
    </tr>
    <tr>
      <th scope="row">09h</th>
      <td>CSS</td>
    </tr>
    <tr>
      <th scope="row">10h</th>
      <td colspan="2">Intervalo</td>
    </tr>
  </tbody>
</table>
```

### Estilo básico com CSS

```css
table {
  border-collapse: collapse;
  width: 100%;
}

th, td {
  border: 1px solid #999;
  padding: 8px 12px;
  text-align: left;
}

thead {
  background-color: #eee;
}

caption {
  font-weight: bold;
  margin-bottom: 8px;
}
```

## Boas práticas para tabelas

- Use tabela apenas para **dados**, nunca para layout.
- Sempre use `<caption>` para descrever a tabela.
- Separe a estrutura com `<thead>`, `<tbody>` e `<tfoot>`.
- Use `<th>` para cabeçalhos e `<td>` para dados.
- Use `scope` nos `<th>` para ajudar leitores de tela.
- Mantenha o número de células por linha consistente, considerando `colspan` e `rowspan`.
- Faça a estilização com CSS, não com atributos obsoletos.
- Em telas pequenas, envolva a tabela em um container com `overflow-x: auto`.

---

# 📋 Formulários

Formulários coletam dados do usuário e os enviam para um servidor ou os processam com JavaScript.

## Tags de formulário

| Tag | Função |
|---|---|
| `<form>` | Container do formulário; define para onde e como os dados são enviados |
| `<label>` | Rótulo de um campo. Clicar nele foca o campo associado |
| `<input>` | Campo de entrada. O comportamento muda conforme o `type` |
| `<textarea>` | Campo de texto com várias linhas |
| `<select>` | Lista suspensa de opções |
| `<option>` | Uma opção dentro de `<select>` ou `<datalist>` |
| `<optgroup>` | Agrupa opções dentro de um `<select>` |
| `<datalist>` | Lista de sugestões para um `<input>` (via atributo `list`) |
| `<button>` | Botão (enviar, limpar ou ação personalizada) |
| `<fieldset>` | Agrupa campos relacionados |
| `<legend>` | Título do `<fieldset>` |
| `<output>` | Exibe o resultado de um cálculo |
| `<progress>` | Barra de progresso |
| `<meter>` | Medidor dentro de uma faixa conhecida (ex.: nível de bateria) |

## Atributos do `<form>`

| Atributo | Função | Valores comuns |
|---|---|---|
| `action` | URL que recebe os dados | `/enviar`, `https://...` |
| `method` | Método HTTP do envio | `get`, `post` |
| `enctype` | Formato de codificação dos dados (só com `post`) | `application/x-www-form-urlencoded`, `multipart/form-data`, `text/plain` |
| `target` | Onde mostrar a resposta | `_self`, `_blank`, `_parent`, `_top` |
| `autocomplete` | Ativa ou desativa o preenchimento automático | `on`, `off` |
| `novalidate` | Desativa a validação nativa do navegador | (booleano) |
| `name` | Nome do formulário | texto |
| `accept-charset` | Codificações de caracteres aceitas | `UTF-8` |

> **GET** envia os dados na URL (bom para buscas). **POST** envia no corpo da requisição (bom para dados sensíveis e uploads).

## Tipos de `<input>`

| `type` | Descrição |
|---|---|
| `text` | Texto de uma linha (padrão) |
| `password` | Texto oculto |
| `email` | E-mail, com validação de formato |
| `tel` | Telefone |
| `url` | Endereço web, com validação de formato |
| `search` | Campo de busca |
| `number` | Número, com `min`, `max` e `step` |
| `range` | Controle deslizante |
| `date` | Data |
| `time` | Hora |
| `datetime-local` | Data e hora locais |
| `month` | Mês e ano |
| `week` | Semana do ano |
| `color` | Seletor de cor |
| `checkbox` | Caixa de marcação (zero, uma ou várias opções) |
| `radio` | Escolha **única** dentro de um grupo (mesmo `name`) |
| `file` | Seleção de arquivo |
| `hidden` | Campo oculto, envia um valor sem mostrar |
| `submit` | Botão que envia o formulário |
| `reset` | Botão que restaura os valores iniciais |
| `button` | Botão sem ação padrão (uso com JavaScript) |
| `image` | Botão de envio em forma de imagem |

## Atributos comuns dos campos

| Atributo | Função |
|---|---|
| `name` | Nome do campo; é a chave dos dados enviados. **Sem `name`, o campo não é enviado** |
| `id` | Identificador único; liga o campo ao `<label for="...">` |
| `value` | Valor inicial (ou valor enviado, em `radio` e `checkbox`) |
| `placeholder` | Dica exibida enquanto o campo está vazio |
| `required` | Campo obrigatório |
| `disabled` | Desativa o campo; **não é enviado** |
| `readonly` | Somente leitura; **é enviado** |
| `autofocus` | Foca o campo ao carregar a página |
| `autocomplete` | Sugestão de preenchimento (`name`, `email`, `off`...) |
| `checked` | Marca `checkbox` ou `radio` inicialmente |
| `multiple` | Permite vários valores (`file`, `email`, `<select>`) |
| `accept` | Tipos de arquivo aceitos em `type="file"` (ex.: `image/*`, `.pdf`) |
| `list` | Liga o campo a um `<datalist>` pelo `id` |
| `size` | Largura visível em caracteres |
| `form` | Associa o campo a um formulário de `id` específico, mesmo fora dele |
| `title` | Texto de ajuda ao passar o mouse; também usado na mensagem do `pattern` |

### Atributos de `<textarea>`

| Atributo | Função |
|---|---|
| `rows` | Número de linhas visíveis |
| `cols` | Largura visível em caracteres |
| `maxlength` / `minlength` | Limites de caracteres |
| `wrap` | Quebra de linha (`soft`, `hard`) |
| `placeholder`, `required`, `readonly`, `disabled` | Iguais aos do `<input>` |

### Atributos de `<select>`, `<option>` e `<optgroup>`

| Atributo | Em qual tag | Função |
|---|---|---|
| `multiple` | `<select>` | Permite escolher várias opções |
| `size` | `<select>` | Quantidade de opções visíveis |
| `value` | `<option>` | Valor enviado |
| `selected` | `<option>` | Opção marcada inicialmente |
| `disabled` | `<option>`, `<optgroup>` | Opção ou grupo desativado |
| `label` | `<optgroup>` | Nome do grupo |

## Validação nativa

| Atributo | Função |
|---|---|
| `required` | Impede enviar o campo vazio |
| `type="email"` / `type="url"` | Valida o formato |
| `min` / `max` | Valor mínimo e máximo (`number`, `range`, datas) |
| `step` | Intervalo entre valores válidos |
| `minlength` / `maxlength` | Quantidade mínima e máxima de caracteres |
| `pattern` | Expressão regular que o valor deve seguir |
| `novalidate` (no `<form>`) | Desliga a validação do navegador |

Pseudo-classes de CSS úteis: `:valid`, `:invalid`, `:required`, `:optional`, `:disabled`, `:checked`.

## Atributos do `<button>`

| Atributo | Função |
|---|---|
| `type` | `submit` (padrão), `reset` ou `button` |
| `name` / `value` | Dados enviados com o formulário quando o botão é clicado |
| `disabled` | Desativa o botão |
| `form` | Associa o botão a um formulário pelo `id` |
| `formaction` | Substitui o `action` do formulário |
| `formmethod` | Substitui o `method` do formulário |
| `formenctype` | Substitui o `enctype` do formulário |
| `formtarget` | Substitui o `target` do formulário |
| `formnovalidate` | Envia sem validar |
| `autofocus` | Foca o botão ao carregar |

## Exemplo de formulário

```html
<form action="/cadastro" method="post">
  <fieldset>
    <legend>Dados pessoais</legend>

    <label for="nome">Nome completo</label>
    <input type="text" id="nome" name="nome" placeholder="Seu nome" required>

    <label for="email">E-mail</label>
    <input type="email" id="email" name="email" required>

    <label for="senha">Senha</label>
    <input type="password" id="senha" name="senha" minlength="8" required>

    <label for="nascimento">Data de nascimento</label>
    <input type="date" id="nascimento" name="nascimento">

    <label for="idade">Idade</label>
    <input type="number" id="idade" name="idade" min="0" max="120">

    <label for="telefone">Telefone</label>
    <input type="tel" id="telefone" name="telefone"
           pattern="[0-9]{2} [0-9]{5}-[0-9]{4}"
           title="Formato: 21 99999-9999">
  </fieldset>

  <fieldset>
    <legend>Preferências</legend>

    <p>Nível de estudo:</p>
    <label>
      <input type="radio" name="nivel" value="iniciante" checked> Iniciante
    </label>
    <label>
      <input type="radio" name="nivel" value="intermediario"> Intermediário
    </label>

    <p>Tecnologias de interesse:</p>
    <label>
      <input type="checkbox" name="tecnologias" value="html"> HTML
    </label>
    <label>
      <input type="checkbox" name="tecnologias" value="css"> CSS
    </label>
    <label>
      <input type="checkbox" name="tecnologias" value="js"> JavaScript
    </label>

    <label for="estado">Estado</label>
    <select id="estado" name="estado">
      <option value="">Selecione...</option>
      <optgroup label="Sudeste">
        <option value="rj">Rio de Janeiro</option>
        <option value="sp">São Paulo</option>
      </optgroup>
      <optgroup label="Sul">
        <option value="rs">Rio Grande do Sul</option>
      </optgroup>
    </select>

    <label for="linguagem">Linguagem favorita</label>
    <input list="linguagens" id="linguagem" name="linguagem">
    <datalist id="linguagens">
      <option value="JavaScript">
      <option value="Python">
      <option value="Java">
    </datalist>

    <label for="mensagem">Mensagem</label>
    <textarea id="mensagem" name="mensagem" rows="4" cols="40"
              maxlength="300" placeholder="Escreva aqui..."></textarea>

    <label for="curriculo">Currículo (PDF)</label>
    <input type="file" id="curriculo" name="curriculo" accept=".pdf">
  </fieldset>

  <label>
    <input type="checkbox" name="termos" required> Aceito os termos de uso
  </label>

  <button type="submit">Enviar</button>
  <button type="reset">Limpar</button>
</form>
```

> **Atenção:** para enviar arquivos (`type="file"`), o formulário precisa de `method="post"` e `enctype="multipart/form-data"`.

## Boas práticas para formulários

- Todo campo deve ter um `<label>` ligado por `for` e `id` (ou envolvendo o campo).
- Use o `type` correto (`email`, `tel`, `date`...): o navegador valida e mostra o teclado certo no celular.
- Dê um `name` a todo campo que precisa ser enviado.
- Em `radio`, use o **mesmo** `name` para formar o grupo.
- Agrupe campos relacionados com `<fieldset>` e `<legend>`.
- Não use `placeholder` no lugar do `<label>`.
- Use `required`, `min`, `max` e `pattern`, mas lembre que a **validação no servidor continua sendo obrigatória**.
- Nunca envie senhas ou dados sensíveis com `method="get"`.
- Não confie só em `readonly` ou `hidden` para proteger valores: o usuário pode alterá-los.

---

# 📚 Referências

- [MDN — Elemento `<table>`](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/table)
- [MDN — Elemento `<form>`](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/form)
- [MDN — Elemento `<input>`](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/input)

---

# 👨‍💻 Autor

**Caio Rafael Silva Teixeira** (Caio Rafael-dev)

Estudante de Full Stack e Segurança da Informação (InfoSec), aprendendo HTML, CSS, JavaScript, Python e Linux.

📍 Santa Cruz, Rio de Janeiro, Brasil

📬 **E-mail:** caio.silva.teixeira15@gmail.com
