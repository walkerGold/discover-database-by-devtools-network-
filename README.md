# Análise de Tráfego de Rede para Login de Site

Este repositório contém instruções para realizar uma análise ética de tráfego de rede para um site de login. O objetivo é verificar como as credenciais e dados são transmitidos e se existem vulnerabilidades de segurança, como a exposição de informações sensíveis (por exemplo, banco de dados JSON ou credenciais).

**Aviso Importante:** Este processo deve ser realizado **somente em sistemas próprios ou com permissão explícita** do proprietário do sistema para evitar violação de privacidade e regras legais.

## Pré-requisitos

- Navegador Chrome ou Firefox
- Acesso ao DevTools (Ferramentas de Desenvolvedor) do navegador
- Acesso à página de login do site em questão (pode ser o seu próprio site ou com permissão explícita para teste)

## Passos para Realizar a Análise

### 1. Abrir o DevTools
- Abra o site de login no navegador.
- Clique com o botão direito em qualquer lugar da página e selecione **Inspecionar** ou pressione `F12` no teclado.
- Isso abrirá as **Ferramentas de Desenvolvedor (DevTools)**.

### 2. Acessar a Aba de Rede (Network)
- Na barra superior do DevTools, selecione a aba **Network** (Rede).
- Certifique-se de que o ícone de gravação está **vermelho**. Caso não esteja, clique no ícone para iniciar a gravação de rede.

### 3. Preencher o Formulário de Login
- Preencha o formulário de login com as credenciais de teste.
- Clique no botão de login para enviar os dados.

### 4. Analisar as Requisições de Rede
- Após enviar o formulário, o DevTools começará a exibir todas as requisições feitas ao servidor.
- Encontre a requisição do tipo **POST** que envia as credenciais (usuário e senha) ao servidor.
- Clique na requisição para expandir suas informações.
  - **Headers**: Veja os cabeçalhos da requisição para identificar informações sobre como os dados estão sendo processados.
  - **Payload**: Aqui você verá os dados enviados (por exemplo, nome de usuário e senha).
  - **Response**: Veja a resposta do servidor para verificar se há algum erro ou informação adicional sobre o processamento.

### 5. Verificar Exposição de Dados
- Se o servidor estiver enviando dados em formato JSON, analise a resposta da requisição para verificar se há informações sensíveis ou estrutura do banco de dados.
- Verifique também se o servidor está expondo caminhos de arquivos, como `db.json` ou outros arquivos internos, através de mensagens de erro ou respostas.

### 6. Testar URLs do Banco de Dados (Opcional)
- Se identificar uma possível URL de banco de dados (exemplo: `/db/data.json`), tente acessá-la diretamente.
- Se o servidor não estiver protegido adequadamente, você pode conseguir acessar o conteúdo do banco de dados.

### 7. Gravar a Tela (Opcional)
- Para documentar ou compartilhar sua análise, você pode usar um software de gravação de tela, como o OBS Studio ou o gravador nativo do sistema operacional.
- Grave a tela enquanto realiza os passos descritos, especialmente ao preencher o formulário e analisar as requisições no DevTools.

## Considerações de Segurança

- **Use HTTPS**: Sempre que possível, certifique-se de que a comunicação entre o cliente e o servidor está protegida por HTTPS para evitar a interceptação de dados sensíveis.
- **Criptografia de Senhas**: Verifique se as senhas estão sendo enviadas de forma segura e nunca em texto simples.
- **Proteção de Arquivos**: Garanta que o banco de dados ou arquivos sensíveis (como arquivos JSON) não estejam acessíveis diretamente através de URLs públicas.

## Conclusão

Esta análise tem como objetivo ajudar a identificar possíveis vulnerabilidades no processo de login de um site e como as credenciais e dados são transmitidos. Assegure-se de sempre obter permissão para realizar esse tipo de teste em sistemas de terceiros. 

**Disclaimer:** Este guia é destinado para fins educacionais e de segurança. Não utilize essas técnicas em sistemas que você não tenha permissão explícita para testar.

---
