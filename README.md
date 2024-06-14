<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Inserir Novo Prato</title>
</head>
<body>
    <h1>Inserir Novo Prato</h1>
    <form action="inserir.php" method="post">
        <label for="nome">Nome do Prato:</label><br>
        <input type="text" id="nome" name="nome" required><br><br>
        <label for="preco">Preço:</label><br>
        <input type="text" id="preco" name="preco" required><br><br>
        <label for="codigo_pagamento">Código de Pagamento:</label><br>
        <input type="text" id="codigo_pagamento" name="codigo_pagamento" required><br><br>
        <label for="imagem">Nome da Imagem:</label><br>
        <input type="text" id="imagem" name="imagem" required><br><br>
        <input type="submit" value="Inserir">
    </form>

    <?php
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        $db = new SQLite3('restaurante.db');

        $nome = $_POST['nome'];
        $preco = $_POST['preco'];
        $codigo_pagamento = $_POST['codigo_pagamento'];
        $imagem = $_POST['imagem'];

        $query = "INSERT INTO pratos (nome, preco, codigo_pagamento, imagem) VALUES ('$nome', '$preco', '$codigo_pagamento', '$imagem')";

        if ($db->exec($query)) {
            echo "Novo prato inserido com sucesso!";
        } else {
            echo "Erro ao inserir o prato.";
        }
    }
    ?>
</body>
</html>
