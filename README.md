# financial_readability

Package that implements the BOFIR score - a readability measure for business and financial texts. The measure ranks a paragraph based on 399 textual features into 5 readability categories ranging from 1 - "very hard to read" to 5 - "easy to read". The measure is also available on a three category scale.

A large part of the features are generated by using the spacy language model "en_core_web_md", available at: https://spacy.io/models/en

## Setup
Install lastest version from GitHub:
```
git clone https://github.com/grooof/financial_readability.git
cd financial_readability
pip install .
```
Note that this should automatically download the spacy "en_core_web_md" model. If not working, manually load the model with:
```
$ python -m spacy download en_core_web_sm
```

## Usage

```
>>> import financial_readability as fr

>>> test_data = ("This could be some complicated business text that contains a lot of difficult language, and is therefore poorly specified in classic readability formulas.")

>>> readability_test = fr.readability(test_data)
>>> readability_test.bofir()
4
```

## List of Functions
The object financial_readability.readability(paragraph) comes with following main methods:


#### Word-features:
word_features(embeddings = False):

        """
        Combines the featuresets to a Dataframe with 
        all the 88 word-features. 
        
        Parameters
        ----------
        embeddings : boolean
            Defines if the word embeddings (n=300) are included or not
            
        Returns
        -------
        d: pandas DataFrame
            Dataframe with all the Output Variables. Each row represents a token 
            and the features are in the columns (n x 88) as there are 88 word-features
        """


#### Paragraph-features:
paragraph_features(embed = False, as_dict = False):

  		"""
        Create the feature set over the total paragraph based on the 
        features estimated per word.
        
        Parameters
        ----------
        embed : boolean
            Defines if the word embeddings (n=300) are included or not
        as_dict : boolean
            Defines if output is a dataframe or dict
            
        Returns
        -------
        d: pandas DataFrame
            Dataframe with all the Output Variables. Each row represents a feature.
            columns: 
                cat: feature category
                value: value of the feature
            
        """

#### BOFIR:   
bofir(cat5 = True):

        """
        Use the paragraph features to calculate the BOFIR score for a
        given paragraph.
        
        Parameters
        ----------
        cat5: boolean
            Defines if BOFIR schould be calculated on 3 or 5 category scale
            
        Returns
        -------
        pred: integer
            The BOFIR score
            
        """
  
#### Readability Measures:  
readability_measures(as_dict = False):

        """
        Return the BOFIR score as well as other classic readability formulas for the paragraph.
        
        Parameters
        ----------
        as_dict : boolean
            Defines if output is a dataframe or dict
            
        Returns
        -------
        d: DataFrame
            DataFrame with the BOFIR score and additional readability measures
            
        """

