K-CAFE
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
    select, input[type="number"], input[type="text"] {
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
    .inventory-item input[type="number"].unit-cost { /* Style for unit cost input */
        width: 100px; /* Slightly wider for cost */
        margin-left: 10px;
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
    button.btn-remove { /* Style for remove button in table */
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
     button.btn-add-inventory { /* Style for add inventory button */
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
    button.btn-remove-inventory { /* Style for remove inventory button */
        background-color: #dc3545; /* Red color */
        color: white;
        padding: 4px 8px; /* Smaller padding */
        font-size: 12px;
        margin-left: 10px;
        border-radius: 4px;
        cursor: pointer;
    }
     button.btn-remove-inventory:hover {
        background-color: #c82333;
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
        /* display: none; /* Hidden by default */ /* Keep visible to show instructions */
    }
     #shareInstructions p {
         font-size: 16px; /* Slightly smaller font for instructions */
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
     #addCurrentInventoryItemForm {
        margin-bottom: 20px;
        padding-bottom: 15px;
        border-bottom: 1px solid #ccc;
    }
    #currentInventory {
        margin-top: 15px;
    }
    #currentInventoryList {
        list-style: none;
        padding: 0;
    }
    #currentInventoryList li {
        margin-bottom: 8px;
        font-size: 16px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 5px 0;
        border-bottom: 1px dashed #eee;
    }
    #currentInventoryList li span {
        flex-grow: 1;
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
    </select>

  <label for="price">Total Price:</label>
  <input type="number" id="price" placeholder="Total Price" min="0">

  <label for="quantity">Quantity:</label>
  <input type="number" id="quantity" placeholder="Quantity" min="1">

  <button class="btn btn-primary" type="button" onclick="addEntry()">Add Entry</button>
  <button class="btn btn-secondary" type="button" onclick="cancelEntry()">Cancel</button> </form>

<div id="reportContent">
    <table id="dataTable">
      <thead>
        <tr>
          <th>Entry Type</th>
          <th>Product</th>
          <th>Total Price</th>
          <th>Quantity</th>
          <th>Unit Price</th>
          <th>Total</th>
          <th>Remove</th>
        </tr>
      </thead>
      <tbody>
        </tbody>
    </table>

    <div id="dayEndReport">
      <h3>Day End Summary</h3>
      <p>Total Purchase Cost: <span id="totalPurchaseDisplay">0.00</span></p>
      <p>Total Sale Revenue: <span id="totalSaleDisplay">0.00</span></p>
      <p>Profit/Loss: <span id="profitLossDisplay">0.00</span></p>
    </div>
</div>


<div id="inventorySection">
    <h3>Inventory Tracking</h3>

    <div id="initialInventoryForm">
        <h4>Set Initial Inventory (Use once for initial setup)</h4>
        <div id="initialInventoryInputs">
            </div>
        <button class="btn btn-add-inventory" onclick="addInitialInventoryField()">Add Product to Initial Inventory</button>
        <button class="btn btn-primary" onclick="saveInitialInventory()">Save Initial Inventory</button>
        <p style="font-size: 0.9em; color: #777; margin-top: 10px;">Use this section only for setting up your inventory for the first time or adding multiple items initially. Includes initial quantity and unit cost.</p>
    </div>

     <div id="addCurrentInventoryItemForm">
        <h4>Add/Update Single Product in Inventory</h4>
        <div class="inventory-item">
            <input type="text" id="newInventoryProductName" class="inventory-product-name" placeholder="Product Name">
            <input type="number" id="newInventoryQuantity" class="inventory-quantity" placeholder="Quantity" min="0" value="0">
             <input type="number" id="newInventoryUnitCost" class="unit-cost" placeholder="Unit Cost" min="0" value="0">
        </div>
        <button class="btn btn-add-inventory" onclick="addNewInventoryItem()">Save Product</button>
         <p style="font-size: 0.9em; color: #777; margin-top: 10px;">Enter name, quantity, and unit cost to add a new product or update an existing one, then click "Save Product".</p>
    </div>


    <div id="currentInventory">
        <h4>Current Inventory Balance</h4>
        <ul id="currentInventoryList">
            </ul>
    </div>
</div>


<button class="btn" id="shareBtn" onclick="generateReportPdf()">Generate PDF Report</button> <div id="shareInstructions">
    <h4>رپورٹ شیئر کرنے کا طریقہ:</h4>
    <p>جب PDF فائل ڈاؤن لوڈ ہو جائے، تو اسے اپنی ڈیوائس کے فائل مینیجر سے تلاش کریں اور WhatsApp پر شیئر کریں۔</p>
