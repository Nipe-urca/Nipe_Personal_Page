---
title: Produção científica do NIPE
---
<style>
    select {
      width: 250px;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 4px;
      background-color: #f9f9f9;
      font-size: 16px;
      color: #333;
      appearance: none;
      -webkit-appearance: none;
      -moz-appearance: none;
      background-image: url('seta.png');
      background-repeat: no-repeat;
      background-position: right 10px center;
    }

    /* Adicionando estilo para o container */
    .select-container {
      position: relative;
      width: 250px;
    }

    /* Adicionando estilo para a seta */
    .select-container::after {
      content: '';
      position: absolute;
      top: 50%;
      right: 10px;
      width: 10px;
      height: 10px;
      background: url('seta.png') no-repeat;
      transform: translateY(-50%);
      pointer-events: none;
    }
</style>


<body>

<label for="trabalhos">Tipo de publicação:</label>
<select name="trabalhos" id="trabalhos" onchange="handleSelection()">
  <option value="selecione">Selecione</option>
  <option value="periodicos">Publicações em periódicos</option>
  <option value="anais">Anais de eventos</option>
  <option value="aceitos">Aceitos para publicação</option>
  <option value="construindo">Em construção</option>
</select>

<p id="result"></p>

<div id="result"></div>
      
<script>
      function handleSelection() {
        var select = document.getElementById("trabalhos");
        var selectedValue = select.options[select.selectedIndex].value;
        var resultText;
        
        switch(selectedValue) {
          case 'selecione':
            resultText = `<p>Selecione um item.</p>`;
            break;
          case 'periodicos':
            resultText = `<hr><h1>2024</h1> <p> <a href="http://dx.doi.org/10.9790/5933-1503020113"> On The Public Investment-Debt-Cash Linkages In The State Government Of Ceará</a>.
            Publicado no <a href = https://www.iosrjournals.org/iosr-jef.html> IOSR Journal of Economics and Finance</a>. Coautoria do Prof. Valdeir Monteiro.
            </p>
            <h1>2025</h1> <p> <a href="https://www.revistas.usp.br/ecoa/article/view/183129/213527"> Desigualdade de oportunidade educacional e o gap de desempenho entre escolas privadas e públicas</a>.
            Publicado na <a href = https://www.revistas.usp.br/ecoa> Revista de Economia Aplicada</a>. Autoria do Prof. Diogo Sobreira e coautoria do Prof. Jair Araujo (PPGER/UFC).
            </p>
            <hr>
            `;
            break;
            case 'anais':
              resultText = `
              <hr> <h1> 2024</h1> 
              <p> (i) <a href = https://anpec.org.br/nordeste/2024/submissao/arquivos_identificados/047-f5025d3d152b6106179721f646cdc017.pdf>Mudanças na Política de Acesso ao Capital Público no Estado do Ceará: Efeitos Sobre o Crescimento Econômico e o Bem-Estar Social. </a>Em Anais do XXIX Encontro Regional de Economia. Autoria do Prof. Helson Gomes.</p>
              <p>(ii) <a href = https://anpec.org.br/nordeste/2024/submissao/arquivos_identificados/031-7ec509291211cee98d5634d76dde3822.pdf > Como as Mudanças nos Padrões Climáticos Incidem Sobre a Produtividade Agrícola? Uma Análise Para o Estado do Ceará.  </a> Em Anais do XXIX Encontro Regional de Economia. Coautoria do Prof. Helson Gomes.</p>
              <p>(iii) <a href = https://www.anpec.org.br/encontro/2024/submissao/files_I/i5-87c99924bcd49b597b686727ba80c19d.pdf > Does The Education of Leaders Affect Municipal Fiscal Conditions? Evidences From Brazil.  </a> Em Anais do LII Encontro Nacional de Economia. Coautoria do Prof. Helson Gomes.</p>
              <p>(iv) <a href = https://www.anpec.org.br/encontro/2024/submissao/files_I/i10-1016a51b22a67704a00965d038d5eb4b.pdf > Measuring the Relative Cost of Staying in Brazilian Municipalities. </a> Em Anais do LII Encontro Nacional de Economia. Coautoria do Prof. Helson Gomes.</p>
              <p> (v) <a href = https://www.anpec.org.br/encontro/2024/submissao/files_I/i12-357c3c82c6b5d0e369062ec4a5798996.pdf > Violência e Homicídios no Campo: Uma Análise doDiferencial de Homicídios em Municípios Rurais e Urbanos no Brasil. </a> Em Anais do LII Encontro Nacional de Economia. Coautoria do Prof. Helson Gomes.</p>
              <p>(vi) <a href = https://anpec.org.br/nordeste/2024/submissao/arquivos_identificados/135-07bc6c5b90274587e3cb46082a1e135c.pdf>. Eficiência Técnica na Produção de Lavouras Temporárias: Uma Abordagem de Metafronteira Estocástica. </a>Em Anais do XXIX Encontro Regional de Economia. Coautoria do Prof. Diogo Sobreira.</p>
              <p>(vii) <a href = https://www.anpec.org.br/encontro/2024/submissao/files_I/i11-f13c823864ba1240ae9d502929a2edba.docx > GapTecnológico e Eficiência Técnica na Produção de Lavouras Temporárias no Brasil. </a> Em Anais do LII Encontro Nacional de Economia. Coautoria do Prof. Diogo Sobreira. </p>
              <p>(viii) <a href = https://www.anpec.org.br/encontro/2024/submissao/files_I/i11-49da61ee8b726a3869bc226ea8754c89.docx > Rural Credit and Family Farming in the Northeast Region of Brazil. </a> Em Anais do LII Encontro Nacional de Economia. Coautoria do Prof. Diogo Sobreira. </p>
              <p>(ix) <a href = https://www.anpec.org.br/encontro/2024/submissao/files_I/i7-1be317e2274093f6416a3008716a58b9.pdf > Transmissão de Risco Entre os Mercados de Commodities: Uma Análise TVP-VAR e QVAR. </a> Em Anais do LII Encontro Nacional de Economia. Autoria do Prof. Valdeir Monteiro. </p>
              <p> (x) <a href = https://www.even3.com.br/anais/iv-econape/994476-analise-da-potencia-da-politica-monetaria-no-brasil-pos-pandemia-da-covid-19/ > Análise da Potência da Política Monetária no Brasil Pós-Pandemia da COVID-19. </a> Em Anais do IV ECONAPE. Coautoria do Prof. Áydano Ribeiro. </p>
              <hr>
              `;
            break;
            case 'aceitos':
              resultText = `
              <hr>
              <p>(i) Testing Kuznets' environmental hypothesis for the Legal Amazon: a nonlinear approach. Environment and Development Economics, 2025. Autoria do Prof. Helson Gomes.</p>
              <p>(ii) Mais acesso ao crédito rural importa? Efeitos sobre a produção agropecuária cearense. Revista Econômica do Nordeste, 2025. Coautoria do Prof. Diogo Sobreira.</p>
              <p>(iii) Desigualdade de Oportunidade no Acesso ao Ensino Superior nos Meios Urbano e Rural das Regiões Brasileiras. Revista Econômica do Nordeste, 2025. Coautoria do Prof. Helson Gomes.</p>
              <p>(iv) Climatic Factors in Economies of Scale: An Insight Into Agricultural Productivity in the State of Ceará-Brazil. The Journal of Developing Areas, 2025. Autoria do Prof. Helson Gomes.</p>
              <p>(v) Escolas em Tempo Integral e Desempenho no Enem: uma avaliação de impacto para o Estado do Ceará. Revista de Economia Aplicada, 2025. Coautoria do Prof. Helson Gomes.</p>
              <p>(vi) Evidências da Pandemia da Covid-19 no Retorno Educacional no Estado do Ceará. Revista Econômica do Nordeste, 2025. Coautoria do Prof. Áydano Ribeiro Leite.</p>
              <hr>
              `;
            break;
            case 'construindo':
              resultText = `
              <hr>
              <p>Nenhum item disponível!</p>
              <hr>
              `;
            break;
            default:
              resultText = "<span style='color:red;'>Seleção inválida.</span>";
        }
        
        document.getElementById("result").innerHTML = resultText;
      }
</script>

</body>
