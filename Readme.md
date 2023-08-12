# Lane Detection using Point Cloud Data

## Process Overview:
    1. Rotation: Estimate vehicle heading and rotate point cloud data.
    2. Spatial Filter: Filter point cloud data based on spatial boundaries.
    3. Lane Filter: Filter point cloud data based on the 'Layer' attribute.
    4. Intensity Filter: Filter point cloud data based on intensity.
    5, Spliting Lanes : Split the left and right lane based on origin
    6. Outlier Filter: Apply outlier filtering to refine lane data.
    7. Non-Linear Fitting: Fit cubic curves to detected lanes using the RANSAC algorithm.


## How to Use the Visualization Class:
    1. Import the required libraries and classes.
    2. Create an instance of the Visualization class, passing the path to the point cloud data file as an argument.
    3. Call the following methods on the instance to perform and visualize each step:

        - rotate_point_cloud()
        - plot_rotated_point_cloud()
        - load_data()
        - plot_spatial_filtered()
        - plot_layer_filtered()
        - plot_intensity_histogram()
        - plot_birds_eye_intensity_filtering()
        - plot_outlier_filtered_lanes()
        - plot_output()

## Important Notes:
scene3 and scene8: For scene3 and scene8, make sure to apply rotation to interpret the non-linear coefficients accurately. Rotation is a crucial step to ensure the correctness of the non-linear fitting process for these scenes.
By following this approach and using the provided Visualization class, you can effectively perform lane detection from point cloud data and visualize the results at each step.


To start the Visualization

```python
import numpy as np
from sklearn.decomposition import PCA
import matplotlib.pyplot as plt
from utils import Visualization
import warnings 
warnings.filterwarnings("ignore")
```

```python
visualization = Visualization("./data/scene1.bin", rotation = False)
visualization.plot_point_cloud()
```


1. Rotation ***(Scene3 & Scene8) should be used.***
The rotation process estimates the vehicle heading based on the principal components of the point cloud data and rotates the data accordingly. This can be done using the rotate_point_cloud() method. You can visualize the rotated point cloud data using the plot_rotated_point_cloud() method.

```python
visualization.plot_rotated_point_cloud()
```


2. Spatial Filter
The spatial filtering step filters the point cloud data based on specific spatial boundaries. Use the plot_spatial_filtered() method to visualize the point cloud data after spatial filtering.

```python
visualization.plot_spatial_filtered()
```

3. Lane Filter
This step filters the point cloud data based on the 'Layer' attribute. You can use the plot_layer_filtered() method to visualize the point cloud data after applying this filter.

```python
visualization.plot_layer_filtered()
```

4. Intensity Filter
Filtering based on the 'intensity' attribute is crucial. You can visualize the histogram of the intensity information using the plot_intensity_histogram() method. The plot_birds_eye_intensity_filtering() method helps visualize the intensity-filtered point cloud data.

```python
visualization.plot_birds_eye_intensity_filtering()
```

5. Spliting Lanes
After filtering the point clouds based on intensity values, the next step is to identify the left and right lanes within the filtered data. The split_two_lanes method is used to separate the points into two separate lanes based on their positions in relation to the origin. This allows us to focus on specific regions of interest corresponding to the lanes.

```python
visualization.plot_find_left_right_lanes()
```

6. Outlier Filter
The outlier filtering process involves filtering points based on their z-scores. Visualize the point cloud data after outlier filtering using the plot_outlier_filtered_lanes() method.

```python
visualization.outlier_filtering()
```

7. Non-Linear Fitting
Non-linear fitting using the RANSAC algorithm helps fit cubic curves to the detected lanes. You can visualize the output of the fitting process, including the cubic curves and the original data, using the plot_output() method.

Remember to create an instance of the Visualization class and call these methods on the instance to perform the respective processes and visualize the results. This class streamlines the entire lane detection process and makes it easy to visualize the effects of each step.