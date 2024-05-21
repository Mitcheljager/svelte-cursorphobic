<script>
  export let range = 200
  export let multiplier = 0.1
  export let smoothing = 0.25

  let element
  let moveDistance = 0
  let moveAngle = 0

  function updatePosition(event) {
    if (!element) return

    const { left, top } = element.getBoundingClientRect()
    const elementCenter = {
      x: left + element.firstChild.clientWidth / 2,
      y: top + element.firstChild.clientHeight / 2,
    }

    const cursor = { x: event.clientX, y: event.clientY }
    const distance = Math.hypot(cursor.x - elementCenter.x, cursor.y - elementCenter.y)
    const angle = Math.atan2(elementCenter.y - cursor.y, elementCenter.x - cursor.x) * (180 / Math.PI)

    if (distance > range) {
      moveDistance = moveAngle = 0
      return
    }

    const angleDifference = angle - moveAngle
    if (Math.abs(angleDifference) > 180) {
      moveAngle += angleDifference > 0 ? 360 : -360
    }

    moveDistance = lerp(moveDistance, range - distance, smoothing)
    moveAngle = lerp(moveAngle, angle, smoothing)
  }

  function lerp(start, end, amount) {
    return start + amount * (end - start)
  }
</script>

<svelte:window on:mousemove={updatePosition} />

<div bind:this={element}>
  <div class="angler" style="--angle: {moveAngle}deg;">
    <div class="positioner" style="--distance: {moveDistance * multiplier}px;">
      <slot />
    </div>
  </div>
</div>

<style>
  .angler {
    transform: rotate(var(--angle));
  }
  .positioner {
    transform: translateX(var(--distance)) rotate(calc(var(--angle) * -1));
  }
</style>
