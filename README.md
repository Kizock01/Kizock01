# Guilherme Bastos Moreira

Estudo Inteligência Artificial em Brasília e quero trabalhar com AI e MLOps: pegar um modelo que funciona no notebook e fazê-lo rodar dentro de uma aplicação, com serviço de inferência, plano B para quando ele cair e medição do que ele entrega. Procuro estágio ou uma vaga de entrada na área.

Moro em Formosa (GO) e posso trabalhar em Brasília, remoto ou híbrido.

[Site do portfólio](https://kizock01.github.io/PortfolioHUB/) · [Repositório do portfólio](https://github.com/Kizock01/PortfolioHUB) · [LinkedIn](https://www.linkedin.com/in/guilherme-bastos-0a87382aa) · [E-mail](mailto:gbastosmoreira@gmail.com)

## Lume

Na Residência em IA (UnB e Instituto ELDORADO), meu grupo de seis pessoas criou o Lume, um app Android que lê o print de uma notícia, procura outras matérias sobre o mesmo fato e mostra, para cada fonte, o trecho que justifica a relação. Ele não diz se a notícia é verdadeira ou falsa.

- [Página do Lume](https://lume-previa.vercel.app/): protótipo 0.4.3, APK para Android e gravação do app funcionando
- [Código no GitHub](https://github.com/matheushpr94/challenge-fakenews-unb)
- [Seção do Lume no meu site (GitHub Pages)](https://kizock01.github.io/PortfolioHUB/#lume), com a divisão do que fiz e do que é do grupo
- [Repositório do site](https://github.com/Kizock01/PortfolioHUB)

Sou quem mais fez commits no repositório (20). Escrevi o app Android com OCR, a comparação de fontes, o sinal do texto e a ligação dos modelos ao app, além do gateway que deixa o celular usar esses modelos sem cabo. O modelo que decide se duas notícias tratam do mesmo fato, o "modelo 6B" do banner, é do Matheus Henrique Picone Rosa; eu o integrei ao aplicativo. Os créditos de cada pessoa estão na [documentação da equipe](https://github.com/matheushpr94/challenge-fakenews-unb/blob/main/docs/scrum_e_equipe.md).

### Ferramentas de IA usadas

| Ferramenta | Papel no Lume |
| --- | --- |
| Google ML Kit | OCR no próprio aparelho, para ler o print sem enviar a imagem |
| BERTimbau ajustado (PyTorch, Transformers) | Lê a afirmação e o título de uma fonte juntos e dá uma nota de 0 a 1 para "mesmo fato" |
| MPNet ajustado e paraphrase-multilingual, via Ollama | Embeddings para medir semelhança de sentido e ordenar as fontes |
| TF-IDF + SVM (scikit-learn), treinado no FakeRecogna | Estimar o estilo da escrita, sem dar veredito |
| spaCy (pt_core_news_sm) | Lematização no servidor do sinal do texto |

### Como os modelos chegam ao app

Os modelos não rodam dentro do celular. Ficam em servidores Python e no Ollama, e o app os chama por HTTP. O que eu montei em volta disso:

- um script que liga o Ollama e os dois servidores Python e confere a rota de saúde de cada um;
- um gateway com chave de acesso no cabeçalho, que repassa as chamadas e não grava o texto recebido;
- a exportação do SVM para JSON e uma versão sem scikit-learn, com teste de paridade (diferença máxima de cerca de 1e-7 contra o pipeline original);
- o plano B: sem os modelos, o app continua só com as regras, e a tela avisa quando o modelo participou da decisão;
- endereços e chaves em arquivo local fora do Git, e pesos de modelo fora do repositório.

A equipe mediu o modelo "mesmo fato" em uma prova lacrada de 100 notícias e 4.298 pares, aberta uma vez: ele achou 7,58 de cada 10 fontes do mesmo fato, com precisão de 74,3%. A regra do app, sozinha, achou 3,57. O app foi validado em emulador; teste em aparelho físico ainda está pendente.

## Outros projetos

- [TranscribeAI](https://github.com/Kizock01/PortfolioHUB/tree/main/projetos-pessoais/app-transcricao): transcreve áudio em texto com faster-whisper, backend em FastAPI e interface em Next.js, com Dockerfiles. Projeto pessoal.
- [StudyQuest](https://github.com/Kizock01/PortfolioHUB/tree/main/projetos-pessoais/StudyQuest/studyquest): app de prática de estudos com quizzes e missões, em Next.js, TypeScript e Supabase. Projeto pessoal em desenvolvimento.

Os dois estão no repositório do [PortfolioHUB](https://github.com/Kizock01/PortfolioHUB).

## O que uso

- IA e ML: PyTorch, Transformers, scikit-learn, spaCy, Ollama, faster-whisper
- Estudo de IA generativa e RAG: LangChain, ChromaDB, Gemini API
- Dados: Python, pandas, SQL
- Desenvolvimento: Python, FastAPI, Kotlin, TypeScript
- Ferramentas: Git, GitHub, Docker

Isso vem de projetos pessoais, acadêmicos e em equipe. Ainda não tenho experiência profissional na área.

## Formação

- Residência em Inteligência Artificial, Instituto ELDORADO e UnB, Campus Gama (em andamento)
- Bacharelado em Inteligência Artificial, CEUB (em andamento)
- Técnico em Inteligência Artificial, IFNMG, EAD (em andamento)
- Ensino médio técnico em Biotecnologia, IFG Formosa

Inglês avançado.
