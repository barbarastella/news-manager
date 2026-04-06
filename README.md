# News Manager (sistema de gestão de notícias)

![Status](https://img.shields.io/badge/Status-666?style=for-the-badge&logo=status&logoColor=white)![Finished](https://img.shields.io/badge/Finished-green?style=for-the-badge&logoColor=white) 
![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Swing](https://img.shields.io/badge/Java_Swing-000000?style=for-the-badge&logo=java&logoColor=white)
![JPA / Hibernate](https://img.shields.io/badge/JPA-59666C?style=for-the-badge&logo=Hibernate&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)

Aplicação Desktop desenvolvida em Java para gestão de notícias, seus tipos e mídias associadas. Possui interface gráfica construída em Swing e persistência de dados em PostgreSQL utilizando Java Persistence API (JPA) sobre Java Database Connectivity (JDBC).

![Demonstração](./.github/images/demo.gif)

## 🔴 Funcionalidades

O sistema atua como um CMS (Content Management System) local, permitindo:

- [x] Gestão e categorização estruturada dos tipos de notícia (ex: Esportes, Política, Tecnologia);

- [x] Cadastro de midias (URLs) associadas às reportagens;

- [x] Controle completo (CRUD) do conteúdo da notícia, título, tipo e mídias;

- [x] Uma mesma notícia pode conter diversas mídias, e uma mesma mídia pode ser reutilizada em diferentes notícias (relacionamento N-N).

## 🟠 Arquitetura

As entidades do sistema englobam: `Noticias`, `TipoNoticia` e `Midias`. Abaixo está a representação da modelagem de domínio e seus relacionamentos estruturais:

![Diagrama](./.github/images/diagrama.png)

A arquitetura do projeto foi dividida em camadas <mark>&nbsp;Model, View, DAO&nbsp;</mark> para manter uma divisão clara das funções de cada parte do sistema. 

- O gerenciamento de transações com o banco de dados é feito manualmente através da manipulação do `EntityManager`;

- Utilização do Hibernate ORM (Mapeamento Objeto-Relacional) e suas anotações (ex: @Entity, @Table, @Column) para o mapeamento direto das classes para as tabelas do PostgreSQL;

- Implementação de relacionamento bidirecional *Many-To-Many* (N-N) entre Noticias e Midias, com tabela associativa gerada e mantida pelo JPA utilizando `@JoinTable`, onde uma Noticia pode ter diversas mídias associadas, e as Midias podem pertencer a várias notícias;

- Implementação de relacionamento unidirecional *Many-to-One* (N-1) entre Noticias e TipoNoticia, onde uma notícia só pode ser de um único tipo, mas um TipoNoticia pode tipifcar diversas notícias;

- Configuração do `FetchType.EAGER` para carregamento imediato das mídias atreladas à notícia, otimizando o consumo na interface gráfica;

- Interface gráfica construída com componentes nativos do Java Swing (ex: JFrame, JDialog, JList, JComboBox) com WindowListeners que recarregam a grade de dados do banco de dados após fechamento de janelas (modais de cadastro e edição) para manter os dados sempre atualizados e disponíveis para uso.

## 🟡 Execução

**Pré-requisitos:** Java JDK (8 ou superior) e PostgreSQL instalados.

```bash
# Clone o repositório
git clone https://github.com/barbarastella/news-manager-java.git

# Configure o banco de dados atualizando as credenciais no persistence.xml
<property name="javax.persistence.jdbc.url" value="jdbc:postgresql://localhost:5432/nome_do_banco"/>
<property name="javax.persistence.jdbc.user" value="seu_usuario"/>
<property name="javax.persistence.jdbc.password" value="sua_senha"/>

# Compile o arquivo TelaSistemaNoticias.java
```

## 🟢 Contato
<p align="left">
  Em caso de dúvidas ou comentários, entre em contato:&nbsp;
  
  <a href="https://www.linkedin.com/in/barbara-wehrmann/" title="LinkedIn">
    <img align="center" src="https://custom-icon-badges.demolab.com/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin-white&logoColor=fff" alt="LinkedIn"/>
  </a>
  <a href="mailto:barbarastellaw@gmail.com" title="Gmail">
    <img align="center" src="https://img.shields.io/badge/-Gmail-FF0000?style=flat-square&labelColor=FF0000&logo=gmail&logoColor=white" alt="Gmail"/>
  </a>
  <a href="https://www.instagram.com/barbarastellaw" title="Instagram">
    <img align="center" src="https://img.shields.io/badge/-Instagram-DF0174?style=flat-square&labelColor=DF0174&logo=instagram&logoColor=white" alt="Instagram"/>
  </a>
</p>