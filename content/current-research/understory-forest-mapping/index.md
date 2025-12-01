---
title: Automated understory fuel inventory
authors:
  - admin
  - David Russell
  - Amritha Pallavoor
summary: "Using 360-degree ground imagery for automated understory vegetation and fuel inventory"

date: 2022-01-02
show_date: false
profile: true
image:
  focal_point: ''
  preview_only: false
  # caption: Automatically detected treetops, with point size indicating tree height, overlaid on drone-derived orthoimagery from the Tahoe National Forest

---

Our automated mapping work supports the [<i class="fas fa-arrow-up-right-from-square"></i> Open Forest Observatory](http://openforestobservatory.org).

Most approaches to automated forest inventory use sensors above the tree canopy, mounted on drones, other aircraft, or satellites. While these approaches can be very powerful, they also have a major limitation: they struggle to accurately capture the forest understory. This limitation is especially great in denser stands with higher canopy cover and lower visibility of the forest understory from above. The understory contains surface fuels, small trees, and other vegetation that is often critical to understand clearly for many ecological and forest management applications, including fire modeling and drought vulnerability forecasting.

To address this gap, we are developing methods to complement our [drone-based automated over-canopy forest inventory methods](/current-research/drone-forest-inventory) with 360-degree understory imagery. To employ this approach, a technician on foot walks a series of transects with a consumer-grade 360-degree camera, such as a GoPro, on a pole. The resulting images can be processed using photogrammetry algorithms much like we do with over-canopy drone imagery. We are developing methods that employ computer vision to segment different understory object types (e.g., tree stem, foliage, log, shrub) in the raw 360-degree images and then project them into 3D geographic space using the Geograypher tool we have developed. The resulting labeled geospatial model can then be summarized to obtain ecologically relevant information, including estimates of the cover and volume of shrubs and logs and the count, locations, and species of understory trees. Ultimately, we wil merge the under-canopy map with the overstory tree data derived by drone to produce a holistic, automated inventory of a forest stand.

Our methods will allow for greatly increased efficiency of forest inventory, a normally very expensive and time-consuming process that is often essential for planning effective forest management. In addition, our approach will enable automated change quantification through repeat surveys of the same sites, supporting quantification and monitoring of forest management effects and outcomes to inform adaptive management.

<!-- Add photos: CV segmented image, segmented mesh -->

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