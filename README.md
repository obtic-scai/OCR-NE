# OCR-NER

This repository contains code developed for spell checking the raw OCRised French texts in the TEI-XML format issued from the [Très Grande Bibliothèque](http://obvil.lip6.fr/tgb/) (TGB).

Three spellchecking libraries have been tested: [`pyspellchecker`](https://github.com/barrust/pyspellchecker), [`pyenchant`](https://github.com/pyenchant/pyenchant) and [`jamspell`](https://github.com/bakwc/JamSpell), with the aim to compare the two approaches in terms of their general performance:

1. approach by dictionary (`pyspellchecker` and `pyenchant` );
2. machine-learning approach  (`jamspell`).

The ultimate goal was not the correction post-OCR _per se_, but the valorisation and the exploitation of the orthographically corrected corpus via the named entity recognition (NER) method, in order to determine the impact of the spellchecking libraries on the NER task.

The code for spellchecking the texts with `pyenchant` was originally written by Nicolas Hiebel, the former intern of the former OBVIL Laboratory of Excellence (cf. the original [repo](https://github.com/Hiebel/Stage-OBVIL-2020/tree/master/Python). 

# Workflow 

The flowchart diagram below illustrates the general idea of the project:
<p align="center">
    <img src="img/post-ocr.drawio.png">
</p>

# Results

The use of those three libraries has relatively improved the text output, even though some results are not perfect:

## `pyspellchecker`

Some tokens have been well corrected, especially those containing the recurrent alternation throughout the text of the type **_ſ:s_**, where the _ſ_ is a ligature designating the "long s" (e.g. _con**ſ**eillers > con**s**eillers, repré**ſ**ente > repré**s**ente, diver**ſ**es > diver**s**es_ and so on).

However, the library sometimes corrects words that do not require correction (_**l**’abondance > abondance_).<br>
The archaic forms of verbs were modernised during the correction (_apport**o**it > apport**a**it_).<br> 
In addition, the less known named entities were not corrected, e.g. _Tchun-t**ſ**iou_ (a book about the description of China), instead of _Tchun-t**s**iou_.

Correction examples:

|     Error    |  Correction  | Frequence | 
|:------------:|:------------:|:---------:|
|   dirfufion  |   diffusion  |     1     |  
|   fubtilité  |   subtilité  |     1     |   
|   confufion  |   confusion  |     1     |   
|   doftrine   |   doctrine   | 1         |   
|   doéleurs   |   douleurs   |     1     |   
|     falle    |     fille    |     1     |   
|    s’étoit   |    sétait    |     1     |   
|  doctrinede  |   doctrine   |     1     |   
|     fophe    |     force    |     1     |   
|  expreflions |  expressions |     1     |   
| cnfcignement | cnfcignement |     1     |   
|   illupcres  |   illustres  | 1         |  

## `pyenchant`

This library corrected some words that `pyspellchecker` did not correct.

Correction examples:

|       Error       |         Correction        |                                                        Context                                                        | File name   |   
|:-----------------:|:-------------------------:|:---------------------------------------------------------------------------------------------------------------------:|-------------|
|      occafion     |          occasion         |      que où osâtes les informerons sont rapportées à l’occafion des événements observations va il falloir donc da     | 5419000.txt |   
| moralepolitiquede | Pas de correction trouvée | pplication pour bien entendre les principes de la moralepolitiquede la chine et pour peu qu’il y eût d’interruption o | 5419000.txt |   
|         qu        |            que            |         ipes de la moralepolitiquede la chine et pour peu que’il y eût d’interruption ou de relâchement dans l        | 5419000.txt |   
|     néceflîté     |         nécessité         |     endus et l’on devoir moins sentir et connaître la néceflîté de suivre la doctrine qu’ils renferment c’efl ce      | 5419000.txt |   
|        efl        |             et            |        essité de suivre la doctrine que’ils renferment c’eflce qui arriva lorsque le trône fut occupé par des         | 5419000.txt |   
|    introduifent   |        introduisent       |    nt de ce moment de négligence et de relâchement s’introduifent à la cour et de la cour fe communiquent aux grand   | 5419000.txt |   
|      defendre     |          défendre         |      nement primitif qui élevé au trône ou qui en fait defendre cependant les guerres fréquentes interrompent le      | 5419000.txt |   
|     inftruâion    | Pas de correction trouvée |     les guerres fréquentes interrompent le cours de l’inftruâion et le progrès de la vertu il fe forme plus de gue    | 5419000.txt |   
|   impoflîbilité   |       impossibilité       |   tie de la nation qui ne pouvoir pas éclairer et l’impoflîbilité de éclairer fit tomber dans l’oubli les livres dé   | 5419000.txt |   
|     confucius     |         confusions        |      et effet l’un de l’autre a l’âge de dix-neuf ans confuciuss aperçut la cause des maux qui défilaient fa patr     | 5419000.txt |   
|    rttablifsant   |        rétablissant       |    atrie et forma le projet d’en arrêter le cours en rttablifsant dans les esprits la doc trône  des premiers temps   | 5419000.txt |   
|                   |                           |                                                                                                                       |             |   


# Conclusion 

For more details, cf. the [internship report](https://docs.google.com/document/d/1DoVp1Ix6xobsaK2XBvQokKUpTzVbAa0B3VEPD7GWmlc/edit?usp=sharing). 
