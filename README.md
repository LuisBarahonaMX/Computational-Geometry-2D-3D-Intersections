# Computational Geometry | 2D and 3D Intersections with Python

### Random Segment Generation, Geometric Intersections, Distance Calculations, and Spatial Visualization

<div align="center">

<img src="./geometria2d_3d.png" alt="Computational Geometry — 2D and 3D Spatial Analysis" width="650">

*Computational Geometry — Exploring geometric relationships, intersections, and spatial structures using Python.*

</div>

**Project Type:** Computational Mathematics and Geometry Experiments  
**Field:** Computational Geometry | Mathematics | Algorithms | Scientific Computing  
**Programming Language:** Python  
**Environment:** Google Colab | Jupyter Notebook  
**Author:** Data Engineer Luis Barahona

---

## 1. Project Overview

This project explores computational geometry through a collection of Python experiments involving randomly generated line segments in two-dimensional (2D) and three-dimensional (3D) coordinate systems.

The notebook investigates how numerical methods and visualization techniques can represent spatial relationships, calculate segment intersections, and explore distances between geometric points.

The experiments use NumPy for numerical operations and Matplotlib for graphical representations.

The notebook includes both introductory geometric calculations and experimental implementations that require additional mathematical validation.

Its primary purpose is educational: understanding how geometric objects can be represented and manipulated computationally.

---

## 2. Project Objectives

- Generate random points and line segments in 2D.
- Represent segments using Cartesian coordinates.
- Visualize multiple geometric objects.
- Calculate intersections between 2D segments.
- Explore determinant-based intersection formulas.
- Calculate Euclidean distances.
- Generate random segments in 3D.
- Explore spatial relationships among segments.
- Compare intersection and distance calculations.
- Generate repeated random geometric experiments.
- Identify limitations in numerical geometry algorithms.

---

## 3. Mathematical Foundations

### 3.1 Two-Dimensional Geometry

A point in a 2D coordinate system is represented by:

```text
P = (x, y)
```

A line segment is defined by two endpoints:

```text
Segment = [(x1, y1), (x2, y2)]
```

The notebook generates endpoints using NumPy:

```python
import numpy as np

x1, y1, x2, y2 = np.random.rand(4) * 10

segment = ((x1, y1), (x2, y2))
```

These coordinates are subsequently used for geometric calculations and visualization.

### 3.2 Three-Dimensional Geometry

A point in 3D space is represented by:

```text
P = (x, y, z)
```

A 3D segment contains two endpoints:

```text
Segment = [(x1, y1, z1), (x2, y2, z2)]
```

Random coordinates are generated using:

```python
x1, y1, z1 = np.random.rand(3) * 10
x2, y2, z2 = np.random.rand(3) * 10
```

The resulting segments are visualized using Matplotlib's 3D plotting capabilities.

---

## 4. Experiment 1 — Random Line Generation in 2D

The first experiment generates random line segments within a two-dimensional coordinate system.

### Procedure

1. Request the number of segments from the user.
2. Generate random endpoint coordinates.
3. Store the endpoints.
4. Plot the segments using Matplotlib.
5. Display the resulting geometric configuration.

### Example

```python
def draw_lines(lines):
    plt.figure(figsize=(8, 8))

    for line in lines:
        (x1, y1), (x2, y2) = line
        plt.plot([x1, x2], [y1, y2], "bo-")

    plt.xlabel("X")
    plt.ylabel("Y")
    plt.title("Random Line Segments")
    plt.grid(True)
    plt.show()
```

### Saved Experiment

The notebook includes a visualization generated with 22 random segments.

This experiment introduces the representation of geometric structures using Python.

---

## 5. Experiment 2 — Segment Intersections in 2D

The notebook explores intersection detection between pairs of randomly generated segments.

### Methodology

For each pair of segments, the algorithm:

1. Extracts the endpoint coordinates.
2. Calculates differences between coordinates.
3. Uses determinants to calculate a candidate intersection.
4. Checks whether the candidate point lies within both segments.
5. Records the intersection when the conditions are satisfied.

### Determinant Function

```python
def det(a, b):
    return a[0] * b[1] - a[1] * b[0]
```

Determinants are useful for solving equations describing intersections of nonparallel lines.

### Pairwise Comparison

The notebook uses combinations and nested iteration to examine segment pairs.

For n segments, the number of distinct pairs is:

```text
n(n - 1) / 2
```

This produces quadratic growth in the number of candidate comparisons.

### Saved Result

One experiment reports:

| Metric | Value |
|:---|---:|
| Generated segments | 22 |
| Calculated intersections | 40 |

This result belongs to a specific randomly generated configuration.

Because no fixed random seed is used, executing the same experiment again may produce different coordinates and intersection counts.

---

## 6. Experiment 3 — Distance Calculations in 2D

The notebook explores distances associated with line segments and calculated intersections.

### Euclidean Distance

For two points:

```text
A = (x1, y1)
B = (x2, y2)
```

The Euclidean distance is:

