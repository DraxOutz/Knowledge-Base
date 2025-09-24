# 🔒 Cybersecurity Notes

Este documento reúne conceitos, práticas e boas referências sobre **cibersegurança**.  
A ideia é servir como guia de estudo e consulta rápida.

# 🪪 Oque é Cibersegurança?
Cibersegurança (ou Cybersecurity) é a área da tecnologia responsável por proteger sistemas, redes, dispositivos e dados contra ataques digitais, acessos não autorizados, roubo de informações ou interrupções de serviço.

# 🛡️ Exemplos práticos de cibersegurança:

- Antivírus e firewalls 🔥
- Autenticação multifator (MFA) 🔑
- Criptografia de dados 🔒
- Monitoramento de redes 🌐
- Backups e planos de recuperação 📂

# 🖥️ Proteção de sistemas

# 🔒 Criptografia
## 1. Hash
Não é exatamente “criptografia” porque não dá pra reverter (é unidirecional).
Transforma um dado em uma sequência fixa de caracteres.
Usado para armazenar senhas, verificar integridade de arquivos, etc.
Exemplos: SHA-256, bcrypt, argon2.

👉 Exemplo: senha 1234 → 03ac674216f3e15c761ee1a5e255f067953623c8…

## 2. Criptografia Simétrica

Usa a mesma chave para criptografar e descriptografar.
Rápida e eficiente.
Problema: é preciso compartilhar a chave com segurança.
Exemplo: AES

👉 Imagine um cofre: quem tem a mesma chave consegue abrir e fechar.

## 3. Criptografia Assimétrica

Usa um par de chaves:
Chave pública → para criptografar
Chave privada → para descriptografar
Resolve o problema de compartilhamento da chave.
Mais lenta, mas muito segura.
Exemplo: RSA, ECC

👉 É o que garante segurança em HTTPS, e-mails seguros, assinaturas digitais.

# 🔑 FA2 (ou 2FA / MFA)

FA2 = Fator de Autenticação Duplo (do inglês: Two-Factor Authentication).
É uma camada extra de segurança no login.
Além da senha, você precisa de outro fator de autenticação, como:
- Código via SMS/Email 📩
- App autenticador (Google Authenticator, Authy) 📱
- Token físico (YubiKey) 🔑
- Biometria (digital, rosto) 👆

👉 A ideia é: mesmo que descubram sua senha, ainda precisam do segundo fator.

# 💉 SQL Injection

SQL Injection é uma vulnerabilidade de segurança que acontece quando **dados do usuário são inseridos diretamente em consultas SQL** sem tratamento adequado.  
Um atacante pode **alterar a consulta**, acessar ou manipular dados que não deveria.

## 📌 Exemplo vulnerável

### Campo sem proteção

SELECT * FROM users 
WHERE username = 'usuario_digitado' 
AND password = 'senha_digitada';

### SQL Injector

SELECT * FROM users 
WHERE username = '' OR '1'='1' 
AND password = '';

**'1'='1' sempre é verdadeiro, então o atacante consegue logar sem saber a senha.**

# 🦾 Proteção

## Senhas e autenticação

- Hash + Salting: use bcrypt ou argon2 para armazenar senhas com hash seguro. (obrigatório)
- 2FA / MFA: adicionar autenticação de segundo fator (app, SMS, biometria). (não é obrigatório, porém recomendado)
- Complexidade de senha: exigir mínimo de caracteres, números, símbolos e letras maiúsculas/minúsculas. (obrigatório)
- Bloqueio de tentativas: limitar logins errados e usar captcha para evitar brute force. (obrigatório)
