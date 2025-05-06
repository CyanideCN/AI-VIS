# AI-VIS

AI-VIS is a Condiitional GAN(CGAN) based model that simulates visible imagery from multiple IR channels of geostationary weather satellites during nighttime. 

The model is trained on Himawari-8/9 Full Disk and Target Area data. The model has been tested on other modern satellites including GOES-R series and GK-2A. Support is expected in the future.

Currently this inference script is only for Himawari-8/9 Target Area. We are continuing to work on support for Full Disk.

**License: Apache 2.0**

Additional terms: All images generated using AI-VIS that are made publically available must be marked as AI-VIS generated to avoid confusion with real visible imagery.

Paper: [Simulating Nighttime Visible Satellite Imagery of Tropical Cyclones Using Conditional Generative Adversarial Networks](https://ieeexplore.ieee.org/document/10988561)

```bash
@ARTICLE{10988561,
  author={Yao, Jinghuai and Du, Puyuan and Zhao, Yucheng and Wang, Yubo},
  journal={IEEE Journal of Selected Topics in Applied Earth Observations and Remote Sensing}, 
  title={Simulating Nighttime Visible Satellite Imagery of Tropical Cyclones Using Conditional Generative Adversarial Networks}, 
  year={2025},
  volume={},
  number={},
  pages={1-18},
  keywords={Clouds;Monitoring;Cloud computing;Data models;Tropical cyclones;Spatial resolution;Satellites;Satellite broadcasting;Loss measurement;Earth;Clouds;tropical cyclone (TC);conditional generative adversarial network (CGAN);deep learning;visible (VIS);nighttime;AHI},
  doi={10.1109/JSTARS.2025.3567074}
}
```

Dataset: [HuggingFace: Dapiya/aivis-dataset](https://huggingface.co/datasets/Dapiya/aivis-dataset)
(Uploading)

Training Code: [GitHub: Dapiya/aivis-training](https://github.com/Dapiya/aivis-training) (Uploading)

# Models 

| Model Name | Params* | Training Finish Time | Weights |
|------------|--------|---------------------| -------|
| aivis-1.0  |  67M   | 2024/3 | [HF🤗](https://huggingface.co/Dapiya/aivis-1.0) |
| aivis-1.5-small  |  67M   | 2024/9 | (Unreleased) |
| aivis-1.5-large  |  263M   | 2024/12 | (Unreleased) |

Upscaler 1.5: [HF🤗](https://huggingface.co/Dapiya/aivis-upscaler-1.5)


*Params are counting generator only, as only the generator is used during inference, and the discriminator is very small compared to the generator.


# Usage

1. Clone the repository
```bash
git clone github.com/Dapiya/AI-VIS.git
```
2. Install the requirements
```bash
pip install -r requirements.txt
```

3. Download the weights and place in ./aivis/weights
(see table above for links)

4. (Optional) Download data from [AWS](https://noaa-himawari9.s3.amazonaws.com/index.html#AHI-L1b-Target/) and place in ./aivis/test_data/HIMAWARI

    Channels 8, 9, 10, 11, 13, 15, 16 is needed

Note: The package already includes a sample of data, if you want to test with anything else, replace it with the data you downloaded.


5. Run the inference script
```bash
python test_aivis.py [--upscale] [--half precision]
```
Note: upscaler model must be downloaded and placed into ./aivis/weights folder when doing --upscale


# Future Plans

- We plan to release AI-VIS 1.5 in the near future, along with a better system for Full Disk
