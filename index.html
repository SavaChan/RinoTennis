import React, { useState, useEffect } from 'react';
import { Trophy, RefreshCw, MessageCircle, AlertCircle, BarChart3, Calendar, Award, TrendingUp } from 'lucide-react';

const RinoTennis = () => {
  const [currentQuestion, setCurrentQuestion] = useState(null);
  const [selectedAnswer, setSelectedAnswer] = useState(null);
  const [showResult, setShowResult] = useState(false);
  const [userQuestion, setUserQuestion] = useState('');
  const [chatHistory, setChatHistory] = useState([]);
  const [loading, setLoading] = useState(false);
  const [errorLog, setErrorLog] = useState([]);
  const [showErrorConsole, setShowErrorConsole] = useState(false);
  const [dailyQuestionAnswered, setDailyQuestionAnswered] = useState(false);

  const logError = (error, context) => {
    const errorEntry = {
      timestamp: new Date().toLocaleString('it-IT'),
      context: context,
      message: error.message || error,
      stack: error.stack || 'N/A'
    };
    setErrorLog(prev => [errorEntry, ...prev.slice(0, 49)]);
    console.error('RinoTennis Error:', errorEntry);
  };

  const generateQuestion = async (isDaily = false) => {
    try {
      setLoading(true);
      const questionType = isDaily ? 'domanda giornaliera' : 'nuova domanda';
      
      const prompt = `Sei un esperto di tennis dell'era Open (dal 1968 ad oggi). Crea una ${questionType} interessante sul tennis professionistico con:

1. Una domanda coinvolgente su statistiche, record, aneddoti o curiosità
2. 4 opzioni di risposta (A, B, C, D)
3. La risposta corretta
4. Una spiegazione dettagliata con statistiche specifiche
5. Un dato interessante o aneddoto correlato

Rispondi SOLO con un oggetto JSON valido in questo formato:
{
  "question": "Testo della domanda qui",
  "options": {
    "A": "Prima opzione",
    "B": "Seconda opzione", 
    "C": "Terza opzione",
    "D": "Quarta opzione"
  },
  "correctAnswer": "A",
  "explanation": "Spiegazione dettagliata con statistiche",
  "funFact": "Aneddoto o curiosità interessante",
  "stats": {
    "mainStat": "Statistica principale",
    "value": "Valore numerico",
    "context": "Contesto della statistica"
  }
}

NON includere backticks o altro testo oltre al JSON.`;

      const response = await window.claude.complete(prompt);
      const questionData = JSON.parse(response);
      
      setCurrentQuestion(questionData);
      setSelectedAnswer(null);
      setShowResult(false);
      
      if (isDaily) {
        setDailyQuestionAnswered(false);
      }
      
    } catch (error) {
      logError(error, 'generateQuestion');
      setCurrentQuestion({
        question: "Chi ha vinto più tornei del Grande Slam nella storia del tennis maschile?",
        options: {
          A: "Roger Federer",
          B: "Rafael Nadal", 
          C: "Novak Djokovic",
          D: "Pete Sampras"
        },
        correctAnswer: "C",
        explanation: "Novak Djokovic detiene il record con 24 titoli del Grande Slam nel tennis maschile.",
        funFact: "Djokovic ha completato il Career Golden Masters per 3 volte!",
        stats: {
          mainStat: "Titoli Grande Slam",
          value: "24",
          context: "Record maschile"
        }
      });
    } finally {
      setLoading(false);
    }
  };

  const handleAnswerSelect = (answer) => {
    if (showResult) return;
    setSelectedAnswer(answer);
    setShowResult(true);
    setDailyQuestionAnswered(true);
  };

  const handleUserQuestion = async () => {
    if (!userQuestion.trim()) return;
    
    try {
      setLoading(true);
      const userMsg = { role: 'user', content: userQuestion };
      const updatedHistory = [...chatHistory, userMsg];
      
      const prompt = `Sei un esperto di tennis dell'era Open. L'utente ha fatto questa domanda: "${userQuestion}"

Storia conversazione precedente:
${JSON.stringify(chatHistory)}

Fornisci una risposta dettagliata e accurata con statistiche quando possibile.

Rispondi con un oggetto JSON:
{
  "response": "La tua risposta completa qui",
  "hasStats": true,
  "stats": {
    "title": "Titolo statistica",
    "data": "Dati statistici se disponibili"
  }
}

Rispondi SOLO con JSON valido, senza backticks.`;

      const response = await window.claude.complete(prompt);
      const aiResponse = JSON.parse(response);
      
      const aiMsg = { role: 'assistant', content: aiResponse.response, stats: aiResponse.stats };
      setChatHistory([...updatedHistory, aiMsg]);
      setUserQuestion('');
      
    } catch (error) {
      logError(error, 'handleUserQuestion');
      const errorMsg = { role: 'assistant', content: 'Scusa, ho avuto un problema nel rispondere. Riprova!' };
      setChatHistory(prev => [...prev, { role: 'user', content: userQuestion }, errorMsg]);
      setUserQuestion('');
    } finally {
      setLoading(false);
    }
  };

  useEffect(() => {
    generateQuestion(true);
  }, []);

  return (
    <div className="min-h-screen bg-gradient-to-br from-green-50 via-white to-green-100">
      <div className="bg-gradient-to-r from-green-600 to-green-700 text-white p-4 shadow-lg">
        <div className="flex items-center justify-between max-w-md mx-auto">
          <div className="flex items-center gap-3">
            <div className="relative">
              <Trophy className="w-8 h-8 text-yellow-300" />
              <div className="absolute -top-1 -right-1 w-3 h-3 bg-yellow-400 rounded-full animate-pulse"></div>
            </div>
            <div>
              <h1 className="text-xl font-bold">RinoTennis</h1>
              <p className="text-green-100 text-xs">Tennis Quiz & Stats</p>
            </div>
          </div>
          <div className="flex gap-2">
            <Calendar className="w-5 h-5 text-green-200" />
            <button 
              onClick={() => setShowErrorConsole(!showErrorConsole)}
              className="text-green-200 hover:text-white"
            >
              <AlertCircle className="w-5 h-5" />
            </button>
          </div>
        </div>
      </div>

      <div className="max-w-md mx-auto p-4 space-y-6">
        
        {showErrorConsole && (
          <div className="bg-red-50 border border-red-200 rounded-lg p-3">
            <div className="flex justify-between items-center mb-2">
              <h3 className="font-semibold text-red-800">Console Errori</h3>
              <button 
                onClick={() => setErrorLog([])}
                className="text-red-600 text-sm hover:text-red-800"
              >
                Pulisci
              </button>
            </div>
            <div className="max-h-40 overflow-y-auto space-y-1">
              {errorLog.length === 0 ? (
                <p className="text-green-600 text-sm">Nessun errore registrato ✓</p>
              ) : (
                errorLog.map((error, idx) => (
                  <div key={idx} className="text-xs bg-red-100 p-2 rounded border-l-2 border-red-400">
                    <div className="font-mono text-red-800">[{error.timestamp}] {error.context}</div>
                    <div className="text-red-600">{error.message}</div>
                  </div>
                ))
              )}
            </div>
          </div>
        )}

        <div className="bg-white rounded-xl shadow-lg border-l-4 border-green-500 overflow-hidden">
          <div className="bg-gradient-to-r from-green-500 to-green-600 text-white p-4">
            <div className="flex items-center gap-2">
              <Award className="w-5 h-5" />
              <span className="font-semibold">Domanda del Giorno</span>
              {dailyQuestionAnswered && <span className="text-green-200 text-sm">✓ Completata</span>}
            </div>
          </div>
          
          {loading && !currentQuestion ? (
            <div className="p-6 text-center">
              <div className="animate-spin rounded-full h-8 w-8 border-b-2 border-green-500 mx-auto"></div>
              <p className="mt-2 text-gray-600">Generando domanda...</p>
            </div>
          ) : currentQuestion ? (
            <div className="p-4">
              <h3 className="font-semibold text-gray-800 mb-4">{currentQuestion.question}</h3>
              
              <div className="space-y-2 mb-4">
                {Object.entries(currentQuestion.options).map(([key, value]) => (
                  <button
                    key={key}
                    onClick={() => handleAnswerSelect(key)}
                    disabled={showResult}
                    className={`w-full text-left p-3 rounded-lg border transition-all ${
                      selectedAnswer === key
                        ? key === currentQuestion.correctAnswer
                          ? 'bg-green-100 border-green-500 text-green-800'
                          : 'bg-red-100 border-red-500 text-red-800'
                        : showResult && key === currentQuestion.correctAnswer
                        ? 'bg-green-100 border-green-500 text-green-800'
                        : 'bg-gray-50 border-gray-200 hover:bg-gray-100'
                    }`}
                  >
                    <span className="font-semibold">{key})</span> {value}
                  </button>
                ))}
              </div>

              {showResult && (
                <div className="space-y-4 pt-4 border-t">
                  <div className="bg-blue-50 p-4 rounded-lg">
                    <h4 className="font-semibold text-blue-800 mb-2">Spiegazione</h4>
                    <p className="text-blue-700 text-sm">{currentQuestion.explanation}</p>
                  </div>

                  {currentQuestion.stats && (
                    <div className="bg-purple-50 p-4 rounded-lg">
                      <div className="flex items-center gap-2 mb-2">
                        <BarChart3 className="w-4 h-4 text-purple-600" />
                        <h4 className="font-semibold text-purple-800">Statistiche</h4>
                      </div>
                      <div className="grid grid-cols-2 gap-2 text-sm">
                        <div>
                          <span className="text-purple-600">{currentQuestion.stats.mainStat}:</span>
                          <span className="font-bold text-purple-800 ml-1">{currentQuestion.stats.value}</span>
                        </div>
                        <div className="text-purple-700">{currentQuestion.stats.context}</div>
                      </div>
                    </div>
                  )}

                  <div className="bg-yellow-50 p-4 rounded-lg">
                    <div className="flex items-center gap-2 mb-2">
                      <TrendingUp className="w-4 h-4 text-yellow-600" />
                      <h4 className="font-semibold text-yellow-800">Lo Sapevi Che...</h4>
                    </div>
                    <p className="text-yellow-700 text-sm">{currentQuestion.funFact}</p>
                  </div>
                </div>
              )}
            </div>
          ) : null}
        </div>

        <button
          onClick={() => generateQuestion(false)}
          disabled={loading}
          className="w-full bg-green-600 hover:bg-green-700 text-white p-4 rounded-xl font-semibold flex items-center justify-center gap-2 transition-colors disabled:opacity-50"
        >
          <RefreshCw className={`w-5 h-5 ${loading ? 'animate-spin' : ''}`} />
          {loading ? 'Generando...' : 'Nuova Domanda'}
        </button>

        <div className="bg-white rounded-xl shadow-lg overflow-hidden">
          <div className="bg-gradient-to-r from-blue-500 to-blue-600 text-white p-4">
            <div className="flex items-center gap-2">
              <MessageCircle className="w-5 h-5" />
              <span className="font-semibold">Fai una Domanda</span>
            </div>
          </div>
          
          <div className="p-4">
            <div className="flex gap-2 mb-4">
              <input
                type="text"
                value={userQuestion}
                onChange={(e) => setUserQuestion(e.target.value)}
                placeholder="Chiedi qualcosa sul tennis..."
                className="flex-1 p-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
                onKeyPress={(e) => e.key === 'Enter' && handleUserQuestion()}
              />
              <button
                onClick={handleUserQuestion}
                disabled={loading || !userQuestion.trim()}
                className="bg-blue-600 hover:bg-blue-700 text-white px-4 py-3 rounded-lg disabled:opacity-50 transition-colors"
              >
                Invia
              </button>
            </div>

            <div className="space-y-3 max-h-64 overflow-y-auto">
              {chatHistory.map((msg, idx) => (
                <div key={idx} className={msg.role === 'user' ? 'text-right' : 'text-left'}>
                  <div className={`inline-block p-3 rounded-lg max-w-[80%] ${
                    msg.role === 'user' 
                      ? 'bg-blue-100 text-blue-800' 
                      : 'bg-gray-100 text-gray-800'
                  }`}>
                    <p className="text-sm">{msg.content}</p>
                    {msg.stats && msg.stats.title && (
                      <div className="mt-2 p-2 bg-white rounded border-l-2 border-blue-400">
                        <div className="text-xs font-semibold text-blue-700">{msg.stats.title}</div>
                        <div className="text-xs text-blue-600">{msg.stats.data}</div>
                      </div>
                    )}
                  </div>
                </div>
              ))}
            </div>
          </div>
        </div>

        <div className="text-center py-4">
          <p className="text-xs text-gray-400 opacity-50">by Cesco</p>
        </div>
      </div>
    </div>
  );
};

export default RinoTennis;
