---
tags:
  - file-management
  - beginner
  - quiz
---

# Check Your Understanding

Ten questions covering the naming convention from the [training page](index.md). Answer one at a time — if you miss one, that choice is eliminated and you try again, so you can't move on until you get it right. Finishing the quiz means you've got the whole convention down, no grading needed.

Questions are pulled from a bank and shuffled (wording, examples, and answer order), so what you see may differ from what someone else sees.

Once you finish, your email and a quick attempts-per-question summary are sent to `esail-subscriptions@tamu.edu` via [Formspree](https://formspree.io).

<form id="fnc-quiz" class="fnc-quiz" markdown="0" action="https://formspree.io/f/mvkagaoy" method="POST">

<input type="hidden" name="_subject" value="File Naming Convention quiz submission">
<input type="hidden" name="email" id="fnc-email-hidden" value="">
<input type="hidden" name="result" value="Completed — all answers correct">
<input type="hidden" name="total_attempts" id="fnc-total-attempts" value="">
<input type="hidden" name="attempts_breakdown" id="fnc-attempts-breakdown" value="">

<div id="fnc-start" class="fnc-stage">
  <label class="fnc-prompt" for="fnc-email-input">Your email address</label>
  <input type="email" id="fnc-email-input" class="fnc-input" placeholder="you@tamu.edu" required>
  <p class="fnc-field-error" id="fnc-email-error"></p>
  <button type="button" id="fnc-start-btn">Start quiz</button>
</div>

<div id="fnc-quiz-stage" class="fnc-stage" hidden>
  <div class="fnc-progress">
    <div class="fnc-progress-track"><div class="fnc-progress-fill" id="fnc-progress-fill"></div></div>
    <p id="fnc-progress-text"></p>
  </div>
  <div id="fnc-question-mount"></div>
</div>

<div id="fnc-done-stage" class="fnc-stage" hidden>
  <p id="fnc-result"></p>
</div>

<p class="fnc-restart"><button type="button" id="fnc-restart-btn">Start over</button></p>

</form>

<style>
  .fnc-quiz {
    --fnc-correct-bg: #e3f2e1;
    --fnc-correct-border: #4a9a4e;
    --fnc-incorrect-bg: #fbe4e2;
    --fnc-incorrect-border: #b3261e;
  }
  [data-md-color-scheme="slate"] .fnc-quiz {
    --fnc-correct-bg: #1f3d22;
    --fnc-correct-border: #4a9a4e;
    --fnc-incorrect-bg: #4a2320;
    --fnc-incorrect-border: #e2897e;
  }

  .fnc-stage {
    border: 1px solid var(--md-default-fg-color--lightest);
    border-radius: 0.4rem;
    padding: 1.1rem 1.25rem 1.2rem;
    margin: 0 0 1rem;
    background: var(--md-default-bg-color);
  }

  .fnc-prompt { margin: 0 0 0.7rem; font-weight: 700; }

  .fnc-input {
    width: 100%;
    max-width: 26rem;
    padding: 0.4rem 0.6rem;
    border: 1px solid var(--md-default-fg-color--lighter);
    border-radius: 0.25rem;
    background: var(--md-default-bg-color);
    color: var(--md-default-fg-color);
    font-family: var(--md-code-font, monospace);
  }

  .fnc-field-error {
    margin: 0.5rem 0 0;
    font-size: 0.85rem;
    font-weight: 700;
    min-height: 1.1rem;
    color: var(--fnc-incorrect-border);
  }

  .fnc-progress { margin: 0 0 1rem; }

  .fnc-progress-track {
    height: 0.4rem;
    border-radius: 999px;
    background: var(--md-default-fg-color--lightest);
    overflow: hidden;
  }

  .fnc-progress-fill {
    height: 100%;
    background: var(--md-primary-fg-color);
    transition: width 0.3s ease;
  }

  #fnc-progress-text {
    margin: 0.4rem 0 0;
    font-size: 0.8rem;
    color: var(--md-default-fg-color--light);
    text-transform: uppercase;
    letter-spacing: 0.04em;
  }

  .fnc-opt {
    display: block;
    border: 1px solid var(--md-default-fg-color--lightest);
    border-radius: 0.3rem;
    padding: 0.5rem 0.75rem;
    margin: 0.4rem 0;
    cursor: pointer;
  }

  .fnc-opt input[type="radio"] { margin-right: 0.6rem; }

  .fnc-opt.fnc-opt-wrong {
    background: var(--fnc-incorrect-bg);
    border-color: var(--fnc-incorrect-border);
    text-decoration: line-through;
    opacity: 0.7;
    cursor: not-allowed;
  }

  .fnc-feedback {
    margin: 0.7rem 0 0;
    font-size: 0.9rem;
    font-weight: 700;
    min-height: 1.1rem;
  }

  .fnc-feedback-correct { color: var(--fnc-correct-border); }
  .fnc-feedback-incorrect { color: var(--fnc-incorrect-border); }

  .fnc-stage button,
  .fnc-restart button {
    font: inherit;
    font-weight: 700;
    padding: 0.55rem 1.3rem;
    border-radius: 0.3rem;
    border: 1px solid var(--md-primary-fg-color);
    background: var(--md-primary-fg-color);
    color: var(--md-primary-bg-color);
    cursor: pointer;
    margin-top: 0.9rem;
  }

  .fnc-restart { margin: 0; }

  .fnc-restart button {
    background: transparent;
    color: var(--md-default-fg-color--light);
    border-color: var(--md-default-fg-color--lighter);
    font-size: 0.8rem;
    font-weight: 400;
    padding: 0.3rem 0.8rem;
    margin-top: 0;
  }

  #fnc-result {
    font-weight: 700;
    font-size: 1.05rem;
    margin: 0;
  }
