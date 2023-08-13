<script>
//@ts-nocheck
import {Anchor,PageWrapper,HdgWithIcon,Centre,Card} from '$lib/cmp';
import {Icons,onMount,toast,ajaxGet} from '$lib/util';
import ThreeCards from '$lib/appComp/ThreeCards.svelte';
import { BASE_URL } from '$lib/cmn/config';
import {Display} from '$lib/SkillEditor';
import quizStringifiedQsToArray from '$lib/appComp/fn/quizStringifiedQsToArray';

let items;
onMount(async ()=>{
    try {
        const resp = await ajaxGet(`${BASE_URL}/publicTests`);
        if (resp.ok){
            const data = await resp.json();
            const items = data.items;
            // debugger;
            for (let i = 0; i < items.length; i++) {
                items[i] = await quizStringifiedQsToArray(items[i]); 
            }
            for (let i = 0; i < items.length; i++) {
                console.log('items[i].questions[0].content[0]' , items[i].questions[0].content[0])
            }
            
            // console.log("items" , items);
        }else {
            toast.push('failed to load');
        }
    } catch (e) {
            toast.push('failed to load');
        // toast.push( e.message);
    }   
});
</script>

<PageWrapper>
<br/>
    <Centre>
        <HdgWithIcon icon={Icons.TEST}>Skillza.com</HdgWithIcon>
    </Centre>

<div class='flex bg-gray-900 p-8 m-8 rounded-md border-2 border-white'>
<ThreeCards />
</div>

<br/>
<div class='flex justify-start m-2 p-2 '>
 <HdgWithIcon icon={Icons.TEST}>Public Tests</HdgWithIcon>
</div>

<!-- <div class='flex justify-center flex-wrap gap-2 bg-gray-900 p-8 m-8 mt-1 rounded-md border-2 border-white'> -->
    {#if items}
    {#each items as item}
    <h1 class='text-white'>sdsd</h1>
        <!-- <div class={'w-3/12'}> -->
            <!-- <CardTemplate -->
            <!-- <Card
                title={item.title}
                url={`/show?quizId=${item._id}` }
                icon= {Icons.RUN}
                titleCharsCount={15}
            /> -->
            <div class="bg-gray-900 rounded-md p-1 m-1  ">

            <Display  contentItem={item.questions[0].content[0]} /> 
            </div>
        <!-- </div> -->
    {/each}
    {/if}
<!-- </div> -->
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
<br/>
</PageWrapper>
