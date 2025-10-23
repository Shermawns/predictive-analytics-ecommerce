
<body>

  <div class="container">
        <header>
            <div>
                <h1>Análise Preditiva de Despesas de Consumidores em E-commerce Utilizando Regressão Linear Múltipla</h1>
                <div class="meta">
                    <strong>Autor:</strong> Shermamm Barbosa Alcântara &nbsp;&middot;&nbsp; 
                    <strong>Data:</strong> 23 de outubro de 2025 &nbsp;&middot;&nbsp; 
                </div>
            </div>
        </header>
        <section class="card">
            <h2>1. Resumo</h2>
          <p>O presente estudo investiga os determinantes do dispêndio anual de clientes em uma plataforma de e-commerce. Utilizando um modelo de Regressão Linear Múltipla, analisou-se a relação entre o "Gasto Anual" (variável dependente) e quatro preditores comportamentais: "Duração Média da Sessão", "Tempo no Aplicativo", "Tempo no Site" e "Tempo como Membro". O conjunto de dados foi segmentado em amostras de treino (70%) e teste (30%) para garantir a validação do modelo em dados não vistos. O modelo final demonstrou alto poder preditivo, explicando 98,1% (R² = 0,981) da variabilidade nos gastos no conjunto de teste, com um Erro Médio Absoluto (MAE) de $8,43. A análise dos coeficientes de regressão indica que o "Tempo como Membro" (β = $61,67) é o preditor de maior impacto financeiro, sugerindo que estratégias de fidelização e retenção de clientes são cruciais para o crescimento da receita.</p>
            <p class="small">
        </section>

   <section class="card">
            <h2>2. Introdução</h2>
            <p>No competitivo setor de e-commerce, a compreensão aprofundada dos fatores que impulsionam o gasto do consumidor é fundamental para a alocação eficiente de recursos e o planejamento estratégico. As empresas coletam vastas quantidades de dados comportamentais, mas extrair insights acionáveis desses dados continua sendo um desafio.</p>
            <p>Este estudo tem como objetivo central desenvolver e validar um modelo de regressão linear múltipla para prever o montante gasto anualmente (<code>Yearly Amount Spent</code>) por clientes de uma plataforma de e-commerce.</p>
            <p>Além da capacidade preditiva, a pesquisa busca responder a duas questões centrais:</p>
           <ol>
                <li>É possível modelar com precisão o gasto anual do cliente utilizando métricas de engajamento digital (tempo em app, tempo em site, duração da sessão) e dados de fidelidade (tempo como membro)?</li>
                <li>Quais desses fatores exercem o impacto estatístico e financeiro mais significativo sobre o gasto do cliente?</li>
            </ol>
            <p>Responder a essas questões permite à gestão da empresa direcionar investimentos de forma mais eficaz, decidindo entre focar no desenvolvimento do aplicativo móvel, na otimização da plataforma web ou em programas de retenção de membros.</p>
            <p>Este documento está estruturado da seguinte forma: a Seção 3 detalha a metodologia, incluindo a descrição dos dados, o pré-processamento e as métricas de avaliação. A Seção 4 apresenta os resultados obtidos, focando no desempenho do modelo e na análise dos coeficientes. A Seção 5 discute as implicações desses resultados, e a Seção 6 conclui o estudo.</p>
        </section>

  <section class="card">
            <h2>3. Materiais e Métodos (Metodologia)</h2>
            
  <h3>3.1. Descrição do Conjunto de Dados</h3>
            <p>O estudo utilizou o conjunto de dados "Ecommerce Customers", que agrega informações anônimas de clientes. As variáveis selecionadas para a modelagem foram:</p>
            <ul>
                <li>
                    <strong>Variável Dependente (y):</strong>
                    <ul>
                        <li><code>Yearly Amount Spent</code>: Gasto total do cliente no último ano (em $).</li>
                    </ul>
  </li>
                <li>
                    <strong>Variáveis Independentes (Preditoras, X):</strong>
                    <ul>
                        <li><code>Avg. Session Length</code>: Duração média da sessão de navegação (em minutos).</li>
                        <li><code>Time on App</code>: Tempo total gasto no aplicativo móvel (em minutos).</li>
                        <li><code>Time on Website</code>: Tempo total gasto no site (em minutos).</li>
                        <li><code>Length of Membership</code>: Tempo que o cliente permanece como membro (em anos).</li>
                    </ul>
                </li>
            </ul>

  <h3>3.2. Análise Exploratória de Dados (EDA)</h3>
            <p>Uma análise exploratória inicial foi conduzida para investigar as relações entre as variáveis. Gráficos de dispersão (scatter plots) e matrizes de correlação (via <code>pairplot</code> da biblioteca Seaborn) foram utilizados. A inspeção visual revelou uma forte correlação linear positiva entre <code>Length of Membership</code> e a variável alvo <code>Yearly Amount Spent</code>, indicando que este seria um preditor potencialmente forte. Outras variáveis, como <code>Time on App</code>, também mostraram correlações positivas, enquanto <code>Time on Website</code> apresentou a correlação mais fraca com o gasto.</p>
            <img width="848" height="830" alt="image" src="https://github.com/user-attachments/assets/fdaea295-d0c0-4886-b444-8c8f05de44b4" />
            <img width="452" height="373" alt="image" src="https://github.com/user-attachments/assets/24ae85d1-afd3-44c1-b42e-af77ff8a5e98" />



