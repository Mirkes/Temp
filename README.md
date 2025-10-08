<p align="center">
<img src="figures/icon.png" width="150"/>
</h1>


<h1 align="center">Robustness bias</h1>


### Installation

Current environment based on environment of [prompt-instability](https://github.com/Dont-Care-Didnt-Ask/prompt-instability) with only few additional repos that can be installed through pip.


### Datasets

#### [Natural-Instructions](https://github.com/allenai/natural-instructions/tree/master) with perturbed formats)

Dataset from [prompt-instability](https://github.com/Dont-Care-Didnt-Ask/prompt-instability)

Use script `dsets/natural_formats/natural_formats.sh` 
- `base_prompts.ipynb` to generate base prompts
- `generate_formats.py` to generate perturbation formats
- `generate_prompts.py` to generate base and perturbed prompts
- `extract.py` to extract features for either base or (base + perturbed) prompts 

Process:
- First run `base_prompts.ipynb` and `extract.py` to identify tasks that the model have learned to solve to some extend.
- Then generate perturbed formats and prompts for feature extraction


Notes:
- currently all prompts and extractions are without instruct template
- results of `generate_formats.py` can be found in this [link](https://www.dropbox.com/scl/fo/gp0i6ueffknutlb8cz9cu/ABeatmWkkSl1Erg1gSLtm2Q?rlkey=qnl6qfrrz3b9a1alpkv9m58d4&dl=0)
- links to [base prompts](https://www.dropbox.com/scl/fo/yctyc7tjs09y8hbs8qsnw/AJLjb-Y8NrJYxy90CrfSnyw?rlkey=xe4rvoqblc5ly1lf87dyhtz85&dl=0) and [base + perturbed prompts](https://www.dropbox.com/scl/fo/z44atbgc465r510hniuz0/AKIAHcT9DCxG5fRzaPJHRDg?rlkey=82k4253lzt95v6up7xr40g0ba&dl=0) 

#### [Natural-Instructions](https://github.com/allenai/natural-instructions/tree/master) with perturbed prompts)


#### FinLoRA

Dataset from [FinLoRA](https://github.com/Open-Finance-Lab/FinLoRA/tree/main/data)
