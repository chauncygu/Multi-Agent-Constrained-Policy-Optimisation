# Multi-Agent Constrained Policy Optimisation (MACPO)

The repository is for the paper: **Multi-Agent Constrained Policy Optimisation**, in which we investigate the problem of safe MARL. The problem of safe multi-agent learning with safety constraints has not been rigorously studied; very few solutions have been proposed, nor a sharable testing environment or benchmarks.   To fill these gaps, in this work, we formulate the safe multi-agent reinforcement learning problem as a constrained Markov game and solve it with trust region methods. Our solutions---*Multi-Agent Constrained Policy Optimisation (MACPO)* and *MAPPO-Lagrangian*---leverage on the theory of  *Constrained Policy Optimisation (CPO)* and multi-agent trust region learning, and critically, they enjoy theoretical guarantees of  both  monotonic improvement in reward and satisfaction of safety constraints  at every iteration. Experimental results reveal that  *MACPO/MAPPO-Lagrangian* significantly outperform baselines in terms of balancing the performance and constraint satisfaction, e.g. [MAPPO](https://arxiv.org/abs/2103.01955), [IPPO](https://arxiv.org/abs/2011.09533), [HAPPO](https://arxiv.org/abs/2109.11251).



## Environments Supported:

- [Safety Multi-Agent Mujoco](https://github.com/chauncygu/Safe-Multi-Agent-Mujoco)




## 1. Installation

####  1.1 Create Environment

``` Bash
# create conda environment
conda create -n macpo python==3.7
conda activate macpo
pip install -r requirements.txt
conda install pytorch torchvision torchaudio cudatoolkit=11.1 -c pytorch -c nvidia
```

```
cd MACPO/macpo (for the macpo algorithm) or cd MAPPO-Lagrangian/mappo_lagrangian (for the mappo_lagrangian algorithm)
pip install -e .
```



#### 1.2 Install Safety Multi-Agent Mujoco


- Install mujoco accoring to [mujoco-py](https://github.com/openai/mujoco-py) and [MuJoCo website](https://www.roboti.us/license.html).
- clone [Safety Multi-Agent Mujoco](https://github.com/chauncygu/Safe-Multi-Agent-Mujoco) to the env path (in this repository, have set the path).

``` Bash
LD_LIBRARY_PATH=${HOME}/.mujoco/mujoco200/bin;
LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libGLEW.so
```



## 2. Train

```
cd MACPO/macpo/scripts or cd MAPPO-Lagrangian/mappo_lagrangian/scripts
chmod +x ./train_mujoco.sh
./train_mujoco.sh
```


## 3. Results

<div align=center>
<img src="https://github.com/anybodyany/Multi-Agent-Constrained-Policy-Optimisation/blob/main/figures/ManyAgent_Ant_results.png" width="850"/>    
<img src="https://github.com/anybodyany/Multi-Agent-Constrained-Policy-Optimisation/blob/main/figures/Ant_results.png" width="850"/> 
<img src="https://github.com/anybodyany/Multi-Agent-Constrained-Policy-Optimisation/blob/main/figures/HalfCheetah_results.png" width="850"/>
</div>
    
<div align=center>
<center style="color:#000000;text-decoration:underline">Figure.1 Cost and reward performance comparison between our MACPO & MAPPO-Lagrangian and SOTA MARL algorithms. The universal safety constraining values are: 15 for ManyAgent Ant, 0.2 for Ant, and 5 for HalfCheetah. The results are averaged over 3 random seeds. Our methods learn safety constraints, and score reward on <a href="https://arxiv.org/abs/2103.01955">MAPPO</a> and <a href="https://arxiv.org/abs/2011.09533)">IPPO</a> level.</center>
</div>


# Acknowledgments

Some sections of the repository is based on [MAPPO](https://github.com/marlbenchmark/on-policy), [HAPPO](https://github.com/cyanrain7/Trust-Region-Policy-Optimisation-in-Multi-Agent-Reinforcement-Learning), [safety-starter-agents](https://github.com/openai/safety-starter-agents), [CMBPO](https://github.com/anyboby/Constrained-Model-Based-Policy-Optimization).





