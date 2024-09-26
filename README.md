# notquiz
// Funktion för att generera quiz baserat på användarens anteckningar
function generateQuiz() {
    const notes = document.getElementById("notes").value;
    const quizContainer = document.getElementById("quiz-container");
    quizContainer.innerHTML = ""; // Rensa tidigare quiz
    
    if (!notes.trim()) {
        alert("Skriv dina anteckningar först!");
        return;
    }

    // Simpel split för att skapa frågor från anteckningarna
    const questions = notes.split('.').filter(sentence => sentence.trim());

    if (questions.length === 0) {
        quizContainer.innerHTML = "Inga tillräckliga data för att skapa ett quiz.";
        return;
    }

    questions.forEach((question, index) => {
        const div = document.createElement("div");
        div.innerHTML = `<p>Fråga ${index + 1}: Vad kan du säga om detta: "${question.trim()}"?</p>`;
        quizContainer.appendChild(div);
    });
}
