# Snippets para Java

Este repositório contém um conjunto de snippets para uso rápido no VS Code. Os snippets ajudam a acelerar tarefas comuns em Java/Spring: logs, componentes, testes, etc.

## Instalação

- Copie `snippets.code-snippets` para a pasta de snippets do VS Code:
  - Windows: `%APPDATA%\Code\User\snippets\`
  - macOS: `~/Library/Application Support/Code/User/snippets/`
  - Linux: `~/.config/Code/User/snippets/`
- Ou importe/cole o conteúdo no arquivo de snippets do seu workspace.

## Como usar

1. No editor, comece a digitar o `prefix` do snippet.
2. Pressione Tab (ou Enter) para expandir.
3. Os placeholders (`$1`, `$2`, etc.) e `$0` permitem navegação com Tab.

## Lista de snippets

* Logger

  * Prefix: `log`
  * Descrição: Cria um logger usando SLF4J
  * Expansão:

    ```java
    private static final Logger log =
        LoggerFactory.getLogger(UserService.class);
    ```

* Guard Clause

  * Prefix: `guard`
  * Descrição: Cria uma guard clause para interromper a execução
  * Expansão:

    ```java
    if (user == null) {
        return;
    }

    processUser(user);
    ```

* Optional Or Throw

  * Prefix: `optthrow`
  * Descrição: Obtém o valor de um `Optional` ou lança uma exceção
  * Expansão:

    ```java
    User user = userRepository.findById(id)
        .orElseThrow(() -> new UserNotFoundException(id));
    ```

* Map List

  * Prefix: `maplist`
  * Descrição: Mapeia uma lista usando a Stream API
  * Expansão:

    ```java
    List<String> names = users.stream()
        .map(User::getName)
        .toList();
    ```

* ResponseEntity

  * Prefix: `response`
  * Descrição: Cria uma resposta HTTP usando `ResponseEntity`
  * Expansão:

    ```java
    return ResponseEntity
        .status(HttpStatus.CREATED)
        .body(user);
    ```

* Spring Controller

  * Prefix: `controller`
  * Descrição: Cria um controller REST básico com Spring
  * Expansão:

    ```java
    @RestController
    @RequestMapping("/api/users")
    @RequiredArgsConstructor
    public class UserController {

    }
    ```

* Spring Service

  * Prefix: `service`
  * Descrição: Cria um service com injeção de dependência via construtor
  * Expansão:

    ```java
    @Service
    @RequiredArgsConstructor
    public class UserService {

        private final UserRepository userRepository;

    }
    ```

* JPA Repository

  * Prefix: `jparepo`
  * Descrição: Cria um repository usando Spring Data JPA
  * Expansão:

    ```java
    public interface UserRepository
        extends JpaRepository<User, Long> {

    }
    ```

* Assert Throws

  * Prefix: `throws`
  * Descrição: Verifica se uma operação lança uma exceção esperada
  * Expansão:

    ```java
    assertThrows(
        UserNotFoundException.class,
        () -> userService.findById(id)
    );
    ```

* Transactional Method

  * Prefix: `transactional`
  * Descrição: Cria um método transacional
  * Expansão:

    ```java
    @Transactional
    public void transfer(
        Long fromId,
        Long toId,
        BigDecimal amount
    ) {
        withdraw(fromId, amount);
        deposit(toId, amount);
    }
    ```


## Dicas rápidas

- Ajuste os placeholders após expandir (use Tab para navegar).
- Edite os snippets conforme seu padrão de codificação (nomes, comentários e formatos).
- Para adicionar novos snippets, edite `snippets.code-snippets` (ou o arquivo de snippets do seu workspace) e recarregue a janela (ou reinicie o VSCode).

Contribuições e melhorias são bem-vindas — abra um PR com novos templates ou ajustes de idioma/estilo.
