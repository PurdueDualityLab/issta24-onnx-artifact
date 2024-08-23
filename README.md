# Interoperability in Deep Learning: A User Survey and Failure Analysis of ONNX Model Converters
The artifacts for this paper are placed into two main folders:
- `Theme 1: User Survey`: The data and code used for the user survey is within the `Theme1` folder, please examine the `README` for that.
-  `Theme 2: Failure Analysis`: The data and code used for the failure analysis is within the `Theme2` folder, please examine the `README` for that.
-  `Theme 3: Macro/Micro Analysis`: The data and code used for the Macro/Micro Analysis analysis is within the `Theme3` folder, please examine the `README` for that.


We use the external [HFTorrent dataset](https://zenodo.org/record/7556031) version 1.0.0. 

## Getting Started
This repository uses `anaconda` to create its python environment. 
I recommend you install a [miniforge](https://conda-forge.org/miniforge/) distribution.

Once you have `anaconda` installed, setup the environment using the following:
```sh
conda create -n onnx-failure python=3.9
pip install -r requirements.txt
conda activate onnx-failure
```
All the subsequent code should be executed using the `onnx-failure` conda environment.

Extract the data from the tarballs using:
```sh
tar -xf Theme1.tar
tar -xf Theme2.tar
tar -xf Theme3.tar
```

## Detailed Description

### Theme 1
The Jupyter Notebook used for processing data is [`onnx.ipynb`](/Theme1/onnx.ipynb).
To output the survey data relevant to interoperability please run the code blocks in `onnx.ipynb`.


### Theme 2
The script used to download GitHub issues is [`issues.py`](./Theme2/issue-downloader/issues.py).
```sh
cd Theme2/issue-downloader
python issues.py
```

The figures and tables for Theme 2 are generated used the [`data_analysis.ipynb`](./Theme2/data_analysis.ipynb) Jupyter notebook.


### Theme 3

#### Real Models
The PyTorch or TensorFlow conversion results are in [`pytorch_conv_results.json`](/Theme3/real-models/pytorch_conv_results.json) and [`tf2onnx_conv_results.json`](/Theme3/real-models/tf2onnx_conv_results.json).
The notebook used for data analysis is [`analyze.ipynb`](/Theme3/real-models/analyze.ipynb).

#### Synthetic Models
The code for analysis of PyTorch models is contained in the [`analysis.ipynb`](/Theme3/synthetic-models/analysis.ipynb).
The code for analysis of TensorFlow models is contained in the [`tf2onnx_analysis.ipynb`](/Theme3/synthetic-models/tf2onnx_analysis.ipynb).
The code for sequence anaylsis is contained in the [`sequence_analysis.ipynb`](/Theme3/synthetic-models/sequence_analysis.ipynb).

To generate models clone and install the following repository:
```sh
git clone https://github.com/pjjajalnnsmith.git
cd nnsmith
pip install ".[torch,onnx,tensorflow]" --upgrade
```
To generate 10 PyTorch models with 10 nodes use the following command:
```sh
cd Theme3/synthetic-models
python model_gen_nnsmith.py model.type=torch +mgen_cfg.max_nodes=10 +mgen_cfg.num_gen=10
```

Please look at the [NNSmith CLI guide](https://github.com/pjjajal/nnsmith/blob/main/doc/cli.md) for more details.

Please cite:
```
@inproceedings{jajal2024analysisfailuresrisksdeep,
      title={Interoperability in Deep Learning: A User Survey and Failure Analysis of {ONNX} Model Converters}, 
      author={Purvish Jajal and Wenxin Jiang and Arav Tewari and Erik Kocinare and Joseph Woo and Anusha Sarraf and Yung-Hsiang Lu and George K. Thiruvathukal and James C. Davis},
      year={2024},
      booktitle={Proceedings of the 33nd ACM SIGSOFT International Symposium on Software Testing and Analysis (ISSTA)},
      url={https://arxiv.org/abs/2303.17708},
}
```