<h3>3.3. Pré-processamento e Amostragem</h3>
            <p>As variáveis independentes (X) e a variável dependente (y) foram definidas. O conjunto de dados foi subsequentemente dividido em amostras de treino e teste (proporção 70/30, respectivamente) utilizando a função <code>train_test_split</code> da biblioteca Scikit-learn. Esta divisão estratificada garante que o modelo seja avaliado em dados não utilizados durante o treinamento, fornecendo uma estimativa imparcial de seu desempenho em produção.</p>

  <h3>3.4. Modelagem</h3>
            <p>Foi instanciado um modelo de Regressão Linear Múltipla (<code>LinearRegression</code> do Scikit-learn), adequado para estimar a relação entre uma variável dependente contínua e múltiplas variáveis independentes. O modelo foi treinado (ajustado) utilizando exclusivamente o conjunto de dados de treino (<code>X_train</code>, <code>y_train</code>).</p>

   <h3>3.5. Métricas de Avaliação</h3>
            <p>Para avaliar a precisão e a confiabilidade do modelo, foram utilizadas as seguintes métricas de desempenho, calculadas sobre o conjunto de teste:</p>
            <ul>
                <li><strong>Coeficiente de Determinação (R²):</strong> Mede a proporção da variância na variável dependente que é previsível a partir das variáveis independentes.</li>
                <li><strong>Erro Médio Absoluto (MAE):</strong> A média das diferenças absolutas entre os valores previstos e os reais. Interpreta o erro médio na unidade original (dólares).</li>
                <li><strong>Erro Quadrático Médio (MSE):</strong> A média dos erros ao quadrado. Penaliza erros maiores.</li>
                <li><strong>Raiz do Erro Quadrático Médio (RMSE):</strong> A raiz quadrada do MSE, retornando o erro à unidade original e sendo sensível a outliers.</li>
            </ul>
            <p>Adicionalmente, foi realizada uma análise de resíduos (a diferença entre <code>y_test</code> e <code>y_pred</code>) para verificar os pressupostos do modelo. A normalidade e a homocedasticidade (distribuição aleatória dos erros em torno de zero) são indicativos de um modelo bem ajustado e sem viés sistemático.</p>
        </section>

  <section class="card">
            <h2>4. Resultados</h2>
            
  <h3>4.1. Desempenho Preditivo do Modelo</h3>
  <p>O modelo treinado foi aplicado ao conjunto de teste (<code>X_test</code>) para gerar previsões (<code>y_pred</code>). As métricas de desempenho resultantes estão sumarizadas na Tabela 1.</p>        
     <h4>Tabela 1: Métricas de Desempenho do Modelo no Conjunto de Teste</h4>
            <table border="1" cellpadding="5" cellspacing="0">
                <thead>
                    <tr>
                        <th>Métrica</th>
                        <th>Valor</th>
                        <th>Unidade</th>
                    </tr>
                </thead>
        <tbody>
                    <tr>
                        <td>R-squared (R²)</td>
                        <td>0,981</td>
                        <td>(Proporção)</td>
                    </tr>
                    <tr>
                        <td>MAE</td>
                        <td>8,43</td>
                        <td>$</td>
                    </tr>
                    <tr>
                        <td>MSE</td>
                        <td>100,60</td>
                        <td>$²</td>
                    </tr>
                    <tr>
                        <td>RMSE</td>
                        <td>10,03</td>
                        <td>$</td>
                    </tr>
                </tbody>
  </table>
          <p>O valor de R² (0,981) indica que o modelo consegue explicar 98,1% da variabilidade observada nos gastos anuais, demonstrando um ajuste excelente e alto poder preditivo nos dados de teste. O MAE indica que, em média, as previsões do modelo diferem em apenas $8,43 do valor real.</p>

  <h3>4.2. Análise de Resíduos</h3>
            <p>O histograma dos resíduos (erros de previsão) demonstrou uma distribuição normal (gaussiana) centrada em zero. Este resultado é ideal e confirma que os erros do modelo são aleatórios e não há viés sistemático nas previsões.</p>
            <img width="440" height="350" alt="image" src="https://github.com/user-attachments/assets/27617caa-d235-41dc-810a-7f1047d7268d" />


  <h3>4.3. Análise de Coeficientes (Impacto das Features)</h3>
            <p>Os coeficientes de regressão, que quantificam o impacto de cada variável independente sobre o gasto anual, foram extraídos do modelo treinado. Os resultados estão detalhados na Tabela 2.</p>

