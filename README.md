# vdem
Exporter application for the latest Vdem dataset v15

---

# V-Dem v15 Dashboard & Data Exporter

This is a web-based, single-file application designed to explore, filter, and export subsets of the **Varieties of Democracy (V-Dem) v15 dataset**. The application is powered by DuckDB-WASM, which allows for efficient, in-browser SQL querying of the large remote dataset hosted on Hugging Face without needing to download the entire file.

Its primary purpose is to serve as a user-friendly tool for researchers, journalists, and students to quickly access and subset the rich V-Dem data for analysis in other platforms.

## Key Features

-   **Interactive Map Visualization:** Displays data for the latest selected year on a world map, colored by the value of the primary selected indicator.
-   **Dynamic Data Table:** View the filtered data directly in the browser in a clean, scrollable table.
-   **Comprehensive Filtering:** Filter the dataset by:
    -   **Multiple Main Indicators** (e.g., Electoral Democracy, Liberal Democracy)
    -   **Multiple Other Indicators** (including sub-components and individual V-Dem variables)
    -   **Regions**
    -   **Countries**
    -   **Year Range** (from 1960 onwards)
-   **User-Friendly Indicator Naming:** Internal V-Dem variable names (e.g., `v2x_polyarchy`) are mapped to their full, descriptive names from the official codebook, making the interface easy to understand.
-   **Synchronized CSV Export:** Export the currently displayed data table to a CSV file with a single click. The exported data perfectly matches the filters applied in the application.
-   **Efficient Data Handling:** Utilizes DuckDB-WASM to query the remote CSV directly via HTTP Range Requests, ensuring fast performance and low memory usage.
-   **Theme Toggle:** Switch between a light and dark mode for comfortable viewing.

## Technology Stack

-   **Frontend:** HTML5, CSS3, JavaScript (ES Modules)
-   **Database:** [DuckDB-WASM](https://duckdb.org/docs/api/wasm.html) for high-performance, in-browser SQL querying.
-   **Mapping:** [Leaflet.js](https://leafletjs.com/) for the interactive map.
-   **Backend:** None. The application is entirely client-side and runs in the browser.

## How to Use

The application is a single HTML file and requires no installation.

### Option 1: Running Directly (Easiest)

1.  Download the `vdem-dashboard.html` file to your computer.
2.  Open it in a modern web browser (e.g., Google Chrome, Mozilla Firefox, Microsoft Edge, Safari).

### Option 2: Running with a Local Web Server (Recommended for Development)

Due to browser security policies (CORS), opening the `file:///...` path directly may block some network requests required by DuckDB-WASM. If you encounter issues, running a simple local web server is the most reliable method.

1.  **Download** the `vdem-dashboard.html` file into a new folder.
2.  **Open a terminal or command prompt** in that folder.
3.  **Run one of the following commands:**

    **If you have Python 3:**
    ```bash
    python -m http.server
    ```

    **If you have Node.js/npm installed:**
    ```bash
    # First, install the server package globally (only needs to be done once)
    npm install -g http-server

    # Then, run the server
    http-server
    ```
4.  **Open your browser** and navigate to the address shown in the terminal (usually `http://localhost:8000` or `http://localhost:8080`).

## File Structure

The entire application is self-contained within the `vdem-dashboard.html` file. It requires no other local files to run. All external libraries (Leaflet, DuckDB-WASM) are loaded from a Content Delivery Network (CDN).

## Data Source

-   **Data Provider:** [V-Dem Institute](https://www.v-dem.net/) at the University of Gothenburg.
-   **Dataset:** Varieties of Democracy (V-Dem) Dataset v15.
-   **Hosting:** The CSV file is hosted on [Hugging Face Datasets](https://huggingface.co/datasets/mnshakoor06/Vdem).
-   **License:** The V-Dem data is provided under the [CC BY 3.0 license](https://creativecommons.org/licenses/by/3.0/). Please ensure proper citation as recommended in the "About" section of the application.
