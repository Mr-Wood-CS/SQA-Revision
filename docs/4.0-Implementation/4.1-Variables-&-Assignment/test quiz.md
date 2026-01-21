<div id="quiz-container"></div>
<div id="score"></div>

<script>
// Quiz data (fill in your questions later)
const quiz = [
    { question: "Is the sky blue?", options: ["A - Yes", "B - No", "C", "D"], answer: 0 },
    { question: "Question 2?", options: ["A", "B", "C", "D"], answer: 1 },
    { question: "Question 3?", options: ["A", "B", "C", "D"], answer: 2 },
    { question: "Question 4?", options: ["A", "B", "C", "D"], answer: 3 },
    { question: "Question 5?", options: ["A", "B", "C", "D"], answer: 0 },
    { question: "Question 6?", options: ["A", "B", "C", "D"], answer: 1 },
    { question: "Question 7?", options: ["A", "B", "C", "D"], answer: 2 },
    { question: "Question 8?", options: ["A", "B", "C", "D"], answer: 3 },
    { question: "Question 9?", options: ["A", "B", "C", "D"], answer: 0 },
    { question: "Question 10?", options: ["A", "B", "C", "D"], answer: 1 },
];

const container = document.getElementById('quiz-container');
let score = 0;

// Render questions
quiz.forEach((q, i) => {
    const qDiv = document.createElement('div');
    qDiv.classList.add('question');
    qDiv.innerHTML = `<strong>Q${i+1}: ${q.question}</strong>`;
    
    const optionsDiv = document.createElement('div');
    optionsDiv.classList.add('options');
    
    q.options.forEach((opt, idx) => {
        const btn = document.createElement('button');
        btn.textContent = opt;
        btn.addEventListener('click', () => {
            // disable all buttons for this question
            optionsDiv.querySelectorAll('button').forEach(b => b.disabled = true);
            
            if(idx === q.answer){
                btn.classList.add('correct');
                score++;
            } else {
                btn.classList.add('wrong');
                // highlight correct answer
                optionsDiv.querySelectorAll('button')[q.answer].classList.add('correct');
            }
            document.getElementById('score').textContent = `Score: ${score} / ${quiz.length}`;
        });
        optionsDiv.appendChild(btn);
    });
    
    qDiv.appendChild(optionsDiv);
    container.appendChild(qDiv);
});
</script>