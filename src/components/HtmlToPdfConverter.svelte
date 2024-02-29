<script>
    import html2pdf from 'html2pdf.js';
    
    /**
   * Converts the specified HTML element into a PDF document.
   * @prop {string} selector - The CSS selector of the element to convert to PDF.
   */
    export let selector = '';
    
    function convertToPDF() {
        const element = document.querySelector(selector);
        if (!element) {
            console.error('Element not found with the provided selector:', selector);
            return;
        }
        
        // Configure html2pdf options
        const options = {
            margin: 1,
            filename: 'document.pdf',
            image: { type: 'jpeg', quality: 0.98 },
            html2canvas: { scale: 2 },
            jsPDF: { unit: 'in', format: 'letter', orientation: 'portrait' }
        };
        
        // Use html2pdf to convert the element
        html2pdf().set(options).from(element).save();
    }

</script>

<div class="card bg-white text-gray-800 border-2 border-gray-600 p-8">
    <p class="text-2xl mb-4">html2pdf.js Svelte Component Version</p>
    <!-- Svelte component for converting HTML to PDF, targeting the iframe content. Note: 'client:only' is necessary for client-side rendering in Astro -->
    <button class="btn text-xl hover:bg-blue-600 hover:border-blue-700 hover:text-white" on:click={() => convertToPDF()}>Convert to PDF</button>
</div>