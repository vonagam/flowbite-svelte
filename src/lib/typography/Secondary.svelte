<script lang="ts">
  import { twMerge } from 'tailwind-merge';

  export let color: string = 'text-gray-500 dark:text-gray-400';
  export let secondaryClass: string = 'font-semibold';
</script>

<small {...$$restProps} class={twMerge(color, secondaryClass, $$props.class)}>
  <slot />
</small>

<!--
  @component
  [Go to Heading Secondary](https://flowbite-svelte.com/docs/typography/heading#Second-level_heading)
  ## Props
  @prop color: string = 'text-gray-500 dark:text-gray-400';
  @prop secondaryClass: string = 'font-semibold';
-->
