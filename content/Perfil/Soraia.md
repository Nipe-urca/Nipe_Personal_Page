---
output: html_document
---

<div style="display: flex; align-items: center; gap: 20px;">
  <div>
    <img src="/images/soraiaCircular.png" width="240" height="240" style="display: block; border-radius: 50%; object-fit: cover;">
  </div>
  <div style="text-align: left;">
    <a href="http://lattes.cnpq.br/1962326036877415" target="_blank" style="font-size: 32px; font-weight: bold; text-decoration: none;">Soraia Araújo Madeira</a>
    <p style="margin: 5px 0 0 0;">Doutora em Economia (UFV)</p>
    <p style="margin: 5px 0 0 0;">Área mãe: Microeconometria</p>
    <p style="margin: 5px 0 0 0;">Contato: soraiamadeira@gmail.com</p>
  </div>
</div>


# Formação acadêmica e atuação profissional

Concluiu a Graduação em Ciências Econômicas pela Universidade Regional do Cariri (URCA) em 2009. Possui o título de Mestrado em Economia Rural pelo Programa de Pós-Graduação em Economia Rural da Universidade Federal do Ceará (PPGER/UFC) obtido em 2012. Possui o título de Doutorado em Economia Aplicada pelo Programa de Pós-Graduação em Economia Aplicada da Universidade Federal de Viçosa (PPGEA/UFV) obtido em 2018. Atualmente é Professora Adjunta do Departamento de Economia da Universidade Regional do Cariri (URCA), atuando no curso de Ciencias Econômicas do Campus Iguatu. Também atua como Economista da Saúde na Prefeitura Municipal de Iguatu-CE.

# Áreas de interesse e atuação

* Economia do trabalho.

* Economia agrária e dos recursos naturais.

* Métodos quantitativos aplicados à economia.

<hr>

# Produção bibliográfica

## Artigos publicados em periódicos

### 2019