</div>

<script>
  // Global variables to store total purchase and sale
  let grandTotalPurchase = 0; // Total cost of goods purchased
  let grandTotalSale = 0; // Total revenue from sales
  let grandTotalSaleCost = 0; // Total cost of goods sold

  // Object to store current inventory (will be loaded from localStorage)
  // Structure: { 'productName': { quantity: X, unitCost: Y } }
  let currentInventory = {};

  // Array to store all product names ever added to inventory (for dropdown)
  let allProductsAdded = [];

  // Function to display the current date
  function displayCurrentDate() {
      const today = new Date();
      const options = { year: 'numeric', month: 'long', day: 'numeric' };
      const formattedDate = today.toLocaleDateString('en-US', options); // Format as "May 7, 2025"
      document.getElementById('reportDate').textContent = `Date: ${formattedDate}`;
  }

  // --- Inventory Functions ---

  // Load inventory and all products from localStorage
  function loadInventory() {
      const savedInventory = localStorage.getItem('kcafeInventory');
      if (savedInventory) {
          currentInventory = JSON.parse(savedInventory);
      } else {
          currentInventory = {};
      }

      const savedProducts = localStorage.getItem('kcafeAllProducts');
      if (savedProducts) {
          allProductsAdded = JSON.parse(savedProducts);
      } else {
          allProductsAdded = [];
      }

      displayCurrentInventory();
      updateProductDropdown(); // Update the product dropdown on load
  }

  // Save inventory and all products to localStorage
  function saveInventory() {
      localStorage.setItem('kcafeInventory', JSON.stringify(currentInventory));
      localStorage.setItem('kcafeAllProducts', JSON.stringify(allProductsAdded));
  }

  // Display current inventory
  function displayCurrentInventory() {
      const inventoryList = document.getElementById('currentInventoryList');
      inventoryList.innerHTML = ''; // Clear previous display

      // Sort inventory items alphabetically by product name for consistent display
      const sortedProducts = Object.keys(currentInventory).sort();

      sortedProducts.forEach(productName => {
          const item = currentInventory[productName];
          const listItem = document.createElement('li');
          listItem.innerHTML = `
              <span>${productName}: ${item.quantity} (Cost: ${item.unitCost.toFixed(2)} each)</span>
              <button class="btn-remove-inventory" onclick="removeInventoryItem('${productName}')">Remove</button>
          `;
          inventoryList.appendChild(listItem);
      });
  }

    // Update the product select dropdown based on all products ever added
    function updateProductDropdown() {
        const productSelect = document.getElementById('product');
        productSelect.innerHTML = ''; // Clear existing options

        // Add a default disabled option
        const defaultOption = document.createElement('option');
        defaultOption.value = "";
        defaultOption.textContent = "Select Product";
        defaultOption.disabled = true;
        defaultOption.selected = true;
        productSelect.appendChild(defaultOption);

        // Sort all products alphabetically
        const sortedAllProducts = allProductsAdded.sort();

        sortedAllProducts.forEach(productName => {
            const option = document.createElement('option');
            option.value = productName;
            option.textContent = productName;
            productSelect.appendChild(option);
        });
    }


  // Add a field to the initial inventory form
  function addInitialInventoryField() {
      const initialInventoryInputsDiv = document.getElementById('initialInventoryInputs');

      const itemDiv = document.createElement('div');
      itemDiv.classList.add('inventory-item');

      const productInput = document.createElement('input');
      productInput.type = 'text';
      productInput.classList.add('inventory-product-name');
      productInput.placeholder = 'Product Name';

      const quantityInput = document.createElement('input');
      quantityInput.type = 'number';
      quantityInput.classList.add('inventory-quantity');
      quantityInput.placeholder = 'Quantity';
      quantityInput.min = '0';
      quantityInput.value = '0';

      const unitCostInput = document.createElement('input');
      unitCostInput.type = 'number';
      unitCostInput.classList.add('unit-cost');
      unitCostInput.placeholder = 'Unit Cost';
      unitCostInput.min = '0';
      unitCostInput.value = '0';
      unitCostInput.step = '0.01'; // Allow decimal values for cost


      itemDiv.appendChild(productInput);
      itemDiv.appendChild(quantityInput);
      itemDiv.appendChild(unitCostInput); // Add unit cost input
      initialInventoryInputsDiv.appendChild(itemDiv);
  }

  // Save initial inventory from the form
  function saveInitialInventory() {
      const initialInventoryInputsDiv = document.getElementById('initialInventoryInputs');
      const items = initialInventoryInputsDiv.querySelectorAll('.inventory-item');

      items.forEach(item => {
          const productNameInput = item.querySelector('.inventory-product-name');
          const quantityInput = item.querySelector('.inventory-quantity');
          const unitCostInput = item.querySelector('.unit-cost'); // Get unit cost input

          const productName = productNameInput.value.trim();
          const quantity = parseInt(quantityInput.value);
          const unitCost = parseFloat(unitCostInput.value); // Get unit cost value

          if (productName && !isNaN(quantity) && quantity >= 0 && !isNaN(unitCost) && unitCost >= 0) {
              currentInventory[productName] = { quantity: quantity, unitCost: unitCost }; // Store quantity and unit cost
              // Add product to the list of all products if not already there
              if (!allProductsAdded.includes(productName)) {
                  allProductsAdded.push(productName);
              }
          } else {
               console.log(`Invalid input for ${productName}. Please check name, quantity, and unit cost.`);
          }
      });

      saveInventory(); // Save to localStorage
      displayCurrentInventory(); // Update display
      updateProductDropdown(); // Update product dropdown
      // Optionally clear the initial inventory form fields after saving
      initialInventoryInputsDiv.innerHTML = '';
  }

  // Add or Update a single product in the current inventory
  function addNewInventoryItem() {
      const productNameInput = document.getElementById('newInventoryProductName');
      const quantityInput = document.getElementById('newInventoryQuantity');
      const unitCostInput = document.getElementById('newInventoryUnitCost'); // Get unit cost input

      const productName = productNameInput.value.trim();
      const quantity = parseInt(quantityInput.value);
      const unitCost = parseFloat(unitCostInput.value); // Get unit cost value


      if (productName && !isNaN(quantity) && quantity >= 0 && !isNaN(unitCost) && unitCost >= 0) {
          currentInventory[productName] = { quantity: quantity, unitCost: unitCost }; // Add or update the quantity and unit cost
           // Add product to the list of all products if not already there
          if (!allProductsAdded.includes(productName)) {
              allProductsAdded.push(productName);
          }
          saveInventory(); // Save to localStorage
          displayCurrentInventory(); // Update display
          updateProductDropdown(); // Update product dropdown
          // Clear the input fields
          productNameInput.value = '';
          quantityInput.value = '0';
          unitCostInput.value = '0';
      } else {
          console.log('Please enter a valid product name, quantity, and unit cost.');
      }
  }

  // Remove a product from the inventory (only removes from current inventory, not the dropdown list)
  function removeInventoryItem(productName) {
      if (currentInventory.hasOwnProperty(productName)) {
          delete currentInventory[productName]; // Remove the product from current inventory
          saveInventory(); // Save to localStorage
          displayCurrentInventory(); // Update display (product will disappear from inventory list)
          // Product remains in allProductsAdded and thus in the dropdown
      }
  }


  // --- Entry Functions ---

  function addEntry() {
    // Get values from the form inputs
    const entryType = document.getElementById('entryType').value;
    const product = document.getElementById('product').value;
    const price = parseFloat(document.getElementById('price').value); // This is total price for the entry
    const quantity = parseInt(document.getElementById('quantity').value);

     // Validate product selection
    if (!product) {
        console.log('Please select a product.');
        return;
    }


    // Validate inputs
    if (!entryType || isNaN(price) || price < 0 || isNaN(quantity) || quantity <= 0) {
      console.log('Please fill in all fields with valid numbers.');
      // In a real application, you would display a message on the page
      return;
    }

    // Calculate unit price for display in the table
    const unitPriceDisplay = price / quantity;


    // Update inventory and financial totals based on entry type
    if (currentInventory.hasOwnProperty(product)) { // Check if product exists in inventory
        if (entryType === 'Purchase') {
            currentInventory[product].quantity += quantity; // Add quantity for purchase
            // Optional: Update unit cost based on purchase price (e.g., weighted average)
            // For simplicity here, we'll just add to total purchase cost
            grandTotalPurchase += price; // Add total purchase price to grand total purchase
        } else if (entryType === 'Sale') {
            currentInventory[product].quantity -= quantity; // Subtract quantity for sale
            grandTotalSale += price; // Add total sale price to grand total sale (revenue)

            // Calculate Cost of Goods Sold (COGS) for this sale
             // Ensure unitCost is a number, default to 0 if not available
            const unitCost = currentInventory[product].unitCost ? parseFloat(currentInventory[product].unitCost) : 0;
            const cogs = quantity * unitCost;
            grandTotalSaleCost += cogs; // Add COGS to grand total COGS

            // Optional: Add a check here to prevent selling more than available
            if (currentInventory[product].quantity < 0) {
                console.log(`Warning: Selling more ${product} than available! Current inventory: ${currentInventory[product].quantity}`);
                // You might want to revert the inventory change or show a message to the user
                // For this example, we'll allow negative inventory for simplicity
            }
        }
        saveInventory(); // Save updated inventory
        displayCurrentInventory(); // Update inventory display
    } else {
        console.log(`Error: Product "${product}" not found in inventory. Please add it to inventory first.`);
        // Prevent adding entry if product not in inventory
        return; // Stop adding the entry
    }


    // Get the table body
    const tableBody = document.querySelector('#dataTable tbody');

    // Create a new table row
    const newRow = tableBody.insertRow();

    // Store entry data in the row itself for easy access when removing
    newRow.dataset.entryType = entryType;
    newRow.dataset.total = price; // Store the total price of the entry
    newRow.dataset.product = product; // Store product name
    newRow.dataset.quantity = quantity; // Store quantity
    // Store COGS for Sale entries to revert correctly
    if (entryType === 'Sale') {
        const unitCost = currentInventory[product].unitCost ? parseFloat(currentInventory[product].unitCost) : 0;
        newRow.dataset.cogs = quantity * unitCost;
    } else {
         newRow.dataset.cogs = 0; // COGS is 0 for Purchase entries
    }


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
    unitPriceCell.textContent = unitPriceDisplay.toFixed(2); // Display calculated unit price for the entry

    const totalCell = newRow.insertCell();
    totalCell.textContent = price.toFixed(2); // Display total price entered again


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
      const total = parseFloat(rowElement.dataset.total); // Total price of the entry
      const product = rowElement.dataset.product; // Get product name
      const quantity = parseInt(rowElement.dataset.quantity); // Get quantity
      const cogs = parseFloat(rowElement.dataset.cogs); // Get COGS for Sale entries


      // Revert financial totals based on entry type
      if (entryType === 'Purchase') {
          grandTotalPurchase -= total; // Subtract total purchase price
          // Revert inventory change
          if (currentInventory.hasOwnProperty(product)) {
              currentInventory[product].quantity -= quantity; // Subtract quantity when removing purchase
          }
      } else if (entryType === 'Sale') {
          grandTotalSale -= total; // Subtract total sale price (revenue)
          grandTotalSaleCost -= cogs; // Subtract COGS

           // Revert inventory change
           if (currentInventory.hasOwnProperty(product)) {
              currentInventory[product].quantity += quantity; // Add quantity back when removing sale
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
    const productSelect = document.getElementById('product');
    if (productSelect.options.length > 0) {
        productSelect.selectedIndex = 0; // Reset to the first option (Select Product)
    }
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

    // Calculate profit/loss using Total Sale Revenue and Total Cost of Goods Sold
    const profitLoss = grandTotalSale - grandTotalSaleCost;

    // Update the display elements
    totalPurchaseDisplay.textContent = grandTotalPurchase.toFixed(2); // Display total purchase cost
    totalSaleDisplay.textContent = grandTotalSale.toFixed(2); // Display total sale revenue

    // Update profit/loss display and apply styling
    profitLossDisplay.textContent = profitLoss.toFixed(2);
    profitLossDisplay.classList.remove('profit', 'loss'); // Remove previous classes
    if (profitLoss > 0) {
      profitLossDisplay.classList.add('profit');
    } else if (profitLoss < 0) {
      profitLossDisplay.classList.add('loss');
    }
  }

   // Function to generate PDF report
  function generateReportPdf() {
      const element = document.getElementById('reportContent'); // Element to convert to PDF

      html2pdf().from(element).save('K-CAFE_Daily_Report.pdf');

      // Optionally show instructions after PDF generation
      document.getElementById('shareInstructions').style.display = 'block';
  }


  // Initialize the day end report display, date, and load inventory on page load
  document.addEventListener('DOMContentLoaded', () => {
      displayCurrentDate();
      loadInventory(); // Load inventory and all products on page load
      updateDayEndReportDisplay();
  });

</script>

<script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>

</body>
</html>
