# Licensing

All Python scripts written for Blender must be open source and compatible with the GPL license. Assets made for or with Blender that are not code, however, do not necessarily need to be open source. This could include custom icons, images, models, scenes, or node groups. 

To use non-GPL assets with a Blender add-on, the add-on must be able to run without error and be considered an independant program with or without them. Assets can be used as a way to unlock certain features depending on the attributes of the asset. For example, it would not be ok for an add-on to depend on an asset and error out if it is changed or missing, but it would be ok for the add-on to detect that an asset with certain attributes is avaliable and change its behavior accordingly. 

Any code that cannot be open source must be created as a separately run program and communicated with via an add-on that acts only as a bridge between the outside program and Blender’s API. 

The license or licenses should be clearly stated in a text document at the top level of the distributed folder and be communicated to users before they purchase or download the files. 