O projeto inicia-se com a extração de dados reais da indústria de games via API RAWG. Foi implementado um algoritmo de coleta automatizada que consome os endpoints da API para recuperar uma amostra de 200 títulos.

Técnica utilizada: Loop controlado com tratamento de exceções e controle de throttling (time.sleep) para garantir a integridade da conexão.

Dados coletados: Nome, nota dos usuários (target), gêneros, tags (mecânicas), nota do Metacritic, contagem de reviews e data de lançamento.

Na etapa de processamento e limpeza os dados brutos foram transformados em um conjunto de dados pronto para análise:

Imputação de Valores Ausentes: Utilizou-se a mediana para preencher lacunas na coluna do Metacritic, evitando que valores nulos distorcessem a média estatística.

Filtragem: Remoção de registros sem avaliação (nota zero), garantindo que a análise se concentre apenas em jogos com recepção de público validada.

Normalização Temporal: Conversão de datas para o formato datetime, permitindo análises baseadas em séries temporais.

Para traduzir conceitos qualitativos em dados quantitativos, foi aplicada a técnica de variáveis binárias (Dummies). Foram criadas cinco novas colunas para representar pilares de design:

estetica_2d, mundo_aberto, narrativa_forte, dificuldade_alta e multiplayer. A lógica foi aplicada através da verificação de tags específicas dentro do conjunto de dados original, permitindo medir o impacto isolado de cada mecânica.

Foram geradas visualizações complexas para validar as hipóteses de negócio:
Distribuição de Notas (Boxplots): Utilizados para observar a variância e a consistência de cada atributo de design.

Relação Popularidade vs. Nota: Um gráfico de dispersão interativo com escala logarítmica para identificar se jogos populares mantêm a qualidade crítica.

Performance Média: Comparativo direto de cada atributo contra a média geral do dataset (Baseline), identificando quais atributos "agregam valor" acima da média.

O ápice do projeto foi a implementação de um modelo de Random Forest Regressor para prever a nota de um jogo:

Divisão de Dados: Separação entre treino (80%) e teste (20%) para validação de performance.

Métricas de Validação: Implementação do R² Score (poder explicativo) e MAE (Erro Médio Absoluto), fornecendo uma base científica para a precisão do modelo.

Importância das Variáveis: O modelo revelou quais características são os maiores "preditores" de uma nota alta, separando o impacto da crítica (Metacritic) do impacto direto das mecânicas de jogo.


Conclusão
Este projeto demonstra que o sucesso de um produto de entretenimento, como um videogame, não é fruto apenas do acaso, mas possui padrões estatísticos identificáveis. Através da análise, ficou evidente que:

Mecânicas Prevalentes: Elementos como "Narrativa Forte" e "Mundo Aberto" não apenas são populares em volume, mas sustentam médias de avaliação superiores, validando a tendência atual de mercado para grandes produções.

Influência da crítica para o público: O modelo de Machine Learning confirmou que a opinião profissional (Metacritic) é o maior preditor de sucesso, mas atributos intrínsecos de design (como o foco narrativo) possuem um peso significativo e mensurável na satisfação final do usuário.

Insights para Game Design: A análise permite que desenvolvedores e investidores tomem decisões baseadas em dados (Data-Driven), minimizando riscos ao escolher mecânicas que historicamente performam melhor dentro do seu nicho específico.
