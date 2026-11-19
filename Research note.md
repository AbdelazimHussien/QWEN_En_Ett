# Research Note: Weight-Space Programming for Swedish Grammar
## 1.	Critically examine the research

From my opinion:
### a.	The article strongest idea
is that weight-space programming can be used as an alternative way instead of doing fine tuning and retraining a model in every simple change which save sources. So I would handle it like a patch improvement in github x.x.x but the fine tuning will be minor or major release. So the strongest evidence is that it can learn from the neural weights also has the ability to detect the failure in neural like car & ramp. After changing only 3.5 % weights the performance reach 100%.
### b.	Limitation:
The most important limitation is that even the model has been asked a simple questions in experiment 7 it still can not differentiate between the sycophantic model and the real one.
### c.	Conclusion
#### a.	LLM can learn the behaviour from weights and fix some failures
#### b.	Their new approach doesn’t fully replace fine tuning in all cases


## 2.	Form a hypothesis
Can the weight-space programming help in fixing Swedish grammar mistakes like the verb is always in position 2 or En/ett word
### a.	Why this question matters
It will help the Swedish grammer to be correct.
### b.	What results would support my hypothesis
The model can learn that the article is decided based on the final word for example like en tågstaion / ett tågspa or ett sjukhus / en sjukvård
### c.	What evidence would challenge it
The model can only improve the words from example and failure with the new words.


## Results 
I have used Swedish KELLY dataset, selected nouns labeled *en* or *ett*. I have **4501 neuron** and divided them stratified to 70%, 15%, and 15% for training, validation, and testing respectively. we used the following promot ``` Vilken artikel har det svenska substantivet '{noun}'? Svar: '''. A threshold was selected at 0.5 and gives 55% balanced performanced.

Targeted intervention
we use 10 en and 10 ett words from the training. The dimension with the huge difference was 0.2687. The target column was 1463 and applied to 3 other columns  102, 1358, amd 2678.

| Condition | Validation balanced accuracy | Final test balanced accuracy |
|---|---:|---:|
| Unchanged Qwen | 55.0% | 54.6% |
| Targeted column 1463 | 54.0% | 55.0% |
| Random column 102 | 53.0% | Not evaluated |
| Random column 1358 | 55.5% | Not evaluated |
| Random column 2678 | 56.0% | Not evaluated |
| Mean of three random controls | 54.8% | Not evaluated |


### Interpretation

The targeted edit reduced validation balanced accuracy by **1.0 percentage point**.

On the final test set, it improved balanced accuracy by **0.4 percentage points**.

However, two random edits performed better than the targeted edit on validation.

### AI use 
I use chatGPT to understand the experiment number 8 also I use it in some parts of the code, and helping in converting text to mark down.

Make a Recommendation:
If I have more time, I would investigate more on how to choose the weights to updates. Also, I would train the model on how to use the last word to know either ett/en. I would also make sure the verb comes in the second position. I would repeat the experiment with different settings


## Reproducibility
Model  `Qwen/Qwen3-0.6B`
