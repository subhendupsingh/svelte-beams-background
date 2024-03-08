<script lang='ts'>
	import Beams from "$lib/components/beams/beams.svelte";
</script>

<Beams>
    <div class="max-w-2xl mx-auto p-8 md:p-4 flex flex-col gap-2 h-full w-full justify-center">
        <h1 class="text-5xl md:text-7xl bg-clip-text text-transparent bg-gradient-to-b from-neutral-200 to-neutral-600 text-center font-sans font-bold">Join the waitlist</h1>
        <p></p>
        <p class="text-neutral-500 max-w-lg mx-auto my-2 text-sm text-center font-inter leading-relaxed">Welcome to MailJet, the best transactional email service on the web. We provide reliable, scalable, and customizable email solutions for your business. Whether you're sending order confirmations, password reset emails, or promotional campaigns, MailJet has got you covered.</p>
        <input placeholder="hi@example.com" class="rounded-lg border border-neutral-800 focus:ring-2 focus:ring-teal-500 w-full mt-4 bg-neutral-950 placeholder:text-neutral-700 py-2 px-4 outline-none text-neutral-500" type="text">
    </div>
</Beams>
    
<style>
    :global(body) {
        background: #0A0A0A;
        overflow: hidden;
    }
</style>