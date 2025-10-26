# MandalaFlow
Anamnese de mandala 

<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sua Mandala Personalizada - Anamnese</title>
    <!-- Carrega Tailwind CSS para estilização moderna e responsiva -->
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap" rel="stylesheet">
    <style>
        /* Estilos personalizados */
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f7f3f8; /* Lilás bem claro de fundo */
        }
        .container-card {
            background-color: #ffffff;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
            border-radius: 1.5rem; /* Mais arredondado */
        }
        .input-style {
            border: 2px solid #ddd6fe; /* Lilás claro */
            transition: border-color 0.3s;
        }
        .input-style:focus {
            border-color: #a78bfa; /* Lilás vibrante */
            box-shadow: 0 0 0 3px rgba(167, 139, 250, 0.2);
        }
        .step-button {
            transition: background-color 0.3s, transform 0.1s;
        }
        .step-button:hover {
            transform: translateY(-1px);
        }
        /* Estilo para botões de seleção (opções) */
        .select-option {
            cursor: pointer;
            transition: all 0.2s;
        }
        .select-option.selected {
            background-color: #a78bfa; /* Cor primária: Lilás */
            color: white;
            border-color: #a78bfa;
            transform: scale(1.02);
            font-weight: 600;
        }
        .select-option:not(.selected):hover {
            background-color: #f3f4f6;
        }
        .result-box {
            background-color: #f3e8ff; /* Fundo lilás claro para o resultado */
            border-left: 5px solid #a78bfa;
        }
    </style>
