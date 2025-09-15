## Como Integrar com Seu Projeto Laravel

Após baixar este pacote, siga os passos abaixo para integrá-lo ao seu projeto Laravel existente ou novo:

1. **Baixe ou clone este repositório:**
    ```bash
    git clone https://github.com/MarcondesJuniorDev/docker00
    cd docker00
    ```

2. **Copie os arquivos da stack para o diretório raiz do seu projeto Laravel:**
    - Se você já possui um projeto Laravel, copie os seguintes arquivos e pastas para o diretório principal do seu projeto:
      ```
      cp -r docker/ docker-compose.yml .env.example .gitignore README.md /caminho/do/seu/projeto-laravel/
      ```
    - Caso esteja iniciando um novo projeto Laravel, primeiro crie o projeto e depois copie os arquivos:
      ```bash
      composer create-project laravel/laravel nome-do-projeto
      cd nome-do-projeto
      # Copie os arquivos da stack para cá
      ```

3. **Ajuste o arquivo `.env.example` conforme necessário e renomeie para `.env`:**
    ```bash
    cp .env.example .env
    ```
    - Edite as variáveis de ambiente para refletir as configurações do seu projeto (nome do banco, usuário, senha, portas, etc).

4. **Suba os containers Docker:**
    ```bash
    docker-compose up -d
    ```

5. **Acesse sua aplicação Laravel:**
    - Abra `http://localhost:8000` no navegador (ou a porta configurada).

### Observações Importantes

- **Não sobrescreva arquivos existentes:** Se seu projeto Laravel já possui arquivos como `.gitignore` ou `.env.example`, revise antes de substituir para evitar perda de configurações.
- **Permissões:** Após copiar os arquivos, garanta que as permissões das pastas `storage` e `bootstrap/cache` estejam corretas:
    ```bash
    chmod -R 775 storage bootstrap/cache
    ```
- **Composer:** Instale as dependências do Laravel dentro do container PHP:
    ```bash
    docker-compose exec php composer install
    ```
- **Migrations:** Rode as migrations normalmente:
    ```bash
    docker-compose exec php php artisan migrate
    ```

### Resumo

Este pacote serve como uma base Docker pronta para projetos Laravel 12+. Basta copiar os arquivos para seu projeto, ajustar as configurações e iniciar os containers para começar a desenvolver rapidamente.

