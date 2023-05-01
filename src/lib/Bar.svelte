<script>
  // @ts-nocheck

  import { T } from "@threlte/core";
  /**
   * @type {any}
   */
  export let x;
  export let z;
  export let y;
  export let color;
</script>

<T.Mesh
  position.x={x}
  position.y={y / 2}
  position.z={z}
  scale.y={y}
  castShadow
  receiveShadow
>
  <T.BoxGeometry />
  <T.MeshStandardMaterial {color} />
</T.Mesh>
