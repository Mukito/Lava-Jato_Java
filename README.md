# Lava-Jato_Java

### 🚗 Fluxo do App de Lavagem de Carro - Java

### 1. Cadastro e Login
#### Grupos de Usuários:

* Cliente
  * Tipos: Normal, Premium
*  Funcionário
* Desenvolvedor

#### Campos comuns no cadastro:
* Nome
* Email
* Telefone
* Senha

----------------------------------------------------------------------------------------------------

### 2. Funcionalidades por Grupo

#### | Grupo | Funcionalidades |

| Cliente	| Cadastrar/Login, Agendar lavagem, Escolher funcionário, Ver status, Pagar via Pix |

| Funcionário | Ver agenda, Confirmar presença, Marcar como concluído |

| Desenvolvedor	| Ver todos os dados, fazer manutenção, liberar novos recursos |

---------------------------------------------------------------------------------------------------

### 3. Agendamento
* Cliente escolhe:
  *  Data e Hora
  * Tipo de lavagem (Simples, Completa, etc)
  * Funcionário disponível
* Sistema verifica disponibilidade
* Agenda é salva
  
----------------------------------------------------------------------------------------------------

### 4. Pagamento
* Após agendamento confirmado:
  *  Cliente escolhe pagamento via Pix
  *  Sistema gera um código QR ou chave Pix fictícia
  *  Confirmação de pagamento (simulação)

-----------------------------------------------------------------------------------------------------

### 🧱 Estrutura de Classes (Java)
```java

abstract class Usuario {
    protected String nome;
    protected String email;
    protected String telefone;
    protected String senha;
}

class Cliente extends Usuario {
    private boolean isPremium;
}

class Funcionario extends Usuario {
    private List<Agendamento> agenda;
}

class Desenvolvedor extends Usuario {
    // Permissões administrativas
}

class Agendamento {
    private Cliente cliente;
    private Funcionario funcionario;
    private LocalDateTime dataHora;
    private String tipoLavagem;
    private boolean confirmado;
    private boolean pago;
}

class Pagamento {
    private Agendamento agendamento;
    private String metodo = "Pix";
    private boolean status;
}


```


--------------------------------------------------------------------------------------------------------------------

### 🗂️ Estrutura de Pastas

```bash
/CarWashApp
├── model/             # Classes como Cliente, Funcionario, Agendamento
├── controller/        # Regras de negócio (agendamento, pagamento)
├── view/              # Interface (Swing ou JavaFX)
├── utils/             # Funções auxiliares (validação, simular pagamento Pix)
└── Main.java          # Inicialização do sistema


```

---------------------------------------------------------------------------------------------

### 🔄 Fluxo Resumido
    1.Usuário abre o app
    
    2.Faz login ou cadastro
    
    3.Cliente acessa painel > escolhe tipo de lavagem, data, horário, funcionário
    
    4.Cliente confirma e escolhe pagar com Pix
    
    5.Funcionário vê agenda
    
    6.Após lavagem, status é marcado como concluído

---------------------------------------------------------------------------------------------------------------

```markdown
1. Backend (Java com API REST) → lógica e banco de dados
2. Frontend Web (React ou HTML/CSS/JS) → navegador
3. App Mobile (React Native ou Flutter) → celular

```

---------------------------------------------------------------------------------------------------------------

### ✅ 1. BACKEND EM JAVA (Spring Boot)
A lógica do seu sistema (cadastro, login, agendamento, pagamento) ficará em uma API RESTful usando Spring Boot.

#### Estrutura:

```css
backend/
├── src/
│   └── main/
│       ├── java/com/carwash/
│       │   ├── model/
│       │   ├── controller/
│       │   ├── service/
│       │   └── repository/
│       └── resources/
│           └── application.properties
├── pom.xml

```

#### Principais funcionalidades da API:
* `POST /usuarios` → cadastro

* `POST /login` → autenticação

* `POST /agendamentos` → agendar lavagem

* `GET /agendamentos/{clienteId}` → ver agendamentos do cliente

* `POST /pagamentos/{agendamentoId}` → simular pagamento via Pix

------------------------------------------------------------------------------------------


### 🌍 2. FRONTEND WEB (React ou HTML)
Você cria uma **página web** com:

#### Páginas:
* Login e Cadastro

* Dashboard do Cliente

  * Agendar lavagem

  * Ver agendamentos

  * Confirmar pagamento via Pix

#### Ferramentas recomendadas:
* **React.js** com TailwindCSS ou Bootstrap

* Comunicação com a API via `fetch` ou `axios`

-------------------------------------------------------------------------------------------

### 📱 3. APP MOBILE (React Native ou Flutter)
O app será conectado à mesma API Java.

#### Telas no app:
* Tela de Login / Cadastro

* Tela de Agendamento

* Tela de Pagamentos

* Tela de Histórico

#### Sugestões de stack:
* **React Native** (mais fácil se já conhece JS)

* Ou **Flutter** (Dart)

------------------------------------------------------------------------------------------

## 🔄 Integração entre camadas (Web/App e Backend Java (Spring Boot)):

| Funcionalidade     | Web/APP envia para API Java         | Backend (Java) faz               |
|--------------------|--------------------------------------|----------------------------------|
| Cadastro           | `POST /usuarios`                    | Salva usuário no banco           |
| Login              | `POST /login`                       | Retorna token/autorização        |
| Agendar lavagem    | `POST /agendamentos`                | Cria o agendamento               |
| Ver agendamentos   | `GET /agendamentos/{clienteId}`     | Retorna lista de agendamentos    |
| Confirmar Pix      | `POST /pagamentos/{agendamentoId}`  | Marca como confirmado            |




### 🚀 Projeto Spring Boot – Lavagem de Carros
#### ✅ Funcionalidades prontas:
* Cadastro de usuários (Cliente Normal, Premium, Funcionário, Desenvolvedor)

* Login (simples, sem segurança complexa, mas fácil de adaptar pra JWT depois)

* Agendamento com data/hora, funcionário e tipo de lavagem

* Pagamento via Pix (simulado)

* Listagem de agendamentos




