```text
d(A, B) = sqrt((x2 - x1)^2 + (y2 - y1)^2)
```

### Python Implementation

```python
distance = np.linalg.norm(
    np.array(point1) - np.array(point2)
)
```

### Experimental Calculations

Several notebook sections explore:

- Distances between geometric points.
- Distances between segment midpoints.
- Distances between calculated intersection points.
- Distances between intersections and segment endpoints.

These calculations illustrate the use of NumPy for geometric measurements.

### Important Distinction

The distance between segment midpoints is not necessarily the shortest distance between two segments.

Likewise, an intersection-point distance calculation must be associated with the correct geometric segments.

The notebook contains exploratory implementations that would benefit from additional validation.

---

## 7. Experiment 4 — Random Line Generation in 3D

The next group of experiments extends line segment generation into three-dimensional space.

### Procedure

1. Request the number of segments.
2. Generate random 3D coordinates.
3. Store the segment endpoints.
4. Create a Matplotlib 3D figure.
5. Plot the segments.
6. Display the resulting spatial configuration.

### Python Example

```python
fig = plt.figure(figsize=(10, 8))
ax = fig.add_subplot(111, projection="3d")

for line in lines:
    (x1, y1, z1), (x2, y2, z2) = line

    ax.plot(
        [x1, x2],
        [y1, y2],
        [z1, z2],
        marker="o"
    )

ax.set_xlabel("X")
ax.set_ylabel("Y")
ax.set_zlabel("Z")
plt.show()
```

### Saved Experiments

The notebook includes 3D visualizations involving 22, 33, and 66 randomly generated segments.

These plots help illustrate the complexity of spatial geometry compared with planar geometry.

---

## 8. Experiment 5 — Experimental 3D Intersection Detection

The notebook includes several attempts to calculate intersections among line segments in 3D.

These implementations explore determinant-based calculations and coordinate relationships.

### Mathematical Challenge

Two segments in 3D do not necessarily intersect, even when their projections intersect in a two-dimensional plane.

Segments can be:

- Intersecting.
- Parallel.
- Collinear.
- Skew, meaning they are not parallel but do not intersect.

### Current Implementation

The notebook contains experimental 3D formulas that do not consistently verify whether the calculated coordinates belong to both segments.

Some calculations use squared expressions that do not represent a general, validated solution to 3D segment intersection.

Consequently, reported intersection counts in these sections should be treated as experimental outputs rather than mathematically verified results.

### Required Improvements

A more reliable implementation should:

1. Represent segments parametrically.
2. Determine whether their supporting lines are parallel or skew.
3. Calculate closest points on both segments.
4. Apply a numerical tolerance.
5. Confirm that both segment parameters lie within valid bounds.
6. Distinguish actual intersections from nearby but nonintersecting segments.

---

## 9. Experiment 6 — Experimental Volume Estimation

One notebook section explores a Monte Carlo-inspired volume calculation.

The implementation generates random points within a coordinate bounding region.

It counts points satisfying coordinate-range conditions associated with the generated segments.

### Saved Result

One 66-segment execution reports an approximate value of:

```text
681.73
```

The notebook labels this value as an approximate volume.

### Interpretation

The generated segments do not define a closed solid.

The coordinate-range test therefore does not establish a mathematically meaningful enclosed geometric volume.

Similarly, counting the number of segments as the number of faces does not establish a valid polyhedral face count.

This experiment should be regarded as an exploration of random sampling and geometric bounds, not a validated volume estimation method.

---

## 10. Experiment 7 — Multiple Random Configurations

The notebook includes an experiment that generates repeated random geometric configurations.

### Procedure

1. Request the number of segments.
2. Generate multiple random configurations.
3. Display each configuration.
4. Execute the experimental intersection-counting procedure.
5. Print the resulting counts.

### Configuration

The final exercise generates 30 separate random configurations.

Each configuration can contain multiple randomly generated 3D segments.

### Computational Consideration

For 33 segments, the number of possible unordered pairs is:

```text
33 × 32 / 2 = 528
```

The saved output includes a reported count of 528.

This corresponds to the number of possible pairs, not evidence that all pairs geometrically intersect.

The current routine requires correction before its counts can be interpreted as valid 3D intersection results.

---

## 11. Technologies Used

| Technology | Purpose |
|:---|:---|
| Python | Programming language |
| NumPy | Random coordinate generation and numerical calculations |
| Matplotlib | Two-dimensional visualization |
| Matplotlib mplot3d | Three-dimensional visualization |
| itertools | Combinatorial iteration |
| collections | Dictionary-based data organization |
| Pandas | Structured experimental data |
| Google Colab | Cloud notebook environment |
| Jupyter Notebook | Interactive execution |

---

## 12. How to Run

### Google Colab

