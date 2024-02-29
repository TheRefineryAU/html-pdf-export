<script>
    // Import the jsPDF module for generating PDF documents
    import { jsPDF } from "jspdf";
    
    // Listener to ensure the DOM is fully loaded before executing the script
    document.addEventListener("DOMContentLoaded", () => {
        // Finds the button by its ID
        const btn = document.getElementById("convertToPDF");
        
        // Adds a click event listener to the button
        btn.addEventListener("click", () => {
            // Creates a new jsPDF document instance
            const doc = new jsPDF();
            
            // Defines the text to be added to the PDF
            const text = "Hello World!";
            
            // Adds the text to the document at the specified position (10, 10)
            doc.text(text, 10, 10);
            
            // Saves the created PDF with the given filename
            doc.save('output.pdf');
        });
    });
</script>

<div class="card bg-white text-gray-800 border-2 border-gray-600 p-8">
    <p class="text-2xl mb-4">JavaScript jsPDF Import Version</p>
    <!-- Button to trigger PDF conversion. It's assumed there's a JavaScript function bound to this button's click event -->
    <button id="convertToPDF" class="btn text-xl hover:bg-blue-600 hover:border-blue-700 hover:text-white">Convert to PDF</button>
</div>
