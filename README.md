# 🌟 Viva Cultura
Projeto elaborado para aumentar a visibilidade da cultura em Parnaíba-PI, incentivando o público a frequentar mais locais artísticos na cidade, não deixando a cultura morrer na cidade tão bela.

**-> Problema encontrado:**

A falta de culturalização da cidade. Hoje tentando ver em algum site possíveis peças teatrais na agenda da cidade e pouco se encontrei a não ser tentativas de divulgação em sites como Tripadvisor que é voltado para "anúncios" de forma geral e nacional, com isso, resolvi desenvolver esse projeto visando a melhoria desse quesito e buscando manter a cultura viva por aqui. Quem sabe isso se torne nacional um dia, mas, o foco atual é a cidade.

**-> Como resolver?**

O sistema vai ser uma aplicação que terá como todos os públicos ver onde está tendo ou vai ter arte e cultura na cidade, os gestores/organizadores de eventos desse estilo poderão anúnciar gratuítamente no site, essa é a base. Como adereços será adicionado funcionalidades de interação, como feedbacks em eventos, confirmação de presença, curtidas e quem sabe até comentários mais para frente.

## TIpos de usuários
- **Publico (geral):** Sem necessidade de login, visita o site somente para conferir os eventos.
- **Usuário (logado):** Pode fazer avaliações, curtir e interagir com as publicações dos eventos.
- **Organizador:** Pode criar publicações de eventos dentro do site.
- **Administrador:** Tem o poder de gerenciar todo o site, afins de controlar comentários ou posts indevidos (somente a equipe de desenvolvimento, ou seja, eu).

# 💻 Área de Desenvolvimento
Área destinada a estrutura de desenvolvimento do projeto e documentação.

**Informações:**

- **Nome do Projeto:** Viva Cultura
- **Objetivo:** Mapear, centralizar e divulgar os eventos artísticos e teatrais de Parnaíba–PI, conectando produtores locais ao público e incentivando a ocupação dos espaços culturais da cidade.

**Público-Alvo:**

- **Espectadores (Geral):** Moradores e turistas de Parnaíba buscando opções culturais e de lazer.

- **Gestores/Produtores:** Artistas, diretores de teatro, companhias independentes e organizadores de eventos locais.

# Requisitos do Sistema
## Requisitos Funcionais (RF):
**Módulo 1: Público Geral (Espectador)**
- RF01 - _Visualização da Agenda: O usuário poderá visualizar a lista de eventos com título, data, horário, local (ex: Teatro Saraiva, Sesc Caixeiral, Porto das Barcas) e imagem._

- RF02 - _Filtro e Busca: Permitir filtragem de eventos por data, categoria (teatro, música, dança, exposição) e gratuidade._

- RF03 - _Detalhes do Evento: Exibir informações completas do evento, sinopse, classificação indicativa, valor do ingresso e link para compra (se houver)._

- RF04 - _Confirmação de Presença: O usuário poderá clicar em "Vou" para indicar presença e ver o número de pessoas interessadas._

- RF05 - _Interação Social: Permitir que o usuário dê "Curtida" (massa/gostei) nos eventos cadastrados._

- RF06 - _Avaliações/Feedbacks (Fase Posterior): Deixar nota/avaliação e comentários sobre o espetáculo após a realização._

**Módulo 2: Produtores / Gestores Culturais**
- RF07 - _Cadastro de Evento: Formulário simplificado para submissão gratuita de novos eventos (Título, Descrição, Data/Horário, Localização, Banner, Preço/Gratuito)._

- RF08 - _Gestão do Evento: O produtor poderá editar ou cancelar informações do evento cadastrado por ele._

## Requisitos Não Funcionais (RNF)
- RNF01 - _Acessibilidade Web (Responsividade): A interface web deve adaptar-se perfeitamente a dispositivos móveis (smartphones) e desktops._

- RNF02 - _Desempenho: O carregamento da página inicial e da agenda deve ocorrer em menos de 2 segundos sob conexão 3G/4G._

- RNF03 - _Usabilidade: A interface deve ser limpa e direta, exigindo o mínimo de cliques possível para encontrar uma peça ou evento._

- RNF04 - _Custo de Infraestrutura: O sistema inicial utilizará serviços com planos gratuitos (Free Tier) para hospedagem e banco de dados, garantindo sustentabilidade ao projeto._

## Banco de Dados

```
  ┌─────────────────┐
  │    USUARIOS     │
  ├─────────────────┤
  │ PK  id_usuario  │
  │     nome        │
  │     email       │
  │     senha_hash  │
  │     tipo        │──────┐
  └────────┬────────┘      │
           │               │
           │ 1             │ 1
           │               │
           │ N             │ N
  ┌────────┴────────┐    ┌─┴────────────────┐
  │   INTERACOES    │    │      LOCAIS      │
  ├─────────────────┤    ├──────────────────┤
  │ PK  id_interacao│    │ PK  id_local     │
  │ FK  id_usuario  │    │ FK  id_criador   │
  │ FK  id_evento   │    │     nome         │
  │     tipo_acao   │    │     endereco     │
  │     comentario  │    │     bairro       │
  └────────┬────────┘    │     ponto_ref    │
           │             └────────┬─────────┘
           │                      │
           │ N                    │ 1
           │                      │
           │ N                    │ N
  ┌────────┴──────────────────────┴─────────┐
  │                 EVENTOS                 │
  ├─────────────────────────────────────────┤
  │ PK  id_evento                           │
  │ FK  id_produtor                         │
  │ FK  id_local                            │
  │     titulo                              │
  │     descricao                           │
  │     categoria                           │
  │     data_hora_inicio                    │
  │     data_hora_fim                       │
  │     preco                               │
  │     banner_url                          │
  │     link_ingresso                       │
  │     status                              │
  └─────────────────────────────────────────┘
  ```

## Stack de Desenvolvimento
- **Linguagens:** Python +3.12 (Principal), HTML, CSS, JavaScript
- **Frameworks:** Django, Django-Ninja
- **Tipo de Banco de Dados:** PostgreSQL
- **Padrões de Desenvolvimento:** DDD (Drive-Domain Design) e CLEAN
- **Containerização:** Docker

## Tipos de Commit
- **feat:** ```Adição de nova funcionalidade/objeto na aplicação```
- **fix:** ```Correção de erros no codigo da aplicação```
- **chore:** ```Mudanças que não afetam o codigo em sí```
- **docs:** ```Mudanças no arquivo README.md do projeto```