<script lang='ts'>
    import anime from "animejs";
	import { onMount } from "svelte";
    import UAParser from "ua-parser-js";

    let parser = new UAParser();
    $: isMobile = parser.getDevice().type==="mobile";
    $: console.log("isMobile", isMobile);
    
    export let index: number;
    const durations = [8000, 9000, 5000, 25000, 20000];
    onMount(()=>{
        const path = document.querySelector('.infinity') as SVGGeometryElement;
        const gradient = document.querySelector(`#linearGradient-${index}`);
        const totalDistance = path?.getTotalLength();
        const val = { distance: 0 };
        const duration  = durations[Math.floor(Math.random()*durations.length)];;
        anime({
            targets: val,
            distance: totalDistance,
            loop: true,
            duration: duration,
            easing: 'linear',
            change(anim) {
                const progress = anim.progress;
                
                gradient?.setAttribute("x1",progress+"%")
                gradient?.setAttribute("y1",progress+"%")
                gradient?.setAttribute("x2",(progress+1.5)+"%")
                gradient?.setAttribute("y2",(progress+1.5)+"%")
            },
        }).play();
    })

    const grayStrokeOpacity = isMobile ? (10 - (index>20 ? index-20 : 0)) : (20 - (index>30 ? index-30 : 0));
</script>

{#key index}
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="-6.1 -1.1 25.2 14.2">
        <defs>
            <linearGradient id={`linearGradient-${index}`}>
                <stop stop-color="#18CCFC" stop-opacity="0"></stop>
                <stop stop-color="#18CCFC"></stop>
                <stop offset="32.5%" stop-color="#6344F5"></stop>
                <stop offset="100%" stop-color="#AE48FF" stop-opacity="0"></stop>
            </linearGradient>
        </defs>
        <path d="M -6 -1 Q -1 7 12 9 Q 17 10 19 13" stroke={"#f0f0f0"+grayStrokeOpacity} class="gray-path" stroke-width={isMobile ? 0.02 : 0.005} fill="none"/>
        <path d="M -6 -1 Q -1 7 12 9 Q 17 10 19 13" stroke={"url(#linearGradient"+`-${index}`+")"} class="infinity" stroke-width={isMobile ? 0.02 : 0.005} fill="none"/>
    </svg>
{/key}