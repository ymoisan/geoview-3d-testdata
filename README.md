# geoview-3d test data

Sample [OGC 3D Tiles 1.1](https://www.ogc.org/standard/3dtiles/) tileset for testing the
[geoview-3d](https://github.com/ymoisan/geoview/tree/geoview-3d/packages/geoview-3d) plugin
(`tiles-3d`) of the GeoView fork. Served by GitHub Pages, which sends
`Access-Control-Allow-Origin: *`, so a viewer on any origin (including `http://localhost:8080`) can
load it directly.

## Tilesets

| Path       | Area                                  | Size  | Tileset URL                                                          |
| ---------- | ------------------------------------- | ----- | -------------------------------------------------------------------- |
| `halifax/` | Halifax, Nova Scotia (about 1 x 1 km) | 91 MB | <https://ymoisan.github.io/geoview-3d-testdata/halifax/tileset.json> |

### halifax

- Bounding box: longitude -63.63619 to -63.62358, latitude 44.64842 to 44.65753.
- 16 glTF binary (`.glb`) tiles under `t/`; the upper levels of the tree are empty.
- About 8,000 buildings (red) and 143,000 trees (green), coloured per vertex (glTF `COLOR_0`) over a
  white material; feature ids in `_FEATURE_ID_0` (`EXT_mesh_features`).
- Heights are orthometric (CGVD2013, metres above sea level, 11.5 to 72.7 m), matching NRCan's
  HRDEM lidar elevation model: building bases sit on the HRDEM ground (median difference -0.16 m).
- The area is inside HRDEM lidar coverage, which geoview-3d uses for terrain.

## Use with geoview-3d

Set the plugin's `tilesetUrl` to the tileset URL above, for example in
`packages/geoview-core/public/configs/demo-3d-config-tiles-3d.json`:

```json
{
  "isOpen": false,
  "tilesetUrl": "https://ymoisan.github.io/geoview-3d-testdata/halifax/tileset.json",
  "version": "1.0"
}
```
