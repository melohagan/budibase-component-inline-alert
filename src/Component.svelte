<script>
  import { getContext } from "svelte"

  export let title
  export let variant

  const { styleable } = getContext("sdk")
  const component = getContext("component")

  const iconMap = {
    info: "Info",
    positive: "CheckmarkCircle",
    negative: "Alert",
    notice: "Alert",
  }
  $: icon = iconMap[variant]
</script>

<div use:styleable={$component.styles}>
  <div class="spectrum-InLineAlert spectrum-InLineAlert--info">
    <div class="spectrum-InLineAlert-header">
        {title}
      <svg class="spectrum-Icon spectrum-Icon--sizeM spectrum-InLineAlert-icon" focusable="false" aria-hidden="true">
        <use xlink:href="#spectrum-icon-18-{icon}" />
      </svg>
    </div>
    <div class="spectrum-InLineAlert-content">
      <slot />
    </div>
  </div>
</div>
