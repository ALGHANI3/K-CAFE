                              **K-CAFE**
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>K-CAFE Daily Report</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      direction: ltr;
      background-image: url('https://i.postimg.cc/gjGgkCY3/Brown-Coffee-Shop-Logo.png');
      background-size: cover;
      background-repeat: no-repeat;
      background-attachment: fixed;
      background-position: center;
      padding: 20px;
      line-height: 1.6;
      color: #333;
    }
    h2 {
      text-align: center;
      color: #333;
      margin-bottom: 10px; /* Adjusted margin */
      text-shadow: 1px 1px 2px rgba(255,255,255,0.7);
    }
    #reportDate {
        text-align: center;
        font-size: 1.1em;
        color: #555;
        margin-bottom: 20px;
    }
    form {
      background: rgba(255, 255, 255, 0.9);
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
      margin-bottom: 20px;
    }
    label {
      display: block;
      margin-bottom: 5px;
      font-weight: bold;
    }
    select, input[type="number"] {
      padding: 10px;
      margin-bottom: 15px;
      font-size: 16px;
      width: calc(100% - 22px);
      border: 1px solid #ccc;
      border-radius: 4px;
      box-sizing: border-box;
    }
    button.btn {
      display: block;
      width: 100%;
      padding: 12px;
      margin-top: 10px; /* Added margin to separate buttons */
      font-size: 18px;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
    button.btn-primary {
        background-color: #007BFF;
        color: white;
    }
    button.btn-primary:hover {
        background-color: #0056b3;
    }
    button.btn-secondary {
        background-color: #6c757d; /* Grey color for cancel */
        color: white;
    }
     button.btn-secondary:hover {
        background-color: #5a6268;
    }

    table {
      width: 100%;
      margin-top: 20px;
      border-collapse: collapse;
      background: rgba(255, 255, 255, 0.9);
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
      border-radius: 8px;
      overflow: hidden;
    }
    th, td {
      padding: 12px;
      text-align: center;
      border: 1px solid #ddd;
    }
    th {
      background-color: #f2f2f2;
      font-weight: bold;
      color: #333;
    }
    tr:nth-child(even) {
      background-color: #f9f9f9;
    }
    tr:hover {
      background-color: #e9e9e9;
    }
    /* Style for the day end report section */
    #dayEndReport {
      margin-top: 30px;
      padding: 20px;
      background: rgba(255, 255, 255, 0.9);
      border-radius: 8px;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    }
    #dayEndReport h3 {
      text-align: center;
      color: #333;
      margin-bottom: 15px;
    }
    #dayEndReport p {
      font-size: 18px;
      margin-bottom: 10px;
    }
    #dayEndReport .profit {
      color: green;
      font-weight: bold;
    }
    #dayEndReport .loss {
      color: red;
      font-weight: bold;
    }
    /* Style for the share button */
    #shareBtn {
        margin-top: 20px;
        background-color: #25D366; /* WhatsApp green */
        color: white;
    }
    #shareBtn:hover {
        background-color: #1DA851;
    }
    #shareInstructions {
        margin-top: 15px;
        padding: 15px;
        background: rgba(255, 255, 255, 0.9);
        border-radius: 8px;
        box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        display: none; /* Hidden by default */
    }
  </style>
</head>
<body>

<h2>K-CAFE - Daily Purchase & Sale Tracker</h2>
<div id="reportDate"></div> <form id="entryForm">
  <label for="entryType">Entry Type:</label>
  <select id="entryType">
    <option value="Sale">Sale</option>
    <option value="Purchase">Purchase</option>
  </select>

  <label for="product">Select Product:</label>
  <select id="product">
    <option value="Water Bottle 1.5L">Water Bottle 1.5L</option>
    <option value="Water Bottle 500ml">Water Bottle 500ml</option>
    <option value="Cold Drinks">Cold Drinks</option>
    <option value="Tea">Tea</option>
    <option value="Fries">Fries</option>
    <option value="Chips">Chips</option>
    <option value="Other">Other</option>
    <option value="Can">Can</option> </select>

  <label for="price">Total Price:</label>
  <input type="number" id="price" placeholder="Total Price" min="0">

  <label for="quantity">Quantity:</label>
  <input type="number" id="quantity" placeholder="Quantity" min="1">

  <button class="btn btn-primary" type="button" onclick="addEntry()">Add Entry</button>
  <button class="btn btn-secondary" type="button" onclick="cancelEntry()">Cancel</button> </form>

<table id="dataTable">
  <thead>
    <tr>
      <th>Entry Type</th>
      <th>Product</th>
      <th>Total Price</th>
      <th>Quantity</th>
      <th>Unit Price</th>
      <th>Total</th>
    </tr>
  </thead>
  <tbody>
    </tbody>
</table>

<div id="dayEndReport">
  <h3>Day End Summary</h3>
  <p>Total Purchase: <span id="totalPurchaseDisplay">0.00</span></p>
  <p>Total Sale: <span id="totalSaleDisplay">0.00</span></p>
  <p>Profit/Loss: <span id="profitLossDisplay">0.00</span></p>
</div>

<button class="btn" id="shareBtn" onclick="shareViaWhatsApp()">Share Day End Summary on WhatsApp</button>

