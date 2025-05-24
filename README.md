<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Quiz Verdadeiro ou Falso - Sistemas Corporativos</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 20px; background-color: #f4f4f4; }
    .container { max-width: 700px; margin: auto; background: white; padding: 20px; border-radius: 10px; box-shadow: 0 0 10px rgba(0,0,0,0.1); }
    .question { margin-bottom: 20px; }
    .buttons { margin-top: 10px; }
    button { margin-right: 10px; padding: 10px 20px; cursor: pointer; }
    .result { font-weight: bold; margin-top: 10px; }
    .hidden { display: none; }
  </style>
</head>
<body>
  <div class="container">
    <h1>Quiz: Verdadeiro ou Falso</h1>
    <div id="quiz"></div>
    <button onclick="nextQuestion()">Próxima</button>
    <div id="score" class="hidden"></div>
  </div>

  <script>
    const questions = [
      { q: "CPD é o mesmo que TI.", a: false },
      { q: "TI inclui hardware, software e peopleware.", a: true },
      { q: "Sistemas legados são sempre atualizados e modernos.", a: false },
      { q: "A pirâmide do conhecimento termina em sabedoria.", a: true },
      { q: "Benchmarking é o processo de copiar sem analisar.", a: false },
      { q: "Gestão do conhecimento trata da criação e uso do saber organizacional.", a: true },
      { q: "KPI significa Indicador de Meta Chave.", a: false },
      { q: "KGI indica o quanto os objetivos estratégicos estão sendo atingidos.", a: true },
      { q: "Gestão à vista significa esconder informações da equipe.", a: false },
      { q: "Dashboard é um painel visual de indicadores.", a: true },
      { q: "First Call Resolution é um exemplo de indicador de desempenho.", a: true },
      { q: "Carreira em Y permite escolha entre especialista ou gestor.", a: true },
      { q: "Peopleware se refere aos softwares utilizados na empresa.", a: false },
      { q: "Ativo físico inclui servidores e cabos de rede.", a: true },
      { q: "Ativo lógico inclui hardware e infraestrutura.", a: false },
      { q: "Sistema de Informação inclui entrada, processamento e saída de dados.", a: true },
      { q: "Feedback é irrelevante em processos informacionais.", a: false },
      { q: "Gestão de mudanças lida com adaptação organizacional.", a: true },
      { q: "ERP é um sistema para relacionamento com clientes.", a: false },
      { q: "CRM é voltado à gestão de clientes.", a: true },
      { q: "SAD é um sistema que ajuda na tomada de decisões.", a: true },
      { q: "OLTP é voltado a análises gerenciais complexas.", a: false },
      { q: "SCADA monitora processos industriais.", a: true },
      { q: "PIMS coleta e analisa dados de processo.", a: true },
      { q: "MES gerencia ordens de produção em tempo real.", a: true },
      { q: "PLC e DCS são usados em automação industrial.", a: true },
      { q: "IoT conecta equipamentos físicos à internet.", a: true },
      { q: "OLAP serve para transações online rápidas.", a: false },
      { q: "Market Share indica participação de mercado de uma empresa.", a: true },
      { q: "TI não influencia na estratégia empresarial.", a: false },
      { q: "JIT visa reduzir estoques ao mínimo.", a: true },
      { q: "Indicadores não são importantes para a gestão.", a: false },
      { q: "ERP integra departamentos de uma empresa.", a: true },
      { q: "SIGE é um tipo de sistema corporativo integrado.", a: true },
      { q: "A pirâmide de prioridades da TI começa com suporte.", a: true },
      { q: "Dados sozinhos já são conhecimento.", a: false },
      { q: "Informação é dado com contexto.", a: true },
      { q: "Conhecimento é a aplicação útil da informação.", a: true },
      { q: "Empreendedorismo não tem relação com TI.", a: false },
      { q: "Construir sua carreira envolve planejamento.", a: true },
      { q: "TI surgiu com os smartphones.", a: false },
      { q: "Indicadores podem ser visuais em dashboards.", a: true },
      { q: "SCADA é um tipo de sistema de gestão financeira.", a: false },
      { q: "Sistemas legados podem ter integração difícil.", a: true },
      { q: "A evolução da TI inclui nuvem e inteligência artificial.", a: true },
      { q: "TI eficiente não precisa ser eficaz.", a: false },
      { q: "KPI mede resultado operacional.", a: true },
      { q: "OLTP registra transações em tempo real.", a: true },
      { q: "TI moderna ignora o peopleware.", a: false }
    ];

    let current = 0;
    let score = 0;

    const quizDiv = document.getElementById('quiz');
    const scoreDiv = document.getElementById('score');

    function showQuestion() {
      if (current >= questions.length) {
        quizDiv.innerHTML = "";
        scoreDiv.innerHTML = `Fim do quiz! Você acertou ${score} de ${questions.length}.`;
        scoreDiv.classList.remove('hidden');
        return;
      }

      const question = questions[current];
      quizDiv.innerHTML = `
        <div class="question">${current + 1}. ${question.q}</div>
        <div class="buttons">
          <button onclick="checkAnswer(true)">Verdadeiro</button>
          <button onclick="checkAnswer(false)">Falso</button>
        </div>
        <div id="result" class="result"></div>
      `;
    }

    function checkAnswer(answer) {
      const isCorrect = questions[current].a === answer;
      if (isCorrect) score++;
      document.getElementById('result').innerText = isCorrect ? 'Correto!' : 'Incorreto!';
    }

    function nextQuestion() {
      current++;
      showQuestion();
    }

    showQuestion();
  </script>
</body>
</html>
