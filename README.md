# spacy-pyinstaller
Getting spaCy models to work with pyinstaller

The spaCy data path needs to be set manually to where the models are stored and models loaded with the folder name. E.g.

```
spacy.util.set_data_path('./')
nlp = spacy.load('en_core_web_sm')
```

Then run PyInstaller with the hidden-imports. Note that .en refers to the language not to the model.

```
pyinstaller pyitest.py --hidden-import cymem.cymem --hidden-import thinc.linalg --hidden-import murmurhash.mrmr --hidden-import cytoolz.utils --hidden-import cytoolz._signatures --hidden-import spacy.strings --hidden-import spacy.morphology --hidden-import spacy.lexeme --hidden-import spacy.tokens --hidden-import spacy.gold --hidden-import spacy.tokens.underscore --hidden-import spacy.parts_of_speech --hidden-import dill --hidden-import spacy.tokens.printers --hidden-import spacy.tokens._retokenize --hidden-import spacy.syntax --hidden-import spacy.syntax.stateclass --hidden-import spacy.syntax.transition_system --hidden-import spacy.syntax.nonproj --hidden-import spacy.syntax.nn_parser --hidden-import spacy.syntax.arc_eager --hidden-import thinc.extra.search --hidden-import spacy.syntax._beam_utils --hidden-import spacy.syntax.ner --hidden-import thinc.neural._classes.difference --hidden-import spacy.vocab --hidden-import spacy.lemmatizer --hidden-import spacy._ml --hidden-import ftfy --hidden-import spacy.lang --hidden-import spacy.lang.en
```

Copy ftfy into the dist folder and any spaCy models into the spaCy data directory inside dist.