<script>
  import { T } from "@threlte/core";
  import { OrbitControls } from "@threlte/extras";
</script>

<T.PerspectiveCamera
  makeDefault
  position={[20, 20, 20]}
  on:create={({ ref }) => {
    ref.lookAt(0, 1, 0);
  }}
>
  <OrbitControls enableDamping target={[0, 4, 0]} />
</T.PerspectiveCamera>
