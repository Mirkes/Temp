<p align="center">
<img src="figures/icon.png" width="150"/>
</h1>


<h1 align="center">Preliminary Look into Confidence Estimation</h1>

The goal of this repository is to provide a preliminary look into methods for confidence estimation for LLMs. The intention is to create new data-based estimation methods that can tell us more about how LLMs work and how it doesn't work.


### Updates

**Current approach:**

- math-specific, better model traces as ground truth, token-level confidence 

### Installation

```bash
conda create -n s-conf python=3.9
```

Need torch, transformers, tqdm. More detailed instructions to follow.

### Preparation

1. Find reasoning traces (of larger better model) for use as ground truth (examples [here](https://www.dropbox.com/scl/fo/2ag3mjb41u1nnfdog9i1u/AKSjIpxf5mULWP8JLx5LtXU?rlkey=hmj7jxvieruofl3oyd7wqc5oz&dl=0) for Synthetic-1-SFT math score 1 shortest solution traces, notebook for extraction is `extract_synthetic1.ipynb`)

2. Use `cache_assistant.py` to extract features from the residual stream (e.g. inputs into `lm_head`) and output logits

3. Use `extract_confidence.sh` to process features, scores and boolean masks (for whether the smaller model matches with the larger model) on a per-token basis

4. Build 'correctors' for confidence estimation with `switch.TokenCorrecter` for each token of interest:

    ```python 
    merges_contents = generate.extract_token_files(
        token_files = ..., # list of token files extracted with `extract_confidence.sh`
        sample_limit = 20000,
        verbose = True
    )

    corrector = switch.TokenCorrecter(
        data = merges_contents['batch_features'],
        masks = merges_contents['batch_masks'],
        verbose = True
    )
    corrector.eval_both()
    corrector.save_cache(...) # save path for the token corrector

    utils.empty_cache()
    del corrector
    ```

5. Test on smaller model traces and visualise (see notebook `eval_test_trace.ipynb`)

 
