
# Construction Accounting

I’ve got a raw list of expense items from your Excel sheet. To make this usable in **construction accounting**, we need to **normalize, deduplicate, and categorize** them into meaningful groups that can tie directly into your chart of accounts and project/job costing.

---

## 🧾 Normalized Expense Item List

### 🏗 Construction Materials & Supplies
- Cement  
- Sand / Sand & Brick  
- Bamboo  
- Brick Breaking  
- Rod  
- G I Wire  
- Cable  
- Pipe  
- Polythene  
- Glass  
- Paint  
- Tin  
- Cutting Disk  
- Tools  
- Safety Accessories (Safety Acce.)  
- Sanitary Accessories (Sanitary Acce.)  
- Shuttering Accessories (Shutering Acce.)  
- Construction Accessories (Con. Acce.)  
- Welding Accessories (Welding Acce.)  
- M S Plate  
- M S Shahed Iron  
- Materials (general)  

### 👷 Labour & Site Costs
- Daily Labour  
- Labour Shed  
- Loading/Unloading  
- Site Allowance  
- Over Time  
- Salary  
- Worker Welfare (Khoraki, Lunch, Dinner, Snacks, Break Fast, Cooking, Cookaries)  

### 🚚 Transport & Fuel
- Conveyance  
- Truck Fair  
- Van Fair  
- Octane  
- Diesel  
- Mobil (fuel/oil)  
- Alom CNG Driver  

### 🏢 Administrative & Overheads
- Bank  
- Bill  
- Office  
- House Rent  
- Mobile Bill  
- B-kash Charge (financial fees)  
- Entertainment  
- Furniture  
- Stationary  
- Grossary (Groceries)  

### 🩺 Health & Safety
- First Aid  
- Medicine  

### 👤 Named Parties / Vendors (likely payees or suppliers)
- Advance (cash advances)  
- Altef  
- Erector Jahid  
- Gazi Enterp.  
- Johirul Stone  
- Liton  
- MD Sir  
- Mizan  
- Moni Ent.  
- Rubel  
- Shohidul  
- Sohel  
- Stone Oahid  
- Tuhin RFL  
- Vashani  

---

## 📊 How to Connect with Construction Accounting

1. **Map Each Item to a Ledger Account**  
   - Example: *Cement → Construction Materials Expense*, *Labour Shed → Site Facilities Expense*, *Diesel → Fuel Expense*, *Lunch/Snacks → Worker Welfare Expense*.  
   - Vendors (e.g., *Liton, Vashani*) should be linked to **Accounts Payable** or **Supplier Ledger**.

2. **Tie to Project/Job Codes**  
   - Every voucher should carry a `project_id` (from your `doc_keeper` schema).  
   - This ensures costs are allocated to the correct construction project.

3. **Record in Workflow**  
   - **Voucher metadata** → `doc_keeper`  
   - **Itemized expense** → `transaction_record`  
   - **Ledger posting** → `ledger_transaction` (Debit expense, Credit cash/bank/AP)

4. **Reporting**  
   - Group by category (Materials, Labour, Fuel, Overheads).  
   - Compare actual vs budget per project.  
   - Track supplier/vendor balances.

---

✅ This cleaned list is now ready to be **mapped into your chart of accounts** and linked to your construction accounting schema.  

1. map each item to an accounting category

---

GAAP-compliant

**Chart of Accounts (CoA)** tailored for your construction business, using the expense items above. I’ll normalize them, group them into categories, and map each to a **ledger account** so they can flow into your `ledger_transaction` table.

---

## 🧾 Construction Chart of Accounts (Expense Mapping)

