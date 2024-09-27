* Sistema de Gerenciamento de Biblioteca 

O Sistema de Gerenciamento de Biblioteca é um projeto desenvolvido para o gerenciamento eficiente de uma biblioteca, permitindo o controle de autores, livros e empréstimos. Utilizando comandos SQL, o sistema realiza operações de criação de banco de dados, inserção de registros, consultas, atualizações e exclusões de dados. Este projeto visa facilitar a administração de um acervo de livros, gerenciando os empréstimos e devoluções de forma automatizada e confiável.

Estrutura do Projeto
O projeto consiste em três tabelas principais no banco de dados:

Autores: Contém informações sobre os autores, como nome e nacionalidade.
Livros: Armazena os dados dos livros, incluindo título, autor, ano de publicação e gênero.
Empréstimos: Registra os empréstimos de livros, com detalhes sobre a data de empréstimo, data de devolução e o nome do usuário.
Funcionalidades
1. Criação do Banco de Dados
O banco de dados chamado Biblioteca é criado, e todas as tabelas necessárias são estruturadas.
2. Tabelas do Sistema
Autores: Tabela que armazena os autores de livros.
CREATE TABLE Autores (
    AutorID INT AUTO_INCREMENT PRIMARY KEY,
    Nome VARCHAR(100) NOT NULL,
    Nacionalidade VARCHAR(100)
);

Livros: Tabela que contém informações dos livros e está relacionada aos autores.
CREATE TABLE Livros (
    LivroID INT AUTO_INCREMENT PRIMARY KEY,
    Titulo VARCHAR(255) NOT NULL,
    AutorID INT,
    AnoPublicacao YEAR,
    Genero VARCHAR(50),
    FOREIGN KEY (AutorID) REFERENCES Autores(AutorID)
);

Empréstimos: Tabela que armazena os dados de empréstimos de livros, vinculando o livro ao usuário que o pegou emprestado.
CREATE TABLE Emprestimos (
    EmprestimoID INT AUTO_INCREMENT PRIMARY KEY,
    LivroID INT,
    DataEmprestimo DATE NOT NULL,
    DataDevolucao DATE,
    NomeUsuario VARCHAR(100) NOT NULL,
    FOREIGN KEY (LivroID) REFERENCES Livros(LivroID)
);

4. Consultas
Listar todos os livros com os nomes de seus autores:
SELECT Livros.Titulo, Autores.Nome AS Autor, Livros.AnoPublicacao
FROM Livros
JOIN Autores ON Livros.AutorID = Autores.AutorID;

Listar todos os empréstimos em aberto
SELECT Emprestimos.EmprestimoID, Livros.Titulo, Emprestimos.DataEmprestimo, Emprestimos.NomeUsuario
FROM Emprestimos
JOIN Livros ON Emprestimos.LivroID = Livros.LivroID
WHERE Emprestimos.DataDevolucao IS NULL;

5. Atualizações
Atualizar a data de devolução de um empréstimo específico:
UPDATE Emprestimos
SET DataDevolucao = '2024-08-22'
WHERE EmprestimoID = 1;

6. Exclusão
Remover um livro e os registros de empréstimos associados:
DELETE FROM Emprestimos WHERE LivroID = 1;
DELETE FROM Livros WHERE LivroID = 1;


Pré-requisitos
Para executar este projeto, você precisará ter:

MySQL instalado.
Uma ferramenta para execução de scripts SQL, como MySQL Workbench, DBeaver ou qualquer outro cliente SQL.
Executando o Projeto
Clone este repositório em sua máquina local.
Abra seu cliente SQL preferido e conecte-se ao banco de dados MySQL.
Execute o script SQL provido para criar o banco de dados, tabelas e realizar as inserções de dados.
Use as consultas SQL fornecidas para visualizar e gerenciar as informações de empréstimos e livros.
Contribuições
Contribuições são bem-vindas! Sinta-se à vontade para criar um fork deste projeto, adicionar melhorias e enviar pull requests.

Licença
Este projeto está licenciado sob a Licença MIT. Consulte o arquivo LICENSE para mais informações.


