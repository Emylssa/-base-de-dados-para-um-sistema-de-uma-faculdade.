# Sistema de uma Faculdade

-- Criação do banco de dados
CREATE DATABASE IF NOT EXISTS banco_portifolio;

-- Selecionando o banco de dados
USE banco_portifolio;

# Criação da tabela Alunos
CREATE TABLE Alunos (
    id_aluno INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(255) NOT NULL,
    data_nascimento DATE NOT NULL,
    cpf VARCHAR(14) NOT NULL UNIQUE,
    email VARCHAR(255) NOT NULL UNIQUE
);

# Criação da tabela Cursos
CREATE TABLE Cursos (
    id_curso INT AUTO_INCREMENT PRIMARY KEY,
    nome_curso VARCHAR(255) NOT NULL,
    carga_horaria INT NOT NULL
);

# Criação da tabela Matérias
CREATE TABLE Materias (
    id_materia INT AUTO_INCREMENT PRIMARY KEY,
    nome_materia VARCHAR(255) NOT NULL,
    codigo VARCHAR(20) NOT NULL,
    semestre INT NOT NULL,
    id_curso INT,
    FOREIGN KEY (id_curso) REFERENCES Cursos(id_curso)
);

# Criação da tabela Professores
CREATE TABLE Professores (
    id_professor INT AUTO_INCREMENT PRIMARY KEY,
    nome_professor VARCHAR(255) NOT NULL,
    especializacao VARCHAR(255),
    email VARCHAR(255) NOT NULL UNIQUE
);

# Criação da tabela Notas
CREATE TABLE Notas (
    id_nota INT AUTO_INCREMENT PRIMARY KEY,
    id_aluno INT,
    id_materia INT,
    nota DECIMAL(5, 2) CHECK (nota >= 0 AND nota <= 10) NOT NULL,
    FOREIGN KEY (id_aluno) REFERENCES Alunos(id_aluno),
    FOREIGN KEY (id_materia) REFERENCES Materias(id_materia)
