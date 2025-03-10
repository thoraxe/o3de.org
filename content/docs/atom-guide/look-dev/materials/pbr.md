---
linktitle: PBR Materials
title: "Physically Based Rendering in Materials"
description: "Learn about physically based rendering and how it applies to materials in Atom."
toc: true
weight: 200
---  

{{< preview-new >}}
{{< todo issue="https://github.com/o3de/o3de.org/issues/688" >}}
{{< /todo >}}

Physically based rendering (PBR) is rendering in a photorealistic way by simulating the physics of real-world lighting models. The following sections describe the basic concepts underlying PBR and how they relate to PBR material types in Atom.

## PBR Shading Model

The fundamental materials used in Atom are based on PBR shading models. The PBR shading model is composed of properties that describe how a material interacts in the physical world. At the basic level, the PBR shading model requires the following properties: base color, metallic, roughness, and specular reflectivity. These properties are enough to define materials such as wood, metal, concrete, and other raw materials. However, materials can become much more complex with properties such as clear coating, subsurface scattering, and more. For example, varnished wood is made from a basic wood material type with an additional clear coating on top.  

The following list of properties are used to define PBR materials in Atom. An overview of which properties are included in which material type is shown in the [Properties in PBR Material Types](#properties-in-pbr-material-types) table. 

| Property | Definition |
| - | - |
| [Base Color](#base-color) | The surface reflected color for non-metals (dielectrics) or reflectance values for metals (conductors). |
| [Metallic](#metallic) | Whether the surface appears metallic or not. |
| [Roughness](#roughness) | Apparent smoothness or roughness of a surface. |
| [Specular Reflectance f0](#specular-reflectance-f0) | Apparent reflectance of non-metal surfaces. The constant f0 represents the specular reflectance at normal incidence (Fresnel 0 angle). |
| Emissive | A mechanism to simulate light emitting from the surface. |
| Occlusion | Describes how much ambient light affects a point on a surface using baked AO and Cavity texture maps. |
| Opacity | Transparency levels of a surface. |
| Normal | A texture mapping technique that simulates bumpiness on a surface. Similar to bump maps. |
| UVs | Texture coordinates that describe how a texture maps to a surface. |
| Clear Coat | A thin translucent layer on top of the surface. |
| Subsurface Scattering | A mechanism that simulates how light that penetrates translucent surfaces is scattered and absorbed before exiting the surface at a different location. |
| Irradiance | Describes how a surface interacts with the global illumination (GI) system's diffuse lighting environment. It does not affect the appearance of the material itself. |
| Parallax | Improves the apparent bumpiness on a surface by displacing texture coordinates, giving an illusion of depth. Also known as displacement mapping. |

### Base Color

The **base color** defines the diffuse albedo for non-metals, and the specular color for metals. 

When configuring the **Base Color** property group in a PBR material type, you can set a linear sRGB color in the `Color` property. This color can be combined with a texture by assigning an image to the `Texture Map` property. The `Texture Blend Mode` dictates how the `Color` and `Texture Map` are combined. And the `Factor` value can be used to adjust the strength of the blend. Colors are stored as linear sRGB on disk and later converted to ACEScg before passing to the shaders and the GPU (for more information, see [Color Management](docs/atom-guide/look-dev/color-management/index.md)). 

### Metallic 

The **Metallic** properties determine whether a material behaves as a dielectric (non-metal) surface, or as a conductor (metal) surface. The metallic value is usually either a completely metal (1) or completely non-metal (0), though in between values will occur when transitioning between the two using a texture map. 

When configuring the **Metallic** property group in a PBR material type, the metallic value is defined using the `Factor` property for uniform surfaces. For surfaces with varying levels of metalness, you can assign an image in the `Texture Map` property to indicate values between 0 and 1 per pixel. 

### Roughness

The **Roughness** properties determine the roughness or glossiness of a surface. The rougher a surface is, the more blurred its reflections appear to be. 

When configuring the **Roughness** property group of a PBR material, the `Factor` property defines how rough (factor = 1) or smooth (factor = 0) a material is, for uniform surfaces. For surfaces with varying levels of roughness, you can assign an image in the `Texture Map` property to indicate roughness values per pixel. You can adjust how the values of the texture map translate to roughness level using the `Upper Bound` and `Lower Bound` properties. 

### Specular Reflectance f0

The **Specular Reflectance f0** properties determine how much light reflects from dielectric (non-metal) surfaces. (Specular reflectivity on conductor (metal) surfaces are controlled by the [**Base Color**](#base-color)). Specular reflection is based on the Fresnel effect, a model which describes how the amount of light that reflects from a surface depends on the viewing angle and the index of refraction (IOR). When looking straight ahead at a surface, the view is at a 0-degree angle, also known as a normal incidence. From this viewing angle, the amount of light reflected is denoted by f0. The f0 values lie in the range 0 to 0.08, meaning the amount of light reflected can be between 0% to 8%. 

When configuring the **Specular Reflectivity f0** property group in a PBR material type, you can specify a specular reflectance value between 0 and 1 in the `Factor` property. This value is mapped to the [0,0.08] range, representing an f0 value between 0% and 8%. For surfaces with varying levels of specular reflectivity, you can assign an image to the `Texture Map` property to indicate values between 0 and 1 per pixel. A texture map is most useful for composite materials, or materials with a significant variation of material types (for example, material for a character with skin, a metal belt, and a leather watch). 

### Multi-scattering Compensation

By default, Atom uses a lighting model that assumes light only bounces once (single-scattering); but in reality, light may bounce multiple times (multi-scattering). With **multi-scattering compensation**, you can configure the lighting model to perform additional calculations to produce more accurate surface lighting. 

You can take multi-scattering into account in your materials by toggling `Multiscattering Compensation`. For a bit extra performance cost, this simulates the fact that light may bounce off a rough surface multiple times at the microscopic level. This feature makes the lighting on certain materials appear more realistic (brighter). The impact is most noticeable on rough metallic surfaces. For smooth surfaces and non-metal surfaces, the impact likely won't be noticed and should be disabled.

## Properties in Material Types

The following table lists which properties are included in which PBR material types.
| Property | StandardPBR | EnhancedPBR | StandardMultilayerPBR |
| -- | -- | -- | -- |
| Base Color  | X | X | X |  
| Metallic  | X | X | X |  
| Roughness  | X | X | X |  
| Specular Reflectivity F0  | X | X | X |  
| Emissive  | X | X | X |  
| Occlusion | X | X | X |  
| Opacity  | X | X |  |  
| Normal  | X | X | X |  
| UVs  | X | X | X |  
| Clear Coat  | X | X | X |  
| Subsurface Scattering  | X | X |  |  
| Irradiance | X | X | X |  
| Parallax | X | X |  |  
| Anistropic Material Response |  | X |  |
| Detail Layer | X | X |  |
| Detail Layer UV | X | X |  |
