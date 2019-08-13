## Use container images as build artefacts

1. Build your app from Dockerfiles

2. Store the resulting images in a registry

3. Keep them forever (or as long as necessary)

4. Test those images in QA, CI, integration...

5. Run the same images in production

6. Something goes wrong? Rollback to previous image

7. Investigating old regression? Old image has your back!

Images contain all the libraries, dependencies, etc. needed to run the app.
