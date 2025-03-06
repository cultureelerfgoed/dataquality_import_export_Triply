# Datakwaliteit Dashboard: Vergelijking tussen de xml file pre en post import in TriplyDB.

### Zie hier de [Dashboard](https://cultureelerfgoed.github.io/dataquality_import_export_Triply/)

Dit prototype is ontwikkeld om op een interactive manier datakwaliteit in kaart te brengen en vragen vanuit de bussiness te beantwoorden. Er is zowel gekeken naar de benodigheden om een dergelijke vergelijking te kunnen maken.

Voor de vergelijkingcode zie: [XML comparisson](https://nbviewer.org/github/cultureelerfgoed/dataquality_import_export_Triply/blob/main/xml-check.ipynb?flush_cache=true)

Voor de code voor data verwerking zie: 
- [XML verwerking Pre-Triply import](https://nbviewer.org/github/cultureelerfgoed/dataquality_import_export_Triply/blob/main/dataset_pre_import_verwerking.ipynb?flush_cache=true)
- [XML verwerking Post-Triply import](https://nbviewer.org/github/cultureelerfgoed/dataquality_import_export_Triply/blob/main/dataset_post_import_verwerking.ipynb?flush_cache=true)


Hieronder de dataflow schema dat weergeeft hoe data verwerkt is in dit pipeline:


```mermaid
graph TD
id1(XML pre import Triply, test_archis.xml) --> id2(script: dataset_pre_import_verwerking.ipynb)
click id2 "https://nbviewer.org/github/cultureelerfgoed/dataquality_import_export_Triply/blob/main/dataset_pre_import_verwerking.ipynb?flush_cache=true" _blank
id2--> id3[(SQLite3)]
id3-->id2
id2-->id4(preTriplyDataframe.csv)
id5(XML post import Triply) --> id6(script: dataset_post_import_verwerking.ipynb)
click id6 "https://nbviewer.org/github/cultureelerfgoed/dataquality_import_export_Triply/blob/main/dataset_post_import_verwerking.ipynb?flush_cache=true"
id6-->id3
id3-->id6

id6-->id7(postTriplyDataframe.csv) 
id7-->id8(script: xml-check.ipynb)
click id8 "https://nbviewer.org/github/cultureelerfgoed/dataquality_import_export_Triply/blob/main/xml-check.ipynb?flush_cache=true"
id4-->id8
id8-->id9(dataset_tellingen_tijdlijn.csv)
id8-->id11(verschillen_vergelijking_choIds.zip)
id11-->id10
id9-->id10(Dashboard)

```


