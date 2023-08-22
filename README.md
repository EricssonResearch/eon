# Ericsson Outlier Nexus (EON) <br> &ndash; KPI Datasets for Forecasting & Anomaly Detection

EON is a repository that contains the following KPI (Key Performance Indicator) datasets that can be used to validate and compare performances of forecasting and time series anomaly detection (AD) algorithms. 

- **EON1-Cell-F** for univariate forecasting
- **EON1-Cell-U** for univariate anomaly detection

Though these datasets are synthetically generated, they have been evaluated by domain experts to confirm that these datasets mimic the characteristics of real network KPI data.

## How to use the datasets

There are 10 KPIs in EON1 identified by letters A through J. Each KPI has a data point for every 15-minute interval. This interval is considered the Result Output Period (ROP). Thus, there are 96 ROPs in a single day (24 hours × 4 intervals = 96). 

Though only one file is provided for a dataset, each dataset is split into training, validation, and testing sets with one month of data each as shown below.

|     #    |     Subset        |     Start                  |     End                    |
|----------|-------------------|----------------------------|----------------------------|
|     1    |     Training      |     2023-02-01 00:00:00    |     2023-02-28 23:45:00    |
|     2    |     Validation    |     2023-03-01 00:00:00    |     2023-03-31 23:45:00    |
|     3    |     Testing       |     2023-04-01 00:00:00    |     2023-04-30 23:45:00    |


### EON1-Cell-F
Cell-F consists of a subset of KPIs in EON1 that are forecastable (the first six) – one column for each KPI. All KPIs in the dataset are nonnegative real numbers.

Column name format: `<Letter>`. <br>
E.g., A, B, C, etc.

|     #    |     Field        |     Type         |
|----------|------------------|------------------|
|     1    |     Timestamp    |     Timestamp    |
|     2    |     A            |     Float        |
|     3    |     B            |     Float        |
|     …    |     …            |     …            |
|     7    |     F            |     Float        |

### EON1-Cell-U

Cell-U also consists of one column per KPI along with an anomaly label column for each KPI. The anomaly label can be one of three values:

-	0 if the KPI value is not anomalous
-	1 if the KPI value is anomalously large (right-tailed anomaly)
-	-1 if the KPI value is anomalously small (left-tailed anomaly)

Column name format for anomaly labels: `Anomaly_<Letter>`. <br>
E.g., Anomaly_A, Anomaly_B, etc.

|     #     |     Field        |     Type         |
|-----------|------------------|------------------|
|     1     |     Timestamp    |     Timestamp    |
|     2     |     A            |     Float        |
|     3     |     Anomaly_A    |     Integer      |
|     4     |     B            |     Float        |
|     5     |     Anomaly_B    |     Integer      |
|     …     |     …            |     …            |
|     20    |     J            |     Float        |
|     21    |     Anomaly_J    |     Integer      |

This dataset is designed for unsupervised time series anomaly detection. Therefore, there are only anomalies present in the validation and testing splits, not in the training split. Anomalies that exist in these datasets occur in multi-ROP sequence, that is, each anomalous occurrence would last for at least 4 ROPs. No isolated anomalies exist in this dataset.


## Citation

Please cite the relevant paper should you wish to utilize the respective dataset in your research publications.
The papers and their respective BibTeX versions are given below. 

The details of the EON1-Cell-F dataset have been mentioned in the [QBSD paper](https://arxiv.org/abs/2306.05989).
 
```bibtex
@misc{ebe2023qbsd,
  title={{QBSD:} Quartile-Based Seasonality Decomposition for Cost-Effective Time Series Forecasting}, 
  author={Ebenezer R H P Isaac and Bulbul Singh},
  year={2023},
  eprint={2306.05989},
  archivePrefix={arXiv},
  primaryClass={cs.LG},
  note={arXiv preprint},
  url={https://arxiv.org/abs/2306.05989}
}
```

The details of the EON1-Cell-U dataset have been mentioned in the [ATH paper](https://arxiv.org/abs/2308.10504).
 
```bibtex
@misc{ebe2023ath,
  title={Adaptive Thresholding Heuristic for KPI Anomaly Detection}, 
  author={Ebenezer R H P Isaac and Akshat Sharma},
  year={2023},
  eprint={2308.10504},
  archivePrefix={arXiv},
  primaryClass={cs.LG},
  note={arXiv preprint},
  url={https://arxiv.org/abs/2308.10504}
}
```

---

## License

[![CC BY-ND 4.0][cc-by-nd-shield]][cc-by-nd]

This work is licensed under a
[Creative Commons Attribution-NoDerivatives 4.0 International License][cc-by-nd].

[![CC BY-SA 4.0][cc-by-nd-image]][cc-by-nd]

[cc-by-nd]: https://creativecommons.org/licenses/by-nd/4.0/
[cc-by-nd-image]: https://licensebuttons.net/l/by-nd/4.0/88x31.png
[cc-by-nd-shield]: https://img.shields.io/badge/License-CC%20BY--ND%204.0-lightgrey.svg
