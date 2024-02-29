<script>
    import html2pdf from 'html2pdf.js';
    
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

<button class="btn text-xl hover:bg-blue-600 hover:border-blue-700 hover:text-white" on:click={() => convertToPDF()}>Convert to PDF</button>
