DOWNLOAD AND UNZIP THE LIGHTWEIGHT MIDTERM PROJECT ZIP FILE TO RUN MIDTERM PROJECT FILES. It had to be zipped because the text files took too much space otherwise. 

Requirements to run all scripts (scroll down to see the instructions to actually run the scripts):
Create a virtual environment in Python 3.8.8
Run the following pip installations (some may be redunant):

pip install numpy
pip install transformers
pip install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cpu
pip install torch
pip install keras
pip install tensorflow

To be more explicit and in case you encounter issues, these are the pip installations that you need in a Python 3.8.8 environment to run all scripts:
Package                      Version
---------------------------- ---------
absl-py                      2.1.0
astunparse                   1.6.3
cachetools                   5.5.0
certifi                      2024.8.30
charset-normalizer           3.3.2
colorama                     0.4.6
filelock                     3.16.1
flatbuffers                  24.3.25
fsspec                       2024.9.0
gast                         0.4.0
google-auth                  2.35.0
google-auth-oauthlib         1.0.0
google-pasta                 0.2.0
grpcio                       1.66.2
h5py                         3.11.0
huggingface-hub              0.25.1
idna                         3.10
importlib_metadata           8.5.0
Jinja2                       3.1.4
keras                        2.13.1
libclang                     18.1.1
Markdown                     3.7
MarkupSafe                   2.1.5
mpmath                       1.3.0
networkx                     3.1
numpy                        1.24.3
oauthlib                     3.2.2
opt_einsum                   3.4.0
packaging                    24.1
pip                          24.2
protobuf                     4.25.5
pyasn1                       0.6.1
pyasn1_modules               0.4.1
PyYAML                       6.0.2
regex                        2024.9.11
requests                     2.32.3
requests-oauthlib            2.0.0
rsa                          4.9
safetensors                  0.4.5
setuptools                   49.2.1
six                          1.16.0
sympy                        1.13.3
tensorboard                  2.13.0
tensorboard-data-server      0.7.2
tensorflow                   2.13.0
tensorflow-estimator         2.13.0
tensorflow-intel             2.13.0
tensorflow-io-gcs-filesystem 0.31.0
termcolor                    2.4.0
tokenizers                   0.20.0
torch                        2.4.1
tqdm                         4.66.5
transformers                 4.45.1
typing_extensions            4.5.0
urllib3                      2.2.3
Werkzeug                     3.0.4
wheel                        0.44.0
wrapt                        1.16.0
zipp                         3.20.2



One you have all installations, follow this procedure to run my scripts and reproduce my results:
1. The raw data for the prompts--public domain novels as txt files-- are stored in the 'uncurtailed_folder' directory. Run 'parse_files_in_directory.py' to parse the data, creating raw prompt txt files.
2. The scripts to make Causal LM predictions on these prompt txt files are located in 'parallel_falcon', 'parallel_opt', 'parallel_distilgpt2', and 'parallel_bloom'. Each of these folders
contains scripts used to run a particular Causal LM according to the name. Within one of these folders are several subfolders with the names of novel titles. The subfolders are identical except for the
prompt txt files inside them and are duplicated for running in parallel. You may name these subfolders whatever you like and place any number of txt files into them according to your preference. To run
predictions, manually move the raw txt files from the previous step to the 'curtailed_folder' directory and run the 'make____predictions.py' file (the blank is filled with the name of the LLM, such as make_falcon_predictions.py)
So, an example pathway to the data directory is 'parallel_falcon\bleak_house_parallel\curtailed_folder' and its corresponding Python script is parallel_falcon\bleak_house_parallel\make_falcon_predictions.py.
3. Manually move the LLM prediction output files generated in the previous step (keeping their default names) to creating_actual_network_test\dataset. creating_actual_network_test\saved_classification_nn_8.keras is the 
saved, best performing model. Run creating_actual_network_test\classification_nn_8_train.py to train a new model (you will have to choose a new filename in the first line of the script because the script will not let you overwrite a trained model),
and run creating_actual_network_test\classification_nn_8_train.py to read in the existing trained model and use it to make a prediction on the training set. The training set is deterministically chosen for a given datset.

