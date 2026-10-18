# Citation

## Citing this project

If you reuse this notebook or protocol, please cite the dataset, the pretrained model and the papers below — they carry the scientific credit. Suggested attribution for the project itself:

```bibtex
@misc{socialmedia-sentiment-comparison,
  title  = {Social Media Sentiment Analysis: A Comparative Study of Classical
            Machine Learning and Pretrained Transformer Models},
  author = {[Your Name]},
  year   = {2026},
  note   = {Educational portfolio project; not peer-reviewed},
  url    = {[repository URL]}
}
```

## Dataset

*Kaggle page*: <https://www.kaggle.com/datasets/crowdflower/twitter-airline-sentiment>
*Licence*: **CC BY-NC-SA 4.0** (verified on the dataset page) — non-commercial use, attribution, share-alike. Data: 14,640 crowd-labelled English tweets toward US airlines, collected February 2015 by CrowdFlower.

```bibtex
@misc{crowdflower-2016-twitter-airline-sentiment,
  author       = {{CrowdFlower}},
  title        = {Twitter {US} Airline Sentiment},
  year         = {2015},
  howpublished = {Kaggle data set},
  url          = {https://www.kaggle.com/datasets/crowdflower/twitter-airline-sentiment},
  note         = {Licensed CC BY-NC-SA 4.0}
}
```

## Pretrained model

`cardiffnlp/twitter-roberta-base-sentiment-latest` — a RoBERTa-base model trained on ~124M tweets (January 2018 – December 2021) and fine-tuned on the TweetEval sentiment benchmark; labels `{0: negative, 1: neutral, 2: positive}`.
*Model card*: <https://huggingface.co/cardiffnlp/twitter-roberta-base-sentiment-latest>

```bibtex
@inproceedings{loureiro-etal-2022-timelms,
  title     = {{TimeLMs}: Diachronic Language Models from {T}witter},
  author    = {Loureiro, Daniel and Barbieri, Francesco and Neves, Leonor and
               Espinosa-Anke, Luis and Camacho-Collados, Jose},
  booktitle = {Proceedings of the 60th Annual Meeting of the Association for
               Computational Linguistics: System Demonstrations},
  year      = {2022},
  url       = {https://aclanthology.org/2022.acl-demo.25/}
}
```

## TweetEval (the sentiment benchmark the model is fine-tuned on)

```bibtex
@inproceedings{barbieri-etal-2020-tweeteval,
  title     = {{TweetEval}: Unified Benchmark and Comparative Evaluation for Tweet Classification},
  author    = {Barbieri, Francesco and Camacho-Collados, Jose and Neves, Leonor and Espinosa-Anke, Luis},
  booktitle = {Findings of the Association for Computational Linguistics: EMNLP 2020},
  year      = {2020},
  url       = {https://arxiv.org/abs/2010.12421}
}
```

## Libraries

```bibtex
@article{pedregosa-2011-scikit-learn,
  title   = {Scikit-learn: Machine Learning in {P}ython},
  author  = {Pedregosa, Fabian and Varoquaux, Ga{\"e}l and Gramfort, Alexandre and others},
  journal = {Journal of Machine Learning Research},
  volume  = {12},
  pages   = {2825--2830},
  year    = {2011}
}

@inproceedings{paszke-2019-pytorch,
  title     = {{PyTorch}: An Imperative Style, High-Performance Deep Learning Library},
  author    = {Paszke, Adam and Gross, Sam and Massa, Francisco and others},
  booktitle = {Advances in Neural Information Processing Systems 32 (NeurIPS 2019)},
  year      = {2019}
}

@inproceedings{wolf-etal-2020-transformers,
  title     = {Transformers: State-of-the-Art Natural Language Processing},
  author    = {Wolf, Thomas and Debut, Lysandre and Sanh, Victor and others},
  booktitle = {Proceedings of the 2020 Conference on Empirical Methods in Natural
               Language Processing: System Demonstrations},
  year      = {2020},
  url       = {https://aclanthology.org/2020.emnlp-demos.6/}
}

@inproceedings{mckinney-2010-pandas,
  title     = {Data Structures for Statistical Computing in {P}ython},
  author    = {McKinney, Wes},
  booktitle = {Proceedings of the 9th Python in Science Conference (SciPy 2010)},
  year      = {2010}
}
```

All URLs were verified at the time of writing.