### 🏗 Direct Construction Costs (Job Costs)
| Expense Item        | Ledger Account Name             | Account Type |
|---------------------|---------------------------------|--------------|
| Cement              | Construction Materials Expense  | Direct Cost  |
| Sand / Sand & Brick | Construction Materials Expense  | Direct Cost  |
| Brick Breaking      | Site Preparation Expense        | Direct Cost  |
| Bamboo              | Structural Materials Expense    | Direct Cost  |
| Rod                 | Reinforcement Materials Expense | Direct Cost  |
| G I Wire            | Electrical/Structural Materials | Direct Cost  |
| Cable               | Electrical Supplies Expense     | Direct Cost  |
| Pipe                | Plumbing Supplies Expense       | Direct Cost  |
| Polythene           | Consumables Expense             | Direct Cost  |
| Cutting Disk        | Tools & Consumables Expense     | Direct Cost  |
| Tools               | Tools & Equipment Expense       | Direct Cost  |
| Machine             | Equipment Expense               | Direct Cost  |
| Welding Accessories | Welding Supplies Expense        | Direct Cost  |
| Shuttering Accessories | Formwork Expense             | Direct Cost  |
| Construction Accessories | General Construction Expense | Direct Cost |
| Safety Accessories  | Safety Equipment Expense        | Direct Cost  |
| Sanitary Accessories | Sanitary Materials Expense     | Direct Cost  |
| M S Plate / M S Shahed Iron | Steel Materials Expense | Direct Cost  |
| Materials (general) | General Materials Expense       | Direct Cost  |

---

### 👷 Labour & Site Costs
| Expense Item        | Ledger Account Name             | Account Type |
|---------------------|---------------------------------|--------------|
| Daily Labour        | Direct Labour Expense           | Direct Cost  |
| Labour Shed         | Site Facilities Expense         | Direct Cost  |
| Loading/Unloading   | Handling & Logistics Expense    | Direct Cost  |
| Site Allowance      | Worker Allowance Expense        | Indirect Cost|
| Over Time           | Overtime Labour Expense         | Direct Cost  |
| Salary              | Salaries & Wages Expense        | Direct Cost  |
| Khoraki (food)      | Worker Welfare Expense          | Indirect Cost|
| Lunch / Dinner / Snacks / Break Fast | Meals & Welfare Expense | Indirect Cost |
| Cooking / Cookaries | Catering Expense                | Indirect Cost|

---

### 🚚 Transport & Fuel
| Expense Item        | Ledger Account Name             | Account Type |
|---------------------|---------------------------------|--------------|
| Conveyance          | Transport Expense               | Indirect Cost|
| Truck Fair          | Transport Expense               | Indirect Cost|
| Van Fair            | Transport Expense               | Indirect Cost|
| Octane              | Fuel Expense                    | Direct Cost  |
| Diesel              | Fuel Expense                    | Direct Cost  |
| Mobil               | Lubricants Expense              | Direct Cost  |
| Alom CNG Driver     | Driver Expense                  | Direct Cost  |

---

### 🏢 Administrative & Overheads
| Expense Item        | Ledger Account Name             | Account Type |
|---------------------|---------------------------------|--------------|
| Bank                | Bank Charges Expense            | Admin Expense|
| Bill                | Miscellaneous Expense           | Admin Expense|
| Office              | Office Expense                  | Admin Expense|
| House Rent          | Rent Expense                    | Admin Expense|
| Mobile Bill         | Communication Expense           | Admin Expense|
| B-kash Charge       | Financial Charges Expense       | Admin Expense|
| Entertainment       | Entertainment Expense           | Admin Expense|
| Furniture           | Office Furniture Expense        | Admin Expense|
| Stationary          | Office Supplies Expense         | Admin Expense|
| Grossary (Groceries)| Consumables Expense             | Admin Expense|

---

### 🩺 Health & Safety
| Expense Item        | Ledger Account Name             | Account Type |
|---------------------|---------------------------------|--------------|
| First Aid           | Health & Safety Expense         | Indirect Cost|
| Medicine            | Medical Supplies Expense        | Indirect Cost|

---

### 👤 Named Parties / Vendors (Payees)
These are **suppliers or individuals** rather than expense categories. They should be mapped to **Accounts Payable / Vendor Ledger**:
- Altef  
- Erector Jahid  
- Gazi Enterp.  
- Johirul Stone  
- Liton  
- MD Sir  
- Mizan  
- Moni Ent.  
- Rubel  
- Shohidul  
- Sohel  
- Stone Oahid  
- Tuhin RFL  
- Vashani  

---

## 📌 How This Connects to Your Schema
- **`doc_keeper`** → stores voucher metadata (`doc_number`, `project_id`, `posting_date`).  
- **`transaction_record`** → records itemized expenses (`item_id`, `quantity`, `rate`, `price`).  
- **`ledger_transaction`** → posts journal entries:  
  - Debit: Expense account (from chart above)  
  - Credit: Cash/Bank/Accounts Payable  
