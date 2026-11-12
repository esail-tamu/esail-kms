---
tags:
  - file-management
  - beginner
  - quiz
  - gap-bronze
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
            prompt: "Which statement correctly describes the casing rule?",
            options: [
              "Category labels (type codes, Homework/Exam/Project) are capitalized; content descriptors are lowercase",
              "Everything is lowercase except the course code",
              "Everything is capitalized except file extensions",
              "Casing doesn't matter, as long as it's consistent",
            ],
            correct: "Category labels (type codes, Homework/Exam/Project) are capitalized; content descriptors are lowercase",
          },
          {
            prompt: "Which file name correctly follows both the delimiter and casing rules?",
            options: [
              "ENGR123-M01-T01-VID-intro_to_loops.mp4",
              "ENGR123-m01-t01-vid-Intro_To_Loops.mp4",
              "ENGR123_M01_T01_VID_intro-to-loops.mp4",
              "engr123-M01-T01-VID-intro_to_loops.mp4",
            ],
            correct: "ENGR123-M01-T01-VID-intro_to_loops.mp4",
          },
        ],
        [
          {
            prompt: "What does the type code in a file name (like <code>VID</code>, <code>QIZ</code>, <code>ASG</code>) actually represent?",
            options: [
              "The actual Canvas tool the content uses",
              "A random abbreviation chosen for style",
              "The file's MIME type",
              "Whatever the instructor personally prefers to call it",
            ],
            correct: "The actual Canvas tool the content uses",
          },
          {
            prompt: "Which type code should be used when the Canvas tool for a piece of content hasn't been decided yet?",
            options: ["UNK", "TBD", "N/A", "FIL"],
            correct: "UNK",
          },
        ],
        [
          {
            prompt: "Which of these is numbered absolutely (course-wide), rather than tied to a specific module/topic?",
            options: ["A quiz", "A video", "A video's slide deck", "A reading tied to one topic"],
            correct: "A quiz",
          },
          {
            prompt: "Why don't Quizzes, Discussions, and Assignments carry a Module/Topic code?",
            options: [
              "They're numbered absolutely, course-wide — 'Quiz 5' always means the same file no matter which module it came from",
              "Because Canvas doesn't allow numbers in file names",
              "Because they aren't part of any module",
              "Because module numbers are only used for videos",
            ],
            correct: "They're numbered absolutely, course-wide — 'Quiz 5' always means the same file no matter which module it came from",
          },
        ],
        [
          {
            prompt: 'A video for Module 1, Topic 2, titled "Lab Safety." Which file name is correct?',
            options: [
              "ENGR123-M01-T02-VID-lab_safety.mp4",
              "ENGR123-VID-M01-T02-lab_safety.mp4",
              "ENGR123-M01-T02-vid-lab_safety.mp4",
              "ENGR123-M01-T02-VID-Lab_Safety.mp4",
            ],
            correct: "ENGR123-M01-T02-VID-lab_safety.mp4",
          },
          {
            prompt: 'A video for Module 3, Topic 1, titled "Sensor Calibration." Which file name is correct?',
            options: [
              "ENGR123-M03-T01-VID-sensor_calibration.mp4",
              "ENGR123-M03-T01-VID-Sensor_Calibration.mp4",
              "ENGR123-VID-M03-T01-sensor_calibration.mp4",
              "ENGR123_M03_T01_VID_sensor_calibration.mp4",
            ],
            correct: "ENGR123-M03-T01-VID-sensor_calibration.mp4",
          },
        ],
        [
          {
            prompt: "Which is the correctly named first quiz file for ENGR123?",
            options: [
              "ENGR123-QIZ-01.md",
              "ENGR123-M01-QIZ-01.md",
              "ENGR123-Quiz-01.md",
              "QIZ-01.md",
            ],
            correct: "ENGR123-QIZ-01.md",
          },
          {
            prompt: "Which is the correctly named first homework assignment for ENGR123, about differential equations?",
            options: [
              "ENGR123-ASG-Homework-01-differential_equations.md",
              "ENGR123-ASG-01-Homework-differential_equations.md",
              "ENGR123-Homework-01-differential_equations.md",
              "ENGR123-ASG-Homework-01-Differential_Equations.md",
            ],
            correct: "ENGR123-ASG-Homework-01-differential_equations.md",
          },
        ],
        [
          {
            prompt: "When should a label like <code>Homework</code>, <code>Exam</code>, or <code>Project</code> follow a type code?",
            options: [
              "Only when the type code alone is ambiguous about which flavor of content this is",
              "Always, on every single file",
              "Never — labels aren't allowed after a type code",
              "Only on videos",
            ],
            correct: "Only when the type code alone is ambiguous about which flavor of content this is",
          },
          {
            prompt: "Which type code most often needs a label, and why?",
            options: [
              "ASG, because it covers several different kinds of submission (homework, exam, project)",
              "QIZ, because quizzes vary widely in format",
              "VID, because videos need extra context",
              "DIS, because discussions are hard to tell apart",
            ],
            correct: "ASG, because it covers several different kinds of submission (homework, exam, project)",
          },
        ],
        [
          {
            prompt: "Which is the correctly named syllabus file for the Fall 2026 offering of ENGR123?",
            options: [
              "ENGR123-Syllabus-26C.pdf",
              "26C-ENGR123-Syllabus.pdf",
              "ENGR123-26C-Syllabus.pdf",
              "Syllabus-ENGR123-26C.pdf",
            ],
            correct: "ENGR123-Syllabus-26C.pdf",
          },
          {
            prompt: "Why does the Syllabus keep its term code as a trailing qualifier, instead of dropping it like other inner files?",
            options: [
              "So multiple draft versions across different terms still sort together under the same 'Syllabus' name",
              "Because syllabi are top-level documents only, and never live inside a course folder",
              "It doesn't — Syllabus drops the term code too, just like everything else",
              "Because 'Syllabus' is a reserved word in Canvas",
            ],
            correct: "So multiple draft versions across different terms still sort together under the same 'Syllabus' name",
          },
        ],
        [
          {
            prompt: "Which is the correctly named project folder for a Fall 2026 offering of 'Intro Robotics' taught by Smith?",
            options: [
              "26C-ENGR123-Intro_Robotics-Smith",
              "26C-ENGR123-intro_robotics-smith",
              "26C-ENGR123-Intro-Robotics-Smith",
              "ENGR123-26C-Intro_Robotics-Smith",
            ],
            correct: "26C-ENGR123-Intro_Robotics-Smith",
          },
          {
            prompt: "Why does the course title inside the project folder name (e.g. <code>Intro_Robotics</code>) stay capitalized, instead of lowercase like other descriptors?",
            options: [
              "Because it's the course's own title, not a content descriptor — the one deliberate exception to the lowercase-descriptor rule",
              "Because folder names must always be capitalized",
              "It doesn't — it should be lowercase like everything else",
              "Because capitalizing it makes it sort first alphabetically",
            ],
            correct: "Because it's the course's own title, not a content descriptor — the one deliberate exception to the lowercase-descriptor rule",
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
        html += '<button type="button" id="fnc-live-next" hidden>Next question</button>';
        mount.innerHTML = html;

        document.getElementById("fnc-live-check").addEventListener("click", checkAnswer);
        document.getElementById("fnc-live-next").addEventListener("click", goToNextQuestion);
      }

      function goToNextQuestion() {
        session.index++;
        if (session.index >= session.questions.length) {
          finishQuiz();
        } else {
          renderQuestion();
        }
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
          mount.querySelectorAll("input[type='radio']").forEach(function (r) {
            r.disabled = true;
          });
          var checkBtn = document.getElementById("fnc-live-check");
          var nextBtn = document.getElementById("fnc-live-next");
          checkBtn.hidden = true;
          nextBtn.hidden = false;
          nextBtn.textContent =
            session.index + 1 >= session.questions.length ? "See results" : "Next question";
          nextBtn.focus();
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
