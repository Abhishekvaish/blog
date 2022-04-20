---
layout: post
title: "Create and delete virtual environment in anaconda(python)"
tags: "virtual environment,python,anaconda"
---
conda makes managing mutiple environment very simple and easy

### In anaconda prompt 
#### Create a Virtual Environment 
```sh
conda create -n name_of_your_env python=x.x
```
python=x.x can be any python version of your to get the latest version of python 3 you can just put python=3 

<br>

#### Activate a Virtual environment 
```sh
conda activate name_of_your_env
```

<br>

#### Deactivate a Virtual environment 
```sh
conda deactivate
```

<br>

#### Get the list of all environment
```sh
conda env list
```

<br>

#### Delete a virtual environment
```sh
conda env remove -n name_of_your_env
```
