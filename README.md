# Dataset of Industrial Metal Objects Labeling Tool

A tool for easily labeling 6D object poses in multi-view RGB images. 
![Screenshot](docs/images/screenshot.png)

## Usage

See [this video](https://youtu.be/qvZfD38i7ro) for detailed usage instructions.

The tool can be used to label datasets using the [BOP format](https://github.com/thodan/bop_toolkit/blob/master/docs/bop_datasets_format.md), provided that camera pose labels are present, and object pose labels are consistent among different viewpoints. 
In each scene folder, labeled object poses are stored in the following files:
* `scene_gt.json`: poses relative to the camera frame, as defined in the BOP format.
* `scene_gt_world.json`: poses relative to the world frame. This file is not part of the original BOP format.

> Note: Currently image names/models names are hardcoded to have 6 digits, i.e: `000001.png`, `obj_000001.ply`

## Set-up

The labeling tool consists of two parts:
* a python back-end, used for loading the dataset and performing pose calculations.
* an Angular front-end, used for user interaction and visualization.

### Back-end
- Conda:
  * Make sure [conda](https://docs.conda.io/en/latest/miniconda.html) is installed.
  * Open a terminal and navigate to the `backend` folder: `cd backend`.
  * Create a new environment: `conda env create -f environment.yml`.
  * Activate the environment: `conda activate dimo-labeling`.
- Pip (preferably in a virtual environment):
  * `pip3 install -r requirements.txt`
* Start the back-end api and pass the path to the dataset folder, the name of the folder containing object models and the name of the camera containing scenes: `python api.py --path "<path-to-dataset>" --models_dir "<models-dir-name>" --images_dir "<camera-dir-name>"`.
```shell
# Example
python api.py --path "./sample_bob_dataset" --models_dir "models" --images_dir "train"
```

### Front-end
* Make sure [nodejs](https://nodejs.org/en/download/) is installed.
* Make sure [nvm](https://github.com/nvm-sh/nvm) is installed.
* Open a terminal and navigate to the `frontend` folder: `cd frontend`.
* Install the correct node version: `nvm install`.
* Activate the correct node version: `nvm use`.
* Install the necessary node packages: `npm install --save-dev`.
* Build and serve the app: `npm run start`.
* Open a browser on `http://localhost:4200/` to open the app.

### Advanced Options
Datasets should be structured using the [BOP format](https://github.com/thodan/bop_toolkit/blob/master/docs/bop_datasets_format.md).
* The following arguments can be used when starting the back-end:
  * `--path`: the path of the dataset.
  * `--models_dir`: the name of the directory where object models are stored.
  * `--images_dir`: the directory containing the scenes with images to label.
