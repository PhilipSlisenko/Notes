package  
module  
distribution  
python setup.py --help  
python setup.py --help-commands    
python setup.py --help install # help on specific command
### Setup.py install and develop  
python setup.py install is used to install (typically third party) packages that you're not going to develop/modify/debug yourself.

For your own stuff, you want to first install your package and then be able to frequently edit the code without having to re-install the package every time — and that is exactly what python setup.py develop does: it installs the package (typically just a source folder) in a way that allows you to conveniently edit your code after it’s installed to the (virtual) environment, and have the changes take effect immediately.

Note that it is highly recommended to use pip install . (install) and pip install -e . (developer install) to install packages, as invoking setup.py directly will do the wrong things for many dependencies, such as pull prereleases and incompatible package versions, or make the package hard to uninstall with pip.
https://stackoverflow.com/questions/19048732/python-setup-py-develop-vs-install  
___
### Requirements.txt vs setup_requires
So the takeaway: 
- `setup.py` should declare the loosest possible dependency versions that are still workable.  Its job is to say what a particular package can work with.
- `requirements.txt` is a deployment manifest that defines an entire installation job, and shouldn't be thought of as tied to any one package.  Its job is to declare an exhaustive list of all the necessary packages to make a deployment work.
- Because these two things have such different content and reasons for existing, it's not feasible to simply copy one into the other.  
https://stackoverflow.com/a/33685899/8949999  
___
### zip_safe
Set `true` if package casn be a zip archive. 
___

## Articles
Overview in russian: https://codecamp.ru/documentation/python/1381/creating-python-packages  
Example from PyPI https://github.com/pypa/sampleproject