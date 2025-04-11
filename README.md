# SnakeAI
[![license](https://img.shields.io/github/license/Genius-Society/SnakeAI.svg)](./LICENSE)
[![hf](https://img.shields.io/badge/huggingface-SnakeAI-ffd21e.svg)](https://huggingface.co/Genius-Society/SnakeAI)
[![ms](https://img.shields.io/badge/modelscope-SnakeAI-624aff.svg)](https://www.modelscope.cn/Genius-Society/SnakeAI)
[![bili](https://img.shields.io/badge/bilibili-BV1bqrgYXEsn-fc8bab.svg)](https://www.bilibili.com/video/BV1bqrgYXEsn/?p=3)

This project aims to use deep reinforcement learning (DRL) to play Snake game automatically. The core DRL method used here is PPO for discrete, which has brilliant performance in the field of discrete action space like in continuous action space. You just need half an hour to train the snake agent and then it can take effect.

## Requirements
```bash
conda create -n py311 python=3.11 -y
conda activate py311
pip install -r requirements.txt
```

## Code download
```bash
git clone git@github.com:Genius-Society/SnakeAI.git
cd SnakeAI
```

## Usage
### Train
```bash
python train.py # after training, the training curve of current round will autometically show
python snake.py # evaluate latest saved model
```

### Evaluate assigned model
```bash
python eval.py # --weight ./model/act-weight_round3_472_82.5.pkl
```

### Plot assigned reward log
```bash
python plot.py # --history ./logs/reward_round3_82.5.csv
```

## Experiments
| Round        |                                                        1                                                         |                                                        2                                                         |                                                        3                                                         |
| :----------- | :--------------------------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------------------: |
| Traing curve | ![round1](https://user-images.githubusercontent.com/20459298/233120722-d300c250-a07e-44c1-8986-d1f26d48c0f8.png) | ![round2](https://user-images.githubusercontent.com/20459298/233120780-43c9b35b-def6-4a57-b7b4-6599ad594c5c.png) | ![round3](https://user-images.githubusercontent.com/20459298/233120831-deb18303-25ec-4ff8-bafc-4726d1a81af4.png) |
| Evaluation   | ![round1](https://user-images.githubusercontent.com/20459298/233120884-b0ea6080-8aa4-4382-9ce5-90c22737cdf3.gif) | ![round2](https://user-images.githubusercontent.com/20459298/233121028-f9431608-3833-49d5-9cde-573fdb82c692.gif) | ![round3](https://user-images.githubusercontent.com/20459298/233121080-9a4f2e95-0f49-40cf-91a4-f7f57d4b861f.gif) |
| Reward_eat   |                                                       +2.0                                                       |                                                       +2.0                                                       |                                                       +2.0                                                       |
| Reward_hit   |                                                       -0.5                                                       |                                                       -1.0                                                       |                                                       -1.5                                                       |
| Reward_bit   |                                                       -0.8                                                       |                                                       -1.5                                                       |                                                       -2.0                                                       |
| Avg record   |                                                       ≈19                                                        |                                                       ≈23                                                        |                                                       ≈28                                                        |

## Conclusions
- Increasing the penalty for death leads to higher average records
- The training result of the low death penalty strategy has a low reward curve, but it performs well in the demo
- A particularly high reward for eating food can lead to quick success regardless of long-term safety

## Future work
- Training time is too short to reflect the advantages of DRL compared to none-DRL method ([Snaqe](https://github.com/Genius-Society/SnakeAI/tree/qt))
- The zigzag of snake body looks ugly, try to add punishment into reward for too many zigzags

## Thanks
- <https://github.com/ZYunfeii/DRL4SnakeGame>