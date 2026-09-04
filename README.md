To install **MARUS2 Visualization gRPC** and its required core dependencies, add them directly to your Unity project's **`Packages/manifest.json`** file under the `"dependencies"` block:

```json
{
  "dependencies": {
    "com.marus2.proto": "https://github.com/MARUSimulator/marus2-proto.git#csharp",
    "com.marus2.core": "https://github.com/MARUSimulator/marus2-core.git",
    "com.marus2.visualization": "https://github.com/MARUSimulator/marus-visualization.git",
    "com.marus2.visualization-grpc": "https://github.com/MARUSimulator/marus-visualization-grpc.git"
  }
}
```

# Visualization gRPC usage

This package enables real-time 3D streaming and visualization of external sensor data and ROS visualization markers in Unity over a gRPC network connection.

Remote connections are established automatically through `RosConnection` when the scene starts.

## Visualization gRPC

A singleton component that subscribes to incoming ROS `Marker` and `MarkerArray` messages streamed over gRPC. It converts markers (spheres, cubes, cylinders, lines, arrows) into Unity GameObjects with correct spatial placement synchronized to ROS TF frames.
* **ROS Message Types**: `visualization_msgs/msg/Marker`, `visualization_msgs/msg/MarkerArray`

## Point Cloud gRPC Visualizer

A singleton streamer that listens for remote 3D point cloud streams over gRPC. It decodes binary point fields (X, Y, Z coordinates, surface normals, and RGB/RGBA colors) and renders them in real time using the GPU-accelerated `PointCloudManager`.
* **ROS Message Type**: `sensor_msgs/msg/PointCloud2`
