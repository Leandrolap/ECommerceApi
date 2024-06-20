# ECommerceApi
Este projeto exemplifica a implementação de um sistema de controle de acesso de um e-commerce utilizando Spring Security e tokens JWT (JSON Web Token). A aplicação é estruturada para fornecer diferentes níveis de acesso com base nos papéis dos usuários.
Os usuários permitidos são os administradores com acesso total, gerentes que terão acessos específicos a funções do sistema, vendedor com acesso a áreas de produtos e vendas e por fim o cliente com acesso limitado a nível de usuário comum.

# Configuração de Segurança

A classe SecurityConfig configura o Spring Security para a aplicação web:
SecurityFilterChain: Define as regras de segurança HTTP, especificando quais endpoints requerem autenticação e quais são públicos ou acessíveis por diferentes papéis de usuário.

Desativação de CSRF: A proteção CSRF é desabilitada para simplificar a integração com APIs.

UserDetailsService: Implementa três usuários em memória (admin, moderado e comum), utilizando senhas criptografadas com BCrypt.

# Controlador de Autenticação (AuthController)

O AuthController gerencia os endpoints de autenticação:
POST /login: Autentica o usuário com base nas credenciais fornecidas e gera um token JWT por meio do serviço de autenticação (AuthService).
GET /username/{token}: Extrai o nome de usuário do token JWT fornecido, utilizando também o serviço de autenticação.
Endpoints Restritos por Papel:
GET /admin: Acesso permitido apenas para usuários com papel "ADMIN". GET /moderado: Acesso restrito a usuários com papel "MODERADO". GET /comum: Acessível a todos os usuários autenticados. Utilização de JWT (JwtUtil) A classe JwtUtil contém métodos para gerar e extrair informações de tokens JWT:
Geração de Token: Cria um token JWT com um tempo de expiração configurado para 10 dias.
Extração de Nome de Usuário: Obtém o nome de usuário a partir do token JWT, validando-o com uma chave secreta.
Serviço de Autenticação (AuthService)
O AuthService fornece métodos para gerar e extrair informações de tokens JWT, encapsulando a lógica relacionada à autenticação e autorização da aplicação.

# Conclusão
Este projeto serve como um exemplo prático de como implementar segurança em uma aplicação web usando Spring Security em conjunto com tokens JWT. Ele demonstra como configurar diferentes níveis de acesso com base em papéis de usuário e como utilizar tokens JWT para autenticar e autorizar usuários de forma eficaz.
Para executar o projeto, é necessário configurar um ambiente de desenvolvimento com as dependências corretas do Spring Security e executar a aplicação em um servidor compatível com Spring Boot.

# Considerações Adicionais
Chave Secreta: A chave secreta utilizada para assinar e verificar tokens JWT deve ser guardada de maneira segura, preferencialmente em variáveis de ambiente ou em um gerenciador de segredos.

Melhorias de Segurança: Em um ambiente de produção real, é recomendável integrar o sistema com um serviço de autenticação centralizado, como OAuth 2.0, e implementar práticas adicionais de segurança, como a utilização de SSL/TLS.
Este projeto é um exemplo educacional que pode ser expandido para atender requisitos específicos de segurança e funcionalidade de aplicações web reais.
Diagrama de fluxo de Controle de Acesso:

![Apresentação sem título](https://github.com/Leandrolap/ECommerceApi/assets/12981655/365db252-7ca1-48fa-a10a-b861e26bea9c)

Link do Diagrama: https://bit.ly/4cbF029

# Capturas de tela
![Apresentação sem título (1)](https://github.com/Leandrolap/ECommerceApi/assets/12981655/a1994e2b-a617-4b7f-90c1-f596dee5aa52)
![Apresentação sem título (2)](https://github.com/Leandrolap/ECommerceApi/assets/12981655/9286eb63-febb-4524-a452-b6a6e7fe468c)
![Apresentação sem título (3)](https://github.com/Leandrolap/ECommerceApi/assets/12981655/417fed5b-5f91-436b-8391-1fe5793132bb)
![Apresentação sem título (4)](https://github.com/Leandrolap/ECommerceApi/assets/12981655/c01afc59-1840-4b36-89cf-b4637c3da96b)




