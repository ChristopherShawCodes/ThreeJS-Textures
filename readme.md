# Three.js Journey

## Setup

# Install dependencies (only the first time)

`npm install`

# Run the local server at localhost:8080

`npm run dev`


---------------------------------------------------------

            --Textures--

https://marmoset.co/posts/basic-theory-of-physically-based-rendering/



-Commonly Used Textures-

---------------------

Color (or Albedo)

-applied on the geometry 

---------
Alpha

-Grayscale image 

-White is visible

-Black not visible

-----------

Height (or Displacement)

-Grayscale image

-Move the vertices to create some relief

--------------
Normal

-add details (lighting)

-verticies won't move 

-doesnt need subdivision 

--------------------

Ambient Occlusion

-Grayscale image

-Adds fake shadows in the crevices (where angles meet, to add contrast )

-Not physically accurate 

-Helps to create contrast 

----------------------------

Metalness

-Grayscale image

-white is metallic

-black is non-metallic 

-used to create reflections 

-------------------------------
Roughness

-Grayscale image

-White is Rough

-Black is smooth 

-Mostly for light dissipation (light doesnt reflect )

----------------------------------------------------

Textures follow PBR principles 

-Physically Based Rendering

-Standard for achieving realistic experiences 

---------------------------------------------------



---------------------------------------------------------

                    How To Load Textures ? 


HINT: One textureLoader can load more than ONE TEXTURE 

1. Use TextureLoader to grab the image and convert it into a texture

2. Apply texture to the material for rendering 

            `const textureLoader = new THREE.TextureLoader()
            const texture = textureLoader.load('/textures/door/color.jpg')



            const material = new THREE.MeshBasicMaterial({ map: texture })`


-------
--------------------------------------------------------
Optional *

From here we can send 3 functions after the image PATH to show console.logs for the images being loaded .

This could be helpful if there is an error loading an image. 

 -load: when the image loaded successfully 
 
 -progress: when the loading is progressing 
 
 -error: when an error occurs 

            `const texture = textureLoader.load(
    '/textures/door/color.jpg',
    () =>
    {
        console.log('Images loaded')
    },
    () =>
    {
        console.log('progress')

    },
    () =>
    {
        console.log('error loading image')

    })`

--------------------------------------------------------

Example of multiple textures being loaded via static images 

            `const loadingManager = new THREE.LoadingManager()
            const textureLoader = new THREE.TextureLoader(loadingManager)


            const colorTexture = textureLoader.load('/textures/door/color.jpg')
            const alphaTexture = textureLoader.load('/textures/door/alpha.jpg')
            const heightTexture = textureLoader.load('/textures/door/height.jpg')
            const normalTexture = textureLoader.load('/textures/door/normal.jpg')
            const ambientOcclusionTexture = textureLoader.load('/textures/door/ambientOcclusion.jpg')
            const metalnessTexture = textureLoader.load('/textures/door/metalness.jpg')
            const roughnessTexture = textureLoader.load('/textures/door/roughness.jpg')`

-------------------------------------------------------

The texture gets placed on the object based on the UV coordinates
