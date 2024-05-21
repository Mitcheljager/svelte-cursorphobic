<script>
  export let range = 200
  export let multiplier = 0.1
  export let smoothing = 0.1

  let element
  let moveDistance = 0
  let moveAngle = 0

  function updatePosition(event) {
    if (!element) return

    const elementRect = element.getBoundingClientRect()
    const elementPosition = {
      x: elementRect.left + element.firstChild.clientWidth / 2,
      y: elementRect.top + element.firstChild.clientHeight / 2,
    }

    const cursorPosition = { x: event.clientX, y: event.clientY }

    const distance = getDistance(cursorPosition, elementPosition)
    const angle = getAngle(cursorPosition, elementPosition)

    if (Math.abs(distance) > range) {
      moveDistance = 0
      moveAngle = 0
      return
    }

    // Handle angle wrapping
    const angleDifference = angle - moveAngle
    if (Math.abs(angleDifference) > 180) {
      moveAngle = angleDifference > 0 ? moveAngle + 360 : moveAngle - 360
    }

    moveDistance = lerp(moveDistance, range - distance, smoothing)
    moveAngle = lerp(moveAngle, angle, smoothing)
  }

  /**
   * Linear interpolation
   * Used to smooth out the animation
   *
   * @param start
   * @param end
   * @param amount
   */
  const lerp = (start, end, amount) => (1 - amount) * start + amount * end

  function getDistance(cursorPosition, elementPosition) {
    const dx = cursorPosition.x - elementPosition.x
    const dy = cursorPosition.y - elementPosition.y
    return Math.sqrt(dx * dx + dy * dy)
  }

  function getAngle(cursorPosition, elementPosition) {
    const angle = Math.atan2(
      elementPosition.y - cursorPosition.y,
      elementPosition.x - cursorPosition.x,
    )
    return angle * (180 / Math.PI)
  }
</script>

<svelte:window on:mousemove={updatePosition} />

<div bind:this={element}>
  <div class="angler" style:--angle={moveAngle + 'deg'}>
    <div class="positioner" style:--distance={moveDistance * multiplier + 'px'}>
      <slot />
    </div>
  </div>
</div>

<style lang="scss">
  .angler {
    transform: rotate(var(--angle));
  }

  .positioner {
    transform: translateX(var(--distance)) rotate(calc(var(--angle) * -1));
  }
</style>
