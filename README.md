# Loop-Form
Track your caddie loops
<!DOCTYPE html>
<html>
<head>
  <title>Job Submission Form</title>
  <style>
    /* Style for the submit button */
    button[type="submit"] {
      background-color: green; /* Green background */
      color: white; /* White text */
      border: none; /* Remove border */
      padding: 10px 20px; /* Add some padding */
      font-size: 16px; /* Increase font size */
      border-radius: 5px; /* Add rounded corners */
      cursor: pointer; /* Add pointer cursor on hover */
    }

    /* Add hover effect */
    button[type="submit"]:hover {
      background-color: darkgreen; /* Darker green on hover */
    }
  </style>
</head>
<body>
  <form id="myForm">
    <label for="loopDate">Loop Date:</label>
    <input type="date" id="loopDate" name="loopDate" required><br><br>

    <label for="loopTime">Loop Time:</label>
    <input type="time" id="loopTime" name="loopTime" required><br><br>

    <label for="course">Course:</label>
    <select id="course" name="course" required>
      <option value="PB">PB</option>
      <option value="SG">SG</option>
      <option value="SB">SB</option>
      <option value="DM">DM</option>
      <option value="CP">CP</option>
      <option value="MPCC">MPCC</option>
      <option value="LPGA">LPGA</option>
    </select><br><br>

    <label for="jobType">Job Type:</label>
    <select id="jobType" name="jobType" required>
      <option value="D">D</option>
      <option value="S">S</option>
      <option value="4FC">4FC</option>
      <option value="3FC">3FC</option>
      <option value="5FC">5FC</option>
      <option value="OP">OP</option>
    </select><br><br>

    <label for="tip">Tip:</label>
    <input type="number" id="tip" name="tip" step="0.01"><br><br>

    <label for="benchRequest">Bench/Request:</label>
    <select id="benchRequest" name="benchRequest" required>
      <option value="Bench">Bench</option>
      <option value="Request">Request</option>
    </select><br><br>

    <label for="notes">Note(s):</label>
    <textarea id="notes" name="notes"></textarea><br><br>

    <button type="submit">Submit</button>
  </form>

  <script>
    const form = document.getElementById('myForm');
    form.addEventListener('submit', async (e) => {
      e.preventDefault();
  
      const formData = new FormData(form);
      const queryString = new URLSearchParams(formData).toString();
  
      const response = await fetch("https://script.google.com/macros/s/AKfycbx6Syf1_tSFmSfgWPronNpZ0WPN3IklfRc8Yr_27Rkz_ffH6cC1b3Hy7eaEOxJ_02Ak/exec", {
        method: "POST",
        body: queryString,
        headers: {
          "Content-Type": "application/x-www-form-urlencoded"
        }
      });
  
      const result = await response.text();
      alert(result);
      form.reset();
    });
  </script>
</body>
</html>
