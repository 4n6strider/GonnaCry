# GonnaCry Rasonware --- ALMOST READY
GonnaCry é um Ransomware que criptografa todos os arquivos do usuário, sem volta, até a comunicar com o servidor para ter a chave privada e assim, desfazer a criptografia.

GonnaCry não deve ser usado para prejudicar ninguém, é apenas um programa acadêmico, feito para gerar estudo e aprendizado.
Não está totalmente completo, nem tem todas as funcionalidades do WannaCry2.0, porém, contém algumas das suas características.

# O que é um ransomware?
Ransonware é um tipo de virus que impede o uso do computador da pessoa infectada.

Alguns Ransomwares bloqueiam a tela do usuario, não permitindo o seu uso, já outros criptografam todos os arquivos importantes do usuário.




Se voce quiser testar: https://github.com/tarcisio-marinho/Ransomware/blob/master/tests/README.md
este teste não afeta os arquivos do seu computador, apenas os arquivos dentro da pasta /teste que eu os coloquei exatamente para testar.

~$ sudo pip install -r requeriments.txt


# Objetivos:
- [x] Criptografar todos os arquivos com AES-256-CBC
- [ ] Comunicação com o servidor para pedir chave privada
- [x] criptografar chave AES com RSA-1024
- [ ] Programa completo


# Geração de Chaves
- O servidor gera sua chave privada e pública (RSA). Únicas, imutáveis, que serão utilizadas para criptografar a chave AES, gerada pelo Ransomware.

- Ao cliente ser infectado, o Ransomware gera 3 chaves:
- Chave para criptografar os arquivos. Algoritmo -> AES (chave simétrica)
- Chave privada única do cliente infectado. Algoritmo -> RSA (chave assimétrica).
- Chave pública única do cliente infectado. Algoritmo -> RSA (chave assimétrica).

# Algoritmo de execução:
- Criptografa todos os arquivos da vítma com a chave AES.
- Ao fim do passo anterior, a chave AES é criptografada com a chave pública do Ransomware.
- A chave privada do Ransomware é criptografada com a chave pública do servidor(única e imutável).

# Para descriptografar:
- Para descriptografar os arquivos, é necessário da chave AES, esta, que só pode ser criptografada por uma chave privada. A mesma chave privada está criptografada com uma chave pública do servidor. Para reverter os dados da vítma, é necessário a chave privada do servidor, para descriptografar a chave privada do Ransomware, com a chave privada do Ransomware, é possível descriptografar a chave AES. Por fim, utilizar a chave AES para descriptografar os arquivos da vítma.
- Pode parecer confuso, muitas "criptografa", "descriptografa" e "chaves" kkkkk
