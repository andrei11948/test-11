<!DOCTYPE html>
<html lang="ro">
<head>
  <meta charset="UTF-8">
  <title>Test Bazele Economiei</title>
  <style>
    .corect { color: green; font-weight: bold; }
    .gresit { color: red; font-weight: bold; }
  </style>
</head>
<body>
  <h1>Test Grilă - Bazele Economiei</h1>
  <form id="quizForm">
    <ol>
      <li>
        Factorii de producție reprezintă:
        <br><label><input type="radio" name="q1" value="0"> Resursele consumate în activitatea de producție</label>
        <br><label><input type="radio" name="q1" value="0"> Resursele atrase în procesul de producție</label>
        <br><label><input type="radio" name="q1" value="1"> Resursele atrase, alocate și consumate în procesul de producție</label>
        <br><label><input type="radio" name="q1" value="0"> Resursele disponibile în economie</label>
      </li><br>

      <li>
        Identificați principalii factori de producție:
        <br><label><input type="radio" name="q2" value="0"> Munca și costul total</label>
        <br><label><input type="radio" name="q2" value="0"> Capitalul, munca și profitul</label>
        <br><label><input type="radio" name="q2" value="1"> Munca, natura și capitalul</label>
        <br><label><input type="radio" name="q2" value="0"> Resursele umane și materiale</label>
      </li><br>

      <li>
        Identificați cauzele care impun economisirea factorilor de producție:
        <br><label><input type="radio" name="q3" value="0"> Diversificarea produselor industriale</label>
        <br><label><input type="radio" name="q3" value="0"> Cererea de lux</label>
        <br><label><input type="radio" name="q3" value="1"> Creșterea prețurilor pentru anumiți factori de producție</label>
        <br><label><input type="radio" name="q3" value="0"> Dezvoltarea urbană</label>
      </li><br>

      <li>
        Munca reprezintă:
        <br><label><input type="radio" name="q4" value="1"> Factor activ</label>
        <br><label><input type="radio" name="q4" value="0"> Factor pasiv</label>
        <br><label><input type="radio" name="q4" value="0"> Factor auxiliar</label>
        <br><label><input type="radio" name="q4" value="0"> Factor neutru</label>
      </li><br>

      <li>
        Natura reprezintă:
        <br><label><input type="radio" name="q5" value="0"> Factor derivat</label>
        <br><label><input type="radio" name="q5" value="0"> Factor determinant</label>
        <br><label><input type="radio" name="q5" value="1"> Factor originar</label>
        <br><label><input type="radio" name="q5" value="0"> Factor tranzitoriu</label>
      </li><br>

      <li>
        Pământul reprezintă:
        <br><label><input type="radio" name="q6" value="1"> Un factor de producție</label>
        <br><label><input type="radio" name="q6" value="0"> O sursă de capital</label>
        <br><label><input type="radio" name="q6" value="0"> Un element consumabil</label>
        <br><label><input type="radio" name="q6" value="0"> Un bun de larg consum</label>
      </li><br>

      <li>
        Forța de muncă reprezintă:
        <br><label><input type="radio" name="q7" value="0"> Doar potențialul fizic al oamenilor</label>
        <br><label><input type="radio" name="q7" value="0"> Doar potențialul intelectual al oamenilor</label>
        <br><label><input type="radio" name="q7" value="1"> Totalitatea capacităților fizice și intelectuale specifice unui individ</label>
        <br><label><input type="radio" name="q7" value="0"> Potențialul profesional al unui colectiv</label>
      </li><br>

      <li>
        Activitatea de producție atrage după sine folosirea unor cantități specifice de factori de producție.
        <br><label><input type="radio" name="q8" value="1"> Adevărat</label>
        <br><label><input type="radio" name="q8" value="0"> Fals</label>
      </li><br>

      <li>
        Factorii de producție se află doar în proprietatea statului.
        <br><label><input type="radio" name="q9" value="0"> Adevărat</label>
        <br><label><input type="radio" name="q9" value="1"> Fals</label>
      </li><br>

      <li>
        Factorii de producție sunt în proprietatea agenților economici.
        <br><label><input type="radio" name="q10" value="1"> Adevărat</label>
        <br><label><input type="radio" name="q10" value="0"> Fals</label>
      </li><br>
    </ol>

    <input type="submit" value="Trimite răspunsurile">
  </form>

  <h2 id="rezultat"></h2>

  <script>
    document.getElementById("quizForm").addEventListener("submit", function(e) {
      e.preventDefault();
      const form = e.target;
      const total = 10;
      let scor = 0;

      const intrebari = form.querySelectorAll("ol > li");
      intrebari.forEach(li => {
        const raspunsuri = li.querySelectorAll("input[type=radio]");
        let corect = false;
        let selectat = false;

        raspunsuri.forEach(radio => {
          const label = radio.parentElement;
          label.classList.remove("corect", "gresit");

          if (radio.checked) {
            selectat = true;
            if (radio.value === "1") {
              scor++;
              label.classList.add("corect");
              corect = true;
            } else {
              label.classList.add("gresit");
            }
          }

          if (!selectat && radio.value === "1") {
            label.classList.add("corect");
          }
        });
      });

      document.getElementById("rezultat").textContent = `Ai obținut nota: ${(scor / total * 10).toFixed(2)} (${scor} din ${total} răspunsuri corecte)`;
      form.querySelector("input[type=submit]").disabled = true;
    });
  </script>
</body>
</html>
