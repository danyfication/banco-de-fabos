# banco-de-fabos

## Banco de dados configurado

- Banco: `escola`
- Tabela: `aluno`
- Colunas: `id_aluno`, `nome`, `nota`
- Procedure: `InserirAluno`

## Comandos usados para configuração

```bash
sudo apt update && sudo apt install -y mysql-server
sudo service mysql start
sudo mysql -u root
```

```sql
CREATE DATABASE escola;
USE escola;

CREATE TABLE aluno (
  id_aluno INT AUTO_INCREMENT PRIMARY KEY,
  nome VARCHAR(100) NOT NULL,
  nota DECIMAL(4,2) NOT NULL
);

DELIMITER //
CREATE PROCEDURE InserirAluno(
  IN p_nome VARCHAR(100),
  IN p_nota DECIMAL(4,2)
)
BEGIN
  INSERT INTO aluno (nome, nota) VALUES (p_nome, p_nota);
END //
DELIMITER ;
```

## Verificação da tabela

```bash
sudo mysql -u root -proot -D escola -e "SELECT id_aluno, nome, nota FROM aluno ORDER BY id_aluno;"
```

## Exemplo de inserção via procedure

```sql
CALL InserirAluno('Ana', 9.50);
```
