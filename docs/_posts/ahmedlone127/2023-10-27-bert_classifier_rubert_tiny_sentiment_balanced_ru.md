---
layout: model
title: Russian BertForSequenceClassification Tiny Cased model (from cointegrated)
author: John Snow Labs
name: bert_classifier_rubert_tiny_sentiment_balanced
date: 2023-10-27
tags: [ru, open_source, bert, sequence_classification, classification, onnx]
task: Text Classification
language: ru
edition: Spark NLP 5.1.4
spark_version: 3.4
supported: true
engine: onnx
annotator: BertForSequenceClassification
article_header:
  type: cover
use_language_switcher: "Python-Scala-Java"
---

## Description

Pretrained BertForSequenceClassification model, adapted from Hugging Face and curated to provide scalability and production-readiness using Spark NLP. `rubert-tiny-sentiment-balanced` is a Russian model originally trained by `cointegrated`.

## Predicted Entities

`negative`, `neutral`, `positive`

{:.btn-box}
<button class="button button-orange" disabled>Live Demo</button>
<button class="button button-orange" disabled>Open in Colab</button>
[Download](https://s3.amazonaws.com/auxdata.johnsnowlabs.com/public/models/bert_classifier_rubert_tiny_sentiment_balanced_ru_5.1.4_3.4_1698379765590.zip){:.button.button-orange.button-orange-trans.arr.button-icon}
[Copy S3 URI](s3://auxdata.johnsnowlabs.com/public/models/bert_classifier_rubert_tiny_sentiment_balanced_ru_5.1.4_3.4_1698379765590.zip){:.button.button-orange.button-orange-trans.button-icon.button-copy-s3}

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

seq_classifier = BertForSequenceClassification.pretrained("bert_classifier_rubert_tiny_sentiment_balanced","ru") \
    .setInputCols(["document", "token"]) \
    .setOutputCol("class")

pipeline = Pipeline(stages=[documentAssembler, tokenizer, seq_classifier])

data = spark.createDataFrame([["PUT YOUR STRING HERE"]]).toDF("text")

result = pipeline.fit(data).transform(data)
```
```scala
val documentAssembler = new DocumentAssembler()
      .setInputCols(Array("text"))
      .setOutputCols(Array("document"))

val tokenizer = new Tokenizer()
    .setInputCols("document")
    .setOutputCol("token")

val seq_classifier = BertForSequenceClassification.pretrained("bert_classifier_rubert_tiny_sentiment_balanced","ru")
    .setInputCols(Array("document", "token"))
    .setOutputCol("class")

val pipeline = new Pipeline().setStages(Array(documentAssembler, tokenizer, seq_classifier))

val data = Seq("PUT YOUR STRING HERE").toDS.toDF("text")

val result = pipeline.fit(data).transform(data)
```

{:.nlu-block}
```python
import nlu
nlu.load("ru.classify.bert.sentiment.tiny").predict("""PUT YOUR STRING HERE""")
```
</div>

{:.model-param}
## Model Information

{:.table-model}
|---|---|
|Model Name:|bert_classifier_rubert_tiny_sentiment_balanced|
|Compatibility:|Spark NLP 5.1.4+|
|License:|Open Source|
|Edition:|Official|
|Input Labels:|[document, token]|
|Output Labels:|[class]|
|Language:|ru|
|Size:|44.2 MB|
|Case sensitive:|true|
|Max sentence length:|256|

## References

References

- https://huggingface.co/cointegrated/rubert-tiny-sentiment-balanced
- https://github.com/sismetanin/sentiment-analysis-in-russian