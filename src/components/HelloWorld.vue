<template>

    <!DOCTYPE html>
    <html lang="en">

    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>

    </head>

    <body>
      <center>
        <div class="app-container">
        <div class="terminal">
            
    <h1>Gerador de História</h1>
    <br>
    <textarea v-model="prompt" placeholder="Digite seu prompt aqui..."></textarea>
    <button @click="generateStory">Gerar História</button>
    <div v-if="loading">Carregando...</div>
    <div v-if="story">
      <h2>Envie:</h2>
      <p>{{ story }}</p>
    </div>
    <div v-if="error" class="error">{{ error }}</div>
  </div>
</div>
    </center>
    
<center>
     
    
<br>


        <div class="quadro">
            <h1>Kauã da Silva Rossanezi</h1>
            <h2>As caixas de água</h2>
        </div>
    </center>    
    
    

    </body>

    </html>

</template>

<script>
// // import { GoogleGenerativeAI } from "@google/generative-ai";

// // export default {
// //   data() {
// //     return {
// //       prompt: "Write a story about a magic backpack.",
// //       story: null,
// //       loading: false,
// //       error: null,
// //     };
// //   },
// //   methods: {
// //     async generateStory() {
// //       this.loading = true;
// //       this.error = null;

// //       // Certifique-se de usar o VUE_APP_API_KEY
// //       const genAI = new GoogleGenerativeAI(process.env.VUE_APP_API_KEY); 
// //       const model = genAI.getGenerativeModel({ model: "gemini-1.5-flash" });

// //       try {
// //         const result = await model.generateContent(this.prompt);
// //         this.story = result.response.text(); // Acessa o texto da resposta
// //       } catch (err) {
// //         this.error = "Erro ao gerar a história: " + err.message;
// //       } finally {
// //         this.loading = false;
// //       }
  

// // export default {
// //     props: ['src'],
// //     data() {
// //         return {
// //             loaded: false
// //         };
// //     },
//     mounted() {
//         const input = this.$refs.input;
//         // alert(input);
//         if (input !== undefined) {
//             input.addEventListener('keydown', this.handleKeyDown);
//         }
//     },
//     methods: {
//         handleKeyDown(event) {
//             if (event.key === 'Enter') {
//                 const command = event.target.value;
//                 this.processCommand(command);
//                 event.target.value = ''; // Limpa o campo de entrada
//             }
//         },
//         processCommand(command) {
//             let response;

//             switch (command.toLowerCase()) {
//                 case 'help':
//                     response = 'Comandos disponíveis:\n' +
//                         '1. help - Mostra esta mensagem.\n' +
//                         '2. clear - Limpa o terminal.\n' +
//                         '3. about - Informações sobre este simulador.';
//                     break;
//                 case 'clear':
//                     this.$refs.output.innerHTML = '';
//                     return; // Não adiciona nada no output
//                 case 'about':
//                     response = 'Este é um simulador de prompt de comando criado como exemplo.';
//                     break;
//                 default:
//                     response = 'Comando desconhecido. Digite "help" para ver a lista de comandos.';
//                     break;
//             }

//             this.$refs.output.innerHTML += `> ${command}\n${response}\n\n`;
//             this.scrollToBottom();
//         },
//         scrollToBottom() {
//             const terminal = this.$el.querySelector('.terminal');
//             terminal.scrollTop = terminal.scrollHeight;
//         }
//     }
// };
// },
//   },
// };
const apiKey = process.env.VUE_APP_API_KEY;
console.log(apiKey);

// const input = document.getElementById('enviar');
// const output = document.getElementById('output');
// if (input !== null) {

//     input.addEventListener('keydown', function (event) {
//         if (event.key === 'Enter') {
//             const command = input.value;
//             processCommand(command);
//             input.value = ''; // Limpa o campo de entrada
//         }
//     });

// }

// // function processCommand(command) {
// //     let response;

// //     switch (command.toLowerCase()) {
// //         case 'help':
// //             response = 'Comandos disponíveis:\n' +
// //                 '1. help - Mostra esta mensagem.\n' +
// //                 '2. clear - Limpa o terminal.\n' +
// //                 '3. about - Informações sobre este simulador.';
// //             break;
// //         case 'clear':
// //             // output.innerHTML = '';
// //             return; // Não adiciona nada no output
// //         case 'about':
// //             response = 'Este é um simulador de prompt de comando criado como exemplo.';
// //             break;
// //         default:
// //             response = 'Comando desconhecido. Digite "help" para ver a lista de comandos.';
// //             break;
// //     }

// //     // output.innerHTML += `> ${command}\n${response}\n\n`;
// //     scrollToBottom();
// // }

// function scrollToBottom() {
//     const terminal = document.querySelector('.terminal');
//     terminal.scrollTop = terminal.scrollHeight;
// }

</script>





<!-- Add "scoped" attribute to limit CSS to this component only -->
<style >
.app-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 20px; /* Espaçamento entre os elementos */
}

.terminal {
    border: 2px solid #e1b7ff;
    padding: 10px;
    height: 400px;
    overflow-y: auto;
    background-color: hwb(262 61% 15% / 0.281);
    box-shadow: 0 0 15px rgba(225, 183, 255, 0.5);
    border-radius: 10px;
    font-family: 'Courier New', Courier, monospace;
    width: 100vh;
}

#output {
    white-space: pre-wrap;
    margin-bottom: 10px;
    color: #e1b7ff;
}

.input-container {
    display: flex;
    margin-top: 10px;
}

input[type="text"] {
    background-color: #2b0a4e;
    color: #e1b7ff;
    border: none;
    flex: 1;
    outline: none;
    padding: 10px;
    font-size: 16px;
    border-radius: 5px;
    margin-right: 10px;
}

input[type="text"]::placeholder {
    color: #c0a0e1;
}

button {
    background-color: #4a90e2;
    color: white;
    border: none;
    border-radius: 5px;
    padding: 10px 20px;
    cursor: pointer;
    transition: background-color 0.3s;
}

button:hover {
    background-color: #357ABD;
}

.quadro {
    background-color: #ffffff;
    border: 2px solid #4a90e2;
    border-radius: 10px;
    padding: 30px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    text-align: center;
    width: 30vh;
    height: 13vh;
}

h1 {
    font-size: 24px;
    color: #333;
}

h2 {
    font-size: 20px;
    color: #666;
}

</style>