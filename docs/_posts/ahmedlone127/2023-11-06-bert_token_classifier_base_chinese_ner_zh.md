---
layout: model
title: Chinese BertForTokenClassification Base Cased model (from ckiplab)
author: John Snow Labs
name: bert_token_classifier_base_chinese_ner
date: 2023-11-06
tags: [zh, open_source, bert, token_classification, ner, onnx]
task: Named Entity Recognition
language: zh
edition: Spark NLP 5.2.0
spark_version: 3.0
supported: true
engine: onnx
annotator: BertForTokenClassification
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

Pretrained BertForTokenClassification model, adapted from Hugging Face and curated to provide scalability and production-readiness using Spark NLP. `bert-base-chinese-ner` is a Chinese model originally trained by `ckiplab`.

## Predicted Entities

`S-WORK_OF_ART`, `S-TIME`, `E-FAC`, `S-PERCENT`, `S-PRODUCT`, `E-LANGUAGE`, `S-NORP`, `S-QUANTITY`, `S-PERSON`, `E-DATE`, `S-LOC`, `S-CARDINAL`, `E-QUANTITY`, `S-GPE`, `S-FAC`, `MONEY`, `S-ORG`, `E-NORP`, `E-GPE`, `E-TIME`, `EVENT`, `DATE`, `CARDINAL`, `FAC`, `E-PERCENT`, `E-PERSON`, `S-ORDINAL`, `NORP`, `LOC`, `E-ORG`, `E-MONEY`, `S-LAW`, `LAW`, `E-LOC`, `S-EVENT`, `ORG`, `TIME`, `ORDINAL`, `E-WORK_OF_ART`, `LANGUAGE`, `S-MONEY`, `E-ORDINAL`, `PERCENT`, `E-EVENT`, `S-LANGUAGE`, `E-PRODUCT`, `QUANTITY`, `WORK_OF_ART`, `E-LAW`, `S-DATE`, `PRODUCT`, `E-CARDINAL`, `PERSON`, `GPE`

{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/bert_token_classifier_base_chinese_ner_zh_5.2.0_3.0_1699302560261.zip){:.button.button-orange.button-orange-trans.arr.button-icon}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/public/models/bert_token_classifier_base_chinese_ner_zh_5.2.0_3.0_1699302560261.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

## How to use



<div class="tabs-box" markdown="1">
{% include programmingLanguageSelectScalaPythonNLU.html %}
```python
documentAssembler = DocumentAssembler() \
    .setInputCol("text") \
    .setOutputCol("document")

tokenizer = Tokenizer() \
    .setInputCols("document") \
    .setOutputCol("token")

tokenClassifier = BertForTokenClassification.pretrained("bert_token_classifier_base_chinese_ner","zh") \
    .setInputCols(["document", "token"]) \
    .setOutputCol("ner")

pipeline = Pipeline(stages=[documentAssembler, tokenizer, tokenClassifier])

data = spark.createDataFrame([["PUT YOUR STRING HERE"]]).toDF("text")

result = pipeline.fit(data).transform(data)
```
```scala
val documentAssembler = new DocumentAssembler()
    .setInputCol("text")
    .setOutputCol("document")

val tokenizer = new Tokenizer()
    .setInputCols("document")
    .setOutputCol("token")

val tokenClassifier = BertForTokenClassification.pretrained("bert_token_classifier_base_chinese_ner","zh")
    .setInputCols(Array("document", "token"))
    .setOutputCol("ner")

val pipeline = new Pipeline().setStages(Array(documentAssembler, tokenizer, tokenClassifier))

val data = Seq("PUT YOUR STRING HERE").toDS.toDF("text")

val result = pipeline.fit(data).transform(data)
```
</div>

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|bert_token_classifier_base_chinese_ner|
|Compatibility:|Spark NLP 5.2.0+|
|License:|Open Source|
|Edition:|Official|
|Input Labels:|[document, token]|
|Output Labels:|[ner]|
|Language:|zh|
|Size:|381.1 MB|
|Case sensitive:|true|
|Max sentence length:|128|

## References

References

- https://huggingface.co/ckiplab/bert-base-chinese-ner
- https://github.com/ckiplab/ckip-transformers
- https://muyang.pro
- https://ckip.iis.sinica.edu.tw
- https://github.com/ckiplab/ckip-transformers
- https://github.com/ckiplab/ckip-transformers