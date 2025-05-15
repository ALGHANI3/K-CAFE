<!DOCTYPE html>
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
      padding: 10px; /* Reduced padding for mobile */
      line-height: 1.6;
      color: #333;
    }
    .header-container {
        display: flex;
        flex-direction: column; /* Stack elements vertically on small screens */
        align-items: center;
        margin-bottom: 20px;
        text-align: center; /* Center text in the header */
    }
    h2 {
      text-align: center;
      color: #333;
      margin: 0 0 10px 0; /* Adjusted margin */
      text-shadow: 1px 1px 2px rgba(255,255,255,0.7);
      flex-grow: 1;
      width: 100%; /* Full width on small screens */
    }
    #reportDate {
        font-size: 1em; /* Slightly smaller font for mobile */
        color: #555;
        text-align: center; /* Center date on small screens */
        width: 100%; /* Full width on small screens */
    }
    form {
      background: rgba(255, 255, 255, 0.9);
      padding: 15px; /* Reduced padding for mobile */
      border-radius: 8px;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
      margin-bottom: 20px;
    }
    label {
      display: block;
      margin-bottom: 5px;
      font-weight: bold;
    }
    select, input[type="number"], input[type="text"], input[type="password"] { /* Added password input */
      padding: 10px;
      margin-bottom: 15px;
      font-size: 16px;
      width: 100%; /* Make inputs full width */
      border: 1px solid #ccc;
      border-radius: 4px;
      box-sizing: border-box;
    }
     .inventory-item {
        display: flex;
        flex-direction: column; /* Stack inventory item inputs vertically */
        margin-bottom: 10px;
        border: 1px solid #eee; /* Add border for clarity */
        padding: 10px;
        border-radius: 4px;
    }
    .inventory-item input[type="text"] {
        margin-right: 0; /* Remove right margin */
        margin-bottom: 10px; /* Add bottom margin */
        width: 100%; /* Full width */
    }
     .inventory-item input[type="number"] {
        width: 100%; /* Full width */
        margin-bottom: 10px; /* Add bottom margin */
    }
    .inventory-item input[type="number"].unit-cost {
        width: 100%; /* Full width */
        margin-left: 0; /* Remove left margin */
        margin-bottom: 0; /* Remove bottom margin */
    }

    button.btn {
      display: block;
      width: 100%;
      padding: 12px;
      margin-top: 10px;
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
        padding: 5px 10px;
        font-size: 14px;
        width: auto;
        margin: 0;
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
        padding: 4px 8px;
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
      overflow-x: auto; /* Add horizontal scroll for table on small screens */
      display: block; /* Make table a block element for scrolling */
      white-space: nowrap; /* Prevent text wrapping in table cells */
    }
     table th, table td {
        white-space: nowrap; /* Ensure nowrap for table cells */
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
    /* Removed initialInventoryForm styles */

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
        flex-wrap: wrap; /* Allow list items to wrap */
    }
     #currentInventoryList li span {
         flex-grow: 1;
         margin-right: 10px; /* Add some space */
         word-break: break-word; /* Break long words */
     }
     #currentInventoryList li button {
         flex-shrink: 0; /* Prevent button from shrinking */
     }
    #emptyInventoryMessage { /* Style for empty inventory message */
        text-align: center;
        color: #777;
        font-style: italic;
        margin-top: 10px;
    }


     /* Login Form Styles */
     #loginForm {
        background: rgba(255, 255, 255, 0.9);
        padding: 20px;
        border-radius: 8px;
        box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        max-width: 400px; /* Limit width of login form */
        margin: 50px auto; /* Center the login form */
        text-align: center;
     }
     #loginForm input[type="text"], #loginForm input[type="password"] {
         margin-bottom: 15px;
     }
     #loginForm button {
         width: auto; /* Adjust button width */
         padding: 10px 20px;
     }
     #loginError {
         color: red;
         margin-top: 10px;
         font-weight: bold;
     }
     #forgotPasswordLink {
        display: block; /* Make it a block element */
        margin-top: 10px;
        font-size: 0.9em;
        color: #007BFF;
        cursor: pointer;
        text-decoration: underline;
     }
     #forgotPasswordLink:hover {
         color: #0056b3;
     }
     #passwordDisplay {
         margin-top: 15px;
         font-weight: bold;
         color: green;
         /* display: none; /* Hidden by default */ /* Keep visible to show the link */
     }


     /* Hide report content by default */
     #reportContentWrapper {
         display: none;
     }

  </style>
