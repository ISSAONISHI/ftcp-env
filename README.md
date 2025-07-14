# onishi_ftcp 仮想環境構築マニュアル（日本語）

このドキュメントは、FTCP (Feature Tensor for Crystal Prediction) 関連コードを Python 3.6 環境で実行するための仮想環境 `onishi_ftcp` のセットアップ手順をまとめたものです。

---

## ✅ 前提条件

- Anaconda または Miniconda がインストールされていること
- Windows 環境を想定

---

## 1. 仮想環境の作成とアクティベート

```bash
conda create -n onishi_ftcp python=3.6.13
conda activate onishi_ftcp
```

---

## 2. 必須パッケージのインストール（バージョン指定）

### 🔹 基本ライブラリ

```bash
pip install numpy pandas matplotlib scikit-learn joblib tqdm
```

### 🔹 機械学習と Keras 環境

```bash
pip install tensorflow==1.15.5 keras==2.3.1
```

### 🔹 材料科学系ライブラリ

```bash
pip install matminer==0.6.2 pymatgen==2022.0.17 monty==3.0.2
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
pip install spyder==4.2.5 spyder-kernels==1.10.2 pyqt5==5.12.3 pyqt5-sip==12.9.1 pyqtwebengine==5.12.1
```

---

## 5. 動作確認

仮想環境が正しく作成されているか確認：

```bash
conda activate onishi_ftcp
python --version
```

正常に TensorFlow 1.15.5 と keras==2.3.1 が import できれば成功です。

---

## 📌 備考

- 依存関係が壊れたときは、一度 `conda remove --name onishi_ftcp --all` で削除してやり直すことを推奨
- TensorFlow 1.15.5 は古いため、環境の再現性のためにも仮想環境のエクスポートを推奨：

```bash
conda list --explicit > onishi_ftcp_env.txt
```








# onishi_ftcp Environment Setup Manual(English)

This document provides detailed steps to set up a virtual environment named `onishi_ftcp` to run the FTCP (Feature Tensor for Crystal Prediction) project on a Python 3.6 environment.

---

## ✅ Prerequisites

- Anaconda or Miniconda is installed  
- Windows OS is assumed

---

## 1. Create and Activate the Virtual Environment

```bash
conda create -n onishi_ftcp python=3.6.13
conda activate onishi_ftcp
```

---

## 2. Install Required Packages (with version specifications)

### 🔹 Basic Libraries

```bash
pip install numpy pandas matplotlib scikit-learn joblib tqdm
```

### 🔹 Machine Learning and Keras Environment

```bash
pip install tensorflow==1.15.5 keras==2.3.1
```

### 🔹 Materials Science Libraries

```bash
pip install matminer==0.6.2 pymatgen==2022.0.17 monty==3.0.2
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
pip install spyder==4.2.5 spyder-kernels==1.10.2 pyqt5==5.12.3 pyqt5-sip==12.9.1 pyqtwebengine==5.12.1
```

---

## 5. Verify the Setup

To confirm the environment is set up correctly:

```bash
conda activate onishi_ftcp
python --version
```

If `tensorflow==1.15.5` and `keras==2.3.1` can be successfully imported, the setup is complete.

---

## 📌 Notes

- If the environment breaks, you can delete it and recreate it using:

```bash
conda remove --name onishi_ftcp --all
```

- Since TensorFlow 1.15.5 is an older version, it is **recommended to export the environment** for reproducibility:

```bash
conda list --explicit > onishi_ftcp_env.txt
```

To restore the environment:

```bash
conda create --name onishi_ftcp --file onishi_ftcp_env.txt
```


これで環境を復元できます：

```bash
conda create --name onishi_ftcp --file onishi_ftcp_env.txt
```
