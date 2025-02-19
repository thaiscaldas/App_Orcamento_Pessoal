# App_Orcamento_Pessoal

O App Orçamento Pessoal é uma aplicação web que permite o cadastramento, armazenamento e consulta de despesas financeiras. O objetivo é ajudar os usuários a manter um controle básico sobre seus gastos de maneira simples e intuitiva.

# Tecnologias Utilizadas

HTML5: Estruturação da página.

CSS3: Estilização e responsividade.

JavaScript (ES6): Lógica de programação e manipulação do localStorage.

Bootstrap 4: Interface gráfica e modais para feedback ao usuário.

# Estrutura do Projeto

O projeto é composto pelos seguintes arquivos principais:

index.html - Página principal com o formulário de cadastro de despesas.

consulta.html - Página para consulta de despesas cadastradas.

app.js - Contém toda a lógica de programação para manipulação das despesas.

bd.js - Classe responsável por armazenar e recuperar as despesas do localStorage.

style.css - Estilos personalizados da aplicação.

# Funcionalidades

* Cadastro de Despesas

O usuário informa:

Data da despesa (dia, mês, ano)

Tipo de despesa (alimentação, transporte, etc.)

Descrição

Valor

O sistema valida os campos e, se tudo estiver correto, armazena a despesa no localStorage.

O usuário recebe um modal de sucesso ou erro.

* Consulta de Despesas

A página consulta.html carrega todas as despesas armazenadas no localStorage e as exibe em uma tabela.

Possui filtros para buscar despesas por data, tipo e descrição.

* Exclusão de Despesas

O usuário pode remover uma despesa clicando no botão correspondente.

O sistema remove o registro do localStorage e recarrega a lista automaticamente.

# Explicação do Código

* bd.js - Classe de Manipulação do LocalStorage

class Bd {
    constructor() {
        if (localStorage.getItem('despesas') === null) {
            localStorage.setItem('despesas', JSON.stringify([]));
        }
    }

    gravar(despesa) {
        let despesas = JSON.parse(localStorage.getItem('despesas'));
        despesas.push(despesa);
        localStorage.setItem('despesas', JSON.stringify(despesas));
    }

    recuperarTodosRegistros() {
        return JSON.parse(localStorage.getItem('despesas')) || [];
    }
}

Essa classe gerencia o armazenamento e a recuperação de despesas no localStorage.

* app.js - Lógica da Aplicação

Captura os valores do formulário e cria um objeto de despesa.

Valida os campos e exibe um modal de sucesso ou erro.

Recupera e exibe despesas na tabela de consulta.

Permite a remoção de despesas pelo usuário.

Exemplo de captura de dados do formulário:

function cadastrarDespesa() {
    let despesa = {
        dia: document.getElementById('dia').value,
        mes: document.getElementById('mes').value,
        ano: document.getElementById('ano').value,
        tipo: document.getElementById('tipo').value,
        descricao: document.getElementById('descricao').value,
        valor: document.getElementById('valor').value
    };

    if (validarDespesa(despesa)) {
        let bd = new Bd();
        bd.gravar(despesa);
        exibirModal('success', 'Despesa cadastrada com sucesso!');
    } else {
        exibirModal('danger', 'Erro! Preencha todos os campos corretamente.');
    }
}

Como Executar o Projeto

Baixe ou clone este repositório.

Abra o arquivo index.html em um navegador.

Preencha o formulário para adicionar despesas.

Acesse consulta.html para visualizar as despesas cadastradas.

Melhorias Futuras

Implementação de um backend para armazenar os dados em um banco de dados.

Melhor interface com Bootstrap 5 ou Tailwind CSS.

Exportação de despesas para um arquivo CSV.

Adição de um dashboard com gráficos de análise financeira.

