<script>
	import jsPDF from 'jspdf';
	import html2canvas from 'html2canvas';
	
	export let selector = '';
	
	async function convertToPDF() {
		if (!selector) {
			console.error('No selector provided for PDF conversion.');
			return;
		}
		
		const element = document.querySelector(selector);
		if (!element) {
			console.error('Element not found with the provided selector:', selector);
			return;
		}
		
		const canvas = await html2canvas(element, {
			scale: 1 // Adjust scale according to your needs
		});
		
		const imgData = canvas.toDataURL('image/png');
		const pdf = new jsPDF({
			orientation: 'portrait',
			unit: 'px',
			format: [canvas.width, canvas.height]
		});
		
		pdf.addImage(imgData, 'PNG', 0, 0, canvas.width, canvas.height);
		pdf.save('downloaded.pdf');
	}
</script>

<button class="btn text-xl hover:bg-blue-600 hover:border-blue-700 hover:text-white" on:click={() => convertToPDF()}>Convert to PDF</button>

<style>
	/* Your styles here */
</style>