</head>
<body>

<div class="header-container">
    <h2>K-CAFE - Daily Purchase & Sale Tracker</h2>
    <div id="reportDate"></div> </div>

<div id="loginForm">
    <h3>Login to Access Report</h3>
    <label for="userId">User ID:</label>
    <input type="text" id="userId" placeholder="Enter User ID">

    <label for="password">Password:</label>
    <input type="password" id="password" placeholder="Enter Password">

    <button class="btn btn-primary" onclick="login()">Login</button>
    <div id="loginError" style="display: none;">Invalid User ID or Password.</div>
    <span id="forgotPasswordLink" onclick="sendPasswordViaWhatsApp()">Forgot Password?</span> <div id="passwordDisplay" style="display: none;"></div> </div>


<div id="reportContentWrapper">

    <div id="pdfContent">
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

             <div id="addCurrentInventoryItemForm">
                <h4>Add/Update Product in Inventory</h4> <div class="inventory-item">
                    <input type="text" id="newInventoryProductName" class="inventory-product-name" placeholder="Product Name">
                    <input type="number" id="newInventoryQuantity" class="inventory-quantity" placeholder="Quantity" min="0" value="0">
                     <input type="number" id="newInventoryUnitCost" class="unit-cost" placeholder="Unit Cost" min="0" value="0">
                </div>
                <button class="btn btn-add-inventory" onclick="addNewInventoryItem()">Add/Update Product</button> <p style="font-size: 0.9em; color: #777; margin-top: 10px;">Enter name, quantity, and unit cost to add a new product or update an existing one.</p>
            </div>


            <div id="currentInventory">
                <h4>Current Inventory Balance</h4>
                <ul id="currentInventoryList">
                     <li id="emptyInventoryMessage">No inventory items added yet. Use the section above to add products.</li>
                </ul>
            </div>

            <button class="btn btn-primary" onclick="saveAllInventoryChanges()">Save All Inventory Changes</button> <p style="font-size: 0.9em; color: #777; margin-top: 10px;">Click this button to save all changes made in the Inventory Tracking section.</p>

        </div>
    </div>


    <div style="margin-top: 30px; padding: 20px; background: rgba(255, 255, 255, 0.9); border-radius: 8px; box-shadow: 0 2px 4px rgba(0,0,0,0.1);">
        <h3 style="text-align: center; color: #333; margin-bottom: 15px;">Generate & Share Report</h3>
        <p style="font-size: 0.9em; color: #777; margin-bottom: 15px;">
            یہ بٹن موجودہ سیشن کی خرید و فروخت کی اینٹریز اور سمری کا PDF تیار کرے گا۔ براہ کرم یقینی بنائیں کہ آپ نے تمام اینٹریز شامل کر لی ہیں۔
        </p>
        <button class="btn" id="shareBtn" onclick="generateReportPdf()">Generate PDF Report</button>
        <div id="shareInstructions" style="margin-top: 15px;">
            <h4>رپورٹ شیئر کرنے کا طریقہ:</h4>
            <p>جب PDF فائل ڈاؤن لوڈ ہو جائے، تو اسے اپنی ڈیوائس کے فائل مینیجر سے تلاش کریں اور WhatsApp یا کسی اور ایپ پر شیئر کریں۔</p>
        </div>
    </div>


