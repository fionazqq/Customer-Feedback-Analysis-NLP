
import pandas as pd
from tqdm import tqdm
import spacy
from keybert import KeyBERT

kw_model = KeyBERT()
pos_model = spacy.load("en_core_web_sm")



def keywords_bert(comment):
    return kw_model.extract_keywords(comment, keyphrase_ngram_range=(1, 3), stop_words='english',
                              use_mmr=True, diversity=0.7)

def keywords_bert_pos(comment):
    # apply bert model and rank tokens
    ranked_candidates = kw_model.extract_keywords(comment, top_n = 9999, 
                                                  stop_words='english', use_mmr=True, diversity=0.7)

    # filter nouns and adjectives
    nouns = []
    adj = []
    for (word, score) in ranked_candidates:
        if pos_model(word)[0].pos_ in ['NOUN', 'PROPN']:
            nouns.append((word, score))
        elif pos_model(word)[0].pos_ in ['ADJ']:
            adj.append((word, score))

    # return top three for both
    result = []
    result.append(nouns[:min(3, len(nouns))])
    result.append(adj[:min(3, len(adj))])
    return result


tqdm.pandas()

# warning this takes quite literally a day to run

case['keyphrases_list'] = case[customercomments].progress_map(keywords_bert)

case['keywords_list_pos'] = case[customercomments].progress_map(keywords_bert_pos)

