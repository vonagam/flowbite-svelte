<script lang="ts">
  import { twMerge } from 'tailwind-merge';

  export let value: number;
  export let size: 'sm' | 'md' | 'lg' = 'md';

  const sizes = {
    sm: 'h-1 range-sm',
    md: 'h-2',
    lg: 'h-3 range-lg'
  };
  let inputClass: string;
  $: inputClass = twMerge('w-full bg-gray-200 rounded-lg appearance-none cursor-pointer dark:bg-gray-700', sizes[size] ?? sizes.md, $$props.class);
</script>

<input type="range" bind:value {...$$restProps} class={inputClass} on:change on:click on:keydown on:keypress on:keyup />

<!--
  @component
  [Go to Range](https://flowbite-svelte.com/docs/forms/range)
  ## Props
  @prop value: number;
  @prop size: 'sm' | 'md' | 'lg' = 'md';
  ## Event
  - on:change
  - on:click
  - on:keydown
  - on:keypress
  - on:keyup
-->
