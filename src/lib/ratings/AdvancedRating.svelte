<script lang="ts">
  import { twMerge } from 'tailwind-merge';
  export let ratings: { label: string; rating: number }[] = [];
  export let divClass: string = 'flex items-center mt-4';
  export let labelClass: string = 'text-sm font-medium text-gray-600 dark:text-gray-500';
  export let ratingDivClass: string = 'mx-4 w-2/4 h-5 bg-gray-200 rounded dark:bg-gray-700';
  export let ratingClass: string = 'h-5 bg-yellow-400 rounded';
  export let rightLabelClass: string = 'text-sm font-medium text-gray-600 dark:text-gray-500';
  export let unit: string = '%';

  let divCls: string = twMerge(divClass, $$props.classDiv);
  let labelCls: string = twMerge(labelClass, $$props.classLabel);
  let ratingDivCls: string = twMerge(ratingDivClass, $$props.classRatingDiv);
  let ratingCls: string = twMerge(ratingClass, $$props.classRating);
  let rightLabelCls: string = twMerge(rightLabelClass, $$props.classRightLabel);
</script>

{#if $$slots.rating}
  <slot name="rating" />
{/if}
{#if $$slots.globalText}
  <slot name="globalText" />
{/if}
{#each ratings as { label, rating }}
  <div class={divCls}>
    <span class={labelCls}>{label}</span>
    <div class={ratingDivCls}>
      <div class={ratingCls} style="width: {rating}%" />
    </div>
    <span class={rightLabelCls}>{rating}{unit}</span>
  </div>
{/each}

<!--
  @component
  [Go to Rating](https://flowbite-svelte.com/docs/components/rating)
  ## Props
  @prop ratings: { label: string; rating: number }[] = [];
  @prop divClass: string = 'flex items-center mt-4';
  @prop labelClass: string = 'text-sm font-medium text-gray-600 dark:text-gray-500';
  @prop ratingDivClass: string = 'mx-4 w-2/4 h-5 bg-gray-200 rounded dark:bg-gray-700';
  @prop ratingClass: string = 'h-5 bg-yellow-400 rounded';
  @prop rightLabelClass: string = 'text-sm font-medium text-gray-600 dark:text-gray-500';
  @prop unit: string = '%';
-->
