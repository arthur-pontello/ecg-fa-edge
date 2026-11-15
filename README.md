# ecg-fa-edge
Repositório destinado para inicio de projeto, com exploração real de ecg com python

## Fonte de Dados e Rastreabilidade

* **Base de dados:** Long-Term AF Database (LTAFDB)
* **Versão:** 1.0.0
* **Repositório oficial:** [PhysioNet - LTAFDB v1.0.0](https://physionet.org/content/ltafdb/1.0.0/) (DOI: `10.13026/C2QG6Q`)
* **Licença:** Open Data Commons Attribution License v1.0 *(https://opendatacommons.org/licenses/by/index.html)*
* **Origem e características do sinal:** Registros ambulatoriais de ECG de longa duração (Holter, ~24 a 25 horas) coletados em pacientes com fibrilação atrial paroxística ou sustentada. Cada registro possui 2 canais digitalizados a uma frequência nominal de 128 Hz.
* **Escopo utilizado nesta tarefa:** Leitura remota via biblioteca `wfdb` (`pn_dir="ltafdb/1.0.0"`) apenas dos **30 segundos iniciais** (`sampfrom=0`, `sampto=3840`) dos registros **`00`** e **`01`**, evitando o download integral da base.

### Estrutura dos Arquivos WFDB Consultados

* **`.hea` (Header):** Arquivo de cabeçalho em texto com os metadados da gravação com instruções para leitura dos dados em .dat.
* **`.dat` (Data):** Arquivo binário contendo as amostras brutas do sinal eletrocardiográfico.
* **`.atr` (Annotations):** As anotações atr foram obtidas por meio de revisão manual do resultado de um sistema automatizado de análise de ECG ; nesses arquivos de anotação, todos os batimentos detectados são classificados por tipo, e alterações no ritmo também são anotadas .
* **`.qrs`:** As anotações QRS foram geradas por um detector automático de QRS; nesses arquivos de anotação, todos os batimentos detectados (incluindo eventuais batimentos ectópicos ventriculares) são rotulados como N, os artefatos detectados são rotulados como '|' e as terminações de FA são rotuladas como T.
