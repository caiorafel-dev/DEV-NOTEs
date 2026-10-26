# 📚 Apontamentos de Desenvolvimento Web: HTML & CSS

Repositório dedicado ao registo de conceitos fundamentais, estruturas e boas práticas de HTML e CSS.

---

## 📊 1. Tabelas HTML (`<table>`)

As tabelas são utilizadas para organizar dados em linhas e colunas estruturadas.

### 🦴 Anatomia Básica de uma Tabela
Uma tabela completa divide-se em três blocos principais (`<thead>`, `<tbody>`, `<tfoot>`) envolvidos pela tag principal `<table>`:

```html
<table>
  <caption>Título ou Descrição da Tabela</caption>
  <thead>
    <tr>
      <th>Cabeçalho 1</th>
      <th>Cabeçalho 2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Dado 1</td>
      <td>Dado 2</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td colspan="2">Rodapé / Total</td>
    </tr>
  </tfoot>
</table>

Principais Tags de Tabelas:
<table>: Define o elemento de tabela.

<caption>: Adiciona um título ou legenda descritiva no topo da tabela.

<thead>: Agrupa o cabeçalho da tabela.

<tbody>: Agrupa o corpo principal (os dados) da tabela.

<tfoot>: Agrupa o rodapé da tabela (geralmente usado para totais ou somas).

<tr> (Table Row): Cria uma linha na tabela.

<th> (Table Header): Cria uma célula de cabeçalho (o texto fica em negrito e centralizado por defeito).

<td> (Table Data): Cria uma célula de dados comum.

📐 Atributos de Célula Importantes:
colspan="N": Faz com que uma célula se estenda horizontalmente por N colunas.

rowspan="N": Faz com que uma célula se estenda verticalmente por N linhas.

💡 Dica de Responsividade: Para evitar que tabelas grandes quebrem o layout em telemóveis, envolve a tag <table> numa <div> com o estilo style="overflow-x: auto;".

                                      FORMULARIO

<form action="/enviar-dados" method="POST">
  <fieldset>
    <legend>Informações Pessoais</legend>
    
    <label for="nome">Nome:</label>
    <input type="text" id="nome" name="nome" placeholder="Escreve o teu nome" required>

    <button type="submit">Enviar</button>
  </fieldset>
</form>

Principais Tags de Formulários:
<form>: Contentor principal que envolve todos os campos. Usa atributos como action (para onde vão os dados) e method (GET ou POST).

<fieldset>: Agrupa secções relacionadas dentro do formulário (cria uma caixa visual à volta dos elementos).

<legend>: Dá um título descritivo ao <fieldset>.

<label>: O rótulo de texto que identifica um campo. Boa prática: usa sempre o atributo for="id-do-input" correspondente ao input para garantir acessibilidade.

<input>: O campo de entrada de dados principal (é uma tag vazia, não tem tag de fecho).

<select> e <option>: Cria listas de seleção suspensas (dropdowns).

<textarea>: Cria uma caixa de texto multilinha (ótima para comentários ou mensagens longas).

<button>: Botão de ação (pode ser type="submit" para enviar, type="reset" para limpar, ou type="button" para ações com JavaScript).

⚙️ Tipos Comuns de type no <input>:
type="text": Texto normal de uma linha.

type="password": Esconde os caracteres digitados (para senhas).

type="email": Valida automaticamente se o formato do e-mail é válido.

type="number": Campo restrito a números.

type="checkbox": Caixa de seleção múltipla (várias opções).

type="radio": Botão de escolha única (num grupo com o mesmo name).

type="submit": Botão de envio do formulário.

🧷 Atributos Essenciais dos Inputs:
id: Identificador único do elemento (ligado ao for do <label>).

name: Nome da variável enviada para o servidor (essencial para o backend processar os dados).

placeholder: Texto de exemplo que desaparece assim que o utilizador começa a digitar.

required: Torna o preenchimento daquele campo obrigatório antes de enviar o formulário.

value: Define o valor pré-definido armazenado no campo.

