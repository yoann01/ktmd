---
layout: post
title:  Houdini VEX
tags: [Houdini, Vex]
categories:
- blog
---

## Vex Split string

prim wrangler > partition

Prim wrangler
```c
//s[]@a = split(s@shop_materialPath, "_");
//@a[-1]
sting bars[] = split(s@shop_materialPath, "_");
s@MatGrpName = bars[-1]
```
partition (will give primitive groups)
```c
part_`@matGrpName`
```
Material
Group -> part_wood

## DOP Random Air Resistance

This one-liner will simply add random air resistance per particle within the minimum and maximum values 

```c
	airresist *= fit01(@id,0.05,1);

```

## DOP Random Spin

This adds random spin to particles – put it in the popspin DOP 

```c
//Add Min and Max controls to node
axis = rand(@id) - set(0.5, 0.5, 0.5);
spinspeed *= fit01(rand(@id+0.1), ch("Min"), ch("Max"));
```

## SOP Fake Collisions Wrangle

This fella will push points within a volume outside of the volume. Pipe the collision SDF into the second input.
```c
vector grad = volumegradient(1, 0, @P);
float dist = volumesample(1, 0, @P);
    if(dist <= 0)
        @P -= normalize(grad) * dist;

```

## SOP Delete Points by Threshold

This snippet will delete random points based on the threshold slider. Taken from http://www.tokeru.com 
```c
if ( rand(@ptnum) > ch('threshold') ) {
   removepoint(0,@ptnum);
}
```

## SOP Create Lines Network

This snippet will create a network of lines based on distance threshold. Taken from Entagma’s “Creating Geo With Vex”  video 
```c
float searchrad = ch("rad");

int nearpnts[] = nearpoints(0, @P, searchrad);

foreach(int pnt; nearpnts){

    int line = addprim(0, "polyline");
    addvertex(0, line, @ptnum);
    addvertex(0, line, pnt);
    }
```

## SOP Random pscale with Ramp, Seed, Min and Max

This useful little dude will create a ramp that can be used with minimum, maximum and seed values to generate random pscale values with weighting.
```c
@pscale = fit01(chramp("Width", rand(@id  + ch("Seed"))), ch("Min"), ch("Max"));
```

## SOP Random Rotation Wrangle
A basic random rotation wrangle
```c
float angle = ch("rot_amount");
float rand = fit01(random(@ptnum+311),0,angle);
p@rot = quaternion(radians(rand), v@up);
```

## SOP Rotation Wrangle

This guy will enable randomised rotations on particles. Add a time variable ($T/$F) into the angle input to get them moving.
```c
f@speed = fit01(rand(@ptnum), ch('minSpeed'), ch('maxSpeed'));

float angle = (ch('angle')+@ptnum)*@speed;
vector axis = sample_direction_uniform(rand(@ptnum*ch('seed')));

@orient = quaternion(angle, axis);
```

## SOP Spiral Curve

Makes input curve into a spiral with controls
```c
@P.x = cos(@ptnum * ch("frequency")) * ch("amp_x") + ch("offset_x");
@P.y = @ptnum * ch("amp_y");
@P.z = sin(@ptnum * ch("frequency")) * ch("amp_z") + ch("offset_z");

```
