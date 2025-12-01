---
title: Drone-based forest mapping
authors:
  - admin
  - David Russell
  - Amritha Pallavoor
summary: "Developing methods to map forests at the individual tree level using drones, photogrammetry, and computer vision"

date: 2025-01-01
show_date: false
profile: true
image:
  focal_point: ''
  preview_only: true
  # caption: Automatically detected treetops, with point size indicating tree height, overlaid on drone-derived orthoimagery from the Tahoe National Forest

banner:
  caption: "Emerald Point, Lake Tahoe, USA"
  image: "tahoe2.jpg"

gallery_item:
- album: photogrammetry
  image: 1-dsm.png
  caption: Digital surface model
- album: photogrammetry
  image: 2-chm.png
  caption: Canopy height model
- album: photogrammetry
  image: 3-orthomosaic.png
  caption: Orthomosaic
- album: photogrammetry
  image: 4-stem-map.png
  caption: Treetops, with point size proportional to tree height, overlaid on orthomosaic

---

Our tree mapping work supports the [<i class="fas fa-arrow-up-right-from-square"></i> Open Forest Observatory](http://openforestobservatory.org).

We are developing an open-source, automated workflow for producing high-accuracy, spatially extensive (10-300 ha) maps of forest stands at the individual tree level using drone imagery. Potential applications of these maps include planning post-fire reforestation treatments, developing thinning and prescribed fire prescriptions, and quantifying carbon stocks. Our workflow enables mapping of over 50 ha (125 acres) of forest area in less than 2 days of a single technician's time (including collection of drone imagery using a single consumer drone and data processing). The workflow has several steps:

### 1. Image collection and photogrammetry

We collect many partially overlapping drone photos across the site. This means any given tree appears in many photos, each from a slightly different angle.

{{< figure src="photogrammetry.jpg" caption="Example of an individual tree viewed from multiple angles in separate drone images." >}}

Because each tree is visible from multiple angles, it is possible to use methods related to stereo vision (specifically, *photogrammetry*) to estimate each tree's 3D structure. The photogrammetry algorithm produces a 3D cloud of points that is very similar to lidar data.

{{< figure src="lidar.PNG" caption="Visualization of a 3D point cloud from our Emerald Point site produced via photogrammetry." >}}

The photogrammetry algorithm is also used to produce an orthomosaic, which is a high-resolution aerial image produced by stitching together the numerous drone photos. It resembles NAIP or Google Earth imagery but generally has much finer resolution (~ 3 cm).

Photogrammetric processing requires parameterization for the specific application. We have thoroughly tested parameterizations for individual tree detection in structurally complex conifer forests and published our results, including recommended parameter values, in [<i class="far fa-file-lines"></i> Methods in Ecology and Evolution](https://besjournals.onlinelibrary.wiley.com/doi/10.1111/2041-210X.13860). We have also built and continue to maintain a [<i class="fab fa-github"></i> software library](https://github.com/open-forest-observatory/automate-metashape) that makes it easy to run multiple photogrammetry workflows with pre-specified parameterizations in a documented, reproducible way.

### 2. Canopy height model (CHM) production

After creation of a point cloud, we process it to compute a digital surface model (DSM). The DSM is a high-resolution (~10-cm) raster indicating the elevation of the vegetation (or ground) surface in each pixel. Then, we subtract elevation values derived from a high-resolution digital elevation model (DEM). The result is a canopy height model (CHM) indicating the height of the vegetation above the ground in each pixel.

{{< gallery album="photogrammetry" >}}


### 3. Tree detection

Next, using a geometric algorithm such as a variable-radius local-maximum filter or a computer vision model like [DeepForest](https://github.com/weecology/DeepForest) with some post-processing, we detect individual tree tops, and their associated heights, from photogrammetry products like the orthomosaic or canopy height model. The selection and parameterization of the optimal tree detection algorithm is a complex process and can depend on the approach used for drone imagery collection and processing. We have evaluated the interactions between these choices for parameterization of a local-maximum filter tree detector and identified a an accurate tree detection parameterization for structurally complex conifer forests. The results are published in [<i class="far fa-file-lines"></i> Methods in Ecology and Evolution](https://besjournals.onlinelibrary.wiley.com/doi/10.1111/2041-210X.13860). We are currently evaluating how the optimal parameterization depends on the forest type and developing guidelines for tree detection in forests of different types. We are also evaluating parameterization of the computer vision model DeepForest for tree detection from an orthomosaic and comparing its performance to the local-maximum filter approach.

Applying tree detection methods -- particularly computer vision approaches -- to large geospatial datasets involves substantial pre-processing (e.g., to break up the large orthomosaic into small "chips" that are accepted by the computer vision model) and post-processing (e.g., to stitch together the predicted tree locations from each chip and restore the geospatial information). We have developed an open-source, user-friendly [Tree Detection Framework](https://github.com/open-forest-observatory/tree-detection-framework) that provides a standardized user interface to multiple back-end models and automates the pre- and post-processing steps.

We are beginning exploration of the potential for using computer vision to detect trees directly from raw drone images, rather than from geospatial data products, and projecting the detected tree locations onto geospatial layers. This approach has the potential to improve tree detection accuracy by leveraging the multiple viewing angles of each tree present in the raw drone images. This approach relies on our tool [Geograypher](https://github.com/open-forest-observatory/geograypher), which enables translation between raw drone images and geospatial layers.

### 4. Tree species identification

After identifying the locations and sizes of individual trees, the next step is to identify each tree taxonomically. We are building a computer vision approach to classify the drone-derived images of each tree into species categories. We take advantage of the fact that each tree appears in dozens to hundreds of individual drone images, often from side angles, allowing us to use the multiple viewing angles to more confidently identify the tree to species. This approach is known as multi-view computer vision.

{{< figure src="multiview-species-id.png" width="500px" title="Workflow for programmatically isolating images of individual detected trees for AI-based species identification. (1) The tree is detected using the CHM, orthomosaic, and/or point cloud. (2) The top and bottom of the tree are projected from 3D space onto the drone photo. (3) The tree top and bottom are used to create a bounding box to crop the single tree from the image. (4) The process is repeated for every drone image in which the focal tree appears. The resulting images are supplied to the computer vision image classification algorithm." >}}

To translate between raw drone images (which are not geospatial) and the geosptaial mapping products such as the orthomosaic, we have developed the open-source and user-friendly tool called [Geograypher](https://github.com/open-forest-observatory/geograypher). Using this software, a geospatial map of species identities (e.g., from a field survey) can be projected onto the raw drone images and used for training a computer vision algorithm to identify tree species from the raw drone images. Similarly, if one has computer vision predictions of tree species from raw drone images, Geograypher can project these tree species labels into geographic space for mapping purposes.

## Funding and support

<div class="container text-center align-content-middle">
  <div class="row">
    <div class="col-sm">
{{< figure src="cal_fire_logo_small.png" width="120px" >}}
    </div>
    <div class="col-sm">
{{< figure src="cci_logo_small.png" width="200px" >}}
    </div>
    <div class="col-sm">
{{< figure src="NSF_4-Color_bitmap_Logo.png" width="200px" >}}
    </div>
    <div class="col-sm">
{{< figure src="the-nature-conservancy-vector-logo.png" width="200px" >}}
    </div>
  </div>

</div>