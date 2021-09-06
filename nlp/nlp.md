# Setup
To create a virtual environment from a yaml file inside the root folder where python notebooks are:
```
conda env create -f nlp_course_env.yml
```
To activate virtual environment:
```
source activate nlp_course
```
To deactivate virtual environment:
```
source deactivate
```
To open jupyter notebook in current folder:
```
jupyter notebook
```
You may convert notebooks to .py files by using nbconvert or just by clicking Save As -> .py file.

## How do you get the Docstring and method list pop-ups in Jupyter Notebook?
Use Tab with your cursor directly after a defined variable to see the list of methods. For example, given: `my_list = [1,2,3]` you could then run that cell to define `my_list` as a variable, afterwards you could just type: `my_list.` (notice the dot) and then press Tab to see the list of methods. For the doctrings of functions, use Shift+Tab with your cursor right after the function.

# Resources
- Udemy NLP with Python course Google Slides - https://drive.google.com/drive/folders/1ignykpRUm2P5dEYOWVL8mTYbwUhZVGFf
- Custom NER using spaCy - https://towardsdatascience.com/custom-named-entity-recognition-using-spacy-7140ebbb3718
- Topic modeling with LDA and NMF - https://medium.com/ml2vec/topic-modeling-is-an-unsupervised-learning-approach-to-clustering-documents-to-discover-topics-fdfbf30e27df
- spaCy training documentation - https://spacy.io/usage/training
- spaCy 101 - https://spacy.io/usage/spacy-101
- Which deep learning algorithm does spacy use to train custom models? - https://stackoverflow.com/questions/60381170/which-deep-learning-algorithm-does-spacy-uses-when-we-train-custom-model