# carpetero-database-design
Database design for Carpetero's inventory

## Tables

### Carpets
table for carpet items/product
```
- id
- name
- description
- carpet_type_id (foreign key from Carpet_types table)
```

### Carpet_types
table for carpet types like wool, nylon, etc
```
- id
- name
- description
```

### Inventory
table that serves as the storage of the item stocks
```
- id
- carpet_id (foreign key from Carpets table)
- width (subject to change based on delivery)
- height (subject to change based on delivery)
- timestamp
```

### Inventory_transaction
table that serves as the audit trail for the inventory whenever there is a delivery
```
- id 
- inventory_id (foreign key from Inventory table)
- previous_width (previous width before deduction)
- previous_height (previous height before deduction)
- height (actual height to be deducted on the inventory)
- width (actual width to be deducted on the inventory)
- timestamp
```

---------------------------------------------------

#### Note: 
```
- I didn't include Order, Customer, and other possible tables that can be included in creating the whole system. I only focus on tracking Carpeteros inventory.
- I just use width and height regardless of how many batches or roll per stock, if there are 3 rolls for that restock the width and height will have 300m value apiece.
- I assume that all records from Carpet table is totally different from each other so it will not be a problem selecting which roll of the carpet to cut from, it is cut by stocks (inventory)
```
