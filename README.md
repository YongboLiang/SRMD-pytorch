# Super-Resolution Network for Multiple Degradations (SRMD)
PyTorch/NSML Implementation of [Learning a Single Convolutional Super-Resolution Network for Multiple Degradations](http://openaccess.thecvf.com/content_cvpr_2018/papers/Zhang_Learning_a_Single_CVPR_2018_paper.pdf) (CVPR 2018)

All the files in the directories `kernels` are from [1]. 


## Requirements
- `python 3.6`
- `nsml` ([link1](https://nsml.navercorp.com/download), [link2](https://github.com/n-CLAIR/nsml-local))
- `pytorch==0.4.0`
- `visdom`
- `pillow`
- `h5py`

## Usage
First, train the network

    $ run -e main.py -d super-resolution -a "--scale_factor=2 --mode='train'"

Second, do testing (*Not implemented yet*)

    $ run -e main.py -d super-resolution -a "--scale_factor=2 --mode='test'"

## Results
- First column: LR image, Second column: SR image, Third column: HR image
### Images (SRMDNFx2)
<img src="img/SRMDx2.png" alt="drawing" width="600px"/>

### Images (SRMDNFx3)
<img src="img/SRMDx3.png" alt="drawing" width="600px"/>

### Images (SRMDNFx4)
<img src="img/SRMDx4.png" alt="drawing" width="600px"/>

## Notes
- The implementation is slightly different with one in original paper.
- At the last layer, any activation function (e.g., `sigmoid`, `tanh`) is not used.
    - Not stable results (bouncing pixels even after large iterations)
- We put a sigmoid function right after the last convolutional layer.

## To-Do
* [ ] To upload test data to NSML server
* [ ] To implement `test()` method of `class Solver` considering users' favor (specific blur kernel as input)
* [x] To train on the other scale factors (SRMDNFx3, SRMDNFx4)
* [ ] To consider additive noise after downsampling (SRMDx2, SRMDx3, SRMDx4) 

## Reference
[1] [MatConvNet implementation](https://github.com/cszn/SRMD) of one author of the paper (**only test code** available, as of June 27, 2018)

## Contact
Dongkyu Kim (d.kim@navercorp.com)