---
layout: post
title: Setting up virtual environments
date: 2018-01-18
comments: true
---
As we heard last week, 96 people expressed interest in attending our [workshop](https://elizavetasemenova.github.io/blog/2018/01/07/Teaching-a-workshop-on-DL-for-NLP).
Anyhow, it is hard to predict how many participants there will be, since they are allowed to decide on the spot. As a consequence, we do not 
know in advance who exactly is coming.

I anticipate slow-downs throughout the workshop due to the software issues. To make sure that we are all on the same page, we will prepare
a **.yaml** file to distribute. Never the less, here are the instructions of how to create the environment yourself.


#### Virtual environments:
Virtual environments allow to separate libraries and different versions of Python, used by different projects and avoid conflicts.

The following instructions are here for your information. There is no need to go through all the steps yourself, rather use the provided amld.yml file, as shown in the last command.

- Download anaconda 

  https://www.continuum.io/downloads
  
From now on either follow the instructions below, or go to the last instruction and use the ditributed **amld.yml** file.

- Create a new environment:

```conda create --name amld python=3```

- List existing environments:

```conda env list```

- Enter the new environment on Mac/Linux:
   
```source activate amld```

- Enter the new environment on Windows:

```activate amld```  

- Install packages:

```conda install numpy matplotlib pandas jupyter notebook```


- List all installed packages:

```conda list```

- Open up the notebook server:

```jupyter notebook```

- To share an environment, we can export it into a *.yml file:

```conda env export > amld.yml```

- Create the environment from the amld.yml file:

```conda env create -f amld.yml```

- Remove an environment:

```conda env remove -n env_name```

#### Documentation:
https://conda.io/docs/user-guide/tasks/manage-environments.html
