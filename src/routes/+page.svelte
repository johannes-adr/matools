<script lang="ts">
    let transkript = $state("")
    let text = $state("");

    $effect(()=>{
        text = transkript.split("\n").filter((v,idx)=>idx % 4 == 0).splice(1).join("\n");
    });

</script>

{#snippet textarea(name: string, value: string, onUpdate: (t: string)=>void)}
<div class="flex flex-col w-full h-full">
    <h1 class="text-xl">{name}</h1>
    <textarea class="w-full h-full rounded-md shadow-md resize-none" value={value} oninput={e=>onUpdate((e.target! as HTMLTextAreaElement).value)}  name="" id=""></textarea>
</div>

{/snippet}

<div class="w-full h-screen flex items-center gap-3 px-20 py-10">
    {@render textarea("transkript", transkript, value=>transkript = value)}
    {@render textarea("text",text, value=>text = value)}
</div>