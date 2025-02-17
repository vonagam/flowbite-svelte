<script lang="ts">
  import { twMerge } from 'tailwind-merge';
  import CloseButton from '../utils/CloseButton.svelte';

  export let id: string = 'sticky-banner';
  export let position: 'static' | 'fixed' | 'absolute' | 'relative' | 'sticky' = 'sticky';
  export let dismissable: boolean = true;
  export let bannerType: 'default' | 'bottom' | 'cta' | 'signup' | 'info' = 'default';
  export let divClass: string = 'z-10 flex justify-between p-4 dark:bg-gray-700 dark:border-gray-600';
  export let innerClass: string = 'flex';

  const divClasses = {
    default: 'top-0 left-0 w-full border-b border-gray-200 bg-gray-50',
    bottom: 'bottom-0 left-0 w-full border-t border-gray-200 bg-gray-50',
    cta: 'flex-col md:flex-row  w-[calc(100%-2rem)] -translate-x-1/2 bg-white border border-gray-100 rounded-lg shadow-sm lg:max-w-7xl left-1/2 top-6',
    signup: 'top-0 left-0 w-full border-b border-gray-200 bg-gray-50',
    info: 'top-0 left-0 flex-col w-full border-b border-gray-200 md:flex-row bg-gray-50'
  };

  const insideDivClasses = {
    default: 'items-center mx-auto',
    bottom: 'items-center mx-auto',
    cta: 'flex-col items-start mb-3 mr-4 md:items-center md:flex-row md:mb-0',
    signup: 'items-center flex-shrink-0 w-full mx-auto sm:w-auto',
    info: 'items-center flex-shrink-0'
  };

  $: divClass = twMerge(position, divClass, divClasses[bannerType], $$props.classDiv);
  $: div2Class = twMerge(innerClass, insideDivClasses[bannerType], $$props.classInner);
  let show = true;
  $: handleHide = () => {
    show = !show;
  };
</script>

{#if show}
  <div {id} tabindex="-1" class={divClass} {...$$restProps}>
    <slot name="header" />
    <div class={div2Class}>
      <slot />
    </div>
    {#if dismissable}
      <div class="flex items-center">
        <CloseButton class="-mx-1.5 -my-1.5" color={$$restProps.color} on:click={handleHide} on:click on:change on:keydown on:keyup on:focus on:blur on:mouseenter on:mouseleave />
      </div>
    {/if}
  </div>
{/if}

<!--
  @component
  [Go to Banner](https://flowbite-svelte.com/docs/components/banner)
  ## Props
  @prop id: string = 'sticky-banner';
  @prop position: 'static' | 'fixed' | 'absolute' | 'relative' | 'sticky' = 'sticky';
  @prop dismissable: boolean = true;
  @prop bannerType: 'default' | 'bottom' | 'cta' | 'signup' | 'info' = 'default';
  @prop divClass: string = 'z-10 flex justify-between p-4 dark:bg-gray-700 dark:border-gray-600';
  @prop insideDiv: string = 'flex';
  ## Event
  - on:click
  - on:change
  - on:keydown
  - on:keyup
  - on:focus
  - on:blur
  - on:mouseenter
  - on:mouseleave
  
-->
