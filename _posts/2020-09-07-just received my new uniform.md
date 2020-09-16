---
layout: post
title: Just received my new Uniform
author: Thomas
excerpt: Why and how we replaced the "Uniform" distribution type
comments_url: 
---



The Uniform distribution type was originally created to tackle an inherent issue with random distribution: gaps.
When you randomly distribute points on a plane, some areas will be more dense, some less dense. There is no way around it, it is the nature of randomness.

But vegetation rarely grows that way. When there is an existing plant, it's very unlikely that another plant will grow almost at the same spot. There won't be enough nutrients, light, etc. Similarly, it's unlikely that there will be empty spaces on the ground, plants tend to grow wherever there is space, light, and decent soil. This is especially true for certain types of plants, like grass and other groundcover.

That's why the "Uniform" distribution type came to be. It is intended to look somewhat random, while avoiding empty spaces or clumps.

![uniform_random]({{ site.url }}/images/uniform_random.png)

In Skatter v1, Uniform was a simple variation of the Grid distribution type. We start with a grid, then randomly move each point within a distance equal to the spacing of the grid, times a percentage (100% by default).
You can think of it as dividing the surface as cells, then randomly placing the points within these cells. Each cell has no more and no less than one object.

![uniform_cells]({{ site.url }}/images/uniform_cells.jpg)

This approach produces decent results, but there are still some points that are very close to one-another.

We thought we could to better for Skatter v2. We created an algorithm very similar to the Poisson-disc sampling algorithm. Basically, we start with a random point, then we look for another random point that is not to far, and not too close from all the points already generated. We repeat until the whole surface is covered.

Here is a great gif that explains it better than I can:

<img src="{{ site.url }}/images/poisson_disk_distribution.gif" alt="poisson_disk_distribution" style="zoom:50%;" />



The result is a much more even distribution that still looks random:

![uniform_v1_vs_v2]({{ site.url }}/images/uniform_v1_vs_v2.jpg)