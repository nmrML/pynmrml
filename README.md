# pynmrML 

pynmrML is a Python library for reading, writing and interfacing with [nmrML](http://nmrml.org) documents. It includes nmrML bindings, nmrCV bindings, and readers and writers for several different NMR formats. It relies on the excellent [NMRglue library](https://github.com/jjhelmus/nmrglue) for processing raw NMR data.

## Installation 

### Installation Prerequisites:
* [scipy](http://www.scipy.org)
* [numpy](http://numpy.scipy.org)
* [lxml](http://lxml.de/)
* [nmrglue](https://github.com/jjhelmus/nmrglue)


### Development Prerequisites:
generateDS.py is required to autogenerate the bindings.

1. [Download generateDS](https://pypi.python.org/pypi/generateDS/#downloads) and install with easy_install:

```bash
wget https://pypi.python.org/packages/2.7/g/generateDS/generateDS-2.11a-py2.7.egg#md5=bf753618fbc822bd9ed66eeb2ceae3b6  
easy_install generateDS-2.11a-py2.7.egg
```

## Library structure

* __nmrML.py__ Enhanced XML bindings that inherit from the autogenerated bindings in __nmrML_lib.py__. This is the class that should be used for interfacing with nmrML since this allows for enhancement while being able to easily regenerate __nmrML_lib.py__ to keep it up to date with nmrML schema development.
* __nmrML_lib.py__ Autogenerated XML bindings (by generateDS.py), should not be used directly
* __cv__ Classes for parsing, and using the nmrCV
* __io__ Factory for building readers and writers
* __readers__ Classes for reading from different formats, a reader for a format should inherit from the AbstractReader class to ensure that they implement the correct interface.
* __writers__ Classes for writing out to different formats (currently only nmrML)
* __util__ Utility classes useful in different parts of the library
	* __util/convert__ unit conversion functions 

## Modifying the XML bindings 

The XML bindings are generated with generateDS.py, for info see http://pythonhosted.org/generateDS/

As described above __nmrML_lib.py__ Autogenerated XML bindings (by generateDS.py), should not be used directly while __nmrML.py__ is the enhanced XML bindings that inherit from the autogenerated bindings in __nmrML_lib.py__. We can autogenerate


To regenerate the bindings from an updated schema run the following command:

```bash 
generateDS.py --subclass-suffix=""  --root-element="nmrML" --external-encoding='utf-8'  --super="nmrML_lib"  -o nmrML_lib.py -s nmrML.py xml-schemata/nmrML.xsd
```

## Authors

* [Michael Wilson](https://github.com/wilsonmichael)




