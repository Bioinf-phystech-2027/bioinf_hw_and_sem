# Задание 1. Подготовка данных.
Для данного задания я выбрала ген, о котором услышала в подкасте правого полушария интроверта - DRD4 (фото-подтверждение прикрепляю):

### Проверка какой формат изначально:

> head -5 ortholog_data/ncbi_dataset/data/protein.faa

XP_002821373.3 DRD4 [organism=Pongo abelii] [GeneID=100462264]

MGNRSTADEDWLLAGLGPDAGAAAGASAGLAGQGAAALVGGVLLIGAVLAGNSLVCVSVATERALQTPTN
SFIVSLAAADLLLALLVLPLFVYSEVQGGAWLLSPRLCDALMAMDVMLCTASIFNLCAISVDRFVAVAVP
LRYNRQGGSRRQLLLIGATWLLSAAVAAPILCGLNDVRGRDPAVCRLEDRDYVVYSSVCSFFLPCPLMLL
LYWATFRGLQRWEVARRAKLHGRAPRRPSGPGPPSPTPPAPRLPQDPCGPDCAPPAPRLPQGPCSPNCAS

### Команда для переименования:

> sed -E 's/^>([A-Za-z0-9_.]+).+\[organism=([^]]+)\].*/>\2_\1/; s/ /_/g' ortholog_data/ncbi_dataset/data/protein.faa > ortholog_data/ncbi_dataset/data/protein_renamed.faa

### Проверка после:

> head -5 ortholog_data/ncbi_dataset/data/protein_renamed.faa

Pongo_abelii_XP_002821373.3

MGNRSTADEDWLLAGLGPDAGAAAGASAGLAGQGAAALVGGVLLIGAVLAGNSLVCVSVATERALQTPTN
SFIVSLAAADLLLALLVLPLFVYSEVQGGAWLLSPRLCDALMAMDVMLCTASIFNLCAISVDRFVAVAVP
LRYNRQGGSRRQLLLIGATWLLSAAVAAPILCGLNDVRGRDPAVCRLEDRDYVVYSSVCSFFLPCPLMLL
LYWATFRGLQRWEVARRAKLHGRAPRRPSGPGPPSPTPPAPRLPQDPCGPDCAPPAPRLPQGPCSPNCAS

# Задание 2. Множественное выравнивание.

В школьные годы пользовалась этим порталом, думаю, что ничего особо не поменялось:

https://www.ebi.ac.uk/jdispatcher/msa/clustalo/summary?jobId=clustalo-I20260420-210636-0263-96832070-p1m

(CLUSTAL)

Проигнорируем манящую вкладку с уже готовым деревом 

(
Phylogenetic Tree
(
(
(
(
(
(
(
(
Macaca_fascicularis_XP_073868820.1:0.26086,
Callithrix_jacchus_XP_035119788.3:0.07867)
:0.02929,
(
Macaca_mulatta_XP_077817737.1:0.00000,
Macaca_fascicularis_XP_045228402.1:0.00000)
:0.02241)
:0.03040,
(
(
(
(
(
(
(
(
Carlito_syrichta_XP_008048868.2:0.15593,
Mandrillus_leucophaeus_XP_011849216.1:-0.07593)
:0.01691,
(
Rhinopithecus_bieti_XP_017714425.1:-0.05817,
Colobus_angolensis_palliatus_XP_011785529.1:0.07945)
:0.06334)
:0.05476,
(
(
(
Otolemur_garnettii_XP_003802825.1:0.02675,
Nycticebus_coucang_XP_053418734.1:0.01685)
:0.02416,
(
(
(
Eulemur_rufifrons_XP_069326520.1:0.01274,
Lemur_catta_XP_045412822.1:-0.00224)
:0.02281,
Microcebus_murinus_XP_020142024.2:0.03817)
:0.00342,
Propithecus_coquereli_XP_012507390.1:0.00843)
:0.00826)
:0.01680,
(
(
Saimiri_boliviensis_XP_039326630.1:0.01305,
(
(
Cebus_imitator_XP_037587084.1:0.03663,
Callithrix_jacchus_XP_035119789.2:0.01037)
:0.00830,
Sapajus_apella_XP_032127362.1:0.02121)
:0.00370)
:0.00338,
Aotus_nancymaae_XP_021532712.2:0.03678)
:0.00840)
:0.00774)
:0.00603,
(
(
(
(
(
(
Symphalangus_syndactylus_XP_063486955.1:0.00483,
Symphalangus_syndactylus_XP_063486954.1:-0.00483)
:0.01235,
Symphalangus_syndactylus_XP_055116073.1:-0.00441)
:0.01766,
Nomascus_leucogenys_XP_030657604.1:0.01715)
:0.00748,
Hylobates_moloch_XP_032005192.2:0.01815)
:0.00588,
(
(
Pan_troglodytes_XP_016775504.1:0.00811,
Pan_paniscus_XP_054949901.2:0.01107)
:0.00987,
Homo_sapiens_NP_000788.2:0.00662)
:0.00472)
:0.00193,
(
Gorilla_gorilla_gorilla_XP_055211722.2:0.02219,
(
Pongo_pygmaeus_XP_054293669.2:0.00394,
Pongo_abelii_XP_002821373.3:0.00820)
:0.01562)
:0.00230)
:0.00321)
:0.00879,
(
Rhinopithecus_roxellana_XP_030774418.1:-0.00436,
Rhinopithecus_roxellana_XP_010354203.2:0.00922)
:0.01613)
:0.00399,
Piliocolobus_tephrosceles_XP_026303071.1:0.03567)
:0.00608,
Trachypithecus_francoisi_XP_033059888.1:0.00854)
:0.00545,
Chlorocebus_sabaeus_XP_072878986.1:0.00972)
:0.00232)
:0.00368,
(
Papio_anubis_XP_003909377.3:0.00175,
Cercocebus_atys_XP_011896378.1:0.00559)
:0.00083)
:0.00053,
Theropithecus_gelada_XP_025213568.1:0.00195)
:0.00034,
Macaca_nemestrina_XP_011760593.2:-0.00015)
:0.00012,
Macaca_fascicularis_XP_005576821.3:0.00000)
:0.00000,
Macaca_thibetana_thibetana_XP_050613855.1:0.00000,
Macaca_mulatta_XP_077817738.1:0.00000);
) 

и перейдем к другому заданию. Выравнивание можете найти в файле clustalo-I20260420-210636-0263-96832070-p1m.aln-clustal.

# Задание 3. Построение филогенетических деревьев.


