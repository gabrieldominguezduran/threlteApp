<script>
  import { Text } from "@threlte/extras";

  /**
   * @type {string}
   */
  export let d;
  /**
   * @type {number}
   */
  export let x;
  /**
   * @type {number}
   */
  export let z;
  /**
   * @type {number}
   */
  export let y;
</script>

<Text
  text={d}
  position.x={x}
  position.y={y}
  position.z={z}
  color="#230612"
  fontSize={0.6}
  rotation.x={-Math.PI / 2}
  rotation.z={Math.PI / 2}
  fillOpacity={1}
  font="https://fonts.gstatic.com/s/raleway/v14/1Ptrg8zYS_SKggPNwIYqWqZPBQ.ttf"
  anchorX="center"
/>