[Open the Computational Geometry Notebook](https://colab.research.google.com/drive/1kCBsk50kuee6xRFbhbIPrtbIJO5IPQkX)

### Install Dependencies

```bash
pip install numpy matplotlib pandas notebook
```

### Local Execution

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open the notebook and execute the desired experiment.

### Execution Instructions

1. Import the required libraries.
2. Select a geometric experiment.
3. Run its code cell.
4. Enter the requested number of segments.
5. Provide additional parameters where required.
6. Examine the generated visualization.
7. Review the calculated output.
8. Compare the results with the limitations described in the notebook.

### Important Notes

- Several functions share the same names across notebook sections.
- Execute experiments independently to avoid unintended function redefinitions.
- Some cells require multiple interactive inputs.
- The random coordinates change between executions.
- The notebook does not set a global random seed.
- Large experiments may produce extensive printed output.

---

## 13. Computational Complexity

Pairwise segment comparison requires considering:

```text
n(n - 1) / 2
```

candidate pairs.

The basic implementation therefore has approximately:

```text
O(n²)
```

pairwise comparison complexity.

For larger datasets, more advanced geometric algorithms and spatial indexing techniques may reduce unnecessary comparisons.

Possible approaches include:

- Sweep-line algorithms for planar intersections.
- Bounding-box filtering.
- Spatial indexing.
- Vectorized numerical operations.
- Optimized computational geometry libraries.

The notebook demonstrates basic pairwise processing rather than optimized large-scale geometric analysis.

---

## 14. Important Limitations

This is an experimental computational geometry notebook.

### Randomness

The input coordinates are generated randomly without a fixed seed, making exact numerical results difficult to reproduce.

### Numerical Precision

Exact floating-point equality tests may fail for geometrically equivalent coordinates.

### 2D Degenerate Cases

Collinear overlaps and other degenerate segment configurations require additional handling.

### 3D Intersection Validation

Several 3D routines do not correctly verify whether segments intersect in three-dimensional space.

### Distance Interpretation

Some distance calculations do not measure the shortest distance between geometric segments.

### Volume Estimation

The Monte Carlo-inspired calculation does not represent the volume of a defined closed solid.

### User Input

Some experiments request line lengths but do not consistently use those values to construct segments of the requested length.

### Repeated Function Names

Functions are redefined across sections, which can affect notebook execution.

### Computational Performance

Pairwise algorithms become increasingly expensive as the number of segments grows.

---

## 15. Future Improvements

Potential developments include:

- Implementing robust 2D segment intersection algorithms.
- Developing correct 3D segment intersection tests.
- Adding numerical tolerance handling.
- Detecting parallel, overlapping, and skew segments.
- Validating coordinates and user input.
- Introducing reproducible random seeds.
- Improving distance calculations.
- Implementing spatial indexing.
- Comparing computational performance.
- Adding automated unit tests.
- Creating interactive 2D and 3D visualizations.
- Separating experiments into reusable Python modules.
- Exploring established computational geometry libraries.

---

## 16. Potential Applications

The mathematical concepts studied in this project can support:

- Computer graphics.
- Geometric simulation.
- Robotics and motion planning.
- Geographic information systems.
- Engineering visualization.
- Collision detection research.
- Spatial data analysis.
- Scientific computing.
- Computer-aided design.

These are potential application areas for computational geometry in general, not validated production capabilities of the current notebook.

---

## 17. Conclusion

This project demonstrates fundamental computational geometry concepts using Python, NumPy, and Matplotlib.

Through a series of experiments, the notebook explores two-dimensional and three-dimensional segment generation, candidate intersection calculations, Euclidean distances, and spatial visualization.

The 2D exercises provide practical demonstrations of determinant-based intersection techniques and coordinate bounds.

The 3D experiments illustrate the additional complexity of spatial geometry while revealing important limitations in the current intersection and volume calculation routines.

Overall, the project provides an educational foundation for further research into numerical geometry, algorithm optimization, and spatial computing.

---

## 18. Project Resources

### Google Colab Notebook

[Open the Original Computational Geometry Notebook](https://colab.research.google.com/drive/1kCBsk50kuee6xRFbhbIPrtbIJO5IPQkX)

### NumPy Documentation

[NumPy — Numerical Computing](https://numpy.org/doc/stable/)

### Matplotlib Documentation

[Matplotlib — Visualization](https://matplotlib.org/stable/)

### Python Documentation

[Python — Official Documentation](https://docs.python.org/3/)

---

## Author

**Data Engineer Luis Barahona**

Mexican Data Engineer and 2026 graduate of Universidad del Caribe, interested in Data Engineering, Data Science, Artificial Intelligence, algorithms, and computational mathematics.

---

## Contact

| Platform | Contact |
|:---|:---|
| Email | [190300395@ucaribe.edu.mx](mailto:190300395@ucaribe.edu.mx) |
| GitHub | [github.com/LuisBarahonaMX](https://github.com/LuisBarahonaMX) |
| LinkedIn | [linkedin.com/in/luis-barahona-mx](https://www.linkedin.com/in/luis-barahona-mx/) |
| Instagram | [@luisbarahonamx](https://www.instagram.com/luisbarahonamx/) |
| X | [@luisbarahonaMX](https://x.com/luisbarahonaMX) |
| Website | [SIKO AI Platform](https://sikoai.web.app/) |
