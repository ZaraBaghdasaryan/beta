<script lang="ts" module>
  export interface AccordionItem {
    content: string
    value: string
    title: string
    text: string
    key?: string
    component?: any
    props?: Record<string, any>
  }

  export interface AccordionProps {
    items: AccordionItem[]
    className?: string
  }

  export let items = []
</script>

<script lang="ts">
  import * as Accordion from './index'

  let { items, className = '' }: { items: AccordionItem[]; className: string } =
    $props()
</script>

<Accordion.Root type="single" class={`w-full sm:max-w-[70%] ${className}`}>
  {#each items as item, index}
    <Accordion.Item
      value={item.value || `item-${index}`}
      class="border-t border-gray-300"
    >
      <Accordion.Trigger
        class="flex justify-between items-center py-4 text-white text-xl font-normal"
      >
        <h2>{item.title}</h2>
      </Accordion.Trigger>
      <Accordion.Content class="py-4 px-6 text-white text-base leading-relaxed">
        {item.text}
        {$inspect('item.component', item.component)}
        {$inspect('item.props', item.props)}

        {#if item.component}
          <item.component {...item.props} />
        {/if}
      </Accordion.Content>
    </Accordion.Item>
  {/each}
</Accordion.Root>
