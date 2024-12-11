Relatório Final: Sistema de Recomendação de Animes


i. Descrição do Problema, Dataset e Pré-processamento
Problema: O desafio deste projeto foi construir um sistema de recomendação de animes que pudesse sugerir opções interessantes para os usuários com base em suas preferências pessoais e no comportamento de outros usuários. O sistema precisava ser capaz de fornecer recomendações precisas para diferentes perfis de usuários, levando em consideração suas avaliações e os gêneros dos animes. O objetivo era criar um sistema que fosse capaz de sugerir animes tanto para aqueles com um histórico de avaliações quanto para novos usuários, sem deixar ninguém de fora.

Dataset: Para esse projeto, utilizei um dataset que contém informações detalhadas sobre animes e interações de usuários com esses animes. As principais colunas do dataset incluem:

Name: O nome do anime.
Genres: Os gêneros atribuídos aos animes, como ação, fantasia, etc.
Score: A avaliação média de cada anime dada pelos usuários.
Members: O número de pessoas que assistiram ou avaliaram o anime.
Anime ID: Um identificador único para cada anime.
Além disso, o dataset inclui dados sobre as avaliações dos usuários, como:

User ID: Identificador único do usuário.
Rating: A nota que o usuário deu a um anime específico.
Anime ID: O identificador do anime que foi avaliado.
Pré-processamento: A primeira etapa do processo foi tratar o dataset para garantir que as informações estivessem limpas e prontas para análise. Isso envolveu:

Limpeza de Dados: Foram removidos dados faltantes ou inválidos, como registros de animes sem pontuação ou com gêneros não informados.
Codificação de Gêneros: Como os gêneros são uma parte importante para recomendar animes, eles foram convertidos em uma representação numérica usando a técnica TF-IDF (Term Frequency-Inverse Document Frequency), que avalia a importância de cada gênero nos animes.
Filtragem de Popularidade: Para garantir que o modelo trabalhasse de forma eficaz, selecionei apenas animes com uma quantidade mínima de interações (>= 50), o que ajudou a melhorar a qualidade das recomendações, ao focar em animes mais populares.


ii. Resultados do Modelo Base e Aprimorado, com Análise Comparativa
Modelo Base: No modelo inicial, a recomendação de animes era baseada exclusivamente na similaridade de gênero. Ou seja, se um usuário gostava de animes de ação e fantasia, o sistema recomendava animes que compartilhassem esses mesmos gêneros. Para calcular a similaridade entre os animes, usei a técnica de similaridade cosseno, que compara as representações dos gêneros de cada anime no espaço vetorial.

Embora essa abordagem tenha dado bons resultados, ela possui limitações, especialmente quando o usuário não tem um histórico claro de preferências. Por exemplo, para usuários novos, ou para animes pouco avaliados, o sistema teria dificuldades em fazer boas recomendações, pois dependia apenas dos gêneros.

Modelo Aprimorado: O modelo aprimorado superou essas limitações ao adicionar a filtragem colaborativa. Agora, além de comparar os gêneros dos animes, o sistema também considera as avaliações feitas por outros usuários com gostos semelhantes. Essa abordagem foi especialmente útil para novos usuários, pois o sistema pode sugerir animes com base em preferências de outros usuários que tenham perfis parecidos.

Combinando as duas abordagens — filtragem baseada em gêneros e filtragem colaborativa — o sistema se tornou mais robusto e diversificado, oferecendo recomendações mais precisas e interessantes para os usuários, independentemente do histórico de avaliações.

Análise Comparativa:

Filtragem Baseada em Similaridade de Gênero (Modelo Base): Foi eficaz em casos onde o usuário tem um gosto claro por certos gêneros, mas foi limitada para novos usuários ou animes pouco avaliados.
Filtragem Baseada em Similaridade de Usuários (Modelo Aprimorado): A abordagem colaborativa se mostrou mais eficiente ao considerar o comportamento de outros usuários, especialmente para aqueles com menos histórico de avaliações. Porém, a precisão das recomendações depende da quantidade de dados disponíveis e da diversidade de usuários.
A combinação das duas abordagens melhorou significativamente as recomendações, tornando-as mais precisas e adaptáveis a diferentes perfis de usuários.



iii. Limitações do Agente e Possíveis Melhorias Futuras
Limitações:

Cold-start Problem: Mesmo com a combinação das abordagens, o sistema ainda enfrenta dificuldades com novos usuários ou animes pouco avaliados. Isso ocorre porque a filtragem colaborativa depende do histórico de interações, o que não está disponível para novos usuários ou animes recentes.
Precisão das Recomendacões: As recomendações podem ser imprecisas em alguns casos, especialmente quando a similaridade entre os gêneros é muito semelhante, mas os gostos dos usuários podem ser diferentes. A filtragem colaborativa também pode ser influenciada por comportamentos atípicos de usuários.
Escalabilidade: O cálculo da similaridade cosseno entre todos os animes e usuários pode se tornar ineficiente com o crescimento do número de animes e avaliações. Isso pode afetar a performance do sistema em bases de dados muito grandes.
Possíveis Melhorias Futuras:

Modelos Híbridos Avançados: A combinação dos dois tipos de filtragem pode ser ainda mais otimizada com o uso de modelos de aprendizado de máquina, como redes neurais ou modelos de fatoração de matrizes, como o ALS (Alternating Least Squares), que pode capturar de forma mais eficiente as interações entre usuários e animes.
Tratamento de Dados Faltantes: Melhorar a estratégia de tratamento de dados faltantes e considerar técnicas de imputação mais avançadas pode ajudar a melhorar a precisão das recomendações, principalmente quando os dados do usuário estão incompletos.
Uso de Informações Adicionais: Incorporar mais informações sobre os animes, como sinopses, trailers, ou até mesmo detalhes de produção, pode enriquecer as recomendações, tornando-as mais contextualizadas e personalizadas.
Análise de Sentimentos: Aplicar técnicas de análise de sentimentos nas avaliações dos usuários pode permitir uma recomendação mais sensível aos sentimentos expressos nas avaliações, melhorando a personalização do sistema.
Sistema de Feedback: Implementar um sistema onde os usuários possam avaliar as recomendações e fornecer feedback direto pode ajudar o modelo a aprender e se ajustar com o tempo, melhorando continuamente a experiência do usuário.
