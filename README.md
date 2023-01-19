# GPU_settings
GPUまわりの設定</br>
まずPyTorchのバージョンを調べる(https://pytorch.org/get-started/locally/)</br>
PyTorchのバージョンに合うように以下の環境構築を行う．

## NVIDIA driver
[【備忘録】Ubuntu 20.04 LTS + GPU 環境構築 (2021年3月版)](https://qiita.com/SwitchBlade/items/5d5bc645822229ee0ed9)

## CUDA11.7
[ubuntu20.04 CUDA11.7](https://developer.nvidia.com/cuda-11-7-0-download-archive?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=20.04&target_type=deb_local)
```
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/cuda-ubuntu2004.pin
sudo mv cuda-ubuntu2004.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget https://developer.download.nvidia.com/compute/cuda/11.7.0/local_installers/cuda-repo-ubuntu2004-11-7-local_11.7.0-515.43.04-1_amd64.deb
sudo dpkg -i cuda-repo-ubuntu2004-11-7-local_11.7.0-515.43.04-1_amd64.deb
sudo cp /var/cuda-repo-ubuntu2004-11-7-local/cuda-*-keyring.gpg /usr/share/keyrings/
sudo apt-get update
sudo apt-get -y install cuda
```
```
vim ~/.bashrc
export PATH=/usr/local/cuda-11.7/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda-11.7/lib64:$LD_LIBRARY_PATH
```

## cuDNN


## いろいろ削除
[UbuntuでCUDAの削除から再インストールまでのメモ](https://misoji-engineer.com/archives/reinstall-cuda-on-ubuntu.html)
```
sudo apt-get --purge remove nvidia* -y
sudo apt-get --purge remove cuda* -y
sudo apt-get --purge remove cudnn* -y
sudo apt-get --purge remove libnvidia* -y
sudo apt-get --purge remove libcuda* -y
sudo apt-get --purge remove libcudnn* -y
sudo apt-get autoremove -y
sudo apt-get autoclean -y
sudo apt-get update
sudo rm -rf /usr/local/cuda*
```

## その他
### セキュアブートをいじった（無効にした）あと，ubuntuでwifiの設定ができなくなった
解決方法:有線LAN接続し，ターミナルでsudo apt update，sudo apt upgradeのあと，rebootしたら解決した．
### 画面暗くなるなどの不具合
[Ubuntu20.04でNvidiaのドライバーを入れたときの問題の対処法](https://coders-shelf.com/ubuntu-nvidia-driver-problem/)
### CUDA11.6
[CUDA Toolkit Linux 版のインストールメモ](https://ss1.xrea.com/penguinitis.g1.xrea.com/computer/programming/CUDA_Linux_install.html)
### W: GPG エラー: 
[W: GPG エラー: https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64 InRelease: 公開鍵を利用できないため、以下の署名は検証できませんでした: NO_PUBKEY A4B469963BF863CC E: リポジトリ https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64 InRelease は署名されていません。 N: このようなリポジトリから更新を安全に行うことができないので、デフォルトでは更新が無効になっています。 N: リポジトリの作成とユーザ設定の詳細は、apt-secure(8) man ページを参照してください。](https://www.nemotos.net/?p=5178)
### $ lspci | grep -i nvidia でGPUの型番が出てこない時
[$ lspci | grep -i nvidia でGPUの型番が出てこない時：](https://pen.envr.tsukuba.ac.jp/~torarimon/?Gpu)
### マウスポインタが表示されない（クリックはできる）
[【Ubuntu + NVIDIA】Ubuntu に NVIDIA ドライバーをインストール](https://tamnology.com/ubuntu-nvidia-driver/)
### reboot後画面が真っ暗になる
[[Ubuntu]CUDAを入れたら画面が真っ黒になった話](https://qiita.com/cv_carnavi/items/b439b81e7c10b95ee7c5)
