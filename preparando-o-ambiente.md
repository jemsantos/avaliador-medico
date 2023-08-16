# O Projeto

1 - Faça o clone do projeto inicial do curso:

<[git clone https://github.com/CViniciusSDias/curso-arquitetura-e-escalabilidade]>

2 - Acesse a pasta recém criada:

<[cd curso-arquitetura-e-escalabilidade]>

3 - Instale as dependências do projeto:

-   a)
    <[composer install>]>

-   b) Caso você não possua o composer instalado localmente, execute no WSL, Linux ou Mac:
    <[docker run --rm -itv $(pwd):/app -w /app -u $(id -u):$(id -g) composer:2.5.8 install]>

-   c) No Windows (sem WSL), no PowerShell:
    <[docker run --rm -itv ${PWD}:/app -w /app composer:2.5.8 install]>

4 - Caso o arquivo .env não exista ainda em seu projeto, crie-o a partir do .env.example:

<[cp .env.example .env]>

5 - Inicie os contêineres do projeto:

<[docker compose up -d --build]>

6 - Dê permissões ao usuário correto para escrever logs na aplicação:

<[docker compose exec app chown -R www-data:www-data /app/storage]>

7 - Garanta que o contêiner de banco de dados está de pé. Os logs devem exibir a mensagem ready for connections nas últimas linhas:

<[docker compose logs database]>

Aguarde até que o comando acima tenha como uma das últimas linhas a mensagem ready for connections.

8 - Com o contêiner de banco de dados de pé, configure o schema e dados do banco:

<[docker compose exec -u $(id -u):$(id -g) app php artisan migrate --seed]>

No Windows (se estiver fora do WSL), omita a parte -u $(id -u):$(id -g).

9 - Muitos dados serão criados (1000 especialistas com 1000 avaliações cada), então essa última etapa será demorada. Enquanto ela executa, a API já estará acessível através do endereço http://localhost:8123/api. Além disso, o endereço http://localhost:8025 provê acesso ao serviço de e-mail Mailpit.

## Outras ferramentas

Para continuar com esse curso você vai precisar de algumas ferramentas como uma IDE (ou editor de códigos, se preferir) e um cliente HTTP.

Nesse curso eu uso o PHPStorm tanto como IDE quanto como cliente HTTP em alguns momentos. Caso prefira uma opção de editor de códigos gratuita, o Visual Studio Code é uma opção bastante famosa no mercado. Aqui estão links para realizar o download de ambos:

-   PHPStorm
-   VS Code

Outro cliente HTTP que usei para realizar chamadas HTTP foi o Postman. Uma outra alternativa bem conhecida é o Insomnia. Seguem os links para download das duas ferramentas:

-   Postman
-   Insomnia

Caso você prefira usar outra ferramenta alternativa, fique à vontade.