</div> <script>
  // Global variables to store total purchase and sale
  let grandTotalPurchase = 0; // Total cost of goods purchased
  let grandTotalSale = 0; // Total revenue from sales
  let grandTotalSaleCost = 0; // Total cost of goods sold

  // Object to store current inventory (will be loaded from localStorage)
  // Structure: { 'productName': { quantity: X, unitCost: Y } }
  let currentInventory = {};

  // Array to store all product names ever added to inventory (for dropdown)
  let allProductsAdded = [];

  // --- Basic Authentication ---
  const CORRECT_USER_ID = "admin";
  const CORRECT_PASSWORD = "admin";
  const WHATSAPP_PHONE_NUMBER = "923442128439"; // User's WhatsApp number

  // WARNING: This is client-side and not secure for sensitive data.

  function login() {
      const userIdInput = document.getElementById('userId').value;
      const passwordInput = document.getElementById('password').value;
      const loginErrorDiv = document.getElementById('loginError');
      const loginFormDiv = document.getElementById('loginForm');
      const reportContentWrapperDiv = document.getElementById('reportContentWrapper');

      if (userIdInput === CORRECT_USER_ID && passwordInput === CORRECT_PASSWORD) {
          loginFormDiv.style.display = 'none'; // Hide login form
          reportContentWrapperDiv.style.display = 'block'; // Show report content
          loginErrorDiv.style.display = 'none'; // Hide error message

          // Initialize report data after successful login
          displayCurrentDate();
          loadInventory(); // Load inventory and all products on page load
          updateDayEndReportDisplay();

      } else {
          loginErrorDiv.style.display = 'block'; // Show error message
          console.log("Login failed: Invalid User ID or Password.");
      }
  }

  // Function to send password via WhatsApp
  function sendPasswordViaWhatsApp() {
      const message = `Your K-CAFE Daily Report Password is: ${CORRECT_PASSWORD}`;
      const whatsappUrl = `https://wa.me/${WHATSAPP_PHONE_NUMBER}?text=${encodeURIComponent(message)}`;

      // Open WhatsApp in a new tab/window
      window.open(whatsappUrl, '_blank');

      // Optionally show a message on the page indicating WhatsApp is opening
      const passwordDisplayDiv = document.getElementById('passwordDisplay');
      passwordDisplayDiv.textContent = `Opening WhatsApp to send your password...`;
      passwordDisplayDiv.style.display = 'block';
       // Hide the message after a few seconds
       setTimeout(() => {
           passwordDisplayDiv.style.display = 'none';
       }, 5000); // Hide after 5 seconds
  }


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
          try {
              currentInventory = JSON.parse(savedInventory);
               console.log("Loaded currentInventory from localStorage:", currentInventory); // Log loaded inventory
          } catch (e) {
              console.error("Error parsing currentInventory from localStorage:", e);
              currentInventory = {}; // Initialize as empty if parsing fails
          }
      } else {
          currentInventory = {};
           console.log("No inventory found in localStorage. Initializing empty currentInventory.");
      }

      const savedProducts = localStorage.getItem('kcafeAllProducts');
      if (savedProducts) {
          try {
              allProductsAdded = JSON.parse(savedProducts);
               console.log("Loaded allProductsAdded from localStorage:", allProductsAdded); // Log loaded products
          } catch (e) {
               console.error("Error parsing allProductsAdded from localStorage:", e);
               allProductsAdded = []; // Initialize as empty if parsing fails
          }
      } else {
          allProductsAdded = [];
           console.log("No product list found in localStorage. Initializing empty allProductsAdded.");
      }

      displayCurrentInventory();
      updateProductDropdown(); // Update the product dropdown on load
  }

  // Save inventory and all products to localStorage
  function saveInventory() {
      try {
          localStorage.setItem('kcafeInventory', JSON.stringify(currentInventory));
          localStorage.setItem('kcafeAllProducts', JSON.stringify(allProductsAdded));
           console.log("Inventory and product list saved to localStorage."); // Log save action
      } catch (e) {
           console.error("Error saving to localStorage:", e);
            // Optionally display a message to the user that saving failed
      }
  }

  // Display current inventory
  function displayCurrentInventory() {
      const inventoryList = document.getElementById('currentInventoryList');
      inventoryList.innerHTML = ''; // Clear previous display

      const sortedProducts = Object.keys(currentInventory).sort();

      if (sortedProducts.length === 0) {
          // Display message if inventory is empty
          const emptyMessageItem = document.createElement('li');
          emptyMessageItem.id = 'emptyInventoryMessage';
          emptyMessageItem.textContent = 'No inventory items added yet. Use the section above to add products.';
          inventoryList.appendChild(emptyMessageItem);
      } else {
          // Display inventory items if not empty
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

        // Log the array content to console for debugging
        console.log("allProductsAdded array content for dropdown:", sortedAllProducts);


        sortedAllProducts.forEach(productName => {
            const option = document.createElement('option');
            option.value = productName;
            option.textContent = productName;
            productSelect.appendChild(option);
        });
    }


  // Add a field to the initial inventory form (This function is now less relevant but kept for potential future use or if user changes mind)
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

  // Process data from the initial inventory form (This function is now less relevant but kept)
  function processInitialInventoryForm() {
      const initialInventoryInputsDiv = document.getElementById('initialInventoryInputs');
      const items = initialInventoryInputsDiv.querySelectorAll('.inventory-item');

      items.forEach(item => {
          const productNameInput = item.querySelector('.inventory-product-name');
          const quantityInput = item.querySelector('.inventory-quantity');
          const unitCostInput = item.querySelector('.unit-cost');

          const productName = productNameInput.value.trim();
          const quantity = parseInt(quantityInput.value);
          const unitCost = parseFloat(unitCostInput.value);

          if (productName && !isNaN(quantity) && quantity >= 0 && !isNaN(unitCost) && unitCost >= 0) {
              currentInventory[productName] = { quantity: quantity, unitCost: unitCost };
              if (!allProductsAdded.includes(productName)) {
                  allProductsAdded.push(productName);
              }
          } else if (productName) { // Log warning if product name is entered but other fields are invalid
               console.log(`Warning: Invalid input for initial inventory product "${productName}". Please check quantity and unit cost.`);
          }
      });

      // Clear the initial inventory form fields after processing
      initialInventoryInputsDiv.innerHTML = '';
  }

  // Process data from the single inventory item form (does NOT save to localStorage)
  function processNewInventoryItemForm() {
      const productNameInput = document.getElementById('newInventoryProductName');
      const quantityInput = document.getElementById('newInventoryQuantity');
      const unitCostInput = document.getElementById('newInventoryUnitCost');

      const productName = productNameInput.value.trim();
      const quantity = parseInt(quantityInput.value);
      const unitCost = parseFloat(unitCostInput.value);

      if (productName && !isNaN(quantity) && quantity >= 0 && !isNaN(unitCost) && unitCost >= 0) {
          currentInventory[productName] = { quantity: quantity, unitCost: unitCost };
          if (!allProductsAdded.includes(productName)) {
              allProductsAdded.push(productName); // Add product name to allProductsAdded array
              console.log(`Added "${productName}" to allProductsAdded.`); // Log when product is added to array
          } else {
               console.log(`Product "${productName}" already in allProductsAdded.`); // Log if product is already in array
          }
          // Clear the input fields
          productNameInput.value = '';
          quantityInput.value = '0';
          unitCostInput.value = '0';
      } else if (productName) { // Log warning if product name is entered but other fields are invalid
           console.log(`Warning: Invalid input for single inventory product "${productName}". Please check quantity and unit cost.`);
      }
  }

  // Save all inventory changes (processes forms and saves to localStorage)
  function saveAllInventoryChanges() {
      console.log("Save All Inventory Changes button clicked."); // Log button click
      // processInitialInventoryForm(); // No longer needed as initial form is removed
      processNewInventoryItemForm(); // Process single inventory item form data

      saveInventory(); // Save the combined inventory to localStorage
      displayCurrentInventory(); // Update the displayed inventory list
      updateProductDropdown(); // Update the product dropdown

      console.log('Inventory changes saved!'); // Optional confirmation message
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
      // Target the new container div that includes report content and inventory
      const element = document.getElementById('pdfContent');
      const tableBody = document.querySelector('#dataTable tbody');
      const rowCount = tableBody.rows.length;
      console.log(`Attempting to generate PDF from #pdfContent. Rows in table: ${rowCount}`); // Log row count


      // Options for html2pdf - adjust as needed for layout
      const pdfOptions = {
          margin: 10,
          filename: 'K-CAFE_Daily_Report.pdf',
          image: { type: 'jpeg', quality: 0.98 },
          html2canvas: { scale: 2 },
          jsPDF: { unit: 'mm', format: 'a4', orientation: 'portrait' }
      };

      // Add a brief delay to ensure all content is rendered before PDF generation
      setTimeout(() => {
          console.log("Generating PDF after delay..."); // Log before generation
          html2pdf().from(element).set(pdfOptions).save().then(() => {
               console.log("PDF generation complete."); // Log after generation
               // Optionally show instructions after PDF generation
               document.getElementById('shareInstructions').style.display = 'block';
          }).catch(error => {
              console.error("Error generating PDF:", error); // Log any errors
              // Optionally display an error message to the user
          });
      }, 1000); // Increased delay to 1000ms (1 second)


  }


  // Initialize the day end report display, date, and load inventory on page load
  // Initial load happens AFTER successful login
  // document.addEventListener('DOMContentLoaded', () => {
  //     displayCurrentDate();
  //     loadInventory(); // Load inventory and all products on page load
  //     updateDayEndReportDisplay();
  // });

</script>

<script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>

</body>
</html>
