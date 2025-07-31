## Layout File Format

To use a custom floor plan, you need to create a `layout.json` file. This file contains an array of table objects. Each object defines a table's properties, telling the application where to draw it and how to orient it.

### **Structure of a Table Object:**

Each object in the array must have the following keys:

* **`internalId`** (Number): A unique, permanent ID for the table. This is what the app uses to track assignments, so it should never change.
* **`displayId`** (String): The number or name that is displayed on the table in the app. This can be anything you want (e.g., "1", "2", "A1", "Patio 1").
* **`orientation`** (String): Must be either `"vertical"` (for a tall table) or `"horizontal"` (for a wide table).
* **`gridRow`** (Number): The row number on the layout grid where the table should be placed (starting from 0).
* **`gridCol`** (Number): The column number on the layout grid where the table should be placed (starting from 0).
* **`capacity`** (Number, optional): The number of seats at the table. Defaults to 10 if not provided.

### **Example `layout.json` File**

Here is a template based on the final layout we created. You can copy this, save it as `layout.json`, and modify it to create your own floor plans.

```json
[
  { "internalId": 17, "displayId": "1", "orientation": "horizontal", "gridRow": 0, "gridCol": 7 },
  { "internalId": 18, "displayId": "2", "orientation": "horizontal", "gridRow": 1, "gridCol": 7 },
  { "internalId": 19, "displayId": "3", "orientation": "horizontal", "gridRow": 2, "gridCol": 7 },
  { "internalId": 20, "displayId": "4", "orientation": "horizontal", "gridRow": 3, "gridCol": 7 },
  { "internalId": 21, "displayId": "5", "orientation": "horizontal", "gridRow": 4, "gridCol": 7 },
  { "internalId": 22, "displayId": "6", "orientation": "horizontal", "gridRow": 5, "gridCol": 7 },
  { "internalId": 23, "displayId": "7", "orientation": "horizontal", "gridRow": 6, "gridCol": 7 },
  { "internalId": 24, "displayId": "8", "orientation": "horizontal", "gridRow": 7, "gridCol": 7 },
  { "internalId": 25, "displayId": "9", "orientation": "horizontal", "gridRow": 8, "gridCol": 7 },
  { "internalId": 26, "displayId": "10", "orientation": "horizontal", "gridRow": 9, "gridCol": 7 },

  { "internalId": 16, "displayId": "11", "orientation": "horizontal", "gridRow": 8, "gridCol": 4 },
  { "internalId": 15, "displayId": "12", "orientation": "horizontal", "gridRow": 7, "gridCol": 4 },
  { "internalId": 14, "displayId": "13", "orientation": "horizontal", "gridRow": 6, "gridCol": 4 },
  { "internalId": 13, "displayId": "14", "orientation": "horizontal", "gridRow": 5, "gridCol": 4 },
  
  { "internalId": 8, "displayId": "15", "orientation": "vertical", "gridRow": 3, "gridCol": 4 },
  { "internalId": 7, "displayId": "16", "orientation": "vertical", "gridRow": 1, "gridCol": 4 },
  
  { "internalId": 4, "displayId": "17", "orientation": "vertical", "gridRow": 0, "gridCol": 3 },
  { "internalId": 3, "displayId": "18", "orientation": "vertical", "gridRow": 0, "gridCol": 2 },
  { "internalId": 2, "displayId": "19", "orientation": "vertical", "gridRow": 0, "gridCol": 1 },
  { "internalId": 1, "displayId": "20", "orientation": "vertical", "gridRow": 0, "gridCol": 0 },
  
  { "internalId": 5, "displayId": "21", "orientation": "vertical", "gridRow": 1, "gridCol": 1 },
  { "internalId": 6, "displayId": "22", "orientation": "vertical", "gridRow": 3, "gridCol": 1 },
  
  { "internalId": 9, "displayId": "23", "orientation": "horizontal", "gridRow": 5, "gridCol": 1 },
  { "internalId": 10, "displayId": "24", "orientation": "horizontal", "gridRow": 6, "gridCol": 1 },
  { "internalId": 11, "displayId": "25", "orientation": "horizontal", "gridRow": 7, "gridCol": 1 },
  { "internalId": 12, "displayId": "26", "orientation": "horizontal", "gridRow": 8, "gridCol": 1 }
]

## Layout Validation Test

Run `node test/validateLayouts.js` to verify all layout files. The script checks every `*.json` file for required fields and duplicate `internalId` values.

## Guest List Format

Guest lists may include a header row with at least these columns:

- **Meal Date** (ignored)
- **Host Name** – used as the party name
- **Seats Required** – total party size
- **Notes** – optional notes

Any additional columns, like **Total Guests**, are ignored. Files without headers are still accepted, treating the first column as the name and the second as the size.