</head>
<body class="min-h-screen flex items-center justify-center p-4">

    <div id="app-container" class="container-card w-full max-w-lg p-6 md:p-10">

        <h1 class="text-3xl font-bold text-center text-gray-800 mb-6">🔮 Sua Mandala de Propósito</h1>
        <p class="text-center text-gray-500 mb-8">Responda a esta breve anamnese para descobrir as cores e elementos que refletem sua energia atual.</p>
        
        <!-- Formulário da Anamnese -->
        <form id="anamnese-form" onsubmit="return false;">

            <!-- Etapa 1: Propósito Central -->
            <div id="step-1" class="step-content">
                <p class="text-lg font-semibold text-gray-700 mb-4">Etapa 1/3: Qual energia você deseja atrair ou fortalecer com sua mandala?</p>
                <div class="space-y-3">
                    <label class="select-option block p-4 border border-gray-300 rounded-xl" data-value="eq">
                        Equilíbrio, Cura e Estabilidade (Harmonia).
                    </label>
                    <label class="select-option block p-4 border border-gray-300 rounded-xl" data-value="anim">
                        Ânimo, Vitalidade, Coragem e Ação.
                    </label>
                    <label class="select-option block p-4 border border-gray-300 rounded-xl" data-value="paz">
                        Paz, Relaxamento, Calma Mental e Espiritualidade.
                    </label>
                    <label class="select-option block p-4 border border-gray-300 rounded-xl" data-value="pros">
                        Prosperidade, Sucesso e Abundância.
                    </label>
                    <label class="select-option block p-4 border border-gray-300 rounded-xl" data-value="amor">
                        Amor, Afeto, Relacionamentos e Autoestima.
                    </label>
                </div>
                <div class="mt-8 flex justify-end">
                    <button type="button" onclick="nextStep(1)" id="btn-step-1" class="step-button bg-indigo-500 text-white font-semibold py-3 px-6 rounded-full opacity-50 cursor-not-allowed" disabled>
                        Próximo →
                    </button>
                </div>
            </div>

            <!-- Etapa 2: Situação Atual -->
            <div id="step-2" class="step-content hidden">
                <p class="text-lg font-semibold text-gray-700 mb-4">Etapa 2/3: Como você se sente HOJE, majoritariamente, na sua rotina?</p>
                <p class="text-sm text-gray-500 mb-4"> (Escolha no máximo 2 opções, ou nenhuma se não se aplicar).</p>
                <div class="space-y-3">
                    <label class="select-option block p-4 border border-gray-300 rounded-xl" data-value="cansaco">
                        Cansado(a), desanimado(a), apático(a).
                    </label>
                    <label class="select-option block p-4 border border-gray-300 rounded-xl" data-value="ansiedade">
                        Ansioso(a), estressado(a), agitado(a).
                    </label>
                    <label class="select-option block p-4 border border-gray-300 rounded-xl" data-value="confusao">
                        Com a mente confusa, sem foco ou clareza.
                    </label>
                    <label class="select-option block p-4 border border-gray-300 rounded-xl" data-value="tristeza">
                        Triste, magoado(a), precisando de afeto.
                    </label>
                </div>
                <div class="mt-8 flex justify-between">
                    <button type="button" onclick="prevStep(2)" class="step-button text-gray-600 font-semibold py-3 px-6 rounded-full hover:bg-gray-100">
                        ← Voltar
                    </button>
                    <button type="button" onclick="nextStep(2)" class="step-button bg-indigo-500 text-white font-semibold py-3 px-6 rounded-full">
                        Próximo →
                    </button>
                </div>
            </div>

            <!-- Etapa 3: Conexão Pessoal e Contato -->
            <div id="step-3" class="step-content hidden">
                <p class="text-lg font-semibold text-gray-700 mb-6">Etapa 3/3: Seu Toque Pessoal e Contato</p>
                
                <div class="space-y-5">
                    <div>
                        <label for="signo" class="block text-sm font-medium text-gray-700 mb-1">Seu Signo Solar:</label>
                        <select id="signo" class="input-style w-full p-3 rounded-xl appearance-none" required>
                            <option value="">Selecione seu Signo</option>
                            <option value="Áries">Áries</option>
                            <option value="Touro">Touro</option>
                            <option value="Gêmeos">Gêmeos</option>
                            <option value="Câncer">Câncer</option>
                            <option value="Leão">Leão</option>
                            <option value="Virgem">Virgem</option>
                            <option value="Libra">Libra</option>
                            <option value="Escorpião">Escorpião</option>
                            <option value="Sagitário">Sagitário</option>
                            <option value="Capricórnio">Capricórnio</option>
                            <option value="Aquário">Aquário</option>
                            <option value="Peixes">Peixes</option>
                        </select>
                    </div>

                    <div>
                        <label for="cor_amada" class="block text-sm font-medium text-gray-700 mb-1">Qual cor você AMA incondicionalmente? (Ex: Roxo, Ouro):</label>
                        <input type="text" id="cor_amada" placeholder="Ex: Roxo" class="input-style w-full p-3 rounded-xl" required>
                    </div>

                    <div>
                        <label for="cor_odiada" class="block text-sm font-medium text-gray-700 mb-1">Existe alguma cor que você DETESTA?</label>
                        <input type="text" id="cor_odiada" placeholder="Ex: Preto (ou deixe vazio)" class="input-style w-full p-3 rounded-xl">
                    </div>
                </div>

                <div class="mt-8 flex justify-between">
                    <button type="button" onclick="prevStep(3)" class="step-button text-gray-600 font-semibold py-3 px-6 rounded-full hover:bg-gray-100">
                        ← Voltar
                    </button>
                    <button type="button" onclick="processAnamnese()" class="step-button bg-indigo-500 text-white font-semibold py-3 px-6 rounded-full">
                        Ver Meu Resultado!
                    </button>
                </div>
            </div>
            
        </form>

        <!-- Etapa 4: Resultado da Anamnese e Contato Final -->
        <div id="step-4" class="step-content hidden">
            <h2 class="text-2xl font-bold text-center text-indigo-600 mb-6">✨ O Resultado da Sua Mandala ✨</h2>
            
            <div id="result-display" class="result-box p-5 space-y-3 mb-6">
                <!-- O resultado da análise será injetado aqui pelo JS -->
            </div>

            <p class="text-center text-sm text-gray-600 mb-6">Para receber esta análise por e-mail e obter o orçamento para sua mandala, preencha seus dados abaixo:</p>

            <form id="contact-form" onsubmit="submitOrder(event)">
                <div class="space-y-4">
                    <div>
                        <label for="client_name" class="block text-sm font-medium text-gray-700 mb-1">Seu Nome:</label>
                        <input type="text" id="client_name" class="input-style w-full p-3 rounded-xl" required>
                    </div>
                    <div>
                        <label for="client_email" class="block text-sm font-medium text-gray-700 mb-1">Seu E-mail:</label>
                        <input type="email" id="client_email" class="input-style w-full p-3 rounded-xl" required>
                    </div>
                </div>
                <!-- Campo oculto para simular o corpo do email -->
                <textarea id="email-content" class="hidden"></textarea>

                <div class="mt-8">
                    <button type="submit" id="btn-submit" class="step-button w-full bg-pink-500 text-white font-bold py-4 rounded-full shadow-lg hover:bg-pink-600">
                        Quero Encomendar Minha Mandala Personalizada!
                    </button>
                </div>
            </form>

            <div id="loading-message" class="hidden mt-4 text-center text-gray-500">Enviando dados...</div>
            <div id="success-message" class="hidden mt-4 text-center text-green-600 font-semibold p-3 bg-green-100 rounded-lg">
                ✅ Recebemos seu pedido! A análise foi enviada para o seu e-mail. Entraremos em contato em breve para finalizar a encomenda.
            </div>
            <div id="error-message" class="hidden mt-4 text-center text-red-600 font-semibold p-3 bg-red-100 rounded-lg">
                ❌ Ocorreu um erro ao processar. Por favor, tente novamente ou anote o seu resultado.
            </div>
        </div>

    </div>

    <script>
        // Mapeamentos de dados (Português - Chave JS)
        const PROPOSITO_MAP = {
            'eq': { 
                cores: ['Verde (Cura)', 'Azul (Calma)', 'Branco (Paz)'], 
                elementos: ['Simetria', 'Ciclos', 'Raízes (Terra)', 'Ondas (Água)'] 
            },
            'anim': { 
                cores: ['Vermelho (Paixão)', 'Laranja (Entusiasmo)', 'Amarelo (Otimismo)'], 
                elementos: ['Triângulos', 'Raios de Sol', 'Expansão', 'Fogo'] 
            },
            'paz': { 
                cores: ['Azul (Tranquilidade)', 'Índigo (Intuição)', 'Violeta (Espiritualidade)'], 
                elementos: ['Ondas Suaves', 'Espiral', 'Proteção', 'Prata'] 
            },
            'pros': { 
                cores: ['Dourado (Riqueza)', 'Amarelo (Sucesso)', 'Laranja (Força)'], 
                elementos: ['Espiral de Crescimento', 'Símbolos de Abundância', 'Tons de Verde'] 
            },
            'amor': { 
                cores: ['Rosa (Afeto)', 'Verde-Claro (Cura Emocional)', 'Dourado'], 
                elementos: ['Corações', 'Flores', 'Formas Acolhedoras', 'Curvas'] 
            }
        };

        const SITUACAO_MAP = {
            'cansaco': { cor: 'Laranja', significado: 'Regeneração e Força' },
            'ansiedade': { cor: 'Azul-Claro', significado: 'Calma e Serenidade' },
            'confusao': { cor: 'Amarelo-Claro', significado: 'Clareza Mental e Foco' },
            'tristeza': { cor: 'Rosa', significado: 'Amor-próprio e Cura Emocional' }
        };

        const SIGNO_MAP = {
            'Ári': { cores: 'Vermelho, Ouro', elementos: 'Picos, Ação (Fogo)' },
            'Tou': { cores: 'Verde-Esmeralda, Marrom', elementos: 'Natureza, Estabilidade (Terra)' },
            'Gêm': { cores: 'Amarelo, Prata', elementos: 'Linhas Interligadas, Dualidade (Ar)' },
            'Cân': { cores: 'Prata, Azul-Água', elementos: 'Lunar, Proteção (Água)' },
            'Leã': { cores: 'Dourado, Laranja', elementos: 'Sol, Raios, Expansão (Fogo)' },
            'Vir': { cores: 'Verde-Oliva, Azul Marinho', elementos: 'Detalhes, Simetria (Terra)' },
            'Lib': { cores: 'Rosa, Azul-Celeste', elementos: 'Balança, Harmonia (Ar)' },
            'Esc': { cores: 'Índigo, Vinho', elementos: 'Transformação, Profundidade (Água)' },
            'Sag': { cores: 'Violeta, Turquesa', elementos: 'Seta, Expansão, Conhecimento (Fogo)' },
            'Cap': { cores: 'Preto, Marrom', elementos: 'Estrutura, Montanhas, Solidez (Terra)' },
            'Aqu': { cores: 'Azul Elétrico, Prata', elementos: 'Ondas, Inovação, Futurismo (Ar)' },
            'Pei': { cores: 'Lilás, Verde-Marinho', elementos: 'Fluidez, Onírico, Espiritual (Água)' }
        };

        let currentStep = 1;
        let anamneseData = {};
        
        // --- Funções de Navegação e Interatividade ---

        // Configura ouvintes de clique para todas as opções de seleção
        document.querySelectorAll('.select-option').forEach(option => {
            option.addEventListener('click', (e) => {
                const step = e.target.closest('.step-content').id;
                
                if (step === 'step-1') {
                    // Seleção única: remove de todos e aplica no clicado
                    document.querySelectorAll('#step-1 .select-option').forEach(opt => opt.classList.remove('selected'));
                    e.target.classList.add('selected');
                    // Habilita o botão
                    document.getElementById('btn-step-1').disabled = false;
                    document.getElementById('btn-step-1').classList.remove('opacity-50', 'cursor-not-allowed');

                } else if (step === 'step-2') {
                    // Seleção múltipla (máximo 2)
                    const selectedOptions = document.querySelectorAll('#step-2 .select-option.selected');
                    
                    if (e.target.classList.contains('selected')) {
                        // Desseleciona se já estiver selecionado
                        e.target.classList.remove('selected');
                    } else if (selectedOptions.length < 2) {
                        // Seleciona se houver menos de 2
                        e.target.classList.add('selected');
                    } else {
                        // Impede a seleção de um terceiro e informa
                        // Como não podemos usar alert(), vamos usar um console.log e ignorar a ação
                        console.log("Máximo de 2 opções permitidas para a Situação Atual.");
                    }
                }
            });
        });

        // Função para avançar para a próxima etapa
        function nextStep(step) {
            const currentDiv = document.getElementById(`step-${step}`);
            const nextDiv = document.getElementById(`step-${step + 1}`);

            if (step === 1) {
                if (!document.querySelector('#step-1 .select-option.selected')) return; // Garante que a opção foi selecionada
            }
            
            if (currentDiv && nextDiv) {
                currentDiv.classList.add('hidden');
                nextDiv.classList.remove('hidden');
                currentStep = step + 1;
            }
        }

        // Função para voltar à etapa anterior
        function prevStep(step) {
            const currentDiv = document.getElementById(`step-${step}`);
            const prevDiv = document.getElementById(`step-${step - 1}`);
            
            if (currentDiv && prevDiv) {
                currentDiv.classList.add('hidden');
                prevDiv.classList.remove('hidden');
                currentStep = step - 1;
            }
        }

        // --- Lógica de Processamento e Análise ---

        function processAnamnese() {
            // 1. Coleta de dados
            const propositoKey = document.querySelector('#step-1 .select-option.selected')?.dataset.value;
            const situacaoKeys = Array.from(document.querySelectorAll('#step-2 .select-option.selected')).map(el => el.dataset.value);
            const signo = document.getElementById('signo').value;
            const corAmada = document.getElementById('cor_amada').value.trim();
            const corOdiada = document.getElementById('cor_odiada').value.trim();

            if (!propositoKey || !signo || !corAmada) {
                console.error("Por favor, preencha todos os campos obrigatórios.");
                return;
            }

            // 2. Análise e geração do resultado
            const proposito = PROPOSITO_MAP[propositoKey];
            
            let coresPrincipais = [...proposito.cores];
            let elementos = [...proposito.elementos];
            let coresApoio = [];

            // Adiciona cores de apoio (Situação Atual)
            situacaoKeys.forEach(key => {
                const apoio = SITUACAO_MAP[key];
                coresApoio.push(`${apoio.cor} (${apoio.significado})`);
            });

            // Adiciona informações do Signo (Toque Pessoal)
            const signoKey = signo.substring(0, 3);
            const infoSigno = SIGNO_MAP[signoKey];

            const resultado = {
                propositoPrincipal: propositoKey,
                coresPrincipais: coresPrincipais,
                coresApoio: coresApoio,
                elementos: elementos,
                signo: signo,
                infoSigno: infoSigno,
                corAmada: corAmada,
                corOdiada: corOdiada,
            };

            anamneseData = resultado;

            // 3. Exibe o resultado e avança para a Etapa 4
            renderResult(resultado);
            
            document.getElementById('step-3').classList.add('hidden');
            document.getElementById('step-4').classList.remove('hidden');
            currentStep = 4;
        }

        function renderResult(data) {
            const display = document.getElementById('result-display');
            let html = `
                <div class="space-y-4">
                    <p class="font-bold text-gray-800">1. Intenção Principal:</p>
                    <ul class="list-disc list-inside ml-4 text-gray-700">
                        <li>**Cores Foco (Propósito):** ${data.coresPrincipais.join(', ')}.</li>
                        <li>**Elementos Sugeridos:** ${data.elementos.join(', ')}.</li>
                    </ul>

                    ${data.coresApoio.length > 0 ? `
                    <p class="font-bold text-gray-800">2. Cores de Apoio (Momento Atual):</p>
                    <ul class="list-disc list-inside ml-4 text-gray-700">
                        ${data.coresApoio.map(cor => `<li>${cor}</li>`).join('')}
                    </ul>` : `<p class="font-bold text-gray-800">2. Cores de Apoio:</p><p class="ml-4 text-gray-700">Nenhuma cor de apoio específica necessária no momento.</p>`}

                    <p class="font-bold text-gray-800">3. Toque Pessoal (Seu Signo - ${data.signo}):</p>
                    <ul class="list-disc list-inside ml-4 text-gray-700">
                        <li>**Cores de Personalidade:** ${data.infoSigno.cores}.</li>
                        <li>**Elementos/Formas de Personalidade:** ${data.infoSigno.elementos}.</li>
                    </ul>

                    <p class="font-bold text-gray-800">4. Preferências:</p>
                    <ul class="list-disc list-inside ml-4 text-gray-700">
                        <li>**Cor Amada (Para Conexão):** ${data.corAmada}.</li>
                        <li>**Cor a Ser Evitada:** ${data.corOdiada || 'Nenhuma informada.'}.</li>
                    </ul>

                    <p class="mt-4 text-sm italic text-indigo-700">**Resumo para a Criação:** A mandala deve ter as cores foco no centro/principais e incorporar os elementos do seu signo e a cor amada nos detalhes, **evitando o ${data.corOdiada || 'preto/cinza (cor neutra)'}**.</p>
                </div>
            `;
            display.innerHTML = html;

            // Prepara o conteúdo do "e-mail"
            const emailContent = `
                --- Análise de Mandala Personalizada ---

                Cliente: [Nome e Email a serem preenchidos]
                Signo: ${data.signo}
                Cor Amada: ${data.corAmada}
                Cor Odiada: ${data.corOdiada || 'Nenhuma'}

                1. Intenção Principal: ${Object.keys(PROPOSITO_MAP).find(k => PROPOSITO_MAP[k] === proposito)}
                - Cores Foco (Propósito): ${data.coresPrincipais.join(', ')}.
                - Elementos Sugeridos: ${data.elementos.join(', ')}.

                2. Cores de Apoio (Momento Atual): ${data.coresApoio.join('; ') || 'Nenhuma.'}

                3. Toque Pessoal (Signo):
                - Cores de Personalidade: ${data.infoSigno.cores}.
                - Elementos/Formas de Personalidade: ${data.infoSigno.elementos}.

                --- FIM DA ANÁLISE ---
            `;
            document.getElementById('email-content').value = emailContent;
        }

        // --- Simulação de Envio de Pedido/Email ---

        function submitOrder(event) {
            event.preventDefault(); // Impede o envio tradicional do formulário
            
            const name = document.getElementById('client_name').value.trim();
            const email = document.getElementById('client_email').value.trim();
            const content = document.getElementById('email-content').value;

            document.getElementById('btn-submit').disabled = true;
            document.getElementById('loading-message').classList.remove('hidden');
            document.getElementById('success-message').classList.add('hidden');
            document.getElementById('error-message').classList.add('hidden');

            // Simulação de envio de dados (Aqui você integraria com um serviço de e-mail real)
            setTimeout(() => {
                document.getElementById('loading-message').classList.add('hidden');

                if (name && email) {
                    console.log("--- SIMULAÇÃO DE ENVIO DE DADOS DE ANAMNESE ---");
                    console.log(`Nome: ${name}, Email: ${email}`);
                    console.log("Conteúdo do E-mail (Análise):");
                    console.log(content.replace('[Nome e Email a serem preenchidos]', `Nome: ${name}, Email: ${email}`));
                    console.log("-----------------------------------------------");

                    document.getElementById('success-message').classList.remove('hidden');
                    document.getElementById('btn-submit').classList.add('hidden');
                } else {
                    document.getElementById('error-message').classList.remove('hidden');
                    document.getElementById('btn-submit').disabled = false;
                }
            }, 1500); // Atraso de 1.5s para simular o processamento
        }
    </script>
</body>
</html>
