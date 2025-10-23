<body>

<div class="container">
        <header>
            <div>
                <h1>Análise Preditiva de Despesas de Consumidores em E-commerce</h1>
            </div>
        </header>

   <section class="card">
            <p>Este repositório contém um projeto de Ciência de Dados focado em prever o gasto anual de clientes de uma plataforma de e-commerce utilizando Regressão Linear Múltipla. O objetivo é entender quais fatores comportamentais impulsionam a receita e fornecer insights estratégicos para a empresa.</p>
         <p><strong>Para uma análise científica detalhada, metodologia completa e a discussão aprofundada dos resultados, consulte o arquivo <code>relatorio.html</code>.</strong></p>
        </section>

   <section class="card">
            <h2>🎯 Objetivo do Projeto</h2>
            <p>O objetivo central é construir um modelo preditivo capaz de estimar o valor gasto anualmente (<code>Yearly Amount Spent</code>) por um cliente, com base nas seguintes métricas de engajamento:</p>
            <ul>
                <li><code>Avg. Session Length</code>: Duração média da sessão de navegação.</li>
                <li><code>Time on App</code>: Tempo total gasto no aplicativo móvel.</li>
                <li><code>Time on Website</code>: Tempo total gasto no site.</li>
                <li><code>Length of Membership</code>: Tempo que o cliente permanece como membro (em anos).</li>
            </ul>
            <p>Além da previsão, o projeto busca identificar quais desses fatores têm o maior impacto financeiro, ajudando a responder questões como: "Devemos investir mais no App ou no Website?" ou "Qual o valor da retenção de clientes?".</p>
        </section>

  section class="card">
            <h2>🛠️ Tecnologias Utilizadas</h2>
            <p>Este projeto foi desenvolvido utilizando as seguintes bibliotecas do ecossistema Python para Ciência de Dados:</p>
            <ul>
                <li><strong>Python 3.x</strong></li>
                <li><strong>Pandas:</strong> Para manipulação e análise dos dados.</li>
                <li><strong>NumPy:</strong> Para operações numéricas.</li>
                <li><strong>Scikit-learn:</strong> Para a criação do modelo de <code>LinearRegression</code> e cálculo das métricas de avaliação (<code>train_test_split</code>, <code>MAE</code>, <code>MSE</code>, <code>R²</code>).</li>
                <li><strong>Matplotlib & Seaborn:</strong> Para a Análise Exploratória de Dados (EDA) e visualização das relações entre as variáveis (ex: <code>pairplot</code>).</li>
                <li><strong>Jupyter Notebook:</strong> Para o desenvolvimento e documentação da análise.</li>
            </ul>
 </section>

<section class="card">
            <h2>🚀 Como Executar o Projeto</h2>
            <ol>
                <li>
                    <strong>Clone o repositório:</strong>
                    <pre><code>git clone https://github.com/seu-usuario/ecommerce-customer-spending-prediction.git
cd ecommerce-customer-spending-prediction</code></pre>
                </li>
                <li>
                    <strong>Crie um ambiente virtual (recomendado):</strong>
                    <pre><code>python -m venv venv
source venv/bin/activate  # No Windows: venv\Scripts\activate</code></pre>
                </li>
                <li>
                    <strong>Instale as dependências:</strong>
                    <p>(É recomendado criar um arquivo <code>requirements.txt</code> com as bibliotecas listadas acima).</p>
                    <pre><code>pip install pandas numpy scikit-learn matplotlib seaborn jupyter</code></pre>
                </li>
                <li>
                    <strong>Execute o Jupyter Notebook:</strong>
                    <pre><code>jupyter notebook</code></pre>
                    <p>Abra o notebook principal (ex: <code>analise_ecommerce.ipynb</code>) para ver todo o processo de análise e treinamento.</p>
                </li>
            </ol>
        </section>
