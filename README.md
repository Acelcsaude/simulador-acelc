import React, { useState } from 'react';
import './App.css';

const planos = [
  { operadora: "Hapvida", plano: "AHO", faixa: "00 a 18 anos", valor: 182.23 },
  { operadora: "Hapvida", plano: "AHO", faixa: "19 a 23 anos", valor: 204.09 },
  { operadora: "Plamedh", plano: "SELECT", faixa: "19 a 23 anos", valor: 244.18 },
];

function App() {
  const [simulacao, setSimulacao] = useState([
    { faixa: "00 a 18 anos", qtde: 0 },
    { faixa: "19 a 23 anos", qtde: 0 },
  ]);
  const [mensagem, setMensagem] = useState("");

  const calcular = () => {
    let total = 0;
    const detalhes = simulacao.map((item) => {
      const plano = planos.find((p) => p.faixa === item.faixa);
      const subtotal = item.qtde * (plano?.valor || 0);
      total += subtotal;
      return `Faixa ${item.faixa} - ${item.qtde} vidas x R$ ${plano?.valor?.toFixed(2)} = R$ ${subtotal.toFixed(2)}`;
    });
    const mensagemGerada = `Plano Hapvida AHO\n${detalhes.join("\n")}\n\nTotal: R$ ${total.toFixed(2)}`;
    setMensagem(mensagemGerada);
  };

  const limpar = () => {
    setSimulacao(simulacao.map((s) => ({ ...s, qtde: 0 })));
    setMensagem("");
  };

  return (
    <div className="App">
      <h1>Simulador Acelc</h1>
      {simulacao.map((item, i) => (
        <div key={item.faixa}>
          <label>{item.faixa}</label>
          <input
            type="number"
            value={item.qtde}
            onChange={(e) => {
              const newSim = [...simulacao];
              newSim[i].qtde = parseInt(e.target.value || "0");
              setSimulacao(newSim);
            }}
          />
        </div>
      ))}
      <button onClick={calcular}>Gerar Simulação</button>
      <button onClick={limpar}>Limpar</button>
      {mensagem && <pre>{mensagem}</pre>}
    </div>
  );
}

export default App;
import React, { useState } from 'react';
import './App.css';

const planos = [
  { operadora: "Hapvida", plano: "AHO", faixa: "00 a 18 anos", valor: 182.23 },
  { operadora: "Hapvida", plano: "AHO", faixa: "19 a 23 anos", valor: 204.09 },
  { operadora: "Plamedh", plano: "SELECT", faixa: "19 a 23 anos", valor: 244.18 },
];

function App() {
  const [simulacao, setSimulacao] = useState([
    { faixa: "00 a 18 anos", qtde: 0 },
    { faixa: "19 a 23 anos", qtde: 0 },
  ]);
  const [mensagem, setMensagem] = useState("");

  const calcular = () => {
    let total = 0;
    const detalhes = simulacao.map((item) => {
      const plano = planos.find((p) => p.faixa === item.faixa);
      const subtotal = item.qtde * (plano?.valor || 0);
      total += subtotal;
      return `Faixa ${item.faixa} - ${item.qtde} vidas x R$ ${plano?.valor?.toFixed(2)} = R$ ${subtotal.toFixed(2)}`;
    });
    const mensagemGerada = `Plano Hapvida AHO\n${detalhes.join("\n")}\n\nTotal: R$ ${total.toFixed(2)}`;
    setMensagem(mensagemGerada);
  };

  const limpar = () => {
    setSimulacao(simulacao.map((s) => ({ ...s, qtde: 0 })));
    setMensagem("");
  };

  return (
    <div className="App">
      <h1>Simulador Acelc</h1>
      {simulacao.map((item, i) => (
        <div key={item.faixa}>
          <label>{item.faixa}</label>
          <input
            type="number"
            value={item.qtde}
            onChange={(e) => {
              const newSim = [...simulacao];
              newSim[i].qtde = parseInt(e.target.value || "0");
              setSimulacao(newSim);
            }}
          />
        </div>
      ))}
      <button onClick={calcular}>Gerar Simulação</button>
      <button onClick={limpar}>Limpar</button>
      {mensagem && <pre>{mensagem}</pre>}
    </div>
  );
}

export default App;
