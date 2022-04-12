---
layout: post
title: Calculating Planet Volumes Using NumPy
image: "/posts/calculating-planet-volumes-title-img.png"
tags: [Python, NumPy, Planets]
---

For us who are fond of the planets of the solar sytem, we would be curious about the volumes of each of the planets. It is easy to calculate them through the formula for the volume of a sphere.

What if we were to calculate the volumes of a large number of planets? Let's say a million of them?

In this post, I'll be showing the how NumPy can perform this calculation very fast.

---

From a very quick search, we can find through Google that the radius measurements of the planets in the solar system, from Mercury to Neptune are as follows:

```python
radii = np.array([2439.7, 6051.8, 6371, 3389.7, 69911, 58232, 25362, 24622])
```

As we all know, the formula for a sphere (since planets are typically spherical) is just (4/3 × π × r^3).

In Python, let's try it for a radius of 10.

```python
r = 10
volume = 4/3 * np.pi * r**3
print(volume)
>>> 4188.790204786391
```

Doing the above would only be applicable for a single volume.

How are we to calculate the volume for all eight planets?

Yes, we could do this by creating a loop that iterates through each planet. But we can do this more swiftly through NumPy.

In order to do so, we can just copy the previous block of code and change the variable name from ```r``` to ```radii``` which we declared in the earlier part of this post.

```python
volumes = 4/3 * np.pi * radii**3
print(volumes)
>>> [1.65644412e+09 4.28023694e+07 1.91978124e+09 ... 1.22488896e+07
 1.90488003e+09 1.21524146e+09]
```

What if instead of just 8 planets we were to go further and calculate the volues for 1,000,000 planets?

For demonstrating this, we can generate radii for these using the ```np.random.randint()``` function.

Here we are just overriding the previous radii variable with:

```python
radii = np.random.randint(1, 1000, 1000000)
```

We can then use the same formula as above to calculate the volumes. If you run this, you will find that it takes less than a second to complete, almost an instant.

```python
volumes = 4/3 * np.pi * radii**3
print(volumes)
>>> [2.83512464e+09 5.88494864e+06 4.10515850e+07 ... 3.50139670e+09
 6.16008724e+07 2.75833092e+06]
```

To double check if it indeed produced an output of 1M volumes, just check the length of the array.

```python
len(volumes)
>>> 1000000
```
