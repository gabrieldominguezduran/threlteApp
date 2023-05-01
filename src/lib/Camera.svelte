<script>
  import { T } from "@threlte/core";
</script>

<T.PerspectiveCamera
  makeDefault
  position={[20, 20, 20]}
  on:create={({ ref }) => {
    ref.lookAt(0, 1, 0);
  }}
/>
