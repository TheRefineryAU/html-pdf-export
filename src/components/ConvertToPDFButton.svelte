<script>

import jsPDF from 'jspdf';
import axios from 'axios';
// const axios = require('axios');
// const jsPDF = require('jspdf');

async function generatePDFfromURL(url, outputPath) {
  try {
    const response = await axios.get(url);
    const textContent = response.data;
    const doc = new jsPDF();
    doc.text(textContent, 10, 10);
    doc.save(outputPath);
    console.log('PDF generated successfully');
  } catch (error) {
    console.error('Error fetching URL:', error);
  }
}

// Usage
generatePDFfromURL('https://localhost:4321');

</script>


<!--<button on:click={generatePDFfromURL} >Convert to PDF</button> -->
<button on:click={() => generatePDFfromURL('https://localhost:4321')}>Convert to PDF</button>


<style>
    /* your styles go here */
</style>
