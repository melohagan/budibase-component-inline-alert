<script>
  import { getContext } from "svelte"

  export let title
  export let variant

  const { styleable } = getContext("sdk")
  const component = getContext("component")

  const iconMap = {
    info: "Info",
    success: "CheckmarkCircle",
    error: "Alert",
    help: "Alert",
  }
  $: icon = iconMap[variant]
  $: helpClass = variant === "help" ? "help" : ""
</script>

<div use:styleable={$component.styles}>
  <div class="spectrum-InLineAlert spectrum-InLineAlert--{variant} {helpClass}">
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

<style>
  .spectrum-InLineAlert {
    --spectrum-semantic-negative-border-color: #e34850;
    --spectrum-semantic-positive-border-color: #2d9d78;
    --spectrum-semantic-informative-border-color: #3978ec;
    --spectrum-semantic-positive-icon-color: #2d9d78;
    --spectrum-semantic-negative-icon-color: #e34850;
    --spectrum-semantic-informative-icon-color: #3978ec;
  }
  .help {
    --spectrum-semantic-informative-border-color: #e88b37;
    --spectrum-semantic-informative-icon-color: #e88b37;
  }
</style>