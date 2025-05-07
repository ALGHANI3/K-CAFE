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
    .header-container {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }
    h2 {
      text-align: center;
      color: #333;
      margin: 0; /* Remove default margin */
      text-shadow: 1px 1px 2px rgba(255,255,255,0.7);
      flex-grow: 1; /* Allow heading to take available space */
    }
    #reportDate {
        font-size: 1.1em;
        color: #555;
        text-align: right; /* Align text to the right */
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
    select, input[type="number"], input[type="text"] { /* Added text input for product name in inventory */
      padding: 10px;
      margin-bottom: 15px;
      font-size: 16px;
      width: calc(100% - 22px);
      border: 1px solid #ccc;
      border-radius: 4px;
      box-sizing: border-box;
    }
     .inventory-item {
        display: flex;
        align-items: center;
        margin-bottom: 10px;
    }
    .inventory-item input[type="text"] {
        flex-grow: 1;
        margin-right: 10px;
        margin-bottom: 0; /* Remove bottom margin */
    }
     .inventory-item input[type="number"] {
        width: 80px; /* Smaller width for quantity */
        margin-bottom: 0; /* Remove bottom margin */
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
    button.btn-remove { /* Style for remove button */
        background-color: #dc3545; /* Red color for remove */
        color: white;
        padding: 5px 10px; /* Smaller padding for table button */
        font-size: 14px;
        width: auto; /* Auto width for table button */
        margin: 0; /* Remove margin */
    }
    button.btn-remove:hover {
        background-color: #c82333;
    }
     button.btn-add-inventory {
        background-color: #28a745; /* Green color for add inventory */
        color: white;
        padding: 8px 15px;
        font-size: 16px;
        width: auto;
        margin-top: 10px;
    }
     button.btn-add-inventory:hover {
        background-color: #218838;
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
    #inventorySection {
        margin-top: 30px;
        padding: 20px;
        background: rgba(255, 255, 255, 0.9);
        border-radius: 8px;
        box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    }
    #inventorySection h3 {
        text-align: center;
        color: #333;
        margin-bottom: 15px;
    }
    #initialInventoryForm {
        margin-bottom: 20px;
        padding-bottom: 15px;
        border-bottom: 1px solid #ccc;
    }
    #currentInventory {
        margin-top: 15px;
    }
    #currentInventory p {
        margin-bottom: 8px;
        font-size: 16px;
    }
  </style>
</head>
<body>

<div class="header-container">
    <h2>K-CAFE - Daily Purchase & Sale Tracker</h2>
    <div id="reportDate"></div> </div>


<form id="entryForm">
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
    <option value="Can">Can</option>
    <option value="Juice">Juice</option> </select>

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
      <th>Remove</th> </tr>
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

