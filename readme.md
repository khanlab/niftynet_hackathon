
## NiftyNet Materials

### Help

- [NiftyNet Documentation](https://niftynet.readthedocs.io/en/dev/)
- [NiftyNet Mailing List](https://groups.google.com/forum/#!forum/niftynet)

### Youtube

- [NiftyNet: Deep Learning platform for medical image analysis - Jorge Cardoso (UCL)](https://www.youtube.com/watch?v=2OweR-sUNfQ&t=772s)
- [MED-NIPS 2017 - Jorge Cardoso](https://www.youtube.com/watch?v=ZaWStjGf0wg)
- [Deep Learning In Practice](https://www.youtube.com/watch?v=Q8lfkTXD69o&list=PLbj_N2x6keChr9xgCS9Y3MeBNV5OxikvI)

### Papers

- [Gibson and Li et al. 2017](https://reader.elsevier.com/reader/sd/pii/S0169260717311823?token=8FC4F5CFA48C0A830D84AA6D8995223F83400652CFC6CD97E864CAC631DB4154E8045BF53F865551B86B75666765CA92)
- [Li et al. 2017](https://arxiv.org/pdf/1707.01992.pdf)

## Install NiftyNet

### For Windows/Linux/Mac **WITH** GPU (modern Nvidia GPU (>= GTX 1050))

- step 1: install Anaconda(python 3.7,64bit) (or Miniconda)

    [Anaconda download](https://www.anaconda.com/distribution/#download-section)

- step 2: run the following command in your terminal

    ```bash
    #create virtual env(A virual env will not mess your installed stuff)
    conda create -n niftynet_env python=3.6 conda pip tensorflow-gpu

    #enter virtual env. For Linux/Mac use `source activate niftynet_env`
    activate niftynet_env
    pip install niftynet
    pip install opencv-python
    pip install SimpleITK
    pip install scikit-image

    #leave virtual env. For Linux/Mac, use `source deactivate`
    deactivate
    ```

### For Windows/Linux/Mac **WITHOUT** GPU

- step 1: install Anaconda(python 3.7,64bit) (or Miniconda)
    
    [Anaconda download](https://www.anaconda.com/distribution/#download-section)

- step 2: run the following command in your terminal
    ```bash
    #create virtual env(A virual env will not mess your installed stuff)
    conda create -n niftynet_env python=3.6 conda pip tensorflow

    #enter virtual env. For Linux/Mac use `source activate niftynet_env`
    activate niftynet_env
    pip install niftynet
    pip install opencv-python
    pip install SimpleITK
    pip install scikit-image

    #leave virtual env. For Linux/Mac: use `source deactivate`
    deactivate
    ```
## Quick start

```bash
#enter virtual env. For Linux/Mac use `source activate niftynet_env`
activate niftynet_env
mkdir test_niftynet
cd test_niftynet
net_download dense_vnet_abdominal_ct_model_zoo
net_segment inference -c ~/niftynet/extensions/dense_vnet_abdominal_ct/config.ini

#The segmentation output of this example application should be located at
~/niftynet/models/dense_vnet_abdominal_ct/segmentation_output/100__niftynet_out.nii.gz
```

## Check segmented results

You can use itk-snap to check the segmented results:

![](pics/itk-snap-show-results.png)


---
## Appendix
---

### Run NiftyNet in singularity container(note: Linux with GPU **only**)

```bash
# install singualrity first:
# sudo apt-get install -y singularity-container
singularity pull --name niftynet_gpu.simg shub://yinglilu/niftynet_gpu_singularity
singularity exec --nv niftynet_gpu.simg <NiftyNet command>
```
