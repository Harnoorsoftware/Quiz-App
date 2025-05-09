<!DOCTYPE html>
<html>

<head>
    <title>e</title>
    <script>
        function submitAnswer(qid) {
            var answer = document.getElementById('answer_' + qid).value;
            var formData = new FormData();
            formData.append('question_id', qid);
            formData.append('answer', answer);

            fetch('/submit', {
                method: 'POST',
                body: formData
            })
                .then(response => response.json())
                .then(data => {
                    document.getElementById('result_' + qid).innerText = data.result;
                });
        }
    </script>
</head>

<body>
    <h1>Answer the questions</h1>
    {Question.1}
    <div style="margin-bottom:20px;">
        <form onsubmit="event.preventDefault(); submitAnswer('{{ qid }}');">
            <label>{What is the capital of India ?}</label><br>
            <input type="text" id="answer_{{ qid }}" name="answer" required>
            <button type="submit">Submit</button>
            <span id="result_{{ qid }}"></span>
        </form>
    </div>
</body>

</html>