<div id="shareInstructions">
    <h4>رپورٹ شیئر کرنے کے طریقے:</h4>
    <p>1. **WhatsApp پر سمری بھیجیں:** اوپر والے بٹن پر کلک کریں، یہ WhatsApp کھولے گا جس میں دن کی سمری کا متن پہلے سے لکھا ہوگا۔</p>
    <p>2. **مکمل رپورٹ PDF میں محفوظ کریں:** اس صفحے پر Right-click (یا موبائل پر مینیو) کر کے 'Print' کا آپشن منتخب کریں۔ Printer کے طور پر 'Save as PDF' منتخب کریں اور فائل کو محفوظ کریں۔ پھر اسے WhatsApp پر دستی طور پر شیئر کریں۔</p>
</div>


<script>
  // Global variables to store total purchase and sale
  let grandTotalPurchase = 0;
  let grandTotalSale = 0;

  // Function to display the current date
  function displayCurrentDate() {
      const today = new Date();
      const options = { year: 'numeric', month: 'long', day: 'numeric' };
      const formattedDate = today.toLocaleDateString('en-US', options); // Format as "May 7, 2025"
      document.getElementById('reportDate').textContent = `Date: ${formattedDate}`;
  }


  function addEntry() {
    // Get values from the form inputs
    const entryType = document.getElementById('entryType').value;
    const product = document.getElementById('product').value;
    const price = parseFloat(document.getElementById('price').value);
    const quantity = parseInt(document.getElementById('quantity').value);

    // Validate inputs
    if (!entryType || !product || isNaN(price) || isNaN(quantity) || price < 0 || quantity <= 0) {
      console.log('Please fill in all fields with valid numbers.');
      // In a real application, you would display a message on the page
      return;
    }

    // Calculate total for the current entry
    const total = price; // Total price is what the user enters now

    // Calculate unit price
    const unitPrice = price / quantity;

    // Add to grand totals based on entry type
    if (entryType === 'Purchase') {
      grandTotalPurchase += total;
    } else if (entryType === 'Sale') {
      grandTotalSale += total;
    }

    // Get the table body
    const tableBody = document.querySelector('#dataTable tbody');

    // Create a new table row
    const newRow = tableBody.insertRow();

    // Create and populate the table cells
    const entryTypeCell = newRow.insertCell();
    entryTypeCell.textContent = entryType;

    const productCell = newRow.insertCell();
    productCell.textContent = product;

    const priceCell = newRow.insertCell();
    priceCell.textContent = price.toFixed(2); // Display total price entered

    const quantityCell = newRow.insertCell();
    quantityCell.textContent = quantity;

    const unitPriceCell = newRow.insertCell(); // Cell for Unit Price
    unitPriceCell.textContent = unitPrice.toFixed(2); // Display calculated unit price

    const totalCell = newRow.insertCell();
    totalCell.textContent = total.toFixed(2); // Display total price entered again (or could be removed if Unit Price is sufficient)

    // Update the day end report display
    updateDayEndReportDisplay();

    // Clear the form inputs after adding entry
    clearForm();
  }

  // Function to clear the form inputs
  function clearForm() {
    document.getElementById('price').value = '';
    document.getElementById('quantity').value = '';
    document.getElementById('product').selectedIndex = 0;
    document.getElementById('entryType').selectedIndex = 0; // Reset entry type to Sale
  }

  // Function to handle cancel button click
  function cancelEntry() {
      clearForm(); // Simply clear the form inputs
  }

  // Function to update the day end report display
  function updateDayEndReportDisplay() {
    const totalPurchaseDisplay = document.getElementById('totalPurchaseDisplay');
    const totalSaleDisplay = document.getElementById('totalSaleDisplay');
    const profitLossDisplay = document.getElementById('profitLossDisplay');

    // Calculate profit/loss
    const profitLoss = grandTotalSale - grandTotalPurchase;

    // Update the display elements
    totalPurchaseDisplay.textContent = grandTotalPurchase.toFixed(2);
    totalSaleDisplay.textContent = grandTotalSale.toFixed(2);

    // Update profit/loss display and apply styling
    profitLossDisplay.textContent = profitLoss.toFixed(2);
    profitLossDisplay.classList.remove('profit', 'loss'); // Remove previous classes
    if (profitLoss > 0) {
      profitLossDisplay.classList.add('profit');
    } else if (profitLoss < 0) {
      profitLossDisplay.classList.add('loss');
    }
  }

  // Function to share day end summary via WhatsApp
  function shareViaWhatsApp() {
      const reportDate = document.getElementById('reportDate').textContent; // Get the date
      const totalPurchase = document.getElementById('totalPurchaseDisplay').textContent;
      const totalSale = document.getElementById('totalSaleDisplay').textContent;
      const profitLoss = document.getElementById('profitLossDisplay').textContent;

      const message = `*K-CAFE Day End Report*\n${reportDate}\n\nTotal Purchase: ${totalPurchase}\nTotal Sale: ${totalSale}\nProfit/Loss: ${profitLoss}`;

      // Replace 03442128439 with the actual number if needed, including country code without '+'
      const phoneNumber = '923442128439'; // Assuming Pakistan's country code +92

      // Construct the WhatsApp URL
      const whatsappUrl = `https://wa.me/${phoneNumber}?text=${encodeURIComponent(message)}`;

      // Open WhatsApp in a new tab/window
      window.open(whatsappUrl, '_blank');

      // Hide instructions after attempting to share
      document.getElementById('shareInstructions').style.display = 'none';
  }


  // Initialize the day end report display and date on page load
  document.addEventListener('DOMContentLoaded', () => {
      displayCurrentDate();
      updateDayEndReportDisplay();
  });

</script>

</body>
</html>
