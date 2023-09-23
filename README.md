Segue a primeira questão do desafio, meu computador com as ferramentas para trabalho não está funcionando, 
realizei o desafio com teste via compilador on-line, https://www.programiz.com/javascript/online-compiler/, 
não tive como aplicar o padrão MVC e nem usar o SOLID para finalizar os ajustes dos sistemas devido o tempo.
 

const funcionarios = [];

function adicionarFuncionario() {
  const id = prompt('Informe a identificação do funcionário que deseja adicionar: ');
  const idJaExiste = funcionarios.find((funcionario) => funcionario.id === id);
  if (idJaExiste) {
    console.log('Esta identificação já está em uso por outro funcionário, tente novamente com outra identificação.');
    return; 
  }
  const nome = prompt('Por favor, digite o nome do funcionário:');
  const vaga = prompt('Informe vaga do funcionário:');
  const salario = parseFloat(prompt('Informe o salário do funcionário:'));
  const novoFuncionario = { id, nome, vaga, salario };
  funcionarios.push(novoFuncionario);
}

function editarFuncionario(id) {
  const funcionarioIndex = funcionarios.findIndex((funcionario) => funcionario.id === id);
  if (funcionarioIndex !== -1) {
    const novoNome = prompt('Informe o novo nome do funcionário:');
    const novaVaga = prompt('Informe a nova vaga do funcionário:');
    const novoSalario = parseFloat(prompt('Por favor, informe o novo salário do funcionário:'));
    
    funcionarios[funcionarioIndex].nome = novoNome;
    funcionarios[funcionarioIndex].vaga = novaVaga;
    funcionarios[funcionarioIndex].salario = novoSalario;
    console.log('Funcionário editado com sucesso.');
  } else {
    console.log('Funcionário não encontrado.');
  }
}

function excluirFuncionario(id) {
  const funcionarioIndex = funcionarios.findIndex((funcionario) => funcionario.id === id);
  if (funcionarioIndex !== -1) {
    funcionarios.splice(funcionarioIndex, 1);
    console.log('Funcionário excluído com sucesso.');
  } else {
    console.log('Funcionário não encontrado.');
  }
}

 function listarFuncionarios() {
  if (funcionarios.length === 0) {
    console.log('Não há funcionários na lista.');
  } else {
        console.log('Lista de Funcionários:');
            funcionarios.forEach((funcionario) => {
             console.log(`ID: ${funcionario.id}, Nome: ${funcionario.nome}, Vaga: ${funcionario.vaga}, Salário: ${funcionario.salario}`);
        });
   }
}

while (true) {
  const opcao = prompt('Escolha uma opção:\n1. Adicionar Funcionário\n2. Editar Funcionário\n3. Excluir Funcionário\n4. Listar Funcionários\n5. Sair \n');

  switch (opcao) {
    case '1':
      adicionarFuncionario();
      break;
    case '2':
      const idEditar = prompt('Por favor, digite o identificação do funcionário que deseja editar:');
      editarFuncionario(idEditar);
      break;
    case '3':
      const idExcluir = prompt('Por favor, digite o identificação do funcionário que deseja excluir:');
      excluirFuncionario(idExcluir);
      break;
    case '4':
      listarFuncionarios();
      break;
    case '5':
      console.log('Encerrando o programa.');
      break;
    default:
      console.log('Opção inválida.');
  }

  if (opcao === '5') {
    break;
  }
}


Segue a segunda questão do desafio, meu computador com as ferramentas para trabalho não está funcionando, 
realizei o desafio com teste via compilador on-line, https://www.programiz.com/javascript/online-compiler/, 
não tive como aplicar o padrão MVC e nem usar o SOLID para finalizar os ajustes dos sistemas devido o tempo.
Usei lógica básica, mas poderia melhorar, principalmente na estrutura condicional if/else e em solicitar ao usuário.



function calcularEmprestimos(cliente) {
  const salario = cliente.salario;
  const funcao = cliente.funcao;

  const emprestimos = [];

   if (salario <= 3000) {
    emprestimos.push({ tipo: 'Empréstimo Pessoal', taxaDeJuros: 0.04 });
  }
  
  if (salario >= 5000) {
    emprestimos.push({ tipo: 'Empréstimo Consignado', taxaDeJuros: 0.02 });
  }

  if (salario <= 3000 && funcao === 'garantia') {
    emprestimos.push({ tipo: 'Empréstimo com Garantia', taxaDeJuros: 0.03 });
  }

  return {
    nomeDoCliente: cliente.nome,
    emprestimosDisponiveis: emprestimos
  };
}

const clienteExemplo = {
  nome: 'PEDRO',
  salario: 5000,
  funcao: 'garantia'
};

const resultado = calcularEmprestimos(clienteExemplo);

console.log(`Cliente: ${resultado.nomeDoCliente}`);
console.log('Empréstimos disponíveis:');
resultado.emprestimosDisponiveis.forEach((emprestimo) => {
  console.log(`- Tipo: ${emprestimo.tipo}, Taxa de Juros: ${emprestimo.taxaDeJuros * 100}%`);
});

