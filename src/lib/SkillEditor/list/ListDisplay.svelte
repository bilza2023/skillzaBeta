<script>
//@ts-nocheck
// export let data;
// export let data;
export let contentItem

function contentToList(contentItem){
  const temp = contentItem.content;
   const list = temp.split('\n');
  return list;
}
</script>
{#if contentItem}
<!-- {#each items as contentItem} -->
<div
  style:padding="{contentItem.paddingY}px {contentItem.paddingX}px"
  style:margin="{contentItem.marginY}px {contentItem.marginX}px"
  style:opacity="{contentItem.opacity}"
  style:border="{contentItem.borderWidth}px {contentItem.borderStyle} {contentItem.borderColor}"
  style:border-radius="{contentItem.borderRadius}px"
  style:background-color="{contentItem.bgColor}"
  style:color="{contentItem.fontColor}"
  style:font-style="{contentItem.fontStyle}"
  style:font-size="{contentItem.fontSize}px"
  style:font-weight="{contentItem.fontWeight}"
  style:text-align="{contentItem.textAlign}"
>
    <!-- <ol class="list-decimal"> -->
    <ol >
    {#each contentToList(contentItem) as li}
        <li>{li}</li>
    {/each}
    </ol>
</div>
{/if}

