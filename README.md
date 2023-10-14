# SOLID

![SOLID](images/SOLID.webp)

## Descrição

### O que é SOLID?

SOLID é um acrõnimo criado por Michael Feathers para observar 5 princípios da programação orientada a objetos que são considerados boas práticas para o desenvolvimento de software.

### Vantagens do SOLID

O uso dos princípios SOLID traz diversas vantagens para o desenvolvimento de software, aqui estão algumas das que eu encontrei:

- **Facilita a manutenção:** O SOLID propõe uma abordagem de código mais limpo e organizada, tornando o software mais fácil de entender e manter, isso reduz a probabilidade de erros e facilita a correção de bugs.
- **Aumenta a reutilização de código:** Implementações que aderem ao SOLID, de forma geral são mais coesas e possuem menos acoplamento, o que possibilita a reutilização de código em diversas partes do software.
- **Melhora a testabilidade:** Classes que seguem o SOLID tendem a ser mais fáceis de testar, pois possuem apenas 1 responsabilidade e são claramente definidas, isso facilita a criação de testes unitários.
- **Aumenta a compreensão do código:** Códigos que seguem os príncipios SOLID são mais legíveis e compreensíveis, facilitando a colaboração entre outros membros da equipe e a manutenção a longo prazo.
- **Melhora a arquitetura de forma geral:** O SOLID contribui para uma arquitetura de software mais robusta e flexível, tornando o software adaptável a mudanças nos requisitos e nas necessidades dos usuários.

Em resumo, o uso dos princípios do SOLID resulta em software de maior qualidade, mais flexível e fácil de manter. Isso é crucial em projetos de desenvolvimento de software de longo prazo, nos quais a escalabilidade e a manutenção são fatores críticos para o sucesso.

## SRP - Single Responsibility Principle

>Princípio da Responsabilidade Única
>Uma classe deve ter uma, e somente uma responsabilidade.

![SRP](images/SRP.webp)

Uma classe deve ter apenas uma responsabilidade dentro do código, ou seja, ela deve ter apenas um motivo para existir.
Se uma classe tem mais de uma responsabilidade, ela tem mais de um motivo para ser alterada.

### Como podemos identificar uma classe que esta fora do SRP?

- A classe possui muitos atributos ou métodos.
- Podemos identificar quando a classe possui muitos "e" ou "ou" em sua descrição.
- A classe é chamada por clientes que não usam todos os seus atributos, métodos e/ou possui muitas dependências.

### Exemplo: errado

```kotlin

class User(
    val name: String,
    val email: String,
    val password: String
) {
    fun save() {
        // Salva o usuário no banco de dados
    }

    fun sendEmail(user: User) {
        // Envia um email para o usuário
    }
}

```

Como podemos ver no exemplo, a classe User, é responsável por:

- Gerenciar os parâmetros de um usuário
- Salvar o usuário no bando de dados
- Enviar um email para um usuário

Isso gera um alto acoplamento, e não conseguimos reutilizar o código em outras partes do software.

### Exemplo: certo

Refatorando e aplicando o SRP na classe user, teremos o seguinte código:

```kotlin

class User(
    val name: String,
    val email: String,
    val password: String
)

class DataBase() {
    fun saveUser(user: User) {
        // Salva um usuário no banco de dados
    }
}

class EmailSender() {
    fun sendEmail(sender: User, recipient: User) {
        // Envia um email para o usuário
    }
}

```

Separamos as responsabilidades em +2 classes.

- A classe user fica responsável somente por gerenciar os parâmetros de um usuário.
- A classe database é responsável por gerenciar o bando de dados, então ela pode salvar, deletar e exibir um usuário.
- A classe emailsender é responsável pelo envio de emails de um usuário a outro.

Agora, além de cada classe ter somente uma responsabilidade, também podemos reutilizar o código em outras partes do software.

---

## Referências

### Cursos

- [SOLID - Os 5 Princípios Para as Boas Práticas da POO](https://www.udemy.com/share/10358U/)

### Vídeos

- [Programadores com código sujo : SOLID](https://www.youtube.com/watch?v=J2ugvRObGT4&ab_channel=LucasMontano)
- [SOLID fica FÁCIL com Essas Ilustrações](https://www.youtube.com/watch?v=6SfrO3D4dHM&ab_channel=FilipeDeschamps)
- [SOLID - O básico para você programar melhor](https://www.youtube.com/watch?v=mkx0CdWiPRA&ab_channel=C%C3%B3digoFonteTV)

### Posts

- [S.O.L.I.D no Android](https://medium.com/android-dev-br/s-o-l-i-d-no-android-d55e23f1c72d)
- [The SOLID Principles for Android Developers](https://medium.com/kayvan-kaseb/the-solid-principles-for-android-developers-75fd4ca3ef84)
- [O que é SOLID: O guia completo para você entender os 5 princípios da POO](https://medium.com/desenvolvendo-com-paixao/o-que-%C3%A9-solid-o-guia-completo-para-voc%C3%AA-entender-os-5-princ%C3%ADpios-da-poo-2b937b3fc530)
- [SOLID — Princípios da Programação Orientada a Objetos](https://medium.com/thiago-aragao/solid-princ%C3%ADpios-da-programa%C3%A7%C3%A3o-orientada-a-objetos-ba7e31d8fb25)
- [The S.O.L.I.D Principles in Pictures](https://medium.com/backticks-tildes/the-s-o-l-i-d-principles-in-pictures-b34ce2f1e898)
- [Os Princípios SOLID em Imagens](https://warcontent.com/principios-solid-imagens/)

### Repositórios

- [SOLID-kotlin](https://github.com/marceloalves95/SOLID-Kotlin)

### Podcasts

- [SOLID: Código bom e bonito](https://open.spotify.com/episode/6fRVaqJxqrqilW1sfQh1pk?si=eRUgCrZgQ8Oq2SNECDocjw)