</style>

<script>
  window.addEventListener("DOMContentLoaded", function () {
    // document$ is Material's own router observable, which fires on every
    // page view (including this first one) and on every instant-navigation
    // swap thereafter. Deferring to DOMContentLoaded guarantees Material's
    // bundle (which defines document$) has already run, even on a fresh
    // full page load where this inline script would otherwise execute first.
    document$.subscribe(function () {
      var root = document.getElementById("fnc-quiz");
      if (!root || root.dataset.fncBound) return;
      root.dataset.fncBound = "true";

      var QUESTION_BANK = [
        [
          {
            prompt: 'A project folder is named <code>26C-ENGR123-...</code>. What does the term code <code>26C</code> mean?',
            options: ["Spring 2026", "Summer 2026", "Fall 2026", "Fall 2016"],
            correct: "Fall 2026",
          },
          {
            prompt: 'A project folder is named <code>25A-CSCE410-...</code>. What does the term code <code>25A</code> mean?',
            options: ["Spring 2025", "Summer 2025", "Fall 2025", "Spring 2015"],
            correct: "Spring 2025",
          },
        ],
        [
          {
            prompt: 'Which is the correctly formatted course code for "ENGR 123," as used inside file names?',
            options: ["ENGR123", "ENGR-123", "ENGR_123", "ENGR 123"],
            correct: "ENGR123",
          },
          {
            prompt: 'Which is the correctly formatted course code for "CSCE 410," as used inside file names?',
            options: ["CSCE410", "CSCE-410", "CSCE_410", "CSCE 410"],
            correct: "CSCE410",
          },
        ],
        [
          {
            prompt: "Which statement describes the delimiter rule?",
            options: [
              "Hyphens separate structured fields; underscores join words inside a title",
              "Underscores separate structured fields; hyphens join words inside a title",
              "Spaces separate everything",
              "It doesn't matter, as long as it's readable",
            ],
            correct: "Hyphens separate structured fields; underscores join words inside a title",
          },
          {
            prompt: "Which file name correctly follows the delimiter rule?",
            options: [
              "ENGR123-M01-T01-Intro_to_Loops.mp4",
              "ENGR123_M01_T01_Intro-to-Loops.mp4",
              "ENGR123-M01-T01-Intro-to-Loops.mp4",
              "ENGR123 M01 T01 Intro to Loops.mp4",
            ],
            correct: "ENGR123-M01-T01-Intro_to_Loops.mp4",
          },
        ],
        [
          {
            prompt: 'A video for Module 1, Topic 2, titled "Lab Safety." Which file name is correct (include the <code>.mp4</code> extension)?',
            options: [
              "ENGR123-M01-T02-Lab_Safety.mp4",
              "ENGR123-M01-T02-Lab-Safety.mp4",
              "ENGR123_M01_T02_Lab_Safety.mp4",
              "ENGR123-M02-T01-Lab_Safety.mp4",
            ],
            correct: "ENGR123-M01-T02-Lab_Safety.mp4",
          },
          {
            prompt: 'A video for Module 3, Topic 1, titled "Sensor Calibration." Which file name is correct (include the <code>.mp4</code> extension)?',
            options: [
              "ENGR123-M03-T01-Sensor_Calibration.mp4",
              "ENGR123-M03-T01-Sensor-Calibration.mp4",
              "ENGR123_M03_T01_Sensor_Calibration.mp4",
              "ENGR123-M01-T03-Sensor_Calibration.mp4",
            ],
            correct: "ENGR123-M03-T01-Sensor_Calibration.mp4",
          },
        ],
        [
          {
            prompt: "What does <code>T00</code> mean in a file name?",
            options: [
              "The topic hasn't been assigned yet",
              "The item applies to the whole module, not one topic",
              "It's a placeholder for an error",
              'It means "Topic 0," the very first topic',
            ],
            correct: "The item applies to the whole module, not one topic",
          },
          {
            prompt: "A file is named <code>ENGR123-M02-T00-Discussion01.md</code>. What does the <code>T00</code> tell you?",
            options: [
              "It applies to all of Module 2, not one specific topic",
              "It's the first topic covered in Module 2",
              "The topic number was left blank by mistake",
              "Discussions never get a topic number",
            ],
            correct: "It applies to all of Module 2, not one specific topic",
          },
        ],
        [
          {
            prompt: "When do Exam and Project files include a module/topic code?",
            options: [
              "Always",
              "They never include one, since exams and projects are usually course-wide",
              "Only exams skip it",
              "Only projects skip it",
            ],
            correct: "They never include one, since exams and projects are usually course-wide",
          },
          {
            prompt: "Which is the correctly named second course project file?",
            options: [
              "ENGR123-Project02.md",
              "ENGR123-M00-T00-Project02.md",
              "ENGR123-M01-T00-Project02.md",
              "26C-ENGR123-Project02.md",
            ],
            correct: "ENGR123-Project02.md",
          },
        ],
        [
          {
            prompt: "Which is the correctly named second exam file for ENGR123?",
            options: [
              "ENGR123-Exam02.md",
              "ENGR123-M00-T00-Exam02.md",
              "26C-ENGR123-Exam02.md",
              "ENGR123-Exam2.md",
            ],
            correct: "ENGR123-Exam02.md",
          },
          {
            prompt: "Which is the correctly named first exam file for CSCE410?",
            options: [
              "CSCE410-Exam01.md",
              "CSCE410-M00-T00-Exam01.md",
              "25A-CSCE410-Exam01.md",
              "CSCE410-Exam1.md",
            ],
            correct: "CSCE410-Exam01.md",
          },
        ],
        [
          {
            prompt: "Which inner file is the exception that keeps the term code, even though inner files usually drop it?",
            options: ["Any assignment", "The Syllabus", "Any quiz", "Any video"],
            correct: "The Syllabus",
          },
          {
            prompt: "Which is the correctly named syllabus file for the Fall 2026 offering of ENGR123?",
            options: [
              "26C-ENGR123-Syllabus.pdf",
              "ENGR123-Syllabus.pdf",
              "26C-ENGR123-M00-T00-Syllabus.pdf",
              "Syllabus-ENGR123-26C.pdf",
            ],
            correct: "26C-ENGR123-Syllabus.pdf",
          },
        ],
        [
          {
            prompt: "Which top-level folder holds content that isn't forced into any particular structure — SMEs can just drop files in?",
            options: ["01-SME-Content", "02-eSAIL-Production", "01-Syllabus", "SME-Content"],
            correct: "01-SME-Content",
          },
          {
            prompt: "Why is the SME intake folder named <code>01-SME-Content</code> instead of just <code>SME-Content</code>?",
            options: [
              "So it always sorts before 02-eSAIL-Production, regardless of case",
              "Folder names are required to start with a number",
              "It indicates the course's first week",
              "It has no particular reason, it's just a style preference",
            ],
            correct: "So it always sorts before 02-eSAIL-Production, regardless of case",
          },
        ],
        [
          {
            prompt: "Which pair of top-level folders sits inside a project, and in what order?",
            options: [
              "eSAIL-Production, then SME-Content",
              "01-SME-Content, then 02-eSAIL-Production",
              "SME, then eSAIL",
              "Work, then Final",
            ],
            correct: "01-SME-Content, then 02-eSAIL-Production",
          },
          {
            prompt: "Why are <code>01-Syllabus</code>, <code>02-Work</code>, and <code>03-Final</code> numbered instead of left alphabetical?",
            options: [
              "Alphabetical order would read Final, Syllabus, Work — out of workflow order",
              "Numbers are required by GitHub Pages",
              "To match the course catalog numbering",
              "Folder names can't start with letters",
            ],
            correct: "Alphabetical order would read Final, Syllabus, Work — out of workflow order",
          },
        ],
      ];

      var startStage = document.getElementById("fnc-start");
      var quizStage = document.getElementById("fnc-quiz-stage");
      var doneStage = document.getElementById("fnc-done-stage");
      var mount = document.getElementById("fnc-question-mount");
      var progressFill = document.getElementById("fnc-progress-fill");
      var progressText = document.getElementById("fnc-progress-text");
      var emailInput = document.getElementById("fnc-email-input");
      var emailError = document.getElementById("fnc-email-error");
      var startBtn = document.getElementById("fnc-start-btn");
      var restartBtn = document.getElementById("fnc-restart-btn");
      var emailHidden = document.getElementById("fnc-email-hidden");
      var totalAttemptsField = document.getElementById("fnc-total-attempts");
      var breakdownField = document.getElementById("fnc-attempts-breakdown");
      var resultEl = document.getElementById("fnc-result");

      var session = null;

      function shuffle(arr) {
        var a = arr.slice();
        for (var i = a.length - 1; i > 0; i--) {
          var j = Math.floor(Math.random() * (i + 1));
          var tmp = a[i];
          a[i] = a[j];
          a[j] = tmp;
        }
        return a;
      }

      function buildSession() {
        var questions = QUESTION_BANK.map(function (slot) {
          var variant = slot[Math.floor(Math.random() * slot.length)];
          return {
            prompt: variant.prompt,
            options: shuffle(variant.options),
            correct: variant.correct,
          };
        });
        return {
          questions: questions,
          index: 0,
          attempts: questions.map(function () {
            return 0;
          }),
        };
      }

      function isValidEmail(value) {
        return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(value.trim());
      }

      function renderQuestion() {
        var q = session.questions[session.index];
        var total = session.questions.length;
        progressText.textContent = "Question " + (session.index + 1) + " of " + total;
        progressFill.style.width = Math.round((session.index / total) * 100) + "%";

        var html = '<p class="fnc-prompt">' + q.prompt + "</p>";
        q.options.forEach(function (opt) {
          var encoded = encodeURIComponent(opt);
          html +=
            '<label class="fnc-opt" data-value="' + encoded + '">' +
            '<input type="radio" name="fnc-live-q" value="' + encoded + '"> ' +
            opt +
            "</label>";
        });
        html += '<p class="fnc-feedback" id="fnc-live-feedback"></p>';
        html += '<button type="button" id="fnc-live-check">Check answer</button>';
        mount.innerHTML = html;

        document.getElementById("fnc-live-check").addEventListener("click", checkAnswer);
      }

      function checkAnswer() {
        var q = session.questions[session.index];
        var checked = mount.querySelector("input[type='radio']:checked");
        var feedback = document.getElementById("fnc-live-feedback");

        if (!checked) {
          feedback.textContent = "Pick an answer first.";
          feedback.className = "fnc-feedback";
          return;
        }

        var chosen = decodeURIComponent(checked.value);

        if (chosen === q.correct) {
          feedback.textContent = "Correct!";
          feedback.className = "fnc-feedback fnc-feedback-correct";
          document.getElementById("fnc-live-check").disabled = true;
          mount.querySelectorAll("input[type='radio']").forEach(function (r) {
            r.disabled = true;
          });
          session.index++;
          setTimeout(function () {
            if (session.index >= session.questions.length) {
              finishQuiz();
            } else {
              renderQuestion();
            }
          }, 700);
        } else {
          session.attempts[session.index]++;
          feedback.textContent = "Not quite — try again.";
          feedback.className = "fnc-feedback fnc-feedback-incorrect";
          var label = mount.querySelector('label[data-value="' + checked.value + '"]');
          if (label) label.classList.add("fnc-opt-wrong");
          checked.disabled = true;
        }
      }

      function finishQuiz() {
        quizStage.hidden = true;
        doneStage.hidden = false;

        var totalAttempts = session.attempts.reduce(function (a, b) {
          return a + b;
        }, 0);
        var breakdown = session.attempts
          .map(function (n, i) {
            return "Q" + (i + 1) + "=" + (n + 1);
          })
          .join(", ");

        emailHidden.value = emailInput.value.trim();
        totalAttemptsField.value = String(totalAttempts + session.questions.length);
        breakdownField.value = breakdown;

        resultEl.textContent = "All correct! Submitting…";

        var formData = new FormData(root);
        fetch(root.action, {
          method: "POST",
          body: formData,
          headers: { Accept: "application/json" },
        })
          .then(function (response) {
            if (response.ok) {
              resultEl.textContent =
                "All correct! A copy was sent to esail-subscriptions@tamu.edu. Redirecting…";
              setTimeout(function () {
                window.location.href = "../thank-you/";
              }, 3000);
            } else {
              resultEl.textContent =
                "All correct, but the submission failed. Please try again or contact ESAIL.";
            }
          })
          .catch(function () {
            resultEl.textContent =
              "All correct, but the submission failed (network error). Please try again.";
          });
      }

      startBtn.addEventListener("click", function () {
        emailError.textContent = "";
        if (!isValidEmail(emailInput.value)) {
          emailError.textContent = "Enter a valid email address before starting.";
          emailInput.focus();
          return;
        }
        session = buildSession();
        startStage.hidden = true;
        quizStage.hidden = false;
        doneStage.hidden = true;
        renderQuestion();
      });

      restartBtn.addEventListener("click", function () {
        quizStage.hidden = true;
        doneStage.hidden = true;
        startStage.hidden = false;
        emailInput.value = "";
        emailError.textContent = "";
        session = null;
      });
    });
  });
</script>