* **Madeira, S. A**; Khan, A. S; Sousa, E. P; Barros, F. L. A; [Análise da modernização agrícola cearense no período de 1996 e 2006](http://dx.doi.org/10.5007/1982-5153.2019v34n72p307). ***GEOSUL (UFSC)***, v.34, p.307-334, 2019.

### 2018 

* Alves, F. F; **Madeira, S. A**; Sousa, L. V. C. [Eficiência e Convergência da Inovação: um Estudo do Progresso Tecnológico para Países Desenvolvidos e em Desenvolvimento](https://seer.ufrgs.br/index.php/AnaliseEconomica/article/view/60686). ***Análise Econômica (UFRGS)***, v.36, p.121-148, 2018.

* **Madeira, S. A**; Sobreira, D. B; Lima, J. E. ; Justo, W. R . [Desempenho do mercado de trabalho cearense em 2000 e 2010](https://www.researchgate.net/publication/338282247_DESEMPENHO_DO_MERCADO_DE_TRABALHO_CEARENSE_EM_2000_E_2010#read), ***Economia e Políticas Públicas***, v.6, p.99-124, 2018.

### 2016

* Sobreira, D. B; **Madeira, S. A**; Freitas, C. O; Lima, J. E. [Eficiência técnica agropecuária no estado da Bahia e seus fatores condicionantes no curto e longo prazo](https://doi.org/10.61673/ren.2016.626). ***Revista Econômica do Nordeste***, v.47, p.59-76, 2016.

### 2012

* Alves. C. L. B; **Madeira, S. A**; Macambira, J. [Serviços e Desenvolvimento Regional: Considerações a Partir do Mercado de Trabalho Cearense](https://www.bnb.gov.br/revista/ren/article/view/204/182). ***Revista Econômica do Nordeste***, v.43, p.155-170, 2012.

* Alves. C. L. B; **Madeira, S. A**; Macambira, J. [Considerações sobre a dinâmica do setor de serviços cearense: uma análise sob a ótica do mercado de trabalho](https://www.ipea.gov.br/ppp/index.php/PPP/article/view/281). ***Planejamento e Politicas Publicas***, v.38, p.211-235, 2012.

<hr>


<p style = "align-content = center; font-size: 25px; text-align: center">
 <strong>Resumo da produção acadêmica</strong>
</p>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<!-- Canvas para Publicações -->
<canvas id="graficopublicacao" width="600" height="220" style="margin-top: 2rem; margin-bottom: 2rem;"></canvas>

<!-- Canvas para Citações por Ano -->
<!--  <canvas id="graficocitacao" width="600" height="220" style="margin-top: 2rem; margin-bottom: 2rem;"></canvas> -->

<!-- Canvas para Citações Acumuladas -->
<!--  <canvas id="graficocitacaoacumulada" width="600" height="220" style="margin-top: 2rem; margin-bottom: 3rem;"></canvas> -->

<script>
  document.addEventListener("DOMContentLoaded", function () {
    const historico = [
      {"ano": "2012", "publicacoes": 2, "citacoes": 0},
      {"ano": "2013", "publicacoes": 0, "citacoes": 0},
      {"ano": "2014", "publicacoes": 0, "citacoes": 0},
      {"ano": "2015", "publicacoes": 0, "citacoes": 0},
      {"ano": "2016", "publicacoes": 1, "citacoes": 0},
      {"ano": "2017", "publicacoes": 0, "citacoes": 0},
      {"ano": "2018", "publicacoes": 2, "citacoes": 0},
      {"ano": "2019", "publicacoes": 1, "citacoes": 0},
      {"ano": "2020", "publicacoes": 0, "citacoes": 0},
      {"ano": "2021", "publicacoes": 0, "citacoes": 0},
      {"ano": "2022", "publicacoes": 0, "citacoes": 0},
      {"ano": "2023", "publicacoes": 0, "citacoes": 0},
      {"ano": "2024", "publicacoes": 0, "citacoes": 0},
      {"ano": "2025", "publicacoes": 0, "citacoes": 0},
      {"ano": "2026", "publicacoes": 0, "citacoes": 0}
    ];

    // 1. Processa e agrupa os dados por ano
    const dadosConsolidados = historico.reduce((acc, item) => {
      if (!acc[item.ano]) {
        acc[item.ano] = { publicacoes: 0, citacoes: 0 };
      }
      acc[item.ano].publicacoes += item.publicacoes;
      acc[item.ano].citacoes += item.citacoes;
      return acc;
    }, {});

    const anos = Object.keys(dadosConsolidados);
    const publicacoes = anos.map(ano => dadosConsolidados[ano].publicacoes);
    const citacoes = anos.map(ano => dadosConsolidados[ano].citacoes);

    // Cálculo da soma acumulada de citações
    let acumulado = 0;
    const citacoesAcumuladas = citacoes.map(qtd => acumulado += qtd);

    // 2. Gráfico 1: Publicações por Ano
    const ctxPublicacao = document.getElementById('graficopublicacao');
    if (ctxPublicacao) {
      new Chart(ctxPublicacao, {
        type: 'bar',
        data: {
          labels: anos,
          datasets: [{
            label: 'Número de Publicações',
            data: publicacoes,
            backgroundColor: 'rgba(54, 162, 235, 0.7)',
            borderColor: 'rgba(54, 162, 235, 1)',
            borderWidth: 1,
            borderRadius: 4
          }]
        },
        options: {
          responsive: true,
          scales: { y: { beginAtZero: true, ticks: { stepSize: 1 } } }
        }
      });
    }
<!--
    // 3. Gráfico 2: Citações por Ano
    const ctxCitacao = document.getElementById('graficocitacao');
    if (ctxCitacao) {
      new Chart(ctxCitacao, {
        type: 'bar',
        data: {
          labels: anos,
          datasets: [{
            label: 'Número de Citações (Anual)',
            data: citacoes,
            backgroundColor: 'rgba(255, 159, 64, 0.7)',
            borderColor: 'rgba(255, 159, 64, 1)',
            borderWidth: 1,
            borderRadius: 4
          }]
        },
        options: {
          responsive: true,
          scales: { y: { beginAtZero: true } }
        }
      });
    }

    // 4. Gráfico 3: Citações Acumuladas
    const ctxAcumulado = document.getElementById('graficocitacaoacumulada');
    if (ctxAcumulado) {
      new Chart(ctxAcumulado, {
        type: 'bar',
        data: {
          labels: anos,
          datasets: [{
            label: 'Citações Acumuladas',
            data: citacoesAcumuladas,
            backgroundColor: 'rgba(153, 102, 255, 0.7)', // Cor roxa para destacar a curva acumulada
            borderColor: 'rgba(153, 102, 255, 1)',
            borderWidth: 1,
            borderRadius: 4
          }]
        },
        options: {
          responsive: true,
          scales: {
            x: { title: { display: true, text: 'Ano' } },
            y: {
              beginAtZero: true,
              title: { display: true, text: 'Total Acumulado de Citações' }
            }
          }
        }
      });
      
      -->
    }
  });
</script>

