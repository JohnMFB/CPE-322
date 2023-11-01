# Lab 3

![image](https://github.com/JohnMFB/CPE-322/assets/122575719/49b7795e-f576-4907-aa8d-d38eecdf0a6a)

## VSCode Changes
- Downloaded VSCode Plugins
  - Python
  - Pylance
  - Jupyter
  - Jupyter Cell Tags
  - Jupyter Keymap
  - Jupyter Slide Show
  - Jupyter Notebook Renderers
  - Python Indent
- Env "myenv" created Python Version 3.10
- Ctrl + Shift + P -> "Selected Interpretor: python" could not show until myenv was created.
  - Use myenv for this project
    - Download Packages to "myenv"
      - jdcal
      - astral
      - geopy
      - psutil
## Start

![Alt text](https://github.com/JohnMFB/CPE-322/blob/main/Assets/Lab_3.png)

### Python Integration Startup

<img width="388" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/7cb49473-3f4b-4b8d-8352-4a1affe8d79f">

<img width="382" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/510532cc-09af-4f6a-99c2-f8df59001217">

### jdcal install to myenv

<img width="527" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/f4342401-716a-4c6d-8d8c-699e069e32ee">

## Conda-Forge Community Channel contains Astral, Geopy, and Psutil

### Adding Conda-Forge and Installing Astral

<img width="575" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/4798e161-10fe-4762-80af-6112dfa82874">

<img width="212" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/94aed93b-3d1d-46bb-a0a6-2c7b8a5c8060">

### Installing Geopy

<img width="525" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/5c1486e2-35f3-4c16-a70e-64406673a4df">

### Installing Psutil

<img width="521" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/4e69189b-7805-4bdb-9bab-7c8458ae6f8a">

# Lab Start

## Jdcal Failure, reinstalling, SUPERSEDED by higher priority conda-forge channel

<img width="579" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/abcb8624-f23f-44e9-a20e-7290c5d06705">

###Jdcal second failure

<img width="580" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/1e5374a5-8f3d-4c33-ad50-724f8d2b2857">

### Fix (myenv needs to be activated manually, not just through activating the interpreter)

<img width="589" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/3ab25e7e-f5b7-40a5-a3b5-c020c79b5944">

<img width="581" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/0e61dd7f-a809-4177-a10f-1986d856751d">

<img width="579" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/777c4094-549d-4b5c-9326-4ce7b43bc2ca">

<img width="591" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/b28cda6a-149e-49bd-89d0-144f8d541f60">

### 'pytz' module not found at 'python3 sun.py 'New York'

<img width="594" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/50c57331-72ca-45b3-8782-644ac9a8ea7d">

### pytz installed

<img width="581" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/0382ebed-5d03-4d70-b592-0b150e4bddbb">

### pytz failed: perform 'conda update -n base -c defaults conda'

<details>
  <summary>Click to View Image</summary>
  <img width="593" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/8eda47a3-5b63-4dc0-9714-7b69de6bc1f4">
  <img width="598" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/cb9a3d2b-60a8-46e7-8e74-c3a76078e0f8">
  <img width="592" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/9af4c9bf-1e5b-4900-b386-ed567e4902a8">
  <img width="599" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/269ae602-b46e-452e-b68c-d98dc00f57ee">
</details>

### pytz failed: perform 'conda update --all' in current myenv env

<details>
  <summary> Click to View Image</summary>
  <img width="591" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/a293815e-602e-4615-8fcb-a4450150f58c">
  <img width="594" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/d0d58ea1-bc3d-4b7c-ba23-5f218325ef10">
  <img width="203" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/7864418e-9458-488d-ba70-89d0437bb20d">
</details>

### pytz failed: all updates were still successful

<img width="588" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/2677a4bb-aaab-4bc5-9f17-d080636c8a53">

#### Note: All commands stopped working for previous steps

#### All required packages are already installed but cannot be accessed anymore

<img width="592" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/2ed20dba-3d6c-47ff-884f-46513c64cb53">

#### Results reflected within Anaconda

<img width="652" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/392af139-aa4f-4f59-8b5e-168c11ad4f9a">
<img width="653" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/0335cc24-9d3c-4b5e-84c2-bbaeea7e3741">
<img width="655" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/24f025e4-a758-4be1-aa02-21df4ebcdda4">
<img width="653" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/8b1db170-961e-44cb-86a5-37717e3d6f3d">
<img width="654" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/7699a9ea-53a0-44cb-97ab-c5feb6d03a3b">

## Retry in 'newenv' python 3.8

<img width="580" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/8d96bd97-1307-4be0-961e-68f404372160">
<img width="597" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/9bacfef8-c3b8-4c66-ac8d-5f39613f9b39">
<img width="584" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/0d38026d-0b3f-43df-b754-455a12cb6443">
<img width="580" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/ac638ca7-feac-4a3c-9f0a-0d681cfce520">

# Failure in new environment, listed packages present

<img width="590" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/0489fe87-1b48-47a0-8bd7-479a7edd3218">

## Retry in 'latestenv' python latest version 3.12.0

<img width="593" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/51cdff85-ad01-4a64-a8d6-d3bc9cb7978d">

## Fail

<img width="594" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/f7b954f0-ca41-4345-bfdf-00118001988e">
