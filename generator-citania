import React, { useState } from 'react';
import { X, FileText, Download, Plus } from 'lucide-react';

export default function GeneratorCitania() {
  const [selectedLanguage, setSelectedLanguage] = useState('custom');
  const [customLanguage, setCustomLanguage] = useState('');
  const [textLength, setTextLength] = useState('');
  const [cefrLevel, setCefrLevel] = useState('');
  const [topic, setTopic] = useState('');
  const [vocabularyInput, setVocabularyInput] = useState('');
  const [vocabularyTags, setVocabularyTags] = useState([]);
  const [includeExercises, setIncludeExercises] = useState(false);
  const [exercises, setExercises] = useState({
    matching: false,
    fillBlanks: false,
    multipleChoice: false,
    openQuestions: false,
    discussion: false
  });

  const handleVocabularyKeyPress = (e) => {
    if (e.key === 'Enter' || e.key === ',') {
      e.preventDefault();
      const value = vocabularyInput.trim();
      if (value && !vocabularyTags.includes(value)) {
        setVocabularyTags([...vocabularyTags, value]);
        setVocabularyInput('');
      }
    }
  };

  const removeTag = (tagToRemove) => {
    setVocabularyTags(vocabularyTags.filter(tag => tag !== tagToRemove));
  };

  const toggleExercise = (type) => {
    setExercises({ ...exercises, [type]: !exercises[type] });
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-indigo-50 via-purple-50 to-pink-50 py-8 px-4">
      <div className="max-w-4xl mx-auto">
        <div className="bg-white rounded-2xl shadow-2xl overflow-hidden">
          {/* Header */}
          <div className="bg-gradient-to-r from-indigo-600 via-purple-600 to-pink-600 px-8 py-10">
            <div className="flex items-center justify-center gap-3 mb-3">
              <FileText className="w-10 h-10 text-white" />
              <h1 className="text-4xl font-bold text-white">Generátor Čítania s Porozumením</h1>
            </div>
            <p className="text-center text-indigo-100 text-lg">
              Vytvorte si text na mieru podľa vašich potrieb
            </p>
          </div>

          <div className="px-8 py-10">
            {/* Language Selection */}
            <div className="mb-8">
              <label className="block text-lg font-semibold text-gray-800 mb-4">
                Vyberte jazyk
              </label>
              <div className="grid grid-cols-4 gap-3">
                <button
                  onClick={() => setSelectedLanguage('english')}
                  className={`px-4 py-3 rounded-xl font-medium transition-all duration-200 ${
                    selectedLanguage === 'english'
                      ? 'bg-indigo-600 text-white shadow-lg scale-105'
                      : 'bg-gray-100 text-gray-700 hover:bg-gray-200'
                  }`}
                >
                  🇬🇧 Angličtina
                </button>
                <button
                  onClick={() => setSelectedLanguage('german')}
                  className={`px-4 py-3 rounded-xl font-medium transition-all duration-200 ${
                    selectedLanguage === 'german'
                      ? 'bg-indigo-600 text-white shadow-lg scale-105'
                      : 'bg-gray-100 text-gray-700 hover:bg-gray-200'
                  }`}
                >
                  🇩🇪 Nemčina
                </button>
                <button
                  onClick={() => setSelectedLanguage('french')}
                  className={`px-4 py-3 rounded-xl font-medium transition-all duration-200 ${
                    selectedLanguage === 'french'
                      ? 'bg-indigo-600 text-white shadow-lg scale-105'
                      : 'bg-gray-100 text-gray-700 hover:bg-gray-200'
                  }`}
                >
                  🇫🇷 Francúzština
                </button>
                <button
                  onClick={() => setSelectedLanguage('custom')}
                  className={`px-4 py-3 rounded-xl font-medium transition-all duration-200 ${
                    selectedLanguage === 'custom'
                      ? 'bg-indigo-600 text-white shadow-lg scale-105'
                      : 'bg-gray-100 text-gray-700 hover:bg-gray-200'
                  }`}
                >
                  🌍 Vlastný jazyk
                </button>
              </div>

              {selectedLanguage === 'custom' && (
                <div className="mt-4">
                  <input
                    type="text"
                    placeholder="napr. Španielčina"
                    value={customLanguage}
                    onChange={(e) => setCustomLanguage(e.target.value)}
                    className="w-full px-4 py-3 rounded-xl border-2 border-gray-200 focus:border-indigo-500 focus:outline-none transition-colors"
                  />
                </div>
              )}
            </div>

            {/* Text Length */}
            <div className="mb-8">
              <label className="block text-lg font-semibold text-gray-800 mb-4">
                Dĺžka textu
              </label>
              <div className="grid grid-cols-3 gap-3">
                {['Krátky', 'Stredný', 'Dlhý'].map((length) => (
                  <button
                    key={length}
                    onClick={() => setTextLength(length)}
                    className={`px-6 py-3 rounded-xl font-medium transition-all duration-200 ${
                      textLength === length
                        ? 'bg-purple-600 text-white shadow-lg scale-105'
                        : 'bg-gray-100 text-gray-700 hover:bg-gray-200'
                    }`}
                  >
                    {length}
                  </button>
                ))}
              </div>
            </div>

            {/* CEFR Level */}
            <div className="mb-8">
              <label className="block text-lg font-semibold text-gray-800 mb-4">
                CEFR úroveň
              </label>
              <div className="grid grid-cols-5 gap-3">
                {['A1', 'A2', 'B1', 'B2', 'C1'].map((level) => (
                  <button
                    key={level}
                    onClick={() => setCefrLevel(level)}
                    className={`px-6 py-3 rounded-xl font-bold text-lg transition-all duration-200 ${
                      cefrLevel === level
                        ? 'bg-pink-600 text-white shadow-lg scale-105'
                        : 'bg-gray-100 text-gray-700 hover:bg-gray-200'
                    }`}
                  >
                    {level}
                  </button>
                ))}
              </div>
            </div>

            {/* Topic */}
            <div className="mb-8">
              <label className="block text-lg font-semibold text-gray-800 mb-4">
                Téma
              </label>
              <select
                value={topic}
                onChange={(e) => setTopic(e.target.value)}
                className="w-full px-4 py-3 rounded-xl border-2 border-gray-200 focus:border-indigo-500 focus:outline-none transition-colors bg-white text-gray-700"
              >
                <option value="">Vyberte tému</option>
                <option value="cestovanie">Cestovanie</option>
                <option value="technologie">Technológie</option>
                <option value="zdravie">Zdravie</option>
                <option value="umenie">Umenie a kultúra</option>
                <option value="sport">Šport</option>
                <option value="príroda">Príroda a životné prostredie</option>
                <option value="história">História</option>
                <option value="jedlo">Jedlo a kuchyňa</option>
                <option value="vzdelávanie">Vzdelávanie</option>
                <option value="biznis">Biznis a ekonomika</option>
              </select>
            </div>

            {/* Target Vocabulary */}
            <div className="mb-8">
              <label className="block text-lg font-semibold text-gray-800 mb-4">
                Cieľová slovná zásoba <span className="text-gray-500 font-normal text-sm">(voliteľné)</span>
              </label>
              <div className="border-2 border-gray-200 rounded-xl p-3 focus-within:border-indigo-500 transition-colors">
                <div className="flex flex-wrap gap-2 mb-2">
                  {vocabularyTags.map((tag, index) => (
                    <span
                      key={index}
                      className="inline-flex items-center gap-2 px-3 py-1 bg-indigo-500 text-white rounded-lg font-medium"
                    >
                      {tag}
                      <button
                        onClick={() => removeTag(tag)}
                        className="hover:bg-indigo-600 rounded-full p-0.5 transition-colors"
                      >
                        <X className="w-4 h-4" />
                      </button>
                    </span>
                  ))}
                </div>
                <input
                  type="text"
                  placeholder="Zadajte slovíčka oddelené čiarkou..."
                  value={vocabularyInput}
                  onChange={(e) => setVocabularyInput(e.target.value)}
                  onKeyPress={handleVocabularyKeyPress}
                  className="w-full outline-none text-gray-700"
                />
              </div>
              <p className="text-sm text-gray-500 mt-2">
                Stlačte Enter alebo čiarku pre pridanie slovíčka ako štítok
              </p>
            </div>

            {/* Include Exercises Toggle */}
            <div className="mb-6">
              <div className="flex items-center justify-between bg-gradient-to-r from-indigo-50 to-purple-50 p-5 rounded-xl">
                <label className="text-lg font-semibold text-gray-800">
                  Zahrnúť cvičenia
                </label>
                <button
                  onClick={() => setIncludeExercises(!includeExercises)}
                  className={`relative w-16 h-8 rounded-full transition-all duration-300 ${
                    includeExercises ? 'bg-indigo-600' : 'bg-gray-300'
                  }`}
                >
                  <span
                    className={`absolute top-1 left-1 w-6 h-6 bg-white rounded-full transition-transform duration-300 ${
                      includeExercises ? 'translate-x-8' : ''
                    }`}
                  />
                </button>
              </div>
            </div>

            {/* Exercise Types */}
            {includeExercises && (
              <div className="mb-8 bg-gradient-to-br from-purple-50 to-pink-50 p-6 rounded-xl border-2 border-purple-100">
                <h3 className="text-lg font-semibold text-gray-800 mb-4">
                  Typy cvičení
                </h3>
                <div className="space-y-3">
                  {[
                    { key: 'matching', label: 'Spájačky' },
                    { key: 'fillBlanks', label: 'Doplňovačky' },
                    { key: 'multipleChoice', label: 'Výber z možností' },
                    { key: 'openQuestions', label: 'Otvorené otázky' },
                    { key: 'discussion', label: 'Otázky do diskusie' }
                  ].map((exercise) => (
                    <label
                      key={exercise.key}
                      className="flex items-center gap-3 cursor-pointer group"
                    >
                      <div className="relative">
                        <input
                          type="checkbox"
                          checked={exercises[exercise.key]}
                          onChange={() => toggleExercise(exercise.key)}
                          className="sr-only"
                        />
                        <div
                          className={`w-6 h-6 rounded-lg border-2 transition-all duration-200 flex items-center justify-center ${
                            exercises[exercise.key]
                              ? 'bg-indigo-600 border-indigo-600 scale-110'
                              : 'border-gray-300 group-hover:border-indigo-400'
                          }`}
                        >
                          {exercises[exercise.key] && (
                            <svg
                              className="w-4 h-4 text-white"
                              fill="none"
                              strokeLinecap="round"
                              strokeLinejoin="round"
                              strokeWidth="3"
                              viewBox="0 0 24 24"
                              stroke="currentColor"
                            >
                              <path d="M5 13l4 4L19 7" />
                            </svg>
                          )}
                        </div>
                      </div>
                      <span className="text-gray-700 font-medium group-hover:text-indigo-600 transition-colors">
                        {exercise.label}
                      </span>
                    </label>
                  ))}
                </div>
              </div>
            )}

            {/* Generate Button */}
            <button className="w-full bg-gradient-to-r from-indigo-600 via-purple-600 to-pink-600 text-white py-4 rounded-xl font-bold text-lg shadow-lg hover:shadow-xl transform hover:scale-105 transition-all duration-200 mb-6">
              Vygenerovať pracovný list
            </button>

            {/* Download Buttons */}
            <div className="grid grid-cols-2 gap-4">
              <button className="flex items-center justify-center gap-2 bg-red-500 text-white py-3 rounded-xl font-semibold shadow-md hover:bg-red-600 hover:shadow-lg transition-all duration-200">
                <Download className="w-5 h-5" />
                Stiahnuť PDF
              </button>
              <button className="flex items-center justify-center gap-2 bg-blue-500 text-white py-3 rounded-xl font-semibold shadow-md hover:bg-blue-600 hover:shadow-lg transition-all duration-200">
                <Download className="w-5 h-5" />
                Stiahnuť DOCX
              </button>
            </div>
          </div>
        </div>

        {/* Footer */}
        <div className="text-center mt-8 text-gray-600">
          <p className="text-sm">
            Profesionálny nástroj na tvorbu vzdelávacích materiálov
          </p>
        </div>
      </div>
    </div>
  );
}
