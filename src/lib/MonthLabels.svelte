<script>
  import { T } from "@threlte/core";
  import { Text } from "@threlte/extras";

  /**
   * @type {{ month: string; }}
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
</script>

<Text
  text={d.month}
  position.x={x - 0.3}
  position.y={0.01}
  position.z={z + 3.5}
  color="#230612"
  fontSize={0.5}
  rotation.x={-Math.PI / 2}
  rotation.z={Math.PI / 2}
  fillOpacity={1}
  font="https://fonts.gstatic.com/s/raleway/v14/1Ptrg8zYS_SKggPNwIYqWqZPBQ.ttf"
  anchorX="center"
/>
