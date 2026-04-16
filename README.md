# dpd-cancer

Graph neural network–based drug response prediction served as a web application.

This repository provides a complete, production-ready stack for running pretrained
GAT-based models for:

- **Binary classification** of compound activity.
- **Per–cell-line regression** (pGI₅₀) for a panel of human cancer cell lines.

All models are deployed behind a Flask web server and accessed via a Redis/RQ-backed
job system. The system is designed for researchers who wish to:

- Host models on a GPU server or HPC cluster.
- Submit compounds as SMILES strings.
- Obtain classification and regression predictions for a curated set of cell lines.
- Interact through a browser-based front-end (HTML templates).
- Produce model-specific interpretation outputs (saliency SVGs) from the command line.


## Conda Environments

The repository assumes three environments:

Web environment (Flask, redis-py, rq, gunicorn/WSGI stack)
- Defined by env_web.yml.
- Used by app.py, main_handler.py, run.py, wsgi.py.

Featuriser environment (Python 3.8, DeepChem, molfeat, RDKit)
- Defined by env_featuriser.yml.
- Used by featuriser.py.

Inference environment (Python 3.12, PyTorch, PyTorch Geometric, Lightning)
- Defined by env_deeppd.yml.
- Used by predict.py and interpret.py.
