<script>
// @ts-nocheck

import Btns from "./Btns.svelte";
import ShowQuestions from "./ShowQuestions.svelte";
import ProgressBar from "$lib/cmp/ProgressBar.svelte";
import Loading from '$lib/cmp/Loading.svelte';
import {Display} from '../../../lib/SkillEditor';
import ShowMcq from "../questionControls/ShowMcq.svelte";

//--we need these only if we want to react to them
export let quiz;
</script>


<br>
<div class="flex justify-center">
  <h1 class="bg-blue-900  p-2 m-1  mt-0  w-full text-center text-2xl rounded-md">{quiz.title}
  </h1>
</div>
  <br>

<div class=" bg-gray-700 p-1  text-white rounded-md w-10/12 mx-auto border-2 border-gray-400">

<div class="bg-gray-900 rounded-md p-1 m-1  ">

{#each quiz.questions as question}

    {#each question.content as contentItem}
    <!-- DivDsiplay will show EACH contentItem of content array one by one -->
    <!-- This is where we inser if contentItem.type == div then -->
    <Display  {contentItem} />  
    {/each}

   <br>
   <ShowMcq {question}  />
   <br/>
   <br/>
{/each}
  </div>
  
<Btns     {quiz}  saveResponse={quiz.saveResponse} />
</div><!--flex box ends--->

