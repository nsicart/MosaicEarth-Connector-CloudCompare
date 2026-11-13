# MosaicEarth-Connector-CloudCompare

CloudCompare GUI, CLI & PythonRuntime connector for synchronizing LiDAR/photogrammetric .laz/.las/.e57 point clouds, M3C2 outputs, DSM rasters & 3D Gaussian Splats with MosaicEarth.

## Releases & Ready-to-Install Downloads (`v0.3.0`)

- [`MosaicEarth-cloudcompare-0.3.0.zip`](https://github.com/nsicart/MosaicEarth-Connector-CloudCompare/releases/download/v0.3.0/MosaicEarth-cloudcompare-0.3.0.zip)
- Also available directly from [MosaicEarth Desktop & Connectors (`app.mosaicearth.app/en/Desktop`)](https://app.mosaicearth.app/en/Desktop).

## Cloud & Local Workstation Endpoints

Every MosaicEarth connector speaks the open **MosaicEarth Synchronization Protocol v1** (chunked `4 MiB` resumable uploads + end-to-end `SHA-256` verification) and can connect to:

- **MosaicEarth Cloud** (default): `https://app.mosaicearth.app`
- **MosaicEarth Desktop (Local Workstation)**: `http://127.0.0.1:19771` (set `MOSAICEARTH_URL=http://127.0.0.1:19771` or select the endpoint in the connector UI).

## Usage & Setup

Download and extract `MosaicEarth-cloudcompare-0.3.0.zip`.

- **Desktop GUI**: run `MosaicEarth-CloudCompare.bat` (Windows) or `./MosaicEarth-CloudCompare.sh` (Linux). Sign in, add `.laz`, `.las`, `.ply` (both Lidar/photogrammetry point clouds, M3C2 distance scalar clouds and 3D Gaussian Splats), `.spz`, `.e57`, `.bin`, `.glb`, `.obj` or `.tif` files, choose a MyEarth Project and optional **4D Capture Date (`YYYY-MM-DD`)**, and click **Push Selected Clouds to MyEarth**.
- **Automatic `-SILENT` Conversion & DSM Rasterization**: for native `.bin` / `.e57` clouds or when a grid step (`--rasterize-dsm-step 0.25`) is specified, the bridge invokes `CloudCompare -SILENT` to export `.laz` and/or rasterize a GeoTIFF DSM (`-RASTERIZE -PROJ MAX -OUTPUT_RASTER_Z`) while preserving the original file as a private attachment.
- **Pull & Open in CloudCompare**: downloads verified Cloud revisions locally and launches CloudCompare with the restored point clouds and meshes.
- **CloudCompare-PythonRuntime (`pycc`)**: users with the embedded Python plugin can also invoke `mosaicearth_cloudcompare.pycc_plugin.push_selected_pycc_entities(...)` to synchronize entities selected in CloudCompare's DB tree.

## License

Released under **GNU Affero General Public License v3.0 or later (`AGPL-3.0-or-later`)** — see [`LICENSE`](./LICENSE).
