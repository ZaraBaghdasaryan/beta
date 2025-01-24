<script module lang="ts">
  export interface GridItem {
    src: string
    alt: string
    name: string
    text: string
    linkedin?: string
    twitter?: string
  }
</script>

<script lang="ts">
  let {
    items = [],
    className = '',
  }: { items: GridItem[]; className?: string } = $props()
</script>

<div
  class={`grid gap-8 my-8 grid-cols-[repeat(auto-fit,minmax(200px,1fr))] ${className}`}
>
  {#each items as member}
    <div
      class="flex flex-col items-center text-start leading-[19px] font-dm-sans text-[16px]"
    >
      <img
        src={member.src}
        alt={member.alt}
        width="200"
        height="200"
        class="rounded-full w-[200px] h-[200px] object-cover sm:w-[130px] sm:h-[130px]"
      />
      <b>{member.name}</b>
      <span>{@html member.text}</span>
      <div class="flex space-x-4">
        {#if member.linkedin}
          <a
            href={member.linkedin}
            target="_blank"
            class="text-white underline decoration-2"
          >
            <img
              alt="LinkedIn logo"
              src="/icons/some/linkedin_white.svg"
              class="social-icon"
            />
          </a>
        {/if}
        {#if member.twitter}
          <a
            href={member.twitter}
            target="_blank"
            class="text-white underline decoration-2"
          >
            <img
              alt="X logo"
              src="/icons/some/x_white.svg"
              class="social-icon"
            />
          </a>
        {/if}
      </div>
    </div>
  {/each}
</div>
