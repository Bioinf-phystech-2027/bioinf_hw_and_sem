Задание 1. Подготовка данных.
Для данного задания я выбрала ген, о котором услышала в подкасте правого полушария интроверта - DRD4 (фото-подтверждение прикрепляю):

Проверка какой формат изначально:

> head -5 ortholog_data/ncbi_dataset/data/protein.faa

XP_002821373.3 DRD4 [organism=Pongo abelii] [GeneID=100462264]

MGNRSTADEDWLLAGLGPDAGAAAGASAGLAGQGAAALVGGVLLIGAVLAGNSLVCVSVATERALQTPTN
SFIVSLAAADLLLALLVLPLFVYSEVQGGAWLLSPRLCDALMAMDVMLCTASIFNLCAISVDRFVAVAVP
LRYNRQGGSRRQLLLIGATWLLSAAVAAPILCGLNDVRGRDPAVCRLEDRDYVVYSSVCSFFLPCPLMLL
LYWATFRGLQRWEVARRAKLHGRAPRRPSGPGPPSPTPPAPRLPQDPCGPDCAPPAPRLPQGPCSPNCAS

Команда для переименования:

> sed -E 's/^>([A-Za-z0-9_.]+).+\[organism=([^]]+)\].*/>\2_\1/; s/ /_/g' ortholog_data/ncbi_dataset/data/protein.faa > ortholog_data/ncbi_dataset/data/protein_renamed.faa

Проверка после:

> head -5 ortholog_data/ncbi_dataset/data/protein_renamed.faa

Pongo_abelii_XP_002821373.3

MGNRSTADEDWLLAGLGPDAGAAAGASAGLAGQGAAALVGGVLLIGAVLAGNSLVCVSVATERALQTPTN
SFIVSLAAADLLLALLVLPLFVYSEVQGGAWLLSPRLCDALMAMDVMLCTASIFNLCAISVDRFVAVAVP
