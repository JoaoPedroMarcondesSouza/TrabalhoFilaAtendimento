

🧾 Resumo do Projeto - Sistema de Gerenciamento de Fila de Atendimento

Este projeto consiste em um sistema desenvolvido em **JavaScript puro**, com HTML e CSS, para gerenciar uma fila de atendimento. Ele simula o atendimento de pessoas com funcionalidades básicas e um **painel de exibição** do último atendimento.

🎯 Funcionalidades Implementadas

#### 1. **Classe Atendimento (models/Atendimento.js)**

Criamos uma classe `Atendimento` que representa cada pessoa da fila com os seguintes atributos:

* `nome` (string)
* `cpf` (string)
* `dataEntrada` e `horaEntrada` (gerados automaticamente através de funções do arquivo `utils.js`)

#### 2. **Utils (utils.js)**

Contém funções para capturar a **data e hora atuais** de forma automatizada, evitando o uso de inputs no HTML:

```js
export function obterDataAtual() {
    return new Date().toLocaleDateString();
}

export function obterHoraAtual() {
    return new Date().toLocaleTimeString();
}
```

#### 3. **Gerenciamento da Fila (controllers/filaController.js)**

Aqui implementamos as funções principais:

* Inserir novo atendimento na fila.
* Listar os nomes das pessoas na fila.
* Buscar atendimento por CPF.
* Atender pessoa: registra horário de saída, calcula tempo de espera e armazena o atendimento no `localStorage` com:

```js
localStorage.setItem('ultimoAtendido', JSON.stringify(atendimento));
```

#### 4. **Painel de Atendimento (painel.html + painelController.js)**

Criamos uma interface simples que exibe o **último atendimento realizado**.

* `painel.html`: contém o título e uma `div` com id="ultimoAtendimento".
* `painelController.js`: responsável por atualizar a interface a cada segundo com:

```js
function atualizarAtendimento() {
    const ultimo = localStorage.getItem('ultimoAtendido');
    const dados = ultimo ? JSON.parse(ultimo) : "Aguardando...";
    document.getElementById('ultimoAtendimento').textContent = 
        typeof dados === 'string' ? dados : `${dados.nome} - CPF: ${dados.cpf} - Entrada: ${dados.dataEntrada} ${dados.horaEntrada}`;
}
setInterval(atualizarAtendimento, 1000);
```

---

 📁 Estrutura de Pastas

```
/models
    Atendimento.js
/utils
    utils.js
/controllers
    filaController.js
    painelController.js
/index.html
/painel.html
```







 🧠 Observações

* A aplicação simula uma fila e pode ser usada para fins educativos.
* O projeto pode ser feito em dupla, mas a apresentação deve ser individual.
* Toda a lógica de tempo e dados foi feita com JavaScript puro, sem frameworks.

PROJETO POR ADILSON E JOÃO PEDRO, PROFESSOR MATHEUS ELOY FRANCO

