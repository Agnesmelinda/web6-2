<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>GST Calculator</title>
  <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>

  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f0f8ff;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .container {
      background-color: #e0f7fa;
      padding: 30px;
      border-radius: 15px;
      width: 320px;
      text-align: center;
      box-shadow: 0 4px 10px rgba(0,0,0,0.2);
    }

    h2 {
      color: #0077cc;
      margin-bottom: 20px;
    }

    label {
      display: block;
      font-weight: bold;
      margin-top: 10px;
    }

    input, select {
      width: 100%;
      padding: 10px;
      margin-top: 8px;
      border-radius: 8px;
      border: 1px solid #ccc;
      font-size: 16px;
      text-align: center;
      box-sizing: border-box;
    }

    .output {
      margin-top: 15px;
      font-size: 16px;
      font-weight: bold;
      color: #333;
    }

    button {
      background-color: #3578e5;
      color: white;
      border: none;
      padding: 10px 20px;
      margin-top: 15px;
      border-radius: 8px;
      font-size: 16px;
      cursor: pointer;
    }

    button:hover {
      background-color: #2851a3;
    }
  </style>
</head>

<body>

  <div class="container">
    <h2>GST Calculator</h2>

    <label for="amount">Amount:</label>
    <input type="number" id="amount" placeholder="Enter amount">

    <label for="gst">GST (%):</label>
    <select id="gst">
      <option value="3">3%</option>
      <option value="5">5%</option>
      <option value="12">12%</option>
      <option value="18">18%</option>
      <option value="28">28%</option>
    </select>

    <div class="output">
      <p>Actual Amount: <span id="actual">0.00</span></p>
      <p>GST: <span id="gstamt">0.00</span></p>
      <p>Total: <span id="total">0.00</span></p>
    </div>

    <button id="reset">Reset</button>
  </div>

  <script>
    $(document).ready(function() {
      // Function to calculate GST
      function calculateGST() {
        let amount = parseFloat($("#amount").val()) || 0;
        let gstPercent = parseFloat($("#gst").val());

        let gstAmount = (amount * gstPercent) / 100;
        let totalAmount = amount + gstAmount;

        $("#actual").text(amount.toFixed(2));
        $("#gstamt").text(gstAmount.toFixed(2));
        $("#total").text(totalAmount.toFixed(2));
      }

      // Trigger GST calculation on events
      $("#amount").on("keyup change", calculateGST);
      $("#gst").on("change", calculateGST);

      // Reset fields
      $("#reset").click(function() {
        $("#amount").val("");
        $("#gst").val("3");
        $("#actual").text("0.00");
        $("#gstamt").text("0.00");
        $("#total").text("0.00");
      });
    });
  </script>

</body>
</html>
