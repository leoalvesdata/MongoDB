# MongoDB - La Liga Data Management (NoSQL Document-Oriented)

This project was developed to practice the fundamental concepts of MongoDB (NoSQL Document-Oriented Database), simulating the data management of football clubs from the Spanish League using the MongoDB Shell (`mongosh`).

---

## Problems We Had to Solve

1. **Unstructured Data (Dynamic Schema):** The provided club data did not share a uniform structure (some clubs had anthems, others did not; some had multiple colors, while others had only one). In a traditional SQL database, this would result in an excessive number of empty columns (`NULL`).
2. **Incomplete Record Updates:** We needed to inject new fields (such as anthems and arrays of colors) into documents that had already been created without that initial information.
3. **Partial Text Filtering (Flexible Search):** We had to find specific clubs based on keywords hidden inside long strings of text (e.g., finding the word "lenda" in the middle of a full club anthem).
4. **Moving Data Between Collections:** We simulated a club being relegated to a lower division, which required extracting a document from one collection and inserting it into another without losing the original data structure.

---

## What Was Done (Step-by-Step)

### 1. Data Insertion (Dynamic Schema)
We created the `Primeira Liga Espanhola` collection and inserted all the club records simultaneously. MongoDB natively accepted the structural variation among the documents.

### 2. Queries and Advanced Filtering
* Listed all available documents in the collection.
* Filtered data using the `$gte` operator to find teams with at least 1 championship title.
* Filtered data using the `$lt` operator to find teams founded before the year 1900.
* Queried directly inside a list (Array) to find teams that use the color "Branco" in their kits.

### 3. Updating and Evolving Documents
We used the `updateOne` method along with the `$set` operator to modify the clubs' data (FC Barcelona, Recreativo de Huelva, and Sevilha FC), correcting foundation years and adding properties that did not exist in the initial stage.

### 4. Regular Expressions (Regex) and Document Removal
* Utilized `/term/i` to perform smart keyword searches within anthems and names (such as the "FC" acronym).
* Combined search filters with the `$not` exclusion operator.
* Cloned the *Recreativo de Huelva* document into a new collection named `Segunda Liga Espanhola` using a combination of `insertOne` + `findOne`, and immediately wiped the original entry using `deleteOne`.

---

## 🛠️ Technologies Used

* **Database Engine:** MongoDB (NoSQL Document-Oriented)
* **Command Line Interface:** MongoDB Shell (`mongosh`)
* **Data Format:** JSON / BSON
