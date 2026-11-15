# Raporti i studentit: UrbanBike AI

Studenti:Kejsi Kapxhiu
Data:11.11.2026
GitHub-i im:https://github.com/KC1103/urbanbike-ai-kejsi.git
Figma:https://www.figma.com/design/uiUliUU5rnkjEPty2X0P3d/UrbanBike-AI-Kejsi-Kapxhiu?node-id=0-1&t=oeisMh42x4N11HwG-1

## Qëllimi

Problemi që zgjidhim:Sa qira biçikletash priten për ditën pasuese në Washington, D.C.?
Target-i y:rentals.
Predictorët X:rentals_lag1: numri i bicikletave te marra me qira nje dite me pare.
rentals_lag7: numri i qirave shtate dite me pare.
rentals_mean7: mesatarja e qirave gjate shtate diteve te meparshme.
temp_c_lag7: temperatura shtate dite me pare.
rain_mm_lag7: reshjet shtate dite me pare.
wind_ms_lag7: shpejtesia e eres shtate dite me pare.
trend_days: numeruesi i diteve nga fillimi i periudhes.
Koha kur parashikojmë dhe çfarë informacioni është i njohur:Modeli parashikon numrin e qirave per diten pasuese, duke perdorur te dhenat e njohura deri ne diten paraardhese. Per variablat meteorologjike perdoren te dhenat me vonese prej shtate ditesh.

## Pastrimi

Burimet reale dhe çelësi i bashkimit:UCI day.csv dhe NASA nasa_weather.csv. Bashkimi u be sipas kolones date.
Dallimi mes origjinaleve dhe kopjes didaktike:Origjinalet nuk u ndryshuan. Problemet u shtuan vetem ne kopjen didaktike.
Rreshtat para/pas:743 rreshta para pastrimit dhe 731 pas pastrimit.
Dublimet: U gjeten dhe u hoqen 12 rreshta duplikate.
Mungesat para/pas konvertimit:Kishte 30 vlera bosh dhe 6 vlera tekstuale te pavlefshme. Pas konvertimit u krijuan gjithsej 36 vlera NaN.
Arsyeja e imputimit vetëm me train:Per te shmangur data leakage dhe qe modeli te mos perdore informacion nga testimi gjate mesimit.

## Grafikët

Vëzhgimi 1 dhe figura përkatëse:Ne grafikun 01_demand.png shihen ndryshime te numrit te qirave gjate diteve, me periudha ku kerkesa eshte me e larte dhe me e ulet.
Vëzhgimi 2 dhe figura përkatëse:Ne grafikun 02_workingday.png krahasohet numri mesatar i qirave ne ditet e punes me fundjavat dhe festat.
Pse një lidhje e dukshme nuk provon shkakësi: Sepse dy variabla mund te ndryshojne ne te njejten kohe, por kjo nuk do te thote qe njera shkakton ndryshimin e tjetres. Mund te ndikojne edhe faktore te tjere.

## Vlerësimi

Modeli   	Validation MAE	  Test MAE	Test RMSE	Test R²
Yesterday	775.203	          916.402	1330.386	0.539
DummyMean	2953.866          2494.628	2790.064	-1.027
Ridge	    687.558           893.251	1252.655	0.591
RandomForest	1821.528	  1671.499	2042.654	-0.087

Modeli i zgjedhur nga validation dhe arsyeja:U zgjodh modeli Ridge, sepse kishte MAE me te ulet ne validation (687.558), krahasuar me Random Forest (1821.528). Kjo tregon se Ridge dha parashikime me te sakta.
Rezultati i provës me Random Forest:Random Forest pati rezultat me te dobet, me MAE 1821.528 ne validation dhe 1671.499 ne test. Pra, modeli me kompleks nuk permiresoi parashikimin.
Interpretimi i gabimit në qira për ditë:Ridge pati MAE 893.251 dhe RMSE 1252.655 ne test. Kjo do te thote se gabimi absolut mesatar ishte rreth 893 qira ne dite. RMSE me i larte tregon ndikimin e gabimeve me te medha.
Rezultati i klasifikimit, nëse u realizua:

## Kufizimet

1.Një qytet dhe periudhë historike: Projekti perdor te dhena vetem per Washington D.C. gjate viteve 2011–2012. Prandaj, rezultatet nuk mund te pergjithesohen automatikisht per qytete ose periudha te tjera.
2.Te dhenat meteorologjike NASA: NASA perdor nje rrjet meteorologjik dhe LST, ndaj te dhenat mund te mos pasqyrojne plotesisht kushtet reale te motit ne cdo zone te qytetit.
3.Parashikimi nje ditor: Modeli supozon se te dhenat e dites se djeshme jane te njohura. Prandaj, nuk mund te konsiderohet nje parashikim i pavarur ne kohe reale.

## Kontributet individuale

Studenti:Kejsi Kapxhiu

Skedari/ekrani:01_clean.py, 02_visualize.py, 03_train.py, 04_classify.py, app.py

Puna dhe vendimi:Pastrimi dhe bashkimi i te dhenave, krijimi i grafikëve, trajnimi dhe vleresimi i modeleve, klasifikimi dhe ndertimi i aplikacionit. Zgjodha Ridge sepse dha MAE me te ulet ne validation.

Commit/prova:Kodet, grafiket dhe rezultatet ne dosjen reports/



## Burimet

UCI: https://doi.org/10.24432/C5W894
NASA: https://power.larc.nasa.gov/docs/services/api/temporal/daily/
Provenienca lokale: data/raw/provenance.json
