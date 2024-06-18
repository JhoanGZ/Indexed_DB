# IndexedDB Database Management Project

## Overview

This project demonstrates a comprehensive implementation of IndexedDB for database management in web applications. It was developed to explore various technologies and methodologies for solving data management problems, thereby serving as a foundation for my growth in learning and mastering database technologies.

## Features

- **IndexedDB Integration**: Utilizes IndexedDB to create and manage object stores for `clientes`, `ventas`, and `productos`.
- **CRUD Operations**: Implements Create, Read, Update, and Delete operations for managing data in the database.
- **Transaction Handling**: Manages database transactions to ensure data integrity and consistency.
- **Error Handling**: Includes robust error handling mechanisms to manage and log errors during database operations.
- **Data Retrieval and Sorting**: Retrieves and sorts data from the object stores based on specific keys and directions.

## Technologies Used

- **JavaScript**: Core programming language used for implementing the database operations.
- **IndexedDB**: A low-level API for client-side storage of significant amounts of structured data.

## Project Structure

The main functionality is encapsulated within an immediately invoked function expression (IIFE) to avoid polluting the global scope. Key features include:

- **Database Connection and Setup**: Opens a connection to the IndexedDB and sets up the object stores if they do not already exist.
- **CRUD Methods**: Methods to add, retrieve, update, and delete data from the object stores.
- **Error Handling**: Logs and alerts the user in case of errors during database operations.
- **Data Sorting**: Retrieves and sorts elements from the object stores based on specified criteria.

## Code Snippet

```javascript
(function() {
    if (!window.indexedDB){ 
        alert("Your browser doesn't support a stable version of IndexedDB.");
        console.log(`The browser doesn't support IndexedDB`);
        return;
    }

    const request = indexedDB.open('Almacen', 1);

    request.onerror = function(event){ 
        alert("Error opening the database");
        console.log(`Error opening the database: ${event.target.errorCode}`);
    }

    request.onupgradeneeded = function(event){
        const db = event.target.result;

        if (!db.objectStoreNames.contains('clientes')) {
            let clientes = db.createObjectStore('clientes', { keyPath: "id_cliente", autoIncrement: false });
        } else {
            alert('The table "clientes" already exists');
        }

        if (!db.objectStoreNames.contains('ventas')) {
            let ventas = db.createObjectStore('ventas', { keyPath: "id_venta", autoIncrement: true });
        } else {
            alert('The table "ventas" already exists');
        }

        if (!db.objectStoreNames.contains('productos')) {
            let productos = db.createObjectStore('productos', { keyPath: "id_producto", autoIncrement: true });
        } else {
            alert('The table "productos" already exists');
        }
    };

    request.onsuccess = function(event){
        console.log(`Database opened successfully`);
        alert('Database opened successfully');
        const db = event.target.result;

        // CRUD operations go here...
    }
})();
```
## Installation and Usage
To use this project:

Clone the repository to your local machine:
bash
Copy code
```https://github.com/JhoanGZ/Indexed_DB.git```

Open the index.html file in your browser to interact with the database management functionality.
## Contribution
Contributions are welcome! Please feel free to submit a Pull Request or open an issue to improve this project.

## License
This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgements
This project was created as part of my ongoing learning and exploration of database technologies. 
Special thanks to the online community and documentation that provided guidance and support throughout the development process.


