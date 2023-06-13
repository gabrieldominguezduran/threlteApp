<script>
  import { Text } from "@threlte/extras";

  const font =
    "https://fonts.gstatic.com/s/raleway/v14/1Ptrg8zYS_SKggPNwIYqWqZPBQ.ttf";
</script>

<Text
  text={"Heathrow Rainfall"}
  position.z={0}
  position.x={-10}
  position.y={12}
  color="#230612"
  fontSize={3}
  rotation.y={Math.PI / 4}
  {font}
  maxWidth={17}
  lineHeight={1.1}
/>
