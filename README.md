# Teachable-Machine
# Gesture Control — Teachable Machine + TensorFlow.js

Projeto acadêmico de Machine Learning aplicado. Um modelo treinado no **Teachable Machine** reconhece gestos pela webcam e, a partir da predição, controla automaticamente o estado de um player na página.

## Objetivo

Demonstrar o ciclo:

**treinar → exportar → integrar → prever em tempo real → executar uma ação → publicar**

A ação avaliada não depende de um clique manual: quando o modelo reconhece uma classe com confiança mínima de 80% durante alguns frames, o sistema executa a ação correspondente.

## Classes treinadas

O modelo deve ter pelo menos 3 classes:

| Classe | Exemplo | Ação |
|---|---|---|
| `PLAY` | 👍 | inicia o player |
| `PAUSE` | ✋ | pausa o player |
| `NEUTRO` | mão fora do enquadramento / posição neutra | não executa ação |

> Importante: os nomes acima precisam ser iguais aos nomes usados no treinamento ou a função `triggerAction()` deve ser adaptada.

## Tecnologias

- JavaScript
- Vite
- TensorFlow.js
- Teachable Machine Image
- Webcam do navegador

## 1. Treinar o modelo

1. Acesse o Teachable Machine.
2. Escolha **Image Project**.
3. Crie as classes `PLAY`, `PAUSE` e `NEUTRO`.
4. Colete exemplos variados para cada classe.
5. Treine o modelo.
6. Teste com imagens que não foram usadas no treinamento.
7. Clique em **Export Model**.
8. Escolha **TensorFlow.js**.
9. Baixe/exporte o modelo.

## 2. Colocar o modelo no projeto

Copie os arquivos exportados para:

```text
model/
```

A pasta deve conter pelo menos:

```text
model/
├── model.json
├── metadata.json
└── arquivos .bin
```

Não crie esses arquivos manualmente: eles precisam ser os arquivos reais gerados pelo Teachable Machine.

## 3. Instalar

Pré-requisito: Node.js instalado.

No terminal, dentro da pasta do projeto:

```bash
npm install
```

## 4. Executar

```bash
npm run dev
```

O Vite mostrará um endereço local, normalmente parecido com:

```text
http://localhost:5173
```

Abra esse endereço no navegador e permita o acesso à webcam.

## 5. Como a ação funciona

O sistema recebe continuamente a imagem da webcam e envia o frame para o modelo.

A aplicação:

1. mostra a confiança de todas as classes;
2. identifica a classe com maior probabilidade;
3. exige pelo menos **80% de confiança**;
4. exige a mesma classe por alguns frames para reduzir oscilações;
5. chama `triggerAction()`;
6. `PLAY` inicia o player;
7. `PAUSE` pausa o player;
8. `NEUTRO` não executa comando.

Assim, a ação é consequência direta da predição.

## 6. Estrutura

```text
teachable-gesture-control/
├── model/
│   ├── model.json
│   ├── metadata.json
│   ├── *.bin
│   └── README.md
├── src/
│   ├── app.js
│   └── style.css
├── .gitignore
├── index.html
├── package.json
└── README.md
```

## 7. Demonstração

Para a apresentação:

1. Execute `npm run dev`.
2. Abra a aplicação.
3. Clique em **Iniciar câmera e modelo**.
4. Mostre a webcam.
5. Faça o gesto `PLAY`.
6. Mostre a confiança acima de 80%.
7. Mostre que o player muda automaticamente para **REPRODUZINDO**.
8. Faça o gesto `PAUSE`.
9. Mostre que o player muda automaticamente para **PAUSADO**.
10. Faça o gesto `NEUTRO` e mostre que nenhuma ação é executada.

## 8. GitHub

Depois de testar:

```bash
git init
git add .
git commit -m "feat: integra modelo de gestos ao player"
git branch -M main
git remote add origin SEU_LINK_DO_REPOSITORIO
git push -u origin main
```

Façam commits dos dois integrantes da dupla para que ambos apareçam no histórico.

## 9. Checklist de entrega

- [ ] Modelo com pelo menos 3 classes
- [ ] Classe `NEUTRO`
- [ ] Modelo exportado em TensorFlow.js
- [ ] `model.json`, `metadata.json` e pesos colocados em `model/`
- [ ] Webcam funcionando
- [ ] Classe e confiança visíveis
- [ ] Limiar de confiança de 80%
- [ ] Ação automática funcionando
- [ ] README atualizado
- [ ] Print ou GIF da aplicação funcionando adicionado ao README
- [ ] Repositório público no GitHub
- [ ] Commits dos dois integrantes
- [ ] Projeto testado localmente

## 10. Print/GIF

Depois de executar o projeto, adicionem ao README uma imagem ou GIF real da aplicação funcionando, por exemplo:

Alunos: Alberto Costa e Matheus Albuquerque

```markdown
![Demonstração](docs/demo.gif)
```

Criem a pasta `docs/` e coloquem nela o arquivo real da demonstração.
