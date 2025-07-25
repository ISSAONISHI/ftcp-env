# ftcp_env 仮想環境構築マニュアル（日本語）

このドキュメントは、FTCP (Feature Tensor for Crystal Prediction) 関連コードを Python 3.6 環境で実行するための仮想環境 `ftcp_env` のセットアップ手順をまとめたものです。

---

## ✓ 前提条件

- Anaconda または Miniconda がインストールされていること
- Windows 環境を想定

---

## 1. 仮想環境の作成とアクティベート

```bash
conda create -n ftcp_env python=3.7
conda activate ftcp_env
```

---

## 2. 必須パッケージのインストール（バージョン指定）

### ■ 基本ライブラリ

```bash
pip install numpy==1.18.5 pandas matplotlib scikit-learn joblib tqdm
```

### ■ 機械学習と Keras 環境（CPU版）

```bash
pip install tensorflow==1.15.5 keras==2.3.1 protobuf==3.20.3
```

### ■ 機械学習と Keras 環境（GPU版）

```bash
pip install tensorflow-gpu==1.15.5 keras==2.3.1 protobuf==3.20.3
```
※ GPU版を使うには以下の環境が必要：
   - CUDA Toolkit 10.0
   - cuDNN 7.4.1（CUDA 10.0対応）
   - 対応する NVIDIA GPU ドライバ
   - CUDA / cuDNN のパスが環境変数に通っていること


### ■ 材料科学系ライブラリ

```bash
pip install matminer==0.6.2 pymatgen==2021.3.9 monty==3.0.2 ase
```

---

## 3. ruamel.yaml の依存関係調整

以下を明示的にインストールすることで pymatgen のバージョン競合を防ぎます。

```bash
pip install ruamel.yaml==0.17.21 ruamel.yaml.clib==0.2.7
```

---

## 4. Spyder（任意：GUIで動かしたい場合）

```bash
conda install -c conda-forge spyder=4.2.5
```

---

## 5. 動作確認

仮想環境が正しく作成されているか確認：

```bash
conda activate ftcp_env
python --version
```

正常に TensorFlow 1.15.5 と keras==2.3.1 が import できれば成功です。

---


## 6. Visual Studio Build Tools のインストール（Windowsユーザー向け）

一部のパッケージ（例：`pymatgen` や `ruamel.yaml`）のビルドには、C++ コンパイラが必要になる場合があります。以下の手順に従って Visual Studio Installer を使ってインストールしてください。

### ■ 手順

1. [Visual Studio Installer](https://visualstudio.microsoft.com/ja/visual-cpp-build-tools/) をダウンロードして実行
2. 以下の **ワークロード** を選択してインストール：
   - ✓ **C++ によるデスクトップ開発**
3. インストール完了後、Anaconda Prompt やターミナルを再起動

---

## 7. ftcp_env.yml ファイルからの環境構築（再現用）

既存環境を他のマシンで再現したい場合や、構築手順を省略したい場合は、以下のように `.yml` ファイルを使用して仮想環境を構築できます。

### ■ 準備

`ftcp_env.yml` ファイルがこのディレクトリに存在していることを確認してください。

### ■ 実行コマンド

```bash
conda env create -f ftcp_env.yml
conda activate ftcp_env
```
---

## 備考

- 依存関係が壊れたときは、一度 `conda remove --name ftcp_env --all` で削除してやり直すことを推奨
- TensorFlow 1.15.5 は古いため、環境の再現性のためにも仮想環境のエクスポートを推奨：

```bash
conda list --explicit > onishi_ftcp_env.txt
```








# ftcp_env Environment Setup Manual(English)

This document provides detailed steps to set up a virtual environment named `ftcp_env` to run the FTCP (Feature Tensor for Crystal Prediction) project on a Python 3.6 environment.

---

## ✓ Prerequisites

- Anaconda or Miniconda is installed  
- Windows OS is assumed

---

## 1. Create and Activate the Virtual Environment

```bash
conda create -n ftcp_env python=3.7
conda activate ftcp_env
```

---

## 2. Install Required Packages (with version specifications)

### ■ Basic Libraries

```bash
pip install numpy==1.18.5 pandas matplotlib scikit-learn joblib tqdm
```

### ■ Machine Learning and Keras Environment (CPU version)

```bash
pip install tensorflow==1.15.5 keras==2.3.1 protobuf==3.20.3
```

### ■ Machine Learning and Keras Environment (GPU version)

```bash
pip install tensorflow-gpu==1.15.5 keras==2.3.1 protobuf==3.20.3
```
※ The following environment is required to use the GPU version：
   - CUDA Toolkit 10.0
   - cuDNN 7.4.1 (CUDA 10.0 compliant)
   - Supported NVIDIA GPU Drivers
   - CUDA / cuDNN path must be passed in the environment variable

### ■ Materials Science Libraries

```bash
pip install matminer==0.6.2 pymatgen==2021.3.9 monty==3.0.2 ase
```

---

## 3. ruamel.yaml Dependency Fix

To avoid compatibility issues with pymatgen, install the following versions explicitly:

```bash
pip install ruamel.yaml==0.17.21 ruamel.yaml.clib==0.2.7
```

---

## 4. Spyder (Optional: If using GUI)

```bash
conda install -c conda-forge spyder=4.2.5
```

---

## 5. Verify the Setup

To confirm the environment is set up correctly:

```bash
conda activate ftcp_env
python --version
```

If `tensorflow==1.15.5` and `keras==2.3.1` can be successfully imported, the setup is complete.


---

## 6. Installing Visual Studio Build Tools (for Windows Users)

Some packages (e.g., `pymatgen` or `ruamel.yaml`) may require a C++ compiler to build correctly. Please follow the steps below to install the required build tools using Visual Studio Installer.

### ■ Instructions

1. Download and run the [Visual Studio Installer](https://visualstudio.microsoft.com/visual-cpp-build-tools/)
2. Select and install the following **workload**:
   - ✓ **Desktop development with C++**
3. After installation, restart your Anaconda Prompt or terminal


---

## ✅ 追記内容（English）

```md
---

## 7. Environment Setup from ftcp_env.yml (for Reproducibility)

To reproduce the exact environment on another machine or avoid manual installation, use the provided `.yml` file to create the environment automatically.

### ■ Prerequisite

Ensure that the file `ftcp_env.yml` exists in the working directory.

### ■ Command to Create the Environment

```bash
conda env create -f ftcp_env.yml
conda activate ftcp_env
```

---

## Notes

- If the environment breaks, you can delete it and recreate it using:

```bash
conda remove --name ftcp_env --all
```

- Since TensorFlow 1.15.5 is an older version, it is **recommended to export the environment** for reproducibility:

```bash
conda list --explicit > onishi_ftcp_env.txt
```

To restore the environment:


```bash
conda create --name ftcp_env --file onishi_ftcp_env.txt
```
