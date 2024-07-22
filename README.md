# scrna-ali
----

This repository contains the data and code to reproduce the results of the reaserch paper: Capybara [https://doi.org/10.1016/j.stem.2022.03.001](https://doi.org/10.1016/j.stem.2022.03.001)

### Dataset 1: Paul 2015
---

The raw data corresponding to this data set is depeosited under GSE ID: GSE72857. 
- The raw counts file and metadata file is dowloaded and processed using the notebook `(./dataset-1-GSE72857/GSE72857/py/GSE72857_download_raw.ipynb)`
- The unfiltered raw counts scanpy object is analysed using the notebook `(./dataset-1-GSE72857/GSE72857/py/GSE72857_analysis_py.py)`. **Note**: This is having a lot of unfiltered data and contains noise.
- The notebook `(./dataset-1-GSE72857/GSE72857/py/GSR72857_analysis_pp_py.ipynb)` contains the code to reproduce to results of Paul 2015 and also the save the data to disk

---

#### Spinning up the environment: 
---

The Paul 2015 dataset up processed in an python 3.7 environment. And an older version of scanpy. Current python versions - 3.11, 3.12 are having dependency clashes with the Library ForceAtlas2. 
ForceAtlas2 is critical in reproducing the results of Paul 2015. Therefore in this repository there is also a Dockerfile to create a docker image which contains all the required depencencies. 

You'll need to install docker in your system. Read : `(https://docs.docker.com/engine/install/ubuntu/)`

Then to sping up a container you can use the docker compose file `(./dataset-1-GSE72857/docker-compose.yml)`.

Command: 

```bash
cd dataset-1-GSE72857/
docker compose -f docker-compose.yml --build up -d
```

This will sping up a Jupyter Lab environment. You can reach the Jupyter Lab window on your browser: `(http://localhost:1000)
You can get the token from the docker logs of the notebook conatiner.

Command: 
```bash
docker logs ${notebook-py-container-id}
```