<div id="inventorySection">
    <h3>Inventory Tracking</h3>

    <div id="initialInventoryForm">
        <h4>Set Initial Inventory (Will be saved in your browser)</h4>
        <div id="initialInventoryInputs">
            </div>
        <button class="btn btn-add-inventory" onclick="addInitialInventoryField()">Add Product to Inventory</button>
        <button class="btn btn-primary" onclick="saveInitialInventory()">Save Initial Inventory</button>
    </div>

    <div id="currentInventory">
        <h4>Current Inventory Balance</h4>
        <div id="currentInventoryDisplay">
            </div>
    </div>
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

  // Object to store current inventory (will be loaded from localStorage)
  let currentInventory = {};

  // Function to display the current date
  function displayCurrentDate() {
      const today = new Date();
      const options = { year: 'numeric', month: 'long', day: 'numeric' };
      const formattedDate = today.toLocaleDateString('en-US', options); // Format as "May 7, 2025"
      document.getElementById('reportDate').textContent = `Date: ${formattedDate}`;
  }

  // --- Inventory Functions ---

  // Load inventory from localStorage
  function loadInventory() {
      const savedInventory = localStorage.getItem('kcafeInventory');
      if (savedInventory) {
          currentInventory = JSON.parse(savedInventory);
      } else {
          // Initialize with default products if no saved inventory
          const products = document.querySelectorAll('#product option');
          products.forEach(option => {
              if (option.value !== "") {
                  currentInventory[option.value] = 0; // Start with 0 for all products
              }
          });
      }
      displayCurrentInventory();
  }

  // Save inventory to localStorage
  function saveInventory() {
      localStorage.setItem('kcafeInventory', JSON.stringify(currentInventory));
  }

  // Display current inventory
  function displayCurrentInventory() {
      const inventoryDisplayDiv = document.getElementById('currentInventoryDisplay');
      inventoryDisplayDiv.innerHTML = ''; // Clear previous display

      for (const product in currentInventory) {
          const p = document.createElement('p');
          p.textContent = `${product}: ${currentInventory[product]}`;
          inventoryDisplayDiv.appendChild(p);
      }
  }

  // Add a field to the initial inventory form
  function addInitialInventoryField() {
      const initialInventoryInputsDiv = document.getElementById('initialInventoryInputs');

      const itemDiv = document.createElement('div');
      itemDiv.classList.add('inventory-item');

      const productInput = document.createElement('input');
      productInput.type = 'text';
      productInput.placeholder = 'Product Name';

      const quantityInput = document.createElement('input');
      quantityInput.type = 'number';
      quantityInput.placeholder = 'Quantity';
      quantityInput.min = '0';
      quantityInput.value = '0';

      itemDiv.appendChild(productInput);
      itemDiv.appendChild(quantityInput);
      initialInventoryInputsDiv.appendChild(itemDiv);
  }

  // Save initial inventory from the form
  function saveInitialInventory() {
      const initialInventoryInputsDiv = document.getElementById('initialInventoryInputs');
      const items = initialInventoryInputsDiv.querySelectorAll('.inventory-item');

      items.forEach(item => {
          const productName = item.querySelector('input[type="text"]').value.trim();
          const quantity = parseInt(item.querySelector('input[type="number"]').value);

          if (productName && !isNaN(quantity) && quantity >= 0) {
              currentInventory[productName] = quantity;
          }
      });

      saveInventory(); // Save to localStorage
      displayCurrentInventory(); // Update display
      // Optionally clear the initial inventory form fields
      initialInventoryInputsDiv.innerHTML = '';
  }


  // --- Entry Functions ---

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

    // Update inventory based on entry type
    if (currentInventory.hasOwnProperty(product)) { // Check if product exists in inventory
        if (entryType === 'Purchase') {
            currentInventory[product] += quantity;
        } else if (entryType === 'Sale') {
            currentInventory[product] -= quantity;
            // Optional: Add a check here to prevent selling more than available
            if (currentInventory[product] < 0) {
                console.log(`Warning: Selling more ${product} than available!`);
                // You might want to revert the inventory change or show a message to the user
                // For this example, we'll allow negative inventory for simplicity
            }
        }
        saveInventory(); // Save updated inventory
        displayCurrentInventory(); // Update inventory display
    } else {
        console.log(`Product "${product}" not found in inventory.`);
        // You might want to add the product to inventory with the entered quantity
        // For this example, we'll just log a message
    }


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

    // Store entry data in the row itself for easy access when removing
    newRow.dataset.entryType = entryType;
    newRow.dataset.total = total;
    newRow.dataset.product = product; // Store product name
    newRow.dataset.quantity = quantity; // Store quantity


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

    // Add remove button cell
    const removeCell = newRow.insertCell();
    const removeButton = document.createElement('button');
    removeButton.textContent = 'Remove';
    removeButton.classList.add('btn', 'btn-remove');
    removeButton.onclick = function() {
        removeEntry(newRow); // Pass the row element to the remove function
    };
    removeCell.appendChild(removeButton);


    // Update the day end report display
    updateDayEndReportDisplay();

    // Clear the form inputs after adding entry
    clearForm();
  }

  // Function to remove an entry
  function removeEntry(rowElement) {
      // Get the stored data from the row
      const entryType = rowElement.dataset.entryType;
      const total = parseFloat(rowElement.dataset.total);
      const product = rowElement.dataset.product; // Get product name
      const quantity = parseInt(rowElement.dataset.quantity); // Get quantity


      // Subtract the total from the grand total based on entry type
      if (entryType === 'Purchase') {
          grandTotalPurchase -= total;
          // Revert inventory change
          if (currentInventory.hasOwnProperty(product)) {
              currentInventory[product] -= quantity;
          }
      } else if (entryType === 'Sale') {
          grandTotalSale -= total;
           // Revert inventory change
           if (currentInventory.hasOwnProperty(product)) {
              currentInventory[product] += quantity;
           }
      }

      // Remove the row from the table
      rowElement.remove();

      // Update the day end report display and inventory display
      updateDayEndReportDisplay();
      saveInventory(); // Save updated inventory
      displayCurrentInventory(); // Update inventory display

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

      // Include current inventory in the message
      let inventorySummary = "\n*Current Inventory:*";
      for (const product in currentInventory) {
          inventorySummary += `\n${product}: ${currentInventory[product]}`;
      }


      const message = `*K-CAFE Day End Report*\n${reportDate}\n\nTotal Purchase: ${totalPurchase}\nTotal Sale: ${totalSale}\nProfit/Loss: ${profitLoss}${inventorySummary}`;

      // Replace 03442128439 with the actual number if needed, including country code without '+'
      const phoneNumber = '923442128439'; // Assuming Pakistan's country code +92

      // Construct the WhatsApp URL
      const whatsappUrl = `https://wa.me/${phoneNumber}?text=${encodeURIComponent(message)}`;

      // Open WhatsApp in a new tab/window
      window.open(whatsappUrl, '_blank');

      // Hide instructions after attempting to share
      document.getElementById('shareInstructions').style.display = 'none';
  }


  // Initialize the day end report display, date, and load inventory on page load
  document.addEventListener('DOMContentLoaded', () => {
      displayCurrentDate();
      loadInventory(); // Load inventory on page load
      updateDayEndReportDisplay();
  });

</script>

</body>
</html>