<h4>Tabela 2: Coeficientes de Regressão por Variável</h4>
            <table border="1" cellpadding="5" cellspacing="0">
                <thead>
                    <tr>
                        <th>Variável (Feature)</th>
                        <th>Coeficiente (β)</th>
                        <th>Impacto em $ (por unidade)</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Length of Membership</td>
                        <td>61,67</td>
                        <td>$61,67</td>
                    </tr>
                    <tr>
                        <td>Time on App</td>
                        <td>38,60</td>
                        <td>$38,60</td>
                    </tr>
                    <tr>
                        <td>Avg. Session Length</td>
                        <td>25,72</td>
                        <td>$25,72</td>
                    </tr>
                    <tr>
                        <td>Time on Website</td>
                        <td>0,46</td>
                        <td>$0,46</td>
                    </tr>
                </tbody>
            </table>
  </section>

  <section class="card">
            <h2>5. Discussão</h2>
            <p>Os resultados apresentados na Seção 4 demonstram que o modelo de regressão linear não apenas é viável (R² = 0,981), mas também oferece insights estratégicos claros para o negócio.</p>
            <p>A análise dos coeficientes (Tabela 2) é particularmente elucidativa. O <code>Length of Membership</code> (Tempo como Membro) emerge como o fator de maior impacto financeiro. Mantendo todas as outras variáveis constantes, cada ano adicional que um cliente permanece como membro está associado a um aumento esperado de $61,67 em seus gastos anuais. Isso quantifica o valor da fidelização do cliente de forma direta.</p>
            <p>O <code>Time on App</code> (Tempo no Aplicativo) também se mostra um fator relevante, com um coeficiente de $38,60. Isso sugere que o engajamento com o aplicativo móvel é um forte impulsionador de receita.</p>
            <p>Em contrapartida, o <code>Time on Website</code> (Tempo no Site) apresenta um coeficiente de apenas $0,46. Este valor, próximo de zero, sugere que o tempo gasto no site tem um impacto financeiro quase insignificante nos gastos anuais, quando comparado ao aplicativo e ao tempo de associação.</p>

  <h3>5.1. Implicações Estratégicas</h3>
            <p>Com base nesta análise, as implicações para a alocação de recursos são claras:</p>
            <ul>
                <li><strong>Foco na Retenção:</strong> O maior retorno sobre o investimento (ROI) parece estar em estratégias de retenção e fidelização. O impacto de $61,67 por ano de membro supera o de qualquer outra métrica de engajamento. Programas de fidelidade, marketing de relacionamento e melhorias na experiência do membro devem ser priorizados.</li>
                <li><strong>Investimento em Aplicativo (App-first):</strong> O aplicativo móvel é significativamente mais valioso que o site. Os esforços de desenvolvimento devem ser concentrados em melhorar a usabilidade, performance e engajamento do app, pois o tempo gasto nele se converte diretamente em receita.</li>
                <li><strong>Reavaliação do Site:</strong> O baixo impacto do site ($0,46) sugere que ele pode estar servindo como um canal de descoberta inicial, mas não como uma plataforma de gastos para clientes estabelecidos. A empresa deve decidir se tenta reverter esse quadro (investindo em melhorias) ou se aceita seu papel secundário, usando-o como um funil para levar os usuários ao aplicativo.</li>
            </ul>
        </section>
 <section class="card">
            <h2>6. Conclusão</h2>
            <p>Este estudo demonstrou com sucesso a aplicação da Regressão Linear Múltipla para prever os gastos anuais de clientes de e-commerce e identificar os principais impulsionadores de receita. O modelo final apresentou alta acurácia (R² = 0,981).</p>
      <p>O principal achado é que a retenção de clientes (<code>Length of Membership</code>) é o fator mais crítico para o aumento da receita, seguido pelo engajamento no aplicativo móvel (<code>Time on App</code>). O tempo gasto no site mostrou-se financeiramente pouco relevante.</p>
            <p>Recomenda-se que a empresa direcione seus esforços estratégicos para programas de fidelização e para o desenvolvimento contínuo de sua plataforma de aplicativo móvel.</p>
            <p>Limitações deste estudo incluem o uso de dados de uma única empresa, o que pode não generalizar para todo o setor. Pesquisas futuras poderiam explorar modelos não lineares que ainda estão sobre meus estudos (ex: Random Forest, Gradient Boosting) para capturar interações mais complexas ou incluir variáveis demográficas e de aquisição de clientes.</p>      </section>

   </div>
</body>
</html>
