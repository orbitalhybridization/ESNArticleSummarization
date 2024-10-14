# ESNArticleSummarization
Using echo state networks (ESNs) for article summarization using the GigaWord dataset. This method uses BERT embeddings of the  since the BERT model is bidirectional and the embeddings can be decoded. You should just be able to run everything in the Jupyter Notebook to get decoded summaries.

## Dependencies
 - reservoirpy
 - gigaword

## Method

1. Generate BERT embeddings of articles and summarizes
2. Feed into reservoir as a timeseries
3. Train readout to map last state of reservoir to BERT embedding of article summary
4. Decode predicted embeddings as text

The method doesn't work great currently, and likely needs some tuning / restructuring. Some potential issues include:
 - *Non-representative embedding space.* BERT embeddings are useful, but something more semantically rich for entities like Wikipedia2Vec might be better
 - *Masking.* Might be better to mask or omit some words. Also some words in Gigaword are masked (e.g., # for numbers and UNK for unknown)
 - *Hyperparameter Tuning.* Likely need a sweep of hyperparameters for memory (leak rate) and spectral radius.

## Examples

| Original Summary   | Reservoir Prediction |
|--------------------|----------------------|
| "downing of plane slows sri lanka 's army onslaught on jaffna by amal jayasinghe"
                   | 'korea: soldiers in the field of battle in korea.korea.malaysia.indonesia.jakarta.malayas.korean army.kamikaze.kampani.'
                      |
| "do n't blame pakistan for poor test ticket sales says manager"
                   | ' takfisk on govt, but on a number of other things.'
                     |
| 'rumsfeld calls zarqawi death significant victory'
                   |'Finance Minister of the Bank of Japan (BoT) says it will bring into an aero-mono plan of an omer-Tobel at the end of the year. e.t.m.e in'
                      |

